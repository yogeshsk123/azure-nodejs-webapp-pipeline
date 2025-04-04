# Node.js Hello World WebApp Pipeline 🌍

This sample demonstrates a simple **Hello World** Node.js application deployed on **Azure App Service**.
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

## Azure Pipeline ⚡

The following image illustrates the **CI/CD pipeline** for deploying the Node.js application on Azure App Service.

### [Azure Node.js Web App Pipeline](https://raw.githubusercontent.com/atulkamble/azure-nodejs-webapp-pipeline/tree/main/azure-nodejs-webapp-pipeline.png)

<img width="953" alt="Azure Node.js Pipeline" src="https://github.com/atulkamble/azure-nodejs-webapp-pipeline/blob/main/azure-nodejs-webapp-pipeline.png" />

---

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Azure Pipeline](#azure-pipeline)
- [Deployment Commands](#deployment-commands)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

---

## Overview 📌

This project provides a minimal **Node.js** application that can be deployed on **Azure App Service Web App**. It is useful for understanding the basics of deploying a Node.js application to the cloud using **Azure CLI**.

---

## Prerequisites ✅

Before getting started, ensure you have the following:

1. **Node.js** (v16 or later) - [Download Here](https://nodejs.org/)
2. **Azure CLI** - [Install Guide](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
3. **Git** - [Download Here](https://git-scm.com/)
4. **An Azure Account** - [Sign up for Free](https://azure.microsoft.com/free/)
5. **Visual Studio Code** (Optional but recommended) - [Download Here](https://code.visualstudio.com/)



## Deployment Commands 🚀

### Reference Documentation:  
📖 [Azure DevOps Node.js Tutorial](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/nodejs-tutorial?view=azure-devops)

### Steps to Deploy

#### 1️⃣ List Available Azure Locations
```sh
az account list-locations --query "[].{Name: name, DisplayName: displayName}" --output table
```

#### 2️⃣ Set Default Location
```sh
az configure --defaults location=westus2
```

#### 3️⃣ Define Variables
```sh
resourceSuffix=$RANDOM
webName="helloworld-nodejs-${resourceSuffix}"
rgName='hello-world-nodejs-rg'
planName='helloworld-nodejs-plan'
```

#### 4️⃣ Create a Resource Group
```sh
az group create --name $rgName
```

#### 5️⃣ Create an App Service Plan
```sh
az appservice plan create --name $planName --resource-group $rgName --sku B1 --is-linux
```

#### 6️⃣ Create a Web App
```sh
az webapp create --name $webName --resource-group $rgName --plan $planName --runtime "node|16-lts"
```

#### 7️⃣ List Deployed Web Apps
```sh
az webapp list --resource-group $rgName --query "[].{hostName: defaultHostName, state: state}" --output table
```

#### 8️⃣ Delete the Resource Group (if needed)
```sh
az group delete --name hello-world-nodejs-rg
```

---

## Troubleshooting 🛠️

### 1️⃣ Azure CLI Not Recognized
If you encounter an error like:
```
'az' is not recognized as an internal or external command
```
- Ensure that **Azure CLI** is installed correctly.
- Restart your terminal or command prompt.
- Run `az --version` to check if Azure CLI is accessible.

### 2️⃣ Web App Not Deploying
- Confirm that your **resource group** and **App Service plan** exist using:
  ```sh
  az group list --output table
  az appservice plan list --output table
  ```
- Ensure the correct **Node.js runtime version** is specified (`node|16-lts`).
- Restart the web app:
  ```sh
  az webapp restart --name $webName --resource-group $rgName
  ```

### 3️⃣ Web App Not Loading
- Check deployment logs:
  ```sh
  az webapp log tail --name $webName --resource-group $rgName
  ```
- Verify that the correct **port** is used (Azure Web Apps use **port 8080** by default).

---

## Contributing 🤝

👤 **Atul Kamble**  

Contributions are welcome! If you'd like to contribute, please **fork** the repository and submit a **pull request**.

Happy Coding! 🚀


