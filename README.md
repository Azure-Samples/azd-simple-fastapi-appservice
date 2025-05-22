<!--
---
page_type: sample
languages:
- azdeveloper
- python
- bicep
- html
products:
- azure
- azure-app-service
urlFragment: azure-simple-fastapi-appservice
name: Deploy a minimal FastAPI Application on Azure App Service (Python)
description: A tiny, no-frills, template to deploy Python's FastAPI web framework to Azure App Service in the free tier.
---
-->
<!-- YAML front-matter schema: https://review.learn.microsoft.com/en-us/help/contribute/samples/process/onboarding?branch=main#supported-metadata-fields-for-readmemd -->

# Simple FastAPI AZD Template

The most basic FastAPI "hello world" application as an AZD template ready for Azure App Service

![system diagram](diagram.png)

## Usage

1. Install AZD and run the following command to initialize the project.

```bash
azd init --template Azure-Samples/azd-simple-fastapi-appservice
```

This command will clone the code to your current folder and prompt you for the following information:

- `Environment Name`: This will be used as a prefix for the resource group that will be created to hold all Azure resources. This name should be unique within your Azure subscription.

2. Login to your Azure account.
```bash
azd auth login
```

3. Run the following command to build a deployable copy of your application, provision the template's infrastructure to Azure and also deploy the applciation code to those newly provisioned resources.

```bash
azd up
```

This command will prompt you for the following information:
- `Azure Location`: The Azure location where your resources will be deployed.
- `Azure Subscription`: The Azure Subscription where your resources will be deployed.

> NOTE: This may take a while to complete as it executes three commands: `azd package` (builds a deployable copy of your application), `azd provision` (provisions Azure resources), and `azd deploy` (deploys application code). You will see a progress indicator as it packages, provisions and deploys your application.

4. Then make changes to app.py and run `azd deploy` again to update your changes.

## Access the free App Service Tier

As the template comes, it is set to a basic plan (see [pricing](https://azure.microsoft.com/en-au/pricing/details/app-service/windows/#pricing) guide), but if you want to get started for free, you can easily update the template before you run `azd up` to leverage the free plan or the discounted developer plan. 

Go to the [/infra/resources.bicep](https://github.com/Azure-Samples/azd-simple-fastapi-appservice/blob/main/infra/resources.bicep) file and update line 58, where the SKU is currently set to `“B1”`. Change this to `“F1”` to deploy up to 10 App Service apps for free on the **free plan** (or `“D1”`  for the **discounted developer rate** if you have more than 10 to deploy concurrently).  

## Notes

This uses the F1 (free) SKU for app service, which has limited CPU and RAM resources.

See the [pricing calculator](https://azure.microsoft.com/en-au/pricing/calculator/) for details on paid SKUs replace the SKU option with a suitable choice.
