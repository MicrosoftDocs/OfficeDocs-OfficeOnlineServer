---
title: New-OfficeWebAppsMachine
TOCTitle: New-OfficeWebAppsMachine
ms:assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219449(v=office.15)
ms:contentKeyID: 48409075
ms.date: 07/25/2014
mtps_version: v=office.15
---

# New-OfficeWebAppsMachine

 

_**Applies to:** Office Web Apps Server_


Adds the current server to an existing Office Web Apps Server farm.

## Syntax

```PowerShell
New-OfficeWebAppsMachine 
    [-MachineToJoin] <String> 
    [-Confirm[<SwitchParameter>]] 
    [-Force <SwitchParameter>] 
    [-Roles <String[]>] 
    [-WhatIf[<SwitchParameter>]]
```

## Detailed Description

The **New-OfficeWebAppsMachine** cmdlet adds the current server to an existing Office Web Apps Server farm and optionally sets one or more roles on the new server.

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
<td><p><strong>MachineToJoin</strong></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the name of any server that is already a member of the Office Web Apps Server farm.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Assumes the answer to any user prompt is Yes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Roles</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String[]</p></td>
<td><p>Specifies one or more server roles, separated by commas, to assign to the new server. If no roles are specified, then the server is assigned all roles.</p>
<p>The role types are as follows:</p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">

> [!IMPORTANT]
> As a best practice, we recommend that all servers in an Office Web Apps Server farm run all roles. Assigning roles is not useful until the Office Web Apps Server farm contains approximately 50 servers.


</div></td>
</tr>
<tr class="odd">
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

```PowerShell
New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com
```

This example adds the current server to the Office Web Apps Server farm that is running on the server named server1.contoso.com.

## See also


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

