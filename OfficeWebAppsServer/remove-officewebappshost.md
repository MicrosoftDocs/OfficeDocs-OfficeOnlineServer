---
title: Remove-OfficeWebAppsHost
TOCTitle: Remove-OfficeWebAppsHost
ms:assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219453(v=office.15)
ms:contentKeyID: 48409080
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Remove-OfficeWebAppsHost

 

_**Applies to:** Office Web Apps Server_


Removes a host domain from the Allow List for an Office Web Apps Server farm.

## Syntax

```PowerShell
Remove-OfficeWebAppsHost 
      -Domain <String>
```

## Detailed Description

The **Remove-OfficeWebAppsHost** cmdlet removes the specified host domain from the Allow List. The Allow List contains the host domains to which Office Web Apps Server allows file operations requests.


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
<td><p>Specifies the host domain to remove from the Allow List.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```PowerShell
Remove-OfficeWebAppsHost -domain "contoso.com"
```

This example removes the domain contoso.com from the Allow List.

## See also


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Get-OfficeWebAppsHost](get-officewebappshost.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

