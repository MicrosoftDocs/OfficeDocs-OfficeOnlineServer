---
title: Get-OfficeWebAppsMachine
TOCTitle: Get-OfficeWebAppsMachine
ms:assetid: 02fadf5e-0382-4e73-8d07-e67d088b1a02
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219432(v=office.15)
ms:contentKeyID: 48409053
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Get-OfficeWebAppsMachine

 

_**Applies to:** Office Web Apps Server_


Returns details about the current server that is in an Office Web Apps Server farm.

## Syntax

```PowerShell
Get-OfficeWebAppsMachine
```

## Detailed Description

The **Get-OfficeWebAppsMachine** cmdlet returns details about the current server that is in a Office Web Apps Server farm. These details include the roles and health status of the current server and the name of the master server for the farm.

## Parameters

## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```PowerShell
Get-OfficeWebAppsMachine
```

This example returns details about the current server that is in a Office Web Apps Server farm.

\------------------EXAMPLE 2---------------------

```PowerShell
(Get-OfficeWebAppsFarm).Machines
```

This example returns details about all servers that are in a Office Web Apps Server farm.

## See also


[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

