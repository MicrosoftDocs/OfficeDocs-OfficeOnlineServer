---
title: Set-SPWOPIBinding
TOCTitle: Set-SPWOPIBinding
ms:assetid: e373528f-e69b-4e25-9df4-3a5f80ab64ac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219454(v=office.15)
ms:contentKeyID: 48409081
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Set-SPWOPIBinding

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Updates the default click action for an application or file name extension binding.

## Syntax

```PowerShell
Set-SPWOPIBinding 
    [-Identity] <SPWopiBindingPipeBind> 
    -DefaultAction <SwitchParameter>
    [-AssignmentCollection <SPAssignmentCollection>] 
    [-Confirm [<SwitchParameter>]] 
    [-WhatIf [<SwitchParameter>]]
```    

## Detailed Description

The **Set-SPWOPIBinding** cmdlet updates the default click action for an application or file name extension binding. For example, you can set the default click action for viewing a Word document in a SharePoint library. To do this, you set the default action to true for the “view”-“Word” bindings.

Typically, you would use the output of the **Get-SPWOPIBinding** command as the value for the -Identity property of this command. For more information, see [Get-SPWOPIBinding](get-spwopibinding.md)


> [!IMPORTANT]
> You can only set bindings that were created by using the <STRONG>New-SPWOPIBinding</STRONG> command. To override a built-in binding, for example the action taken when viewing a Word document in a SharePoint library, create a new binding, using <STRONG>New-SPWOPIBinding</STRONG> and assign a different action. For more information, see <A href="new-spwopibinding.md">New-SPWOPIBinding</A>.



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
<td><p><strong>Identity</strong></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Specifies the binding. Typically, you would use the output of the <strong>Get-SPWOPIBinding</strong> command as the value for the –Identity.</p></td>
</tr>
<tr class="even">
<td><p><strong>DefaultAction</strong></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Specifies whether the binding should be set as the default click action for an application or file name extension in the binding.</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
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
Get-SPWOPIBinding -Action "view" -Application "Word"| Set-SPWOPIBinding -DefaultAction
```

This example sets the default click action to view for a Word document in a SharePoint library. You can verify that the default click action is set to view for Word by running the cmdlet **Get-SPWOPIBinding –Action “view” –Application “Word”**. The **IsDefaultAction** value is set to “True.”

## See also


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  
[New-SPWOPIBinding](new-spwopibinding.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

