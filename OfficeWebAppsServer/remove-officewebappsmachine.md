---
title: Remove-OfficeWebAppsMachine
TOCTitle: Remove-OfficeWebAppsMachine
ms:assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219440(v=office.15)
ms:contentKeyID: 48409063
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Remove-OfficeWebAppsMachine

 

_**Applies to:** Office Web Apps Server_


Removes the current server from the Office Web Apps Server farm.

## Syntax

```PowerShell
Remove-OfficeWebAppsMachine 
      [-Confirm [<SwitchParameter>]] 
      [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

The **Remove-OfficeWebAppsMachine** cmdlet removes the current server from the Office Web Apps Server farm. As part of this process, the cmdlet removes the web applications and shuts down the services that are related to Office Web Apps Server. If you cannot run the **Remove-OfficeWebAppsMachine** cmdlet from the server that you want to remove, use the **Repair-OfficeWebAppsFarm** cmdlet from any other server in the Office Web Apps farm.


> [!NOTE]
> If the local server is designated as the master server in the Office Web Apps Server farm, you cannot remove it from the farm until you assign a different server as master by using the <STRONG>Set-OfficeWebAppsMachine</STRONG> cmdlet, or until you remove all other servers from the farm.



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
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```
Remove-OfficeWebAppsMachine
```

This example removes the current server from the Office Web Apps Server farm.

## See also


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

