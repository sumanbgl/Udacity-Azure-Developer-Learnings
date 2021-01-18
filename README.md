# Udacity-Azure-Developer-Learnings
Stores notes on learnings from Udacity Azure Developer program

**January 18, 2021**

**azure cli commands for resource group creation**
```
az account list-locations -o table
az group create --name resource-group-west --location westus2
```

**Azure cli documentation reference**
https://docs.microsoft.com/en-us/cli/azure/

**azure cli commands related to Creating a VM**

Use below command to get public IP of a specific VM

```
az vm list-ip-addresses -g <RESOURCE-GROUP> -n <VIRTUAL-MACHINE-NAME>
```
