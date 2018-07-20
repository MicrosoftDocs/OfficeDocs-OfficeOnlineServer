---
title: Repair-OfficeWebAppsFarm
TOCTitle: Repair-OfficeWebAppsFarm
ms:assetid: 083d8e25-ce82-4884-9bbc-06375185011c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219433(v=office.15)
ms:contentKeyID: 48409054
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Repair-OfficeWebAppsFarm

 

_**Applies to:** Office Web Apps Server_


Removes all servers flagged as unhealthy from an Office Web Apps Server farm.

## Syntax

```PowerShell
Repair-OfficeWebAppsFarm 
      [-Confirm [<SwitchParameter>]] 
      [-Force <SwitchParameter>] 
      [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

The **Repair-OfficeWebAppsFarm** cmdlet removes all servers flagged as unhealthy from a Office Web Apps Server farm. This cmdlet updates the farm topology but does not clean up services and web applications on the servers that are removed. For this reason, we recommend making every effort to run the **Remove-OfficeWebAppsMachine** cmdlet from the unhealthy servers so that they are cleanly removed from the farm. Use the **Repair-OfficeWebAppsFarm** cmdlet only if the unhealthy servers have failed and you cannot run the **Remove-OfficeWebAppsMachine** cmdlet directly on them.

If there are multiple unhealthy servers, you are prompted before each server is removed. If there are no unhealthy servers, this cmdlet does nothing.

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
<td><p><strong>Force</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Assumes the answer to any user prompt is Yes.</p></td>
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
(Get-OfficeWebAppsFarm).Machines
```

This example displays the health status of all servers in the Office Web Apps Server farm.

\------------------EXAMPLE 2---------------------

```PowerShell
Repair-OfficeWebAppsFarm
```

This example removes all unhealthy servers from the Office Web Apps Server farm.

## See also


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

