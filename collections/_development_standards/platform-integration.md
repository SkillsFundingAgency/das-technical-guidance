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

#### References

* [Managed Identity Documentation](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/)
* [MI Overview - Microsoft](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview)
* [MI Obtain tokens for Azure resources - Microsoft](https://docs.microsoft.com/en-us/azure/app-service/overview-managed-identity?tabs=dotnet#asal)
* [MI Connecting to a SQL database - Microsoft](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-connect-msi)