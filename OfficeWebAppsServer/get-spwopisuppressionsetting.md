---
title: Get-SPWOPISuppressionSetting
TOCTitle: Get-SPWOPISuppressionSetting
ms:assetid: a7924964-e16f-4eca-be91-7aff8d45e0c6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219445(v=office.15)
ms:contentKeyID: 48409070
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Get-SPWOPISuppressionSetting

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Returns the suppression settings on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
Get-SPWOPISuppressionSetting 
    [-AssignmentCollection <SPAssignmentCollection>]
```

## Detailed Description

The **Get-SPWOPISuppressionSetting** cmdlet returns the suppression settings on the current SharePoint farm where this cmdlet is run.

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
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>Manages objects for the purpose of proper disposal. Use of objects, such as <strong>SPWeb</strong> or <strong>SPSite</strong>, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the <strong>SPAssignment</strong> object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When <strong>SPWeb</strong>, <strong>SPSite</strong>, or <strong>SPSiteAdministration</strong> objects are used, the objects are automatically disposed of if an assignment collection or the <strong>Global</strong> parameter is not used.</p>
<div class="alert">

> [!NOTE]
> When the <STRONG>Global</STRONG> parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the <STRONG>Stop-SPAssignment</STRONG> command, an out-of-memory scenario can occur.


</div></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\--------------EXAMPLE-----------------

```PowerShell
Get-SPWOPISuppressionSetting
```

This example returns all the suppression settings on the current SharePoint farm where this cmdlet is run. The suppression settings returned include the **DocType** and **WOPIAction**.

## See also


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

