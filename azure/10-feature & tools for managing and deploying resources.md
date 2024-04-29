# Azure Management and Deployment

This module introduces various Azure features and tools that assist in managing and deploying resources across Azure, on-premises, and multicloud environments.

| Feature               | Description                                                              | Example Code Snippet                                                                                                       |
| --------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| **Azure Portal**      | Web-based UI for managing Azure resources.                               | GUI-based, no code snippet.                                                                                                |
| **Azure Cloud Shell** | Browser-based shell experience, supports Azure PowerShell and Azure CLI. | `# Access Cloud Shell in Azure Portal`                                                                                     |
| **Azure PowerShell**  | Manages Azure resources using PowerShell cmdlets.                        | `powershell\nConnect-AzAccount\nNew-AzVm -ResourceGroupName 'MyResourceGroup' -Name 'MyVm' -Location 'East US'\n`          |
| **Azure CLI**         | Command-line tool that uses Bash commands for Azure management.          | `bash\naz login\naz group create --name MyResourceGroup --location "East US"\n`                                            |
| **Azure Arc**         | Extends Azure management to hybrid and multicloud environments.          | `bash\naz connectedmachine connect --resource-group MyResourceGroup --name MyServer --location "East US"\n`                |
| **ARM Templates**     | Declarative JSON format for deploying Azure resources.                   | `json\n{"type": "Microsoft.Compute/virtualMachines", "apiVersion": "2019-12-01", "name": "MyVm", "location": "East US"}\n` |
| **Bicep**             | Language for deploying Azure resources, simpler than ARM Templates.      | `bicep\nresource myVm 'Microsoft.Compute/virtualMachines@2020-06-01' = { name: 'MyVm', location: 'East US' }\n`            |

## Tools for Interacting with Azure

### Azure Portal

- **Description**: A web-based, graphical user interface for managing Azure resources.
- **Features**:
  - Build, manage, and monitor applications and services.
  - Create custom dashboards.
  - Configure accessibility options.
  - Continuously updated without downtime.

### Azure Cloud Shell

- **Description**: A browser-based shell experience.
- **Features**:
  - No local installation required.
  - Automatically authenticated with Azure credentials.
  - Supports both Azure PowerShell and Azure CLI.
- **Accessibility**: Available through the Azure portal via the Cloud Shell icon.

### Azure PowerShell

- **Description**: A command-line tool that uses PowerShell cmdlets to manage Azure resources.
- **Capabilities**:
  - Perform management tasks by calling Azure REST APIs.
  - Scripts can be combined for complex operations.
- **Availability**: Installable on Windows, Linux, and Mac; also available via Azure Cloud Shell.

```PowerShell
# Connect to Azure with interactive login
Connect-AzAccount

# Create a new Azure VM
New-AzVm `
    -ResourceGroupName 'MyResourceGroup' `
    -Name 'MyVm' `
    -Location 'East US'

```

### Azure CLI

- **Description**: Similar to Azure PowerShell but uses Bash commands.
- **Capabilities**:
  - Handles discrete tasks and orchestrates complex operations.
- **Availability**: Installable on multiple OS and accessible through Azure Cloud Shell.

```Bash
# Log in to Azure
az login

# Create a resource group
az group create --name MyResourceGroup --location "East US"

```

## Azure Arc

- **Purpose**: Extends Azure management to hybrid and multicloud environments.
- **Capabilities**:
  - Manage non-Azure resources like on-premises servers and multicloud resources as if they were native Azure resources.
  - Utilize Azure services and management capabilities irrespective of the resources' location.

## Azure Resource Manager (ARM)

- **Functionality**: Central management entity for all Azure resources.
- **Features**:
  - Declarative templates for infrastructure management.
  - Consistent management layer across Azure services.
  - Deploy, manage, and monitor resources as a group.
  - Define dependencies and deploy resources in the correct order.
  - Native integration with RBAC and tagging for organization and billing.

### ARM Templates and Bicep

- **ARM Templates**:
  - Use JSON format to define and deploy Azure resources.
  - Ensure resources are deployed in a consistent state with repeatable results.

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Compute/virtualMachines",
      "apiVersion": "2019-12-01",
      "name": "MyVm",
      "location": "East US",
      "properties": {
        "hardwareProfile": {
          "vmSize": "Standard_DS1_v2"
        }
      }
    }
  ]
}
```

- **Bicep**:
  - Simplified language for declaring Azure resources.
  - More concise and readable than JSON ARM templates.
  - Supports modularity and reusability of code.

```Bicep
resource myVm 'Microsoft.Compute/virtualMachines@2020-06-01' = {
  name: 'MyVm'
  location: 'East US'
  properties: {
    hardwareProfile: {
      vmSize: 'Standard_DS1_v2'
    }
  }
}

```
