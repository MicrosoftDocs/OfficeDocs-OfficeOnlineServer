---
title: Remove-SPWOPISuppressionSetting
TOCTitle: Remove-SPWOPISuppressionSetting
ms:assetid: cbaef5a8-e682-4166-be44-15ab1c79acca
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219452(v=office.15)
ms:contentKeyID: 48409079
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Remove-SPWOPISuppressionSetting

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Removes the suppression settings for a file name extension or programmatic ID and action on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
Remove-SPWOPISuppressionSetting 
      [-Action <String>] 
      [-AssignmentCollection <SPAssignmentCollection>] 
      [-Confirm [<SwitchParameter>]] [-Extension <String>] 
      [-ProgId <String>] 
      [-WhatIf [<SwitchParameter>]]
```      

```PowerShell
Remove-SPWOPISuppressionSetting 
       [-AssignmentCollection <SPAssignmentCollection>] 
       [-Confirm [<SwitchParameter>]] [-Identity <String>] 
       [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

The **Remove-SPWOPISuppressionSetting** cmdlet removes the suppression settings for a file name extension or programmatic indentifier (ProgID) and action on the current SharePoint farm where this cmdlet is run.

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
<td><p>Specifies the action for a given file name extension or programmatic identifier (ProgId). For example, “view,” “edit,” and “embedview.”</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Manages objects for the purpose of proper disposal. Use of objects, such as <strong>SPWeb</strong> or <strong>SPSite</strong>, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the <strong>SPAssignment</strong> object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When <strong>SPWeb</strong>, <strong>SPSite</strong>, or <strong>SPSiteAdministration</strong> objects are used, the objects are automatically disposed of if an assignment collection or the <strong>Global</strong> parameter is not used.</p>
<div class="alert">

> [!NOTE]
> When the <STRONG>Global</STRONG> parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the <STRONG>Stop-SPAssignment</STRONG> command, an out-of-memory scenario can occur.


</div>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the file name extension. Run Get-SPWOPIBinding to get the list of file name extensions the WOPI application supports.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Identity</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies a string that represents a SPWOPISuppressionSetting. Run Get-SPWOPISuppressionSetting to see examples of such strings.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the programmatic identifier (ProgID) for an application to suppress. Run Get-SPWOPIBinding to get the list of ProgIDs that the WOPI application supports.</p></td>
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

\--------------EXAMPLE 1-----------------

```PowerShell
Remove-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"
```

This example removes suppression settings for viewing Excel workbooks that have the file name extension “.xlsx.”

\--------------EXAMPLE 2-----------------

```PowerShell
Get-SPWOPISuppressionSetting | Remove-SPWOPISuppressionSetting
```

This example removes all suppression settings on the current SharePoint farm where this cmdlet is run.

## See also


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

