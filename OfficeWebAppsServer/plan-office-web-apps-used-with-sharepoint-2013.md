---
title: Plan Office Web Apps (Used with SharePoint 2013)
TOCTitle: Plan Office Web Apps
ms:assetid: 3bd0a617-5f12-4a7e-bb75-b15c86c7e504
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ff431682(v=office.15)
ms:contentKeyID: 48409058
ms.date: 04/08/2015
mtps_version: v=office.15
---

# Plan Office Web Apps (Used with SharePoint 2013)

 

_**Applies to:** Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_


**Summary:** Review planning guidance for Office Web Apps when it is used with SharePoint 2013 on-premises.

**Audience:** IT Professionals

To plan how Office Web Apps is used with SharePoint 2013 on-premises, you should review browser support, SharePoint authentication requirements, and licensing considerations for viewing and editing Office files by using Office Web Apps. Then, you can decide whether you want SharePoint 2013 to use the web browser or a client application when a user opens Office files from a SharePoint 2013 document library.


> [!IMPORTANT]
> This article is part of the <A href="content-roadmap-for-office-web-apps-server.md">Content roadmap for Office Web Apps Server</A>. Use the roadmap as a starting point for articles, downloads, and videos that help you deploy and manage Office Web Apps Server.<BR><STRONG>Are you looking for help with Office Web Apps on your desktop or mobile device?</STRONG> You can find this information by searching for "Office Web Apps" on <A href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</A>.



In this article:

  - About planning for Office Web Apps

  - Browser support for Office Web Apps

  - SharePoint authentication requirements for Office Web Apps

  - Licensing Office Web Apps for editing Office files

  - Considerations for customers who had deployed Office Web Apps with SharePoint 2010

  - Default open behavior for documents opened from SharePoint 2013 document libraries

## About planning for Office Web Apps

The guidance in this article is a subset of the overall planning you’ll do when you deploy Office Web Apps Server on-premises in your organization. For example, hardware, software, and virtualization requirements, farm sizing and topology, and security are all part of Office Web Apps Server planning. After you make those decisions, you can plan how to configure Office Web Apps functionality that is specific to SharePoint 2013. If you haven’t heard of Office Web Apps Server or reviewed its requirements and planning guidance, see [Office Web Apps Server overview](office-web-apps-server-overview.md) and [Plan Office Web Apps Server](plan-office-web-apps-server.md).

## Browser support for Office Web Apps

Browser support for Office Web Apps is the same as for SharePoint 2013. Refer to the article [Plan browser support in SharePoint 2013](https://technet.microsoft.com/en-us/library/cc263526\(v=office.15\)) for more information.

## SharePoint authentication requirements for Office Web Apps

Office Web Apps can be used only by SharePoint 2013 web applications that use claims-based authentication. Office Web Apps rendering and editing will not work on SharePoint 2013 web applications that use classic mode authentication. If you migrate SharePoint 2010 web applications that use classic mode authentication to SharePoint 2013, you must migrate them to claims-based authentication to allow them to work with Office Web Apps. To learn more, see [Migrate from classic-mode to claims-based authentication in SharePoint 2013](https://technet.microsoft.com/en-us/library/gg251985\(v=office.15\)).

## Licensing Office Web Apps for editing Office files

Enterprise customers who are licensed for Office 2013 through a Volume Licensing program can enable Office Web Apps editing for SharePoint 2013 on-premises. This helps make sure that users have Office editing capabilities at home or in other locations where Office clients might not be installed.

For exact details about your license, refer to the Microsoft Software License Terms that is shown when you install Office Web Apps Server. For more information about how licensing works in SharePoint 2013, see [Configure licensing in SharePoint Server 2013](https://technet.microsoft.com/en-us/library/jj219627\(v=office.15\)).

## Considerations for customers who use the database attach method to upgrade from SharePoint 2010

If you installed Office Web Apps together with SharePoint 2010, Office Web Apps will not be available after you upgrade to SharePoint 2013. You must deploy Office Web Apps Server and then connect SharePoint 2013 to it after the content databases are upgraded. You don't have to wait until the site collections are upgraded because Office Web Apps Server supports both the 2010 and 2013 site collection modes in SharePoint 2013. For more information about the database attach method, see [Overview of the upgrade process to SharePoint 2013](https://technet.microsoft.com/en-us/library/cc262483\(v=office.15\)).

## Default open behavior for documents that are opened from SharePoint 2013 document libraries

You can configure whether Word, PowerPoint, Excel, and OneNote files are opened in a client application (if it is installed) or in the browser. By default, after SharePoint 2013 is configured to use Office Web Apps Server, Office files are opened in the browser. There are two ways to change the default behavior to allow client applications to open files directly:

  - **For the SharePoint 2013 farm** You can adjust the default open behavior on a per-file-type basis for the SharePoint 2013 farm by using the [New-SPWOPIBinding](new-spwopibinding.md) and [Set-SPWOPIBinding](set-spwopibinding.md) Windows PowerShell cmdlets.

  - **On site collections or document libraries** Site collection administrators and users can specify whether Office files are opened in the client applications if it is installed. Users can change this setting in the document library properties, and site collection administrators can change this setting in Site Collection Administration or by using the Install-SPFeature cmdlet to install the OpenInClient feature. For more information, see [Install-SPFeature](https://technet.microsoft.com/en-us/library/ff607825\(v=office.15\)).

## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[How Office Web Apps work on-premises with SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  


[Configure SharePoint 2013 Preview to use Office Web Apps Server Preview in a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

