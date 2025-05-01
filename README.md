# MiHCM Data Azure AI Agent Template

This repository provides a template for deploying and managing an Azure AI Agent for MiHCM's HR system. The project leverages Azure Bicep for infrastructure deployment and Python for interacting with Azure AI services and APIs.

## Features

- **Azure AI Agent Deployment**: Automates the deployment of Azure AI resources, including AI Hubs, AI Projects, and dependent resources.
- **Integration with MiHCM HR System**: Provides tools to interact with MiHCM's HR APIs for tasks like leave management, feedback handling, and work activity tracking.
- **OpenAPI Integration**: Uses OpenAPI specifications to define and interact with MiHCM's external APIs.

## Project Structure

- `.env` – Environment variables for the project  
- `main.bicep` – Main Bicep file for deploying the AI Agent setup  
- `externalapi.json` – OpenAPI specification for MiHCM's external API  
- `openAPI3Agent.py` – Python script for interacting with Azure AI and MiHCM APIs  
- `requirements.txt` – Python dependencies for the project  
- `modules-mi-agent/` – Bicep modules for modular resource deployment  
  - `add-capability-host.bicep` – Adds capability host resource  
  - `ai-service-role-assignments.bicep` – Sets role assignments for AI services  
  - `standard-ai-hub.bicep` – Deploys standard AI Hub  
  - `standard-ai-project.bicep` – Deploys standard AI Project  
  - `standard-dependent-resources.bicep` – Deploys dependent resources  
- `README.md` – Project documentation  



## Prerequisites

1. **Azure Subscription**: Ensure you have an active Azure subscription.
2. **Azure CLI**: Install the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).
3. **Bicep CLI**: Install the [Bicep CLI](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/install).
4. **Python**: Install Python 3.8 or later.
5. **Dependencies**: Install Python dependencies using `pip install -r requirements.txt`.

## Deployment

### Step 1: Configure Environment Variables

Create a `.env` file in the root directory with the following variables:

```properties
PROJECT_CONNECTION_STRING="<Your AI project key>"
PROJECT_OPENAPI_CONNECTION_NAME="<Connection name of your API key>"
```

### Step 2: Deploy Azure Resources
 - Deploy the resources using the `main.bicep` file.
 - Update `PROJECT_CONNECTION_STRING` with the connection string obtained.

### Step 3: Define the API Key 
- Navigate to your AI Project and add your API Key as a custom key in the below format:
```
Ocp-Apim-Subscription-Key: <your key>
```
- Update the `PROJECT_OPENAPI_CONNECTION_NAME` with the connection name you created.

### Step 4: Run the python script
- Use the `openAPI3Agent.py` script to interact with the deployed Azure AI Agent and MiHCM APIs.
- Update the `agent_request` value with different requests for the agent.
