---
title: Update-SPWOPIProofKey
TOCTitle: Update-SPWOPIProofKey
ms:assetid: fe7f3a87-082e-4a43-a5f3-7be41d8e91a3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219460(v=office.15)
ms:contentKeyID: 48409088
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Update-SPWOPIProofKey

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


Updates the public key that is used to connect to the WOPI application on the current SharePoint farm where this cmdlet is run.

## Syntax

```PowerShell
Update-SPWOPIProofKey 
  [-AssignmentCollection <SPAssignmentCollection>] 
  [-ServerName <String>]
```

## Detailed Description

The **Update-SPWOPIProofKey** cmdlet updates the public key that is used to connect to the WOPI application (which could be a server that runs Office Web Apps Server) on the current SharePoint farm where this cmdlet is run. You may want to use this cmdlet if the keys become unsynchronized between the SharePoint farm and the WOPI application. If the keys are unsynchronized, documents may not open in the browser and messages such as “Invalid Proof Signature for file…” or “Invalid Proof Signature for folder...” are found in the Unified Logging System (ULS) logs.

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
<tr class="even">
<td><p><strong>ServerName</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the WOPI application to obtain the key from. This may be a server that runs Office Web Apps Server. If this parameter is missing, public keys for all WOPI applications which are connected to the current SharePoint farm, are updated.</p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\--------------EXAMPLE-----------------

```PowerShell
Update-SPWOPIProofKey -ServerName "Server.corp.Contoso.com"
```

This example obtains the current public key from the WOPI application (such as a server that runs Office Web Apps Server) and updates the key that is stored on the SharePoint farm.

## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Office Web Apps with SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

