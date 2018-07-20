---
title: New-SPWOPIBinding
TOCTitle: New-SPWOPIBinding
ms:assetid: 696f01b4-a144-431b-9bae-1c3ede78609d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219441(v=office.15)
ms:contentKeyID: 48409064
ms.date: 10/13/2017
mtps_version: v=office.15
---

# New-SPWOPIBinding

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Creates a new binding to associate file name extensions or applications with actions on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
New-SPWOPIBinding 
    -ServerName <String> 
    [-Action <String>] 
    [-AllowHTTP <SwitchParameter>] 
    [-Application <String>] 
    [-AssignmentCollection <SPAssignmentCollection>] 
    [-Confirm[<SwitchParameter>]] 
    [-Extension <String>] 
    [-FileName <String>] 
    [-ProgId <String>] 
    [-WhatIf[<SwitchParameter>]]
```
   

## Detailed Description

The **New-SPWOPIBinding** cmdlet associates file name extensions or applications to actions on the current SharePoint farm where this cmdlet is run. Each binding allows you to use the WOPI application to view or edit files in your SharePoint library. For example, when a user sees a Word document in a SharePoint document list, the SharePoint list will display the available options to view or edit the document based on the actions that are bound to Word on that SharePoint farm.

To use a WOPI application, such as a server that runs Office Web Apps Server, for Office Web Apps, you must run this cmdlet on the SharePoint farm before you can use the Office Web Apps.

If you run **New-SPWOPIBinding** for an application or file name extension where the binding (or association) already exists, the cmdlet will fail.

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
<td><p><strong>ServerName</strong></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the name or fully qualified domain name (FQDN) of the WOPI application (such as a server that runs Office Web Apps Server).</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the action to bind. For example, “view,” “edit,” and “embedview.” For a list of actions that the WOPI application supports, run <strong>Get-SPWOPIBinding</strong>. Typically, you will not use this parameter. If you specify some actions but not others, some SharePoint features may not work.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHTTP</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Specifies that the cmdlet can use HTTP for discovery of what the WOPI application supports. If this is specified as True, the discovery information from the WOPI application will be sent on a nonsecure connection.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies applications to bind. Possible applications are as follows: “Word,” “Excel,” “PowerPoint,” or “OneNote.” Run <strong>Get-SPWOPIBinding</strong> to get the full list of application the WOPI application supports.</p></td>
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
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the file name extensions to bind. Run <strong>Get-SPWOPIBinding</strong> to get the list of file name extensions the WOPI application supports.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the path of the xml file that contains the discover information for the WOPI application. You can load discovery information from an xml file instead of requesting from the WOPI application directly.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the programmatic identifier (ProgID) for an application to bind. Run <strong>Get-SPWOPIBinding</strong> to get the list of ProgIDs that the WOPI application supports. You may only want to use this parameter to associate an action to an OneNote folder.</p></td>
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

\--------------EXAMPLE 1-----------------

```PowerShell
New-SPWOPIBinding -ServerName "Server.corp.Contoso.com"
```

This example creates bindings for all the applications and file name extensions that the WOPI application supports on the current SharePoint farm where this cmdlet is run.

\--------------EXAMPLE 2-----------------

```PowerShell
New-SPWOPIBinding -ServerName "Server.corp.Contoso.com" -Application "Excel"
```

This example associates Excel with all the actions that the WOPI application supports for Excel on the current SharePoint farm where this cmdlet is run.

## See also


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

