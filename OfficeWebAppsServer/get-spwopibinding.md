---
title: Get-SPWOPIBinding
TOCTitle: Get-SPWOPIBinding
ms:assetid: b757301b-f6c5-43a5-a8ca-2ef33ede0ae8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219450(v=office.15)
ms:contentKeyID: 48409076
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Get-SPWOPIBinding

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Returns a list of bindings that were created by using **New-SPWOPIBinding** on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
Get-SPWOPIBinding 
    [-Action <String>] 
    [-Application <String>] 
    [-AssignmentCollection <SPAssignmentCollection>] 
    [-Extension <String>] 
    [-ProgId <String>] 
    [-Server <String>] 
    [-WOPIZone <String>]
```

## Detailed Description

The **Get-SPWOPIBinding** returns a list of bindings that were created by using **New-SPWOPIBinding** on the current SharePoint farm where this cmdlet is run. Results include actions, applications, file types and zones that are configured for a WOPI application (such as a server that runs Office Web Apps Server).

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
<td><p>Specifies the action to return bindings for.</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the application to return bindings for.</p></td>
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
<td><p><strong>Extension</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the file name extension to return bindings for.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the programmatic identifier (ProgID) for an application to return bindings for.</p></td>
</tr>
<tr class="even">
<td><p><strong>Server</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the name of WOPI application (such as a server that runs Office Web Apps Server) to return bindings for.</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the zone to return bindings for.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\--------------EXAMPLE 1-----------------

```PowerShell
Get-SPWOPIBinding -Server "Server.corp.Contoso.com"
```

This example returns a list of bindings that were created on the current SharePoint farm where this cmdlet is run for the WOPI application "Server.corp.Contoso.com." The WOPI application may be the server that runs Office Web Apps Server.

\--------------EXAMPLE 2-----------------

```PowerShell
Get-SPWOPIZone | Get-SPWOPIBinding
```

This example returns a list of bindings that were created on the current SharePoint farm where this cmdlet is run for the zone configured for the WOPI application.

## See also


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

