---
title: Set-OfficeWebAppsMachine
TOCTitle: Set-OfficeWebAppsMachine
ms:assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219448(v=office.15)
ms:contentKeyID: 48409074
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Set-OfficeWebAppsMachine

 

_**Applies to:** Office Web Apps Server_


Changes the settings of the current server that is in an Office Web Apps Server farm.

## Syntax

```PowerShell
Set-OfficeWebAppsMachine 
    [-Confirm [<SwitchParameter>]] 
    [-Master <String>] [-Roles <String[]>] 
    [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

The **Set-OfficeWebAppsMachine** cmdlet changes the settings of the current server that is in an Office Web Apps Server farm. The settings include the roles held by the current server and the designated master server for the farm.

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
<td><p><strong>Master</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p></p>
<p>Specifies the server that stores the master farm configuration files.</p>
<p>If you set the local server as the master, you must run <strong>Set-OfficeWebAppsMachine -Master</strong> on all of the remaining servers in the Office Web Apps Server farm to point them to the new master.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Roles</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String[]</p></td>
<td><p>Specifies the list of server roles to assign to the local server, separated by commas.</p>
<p>The role types are as follows:</p>
<p><strong>All</strong></p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">

> [!IMPORTANT]
> As a best practice, we recommend that all servers in an Office Web Apps Server farm run all roles. Assigning roles is not useful until the Office Web Apps Server farm contains approximately 50 servers.


</div></td>
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

```PowerShell
(Get-OfficeWebAppsFarm).Machines
```

This example shows the roles held by each server in the Office Web Apps Server farm.

\------------------EXAMPLE 2---------------------

```PowerShell
Set-OfficeWebAppsMachine -Roles FrontEnd
```

This example configures the current server as a Front End server.

\------------------EXAMPLE 3---------------------

```PowerShell
Set-OfficeWebAppsMachine -Roles All
```

This example configures the current server to host all roles.

## See also


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

