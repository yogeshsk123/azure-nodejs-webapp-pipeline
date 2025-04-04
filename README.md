---
page_type: sample
languages:
- nodejs
- javascript
products:
- azure
- azure-app-service
description: "This sample demonstrates a tiny Hello World Node.js app for Azure App Service."
---

# Node.js Hello World

This sample demonstrates a tiny Hello World node.js app for [App Service Web App](https://docs.microsoft.com/azure/app-service-web).

## [azure-nodejs-webapp-pipeline](https://raw.githubusercontent.com/atulkamble/azure-nodejs-webapp-pipeline/tree/main/azure-nodejs-webapp-pipeline.png)
</p>
<img src="https://atulkamble/azure-nodejs-webapp-pipeline/blob/main/azure-nodejs-webapp-pipeline.png" alt="Git" width="50" height="50"/>
</p>


## Commands 

Ref: https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/nodejs-tutorial?view=azure-devops

// Azure CLI
```
az account list-locations --query "[].{Name: name, DisplayName: displayName}" --output table

az configure --defaults location=westus2

resourceSuffix=$RANDOM

webName="helloworld-nodejs-${resourceSuffix}"
rgName='hello-world-nodejs-rg'
planName='helloworld-nodejs-plan'

az group create --name $rgName

az appservice plan create --name $planName --resource-group $rgName --sku B1 --is-linux

az webapp create --name $webName --resource-group $rgName --plan $planName --runtime "node|16-lts"

az webapp list --resource-group $rgName --query "[].{hostName: defaultHostName, state: state}" --output table

az group delete --name hello-world-nodejs-rg
```
## Contributing

- Atul Kamble
