---
title: New-OfficeWebAppsHost
TOCTitle: New-OfficeWebAppsHost
ms:assetid: f1d523ab-45c6-4e3c-b274-22c0d229a6a0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219459(v=office.15)
ms:contentKeyID: 48409087
ms.date: 07/25/2014
mtps_version: v=office.15
---

# New-OfficeWebAppsHost

 

_**Applies to:** Office Web Apps Server_


Adds a host domain to the Allow List for an Office Web Apps Server farm.

## Syntax

```PowerShell
New-OfficeWebAppsHost 
    -Domain <String>
```

## Detailed Description

The **New-OfficeWebAppsHost** cmdlet adds a host domain to the list of host domains to which Office Web Apps Server allows file operations requests, such as file retrieval, metadata retrieval, and file changes. This list, known as the Allow List, is a security feature that prevents unwanted hosts from connecting to a Office Web Apps Server farm and using it for file operations without your knowledge.


> [!TIP]
> You may any domain type including: Public, Pool, Farm, and Active Directory domain names. Just make sure that the domain you're granting access to meets your security requirements.



The wildcard \* is assumed for any domain that is added to the Allow List so that requests to all subdomains are also allowed. For example, if you add the domain contoso.com to the Allow List, Office Web Apps Server also allows requests to the domains corp.contoso.com and dev.contoso.com. Requests to other domains (such as fabrikam.com) are not allowed.


> [!WARNING]
> If there are no domains on the Allow List, Office Web Apps Server allows file requests to hosts in any domain. Do not leave this list blank if your Office Web Apps Server farm is accessible from the Internet. Otherwise anyone can use your Office Web Apps Server farm to view and edit content.



## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Domain</strong></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the domain to add to the Allow List. Do not specify an asterisk or start it with a period.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```PowerShell
New-OfficeWebAppsHost -domain "contoso.com"
```

This example adds the domain contoso.com to the Allow List.


> [!NOTE]
> You cannot add multiple host domains to the Allow List all at the same time. You must run the New-OfficeWebAppsHost cmdlet for each host domain that you want to add to the Allow List.



## See also


[Get-OfficeWebAppsHost](get-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

