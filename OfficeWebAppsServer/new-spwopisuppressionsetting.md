---
title: New-SPWOPISuppressionSetting
TOCTitle: New-SPWOPISuppressionSetting
ms:assetid: 7e6bb8f5-3124-4568-80c6-02cae46b803b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219443(v=office.15)
ms:contentKeyID: 48409066
ms.date: 10/13/2017
mtps_version: v=office.15
---

# New-SPWOPISuppressionSetting

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


The **New-SPWOPISuppressionSetting** cmdlet turns off Office Web Apps for the action, file name extension, or programmatic identifier that you’ve specified on the current SharePoint farm.

## Syntax

```PowerShell
New-SPWOPISuppressionSetting 
    [-Action <String>] 
    [-AssignmentCollection <SPAssignmentCollection>] 
    [-Confirm[<SwitchParameter>]] 
    [-Extension <String>] 
    [-ProgId <String>] 
    [-WhatIf[<SwitchParameter>]]
```

## Detailed Description

The **New-SPWOPISuppressionSetting** cmdlet turns off Office Web Apps for the action, file name extension, or programmatic identifier (ProgId) that you’ve specified on the current SharePoint farm. The cmdlet does this without removing the discovery information or the ability for users to use the SharePoint Share by link feature to send a link to a document and allow the recipient to use Office Web Apps for that document type. You may have to use this cmdlet if you want to use Excel Services to view Excel workbooks instead of the WOPI application (for example Office Web Apps Server).

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
<td><p><strong>Action</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the action to suppress for a given extension or programmatic identifier (ProgId). For example, “view,” “edit,” and “embedview.” For a full list of actions, run <strong>Get-SPWOPIBinding</strong>.</p></td>
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
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the file name extension to suppress. Run Get-SPWOPIBinding to get the list of file name extensions the WOPI application supports.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the programmatic identifier (ProgId) for an application to suppress. Run Get-SPWOPIBinding to get the list of ProgIds that the WOPI application supports.</p></td>
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

\--------------EXAMPLE 1-----------------

```PowerShell
New-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"
New-SPWOPISuppressionSetting -Extension "XLS" -Action "view"
```

This example turns off the ability of a user to use Office Web Apps to view Excel workbooks that have file name extensions “.xlsx” or “.xls”.

## See also


[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

