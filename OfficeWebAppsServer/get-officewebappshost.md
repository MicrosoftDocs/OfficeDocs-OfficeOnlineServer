---
title: Get-OfficeWebAppsHost
TOCTitle: Get-OfficeWebAppsHost
ms:assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219446(v=office.15)
ms:contentKeyID: 48409071
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Get-OfficeWebAppsHost

 

_**Applies to:** Office Web Apps Server_


Returns the list of host domains that are on the Allow List for an Office Web Apps Server farm.

## Syntax

```PowerShell
Get-OfficeWebAppsHost
```

## Detailed Description

The **Get-OfficeWebAppsHost** cmdlet returns the list of host domains to which Office Web Apps Server allows file operations requests, such as file retrieval, metadata retrieval, and file changes. This list, known as the Allow List, is a security feature that prevents unwanted hosts from connecting to an Office Web Apps Server farm and using it for file operations without your knowledge.

The wildcard \* is assumed for any domain that appears on the Allow List so that requests to all subdomains are also allowed. For example, if the domain contoso.com is on the Allow List, then Office Web Apps Server also allows requests to the domains corp.contoso.com and dev.contoso.com. Requests to other domains (such as fabrikam.com) are not allowed.


> [!WARNING]
> If there are no domains on the Allow List, Office Web Apps Server allows file requests to hosts in any domain. Do not leave this list blank if your Office Web Apps Server farm is accessible from the Internet. Otherwise anyone can use your Office Web Apps Server farm to view and edit content.



## Parameters

## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```PowerShell
Get-OfficeWebAppsHost
```

This example returns the host domains that are on the Allow List.

## See also


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

