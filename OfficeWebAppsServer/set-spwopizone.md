---
title: Set-SPWOPIZone
TOCTitle: Set-SPWOPIZone
ms:assetid: bc751cc4-8ac8-45f7-b6ea-da6fcb5473ac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219451(v=office.15)
ms:contentKeyID: 48409077
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Set-SPWOPIZone

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Configures the zone that the current SharePoint farm will use to navigate the browser to the WOPI application.

## Syntax

```PowerShell
Set-SPWOPIZone 
    [[-Zone] <String>] 
    [-AssignmentCollection <SPAssignmentCollection>] 
    [-Confirm [<SwitchParameter>]] 
    [-WhatIf [<SwitchParameter>]]
```


## Detailed Description

The **Set-SPWOPIZone** cmdlet configures the zone that the current SharePoint farm will use to navigate the browser to the WOPI application (such as a server that runs Office Web Apps Server). The SharePoint Server page in the browser creates a frame that contains a page on the WOPI application. The zone for the URL of the WOPI application page is determined by this setting.

If you do not set the zone, the default is “internal-HTTPS.” If you select a zone that is not supported by the WOPI application, Office Web Apps will not work. Only use HTTP when you are on a fully secure network that uses IPSEC (full encryption) or in a test environment that does not contain sensitive data.

SharePoint Management Shell

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
<td><p><strong>Zone</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the zone. For a list of zones that the WOPI application supports, run <strong>Get-SPWOPIBinding</strong>.</p>
<p>If you have a SharePoint farm that's internal and external, specify external. If you have a SharePoint farm that's internal only, specify internal. Only use HTTP when you are on a fully secure network that uses IPSEC (full encryption) or in a test environment that does not contain sensitive data. The options are as follows:</p>
<p>- Internal-HTTP</p>
<p>- Internal-HTTPS</p>
<p>- External-HTTP</p>
<p>- External-HTTPS</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Manages objects for the purpose of proper disposal. Use of objects, such as <strong>SPWeb</strong> or <strong>SPSite</strong>, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the <strong>SPAssignment</strong> object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When <strong>SPWeb</strong>, <strong>SPSite</strong>, or <strong>SPSiteAdministration</strong> objects are used, the objects are automatically disposed of if an assignment collection or the <strong>Global</strong> parameter is not used.</p>
<div class="alert">

> [!NOTE]
> When the <STRONG>Global</STRONG> parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the <STRONG>Stop-SPAssignment</STRONG> command, an out-of-memory scenario can occur.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\--------------EXAMPLE-----------------

```PowerShell
Set-SPWOPIZone -Zone "external-https"
```

This example configures the current SharePoint farm to use external connections through HTTPS to the WOPI application (such as a server that runs Office Web Apps Server).

## See also


[Get-SPWOPIZone](get-spwopizone.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

