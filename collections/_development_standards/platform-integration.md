---
layout: default
title:  "Platform Integration"
category: development_standards
---

## Platform Integration

Below are described the patterns currently in-use across the Service for integrating applications with Azure resources.

### Managed Identities (MI)

Using a managed identity allows an application to authenticate to any service that supports Azure AD authentication without having credentials.  This simplifies configuration which in turn reduces the number of app settings that need to be referenced in code and increases the reliability of the deployment process across multiple environments.  In addition by offloading authentication to Azure AD instead of relying on manually created secrets the security of the service's data will be enhanced.

* Secretless configuration
* Acquiring a bearer token for an API behind Azure AD authentication
* Connecting to a SQL database

The ```Microsoft.Azure.Services.AppAuthentication``` library manages authentication automatically

#### Example - Authenticating with another app service, eg internal API

```csharp
public class ApiClient
{
    private readonly HttpClient _httpClient;

    public ApiClient(IHttpClientFactory httpClientFactory) {
        _httpClient = httpClientFactory.CreateClient();
    }

    public async Task<string> GetAccessTokenAsync(string identifier)
    {
        var azureServiceTokenProvider = new AzureServiceTokenProvider();
        var accessToken = await azureServiceTokenProvider.GetAccessTokenAsync(identifier);
        
        return accessToken;
    }

    # Acquire a bearer token
    var identifier = "https://tenant.onmicrosoft.com/das-env-api-as-ar" # IdentifierUri of Azure AD App registration
    var accessToken = await GetAccessTokenAsync(identifier);

    # Add the token as a header
    _httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);

    # Make an API call
    var response = await _httpClient.GetAsync("https://azurewebsites.net/resource/resourceid");
}
```

#### References

* [Managed Identity Documentation](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/)
* [MI Overview - Microsoft](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview)
* [MI Obtain tokens for Azure resources - Microsoft](https://docs.microsoft.com/en-us/azure/app-service/overview-managed-identity?tabs=dotnet#asal)
* [MI Connecting to a SQL database - Microsoft](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-connect-msi)

### ASP.NET Core Data Protection

Web applications often need to store security-sensitive data. The ASP.NET Core data protection stack is designed to serve as the long-term replacement for the `<machineKey>` element in ASP.NET 1.x - 4.x. One common use of Data Protection is the storing of cookies for apps using the standard ASP.NET Core cookie authentication.

By default, apps hosted on app services have data protection keys that are persisted to the `%HOME%\ASP.NET\DataProtection-Keys` folder. This folder is backed by network storage and is synchronized across all machines hosting the app.

Separate deployment slots (Staging and Production) don't share a key ring, meaning the standard slot swapping deployment that takes place in releases would result in an app using Data Protection to not be able to decrypt stored data using the key ring inside the previous slot.

To maintain zero-downtime releases for Apprenticeship Service applications, data protection keys should be persisted to the environment's Redis Cache, where the redis connection string and database number are in the application's configuration.

#### Example

```csharp
using Microsoft.AspNetCore.DataProtection;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using SFA.DAS.AppName.Configuration;
using StackExchange.Redis;

namespace SFA.DAS.AppName.Web.Startup
{
    public static class DataProtectionStartupExtensions
    {
        public static IServiceCollection AddDataProtection(this IServiceCollection services, IConfiguration configuration, IHostingEnvironment environment)
        {
            if (!environment.IsDevelopment())
            {
                var redisConfiguration = configuration.GetSection(ConfigurationKeys.ConnectionStrings)
                    .Get<AppNameSettings>();

                if (redisConfiguration != null)
                {
                    var redisConnectionString = redisConfiguration.RedisConnectionString;
                    var dataProtectionKeysDatabase = redisConfiguration.DataProtectionKeysDatabase;

                    var redis = ConnectionMultiplexer
                        .Connect($"{redisConnectionString},{dataProtectionKeysDatabase}");

                    services.AddDataProtection()
                        .SetApplicationName("RepositoryName")
                        .PersistKeysToStackExchangeRedis(redis, "DataProtection-Keys");
                }
            }
            return services;
        }
    }
}
```

[Example](https://github.com/SkillsFundingAgency/das-employercommitments-v2/pull/137/files) of persisting data protection keys in an Apprenticeship Service app.

#### References

* [ASP.NET Core Data Protection overview](https://docs.microsoft.com/en-us/aspnet/core/security/data-protection/introduction?view=aspnetcore-5.0)
* [Configuring ASP.NET Core Data Protection](https://docs.microsoft.com/en-us/aspnet/core/security/data-protection/configuration/overview?view=aspnetcore-3.1)
* [Data Protection key management and lifetime in ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/security/data-protection/configuration/default-settings?view=aspnetcore-3.1)

### Logging to Redis and not to File

All applications use NLog to write logs to logging Redis Cache on Azure instances.

The following flow is applied:

1. App Services use NLog to write to our Redis Cache on Azure instances.
1. Each Redis Cache will buffers the logs.
1. Logstash indexes the logs from Redis Cache and performs data transformation and processing.
1. Kibana is used to visualise the data in Elasticsearch.

Logging to file, as configured in the NLog configuration, results in a storage exception such as `There is not enough space on the disk : 'D:\home\site\wwwroot\logs\app-name.YYYY-MM-DD.log'` due to a local cache limit of 1GB being reached.

As Kibana is reliably available and checking logs on individual app services is impractical for debugging, only Redis should be logged to and not File.

For local development, it is useful to log to File.

[Example](https://github.com/SkillsFundingAgency/das-providercommitments/pull/176/files) of NLog configuration, with logging to File for develeopment mode and logging to Redis for non-development mode (running on Azure app services).

#### References

* [App Service local cache size limits](https://docs.microsoft.com/en-us/azure/app-service/overview-local-cache#how-the-local-cache-changes-the-behavior-of-app-service)
