---
title: Remove-SPWOPIBinding
TOCTitle: Remove-SPWOPIBinding
ms:assetid: 52855c21-ee2c-497a-b308-bf5eeabe4bbe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219438(v=office.15)
ms:contentKeyID: 48409060
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Remove-SPWOPIBinding

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Removes bindings for applications, file name extensions, and their associated actions on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
Remove-SPWOPIBinding 
      [[-Identity] <SPWopiBindingPipeBind>] 
      [-AssignmentCollection <SPAssignmentCollection>] 
      [-Confirm[<SwitchParameter>]] 
      [-WhatIf[<SwitchParameter>]]
```

```PowerShell
Remove-SPWOPIBinding 
      [-Action <String>] 
      [-Application <String>] 
      [-AssignmentCollection <SPAssignmentCollection>] 
      [-Confirm[<SwitchParameter>]] 
      [-Extension <String>] 
      [-ProgId <String>] 
      [-Server <String>] 
      [-WhatIf[<SwitchParameter>]] 
      [-WOPIZone <String>]
```

```PowerShell
Remove-SPWOPIBinding 
      [-All <SwitchParameter>] 
      [-AssignmentCollection <SPAssignmentCollection>] 
      [-Confirm[<SwitchParameter>]] 
      [-WhatIf[<SwitchParameter>]]
```

## Detailed Description

The **Remove-SPWOPIBinding** cmdlet removes bindings for applications, file name extensions, and their associated actions on the current SharePoint farm where this cmdlet is run. After you run this cmdlet, you can use **New-SPWOPIBinding** to re-create the bindings as needed. If you remove all the bindings for an application, users cannot use Office Web Apps or the SharePoint Share by link feature for that application. If you remove all the bindings on the SharePoint farm where this cmdlet is run, users cannot use Office Web Apps or the SharePoint Share by link feature for any applications in the SharePoint library.

If you want to stop using Office Web Apps for default clicks, but must preserve the bindings’ discovery information and the ability for users to use the SharePoint Share by link feature to send a link to a document and allow the recipient to use Office Web Apps for that document type, use the **New-SPWOPISuppression** cmdlet instead.

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
<td><p>Optional</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>Specifies the binding.</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the action to remove bindings for. For example, “view,&quot; “edit,&quot; and “embedview.&quot; For a list of actions run <strong>Get-SPWOPIBinding</strong>. Most typically you will not use this parameter. If you specify some actions but not others, some features in SharePoint may not work.</p></td>
</tr>
<tr class="odd">
<td><p><strong>All</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Removes all bindings.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies application to remove bindings for. Possible applications are as follows: “Word,&quot; “Excel,&quot; “PowerPoint,&quot; or “OneNote.&quot; Run <strong>Get-SPWOPIBinding</strong> to get the list of applications.</p></td>
</tr>
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
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the file name extensions to remove bindings for. Run <strong>Get-SPWOPIBinding</strong> to get the list of file name extensions.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the programmatic identifier (ProgID) for an application to remove bindings for. Run <strong>Get-SPWOPIBinding</strong> to get the list of ProgIDs. You may only want to use this parameter to remove bindings for OneNote.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the name of WOPI application (like Office Web Apps Server) to remove bindings for.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the zone to remove bindings for.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\--------------EXAMPLE 1-----------------

```PowerShell
Remove-SPWOPIBinding -Application "Excel"
```

This example removes all bindings for Excel on the current SharePoint farm where this cmdlet is run.

\--------------EXAMPLE 2-----------------

```PowerShell
Remove-SPWOPIBinding -All:$true
```


This example removes all bindings on the current SharePoint farm where this cmdlet is run.

\--------------EXAMPLE 3-----------------

```PowerShell
Get-SPWOPIBinding -Action "MobileView" | Remove-SPWOPIBinding
```

This example removes all bindings for Office Mobile Web Apps on the current SharePoint farm where this cmdlet is run.

## See also


[New-SPWOPIBinding](new-spwopibinding.md)  
[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

