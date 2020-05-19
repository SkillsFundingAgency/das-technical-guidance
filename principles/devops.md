---
layout: default
title:  "DevOps Principles"
---

# DevOps

## Introduction

**DevOps is a service wide way of working, we are all in this together.** It is not the tools, nor is it a single team. It is famously summarised in a single sentance by Donovan Brown (Principal DevOps Manager at Microsoft):

> DevOps is the union of people, process, and products to enable continuous delivery of value to our end users.

We follow this ethos to ensure delivery of value to all of the Digital Apprenticeship Service users, internal and external. It is a combination of the passion, hard work and process that enables DevOps culture within the service. The continuous set of processes that we follow forms the methodology for our Agile planning and continuous delivery, for example aligned sprints across all teams.

Adhereing to DevOps provides the service with the following benefits:

- **Speed and quality.** DevOps speeds up our releases using continuous delivery, encouraging faster feedback, and allowing our developers to fix bugs in the system in the early stages. We can focus on the quality of the services we build and automate processes.

- **Apprenticeship benefits.** With DevOps, we can react to change requests from users faster, adding new features and updating existing. As a result, value-delivery rates increase.

- **Better internal culture.** DevOps principles lead to better communication between our team members, and increased productivity and agility. We are more productive and cross-skilled.

There are many blogs, books and courses on DevOps, and the CAMS model is often written about. The CAMS model was invented by Damon Edwards and John Willis, authors of the famous Podcast, DevOps Cafe. CAMS stands for Culture, Automation, Measurement and Sharing. Using the CAMS model, we can break down our core principles and provide an insight into how we deliver and continuously improve on those principles.

## Culture

The purpose of DevOps in the Apprenticeship Service is to bring unity among the teams so that they all work as a single entity to achieve a goal or rollout new features and services. Working together creates a positive attitude and in turn improves the overall environment for the teams to work in. This enables continuous learning and sharing of skills. All this leads to efficient and innovative development and delivery. These are some of the cultural advantages DevOps provides for the service:

- **Agile ways of working.** Across the service we perform daily collaboration through Agile ceremonies; sprint planning, daily standup, sprint reviews and retrospectives. Support and trust are key to our ways of working which helps enable our continuous delivery. There are also other ceremonies that bring all of the teams together such as the Scrum of Scrums, Clan Leads meeting, Architecture board, Quality Guild and a regular service wide standup.

- **Show and tell.** These are regular meetings that allow teams to celebrate their work and talk about what they’ve learned. It's a chance to bring teams together, share success and improve on collaboration. Progress is highlighted along with question and feedback sessions. Transparency is encouraged to glimpse 'behind the curtain' of the products in development and to highlight where dependencies may exist between teams. A great show and tell session is one that is performed on a regular basis to ensure continuous feedback.

## Automation

This is the most vital factor of the DevOps culture. The purpose of automation is to build a system that eliminates various human errors and provide a successful repeating process with no manual intervention required. Automation greatly improves the workflow and productivity of the service. 

- **Infrastructure as Code (IaC).** IaC is an infrastructure management approach that makes continuous delivery and DevOps possible. Without IaC, our developers and engineers would have to treat each target environment individually, which becomes a tedious task as we have different environments for development, testing, and production use. We include the Azure Resource Manager (ARM) templates and Azure DevOps build definitions along side an applications codebase in the GitHub repository, this is to match the development lifecycle of an application. As application requirements change, so can the build and release along side it. 

- **Cloud infrastructure.** We are a cloud first service as it provides the flexibility, toolsets, and scalability required. All our architectures rely on PaaS solutions. Through IaC and continuous integration and continuous deployment (CI/CD) we can quickly deploy infrastructure and ensure there is no environment or configuration drift. Builds can be deployed to each environment providing consistant dev/test and production environments. It enables our teams to test applications in production-like environments early in the development cycle.

## Measurement

Measurement is all about monitoring and tracking the progress of various activities involved in the DevOps environment. Like Automation, measurement is also important because by measuring the different system metrics, we can know how the system works or what needs to be done to increase performance and productivity etc. for eg. the software development lifecycle.

- **Tracking development lifecycle performance.** Performing CI/CD using Azure DevOps Pipelines, we can measure build times as well as time it takes for a release. By monitoring our CI/CD build and release times can help identify any bottlebecks in the development lifecycle. 

- **Collecting and analysing logs.** Logs are shipped to our logging cloud platform reliably and securely. We can analyse and visualise our logs for all environments. It provides search and data visualisation capabilities for data that is indexed to review and gain insight into the health and activity of our services.

- **Visualising metrics.** Metrics from our cloud infrastructure are visualised in a centralised platform allowing interactive visualisation of our metrics. Using various data sources across the service we create complex monitoring dashboards using interactive query builders. These dashboards provide insight to help identify improvements and generate reporting for the Quality Guild. Our metrics are open and transparent for all stakeholders, it helps drive our value quickly and efficiently ensuring we act on the results we get from the dashboards.

## Sharing

The key success of DevOps in the service is the sharing of tools, discoveries, and knowledge among each of the teams. We create opportunities through collaboration, eliminate redundant work and find people with common interests resulting in better engagement. 

- **Documentation.** All teams create, collaborate, and organise their work in one cloud based platform. 
