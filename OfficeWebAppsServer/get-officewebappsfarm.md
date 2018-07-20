---
title: Get-OfficeWebAppsFarm
TOCTitle: Get-OfficeWebAppsFarm
ms:assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219434(v=office.15)
ms:contentKeyID: 48409055
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Get-OfficeWebAppsFarm

 

_**Applies to:** Office Web Apps Server_


Returns details about the OfficeWebAppsFarm object that the current server is a member of.

## Syntax

    Get-OfficeWebAppsFarm

## Detailed Description

The **Get-OfficeWebAppsFarm** cmdlet returns details about the OfficeWebAppsFarm object that the current server is a member of. This object represents a group of servers that work as a unit to provide web-based editing and viewing of Office documents. No parameters are used with the **Get-OfficeWebAppsFarm** cmdlet.

## Parameters

## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

    Get-OfficeWebAppsFarm

This example returns details about the OfficeWebAppsFarm object.

\------------------EXAMPLE 2---------------------

    (Get-OfficeWebAppsFarm).Machines

This example returns details about the servers that are members of the Office Web Apps Server farm. These details include the health status and roles held by each server.

## See also


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

