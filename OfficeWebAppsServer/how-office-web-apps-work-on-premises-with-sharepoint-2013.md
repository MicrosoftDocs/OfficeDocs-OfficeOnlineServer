---
title: How Office Web Apps work on-premises with SharePoint 2013
TOCTitle: Office Web Apps on-premises with SharePoint 2013
ms:assetid: 8480064e-14a4-4b46-ad6b-0c836b192af2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ff431685(v=office.15)
ms:contentKeyID: 48409067
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How Office Web Apps work on-premises with SharePoint 2013

 

_**Applies to:** SharePoint Server 2013, SharePoint Foundation 2013, Office Web Apps_


**Summary:** Provides information about Office Web Apps, Office Web Apps Server, and how they work on-premises with SharePoint 2013.

**Audience:** IT Professionals

When used together with SharePoint Server 2013, Office Web Apps Server provides updated versions of Word Web App, Excel Web App, PowerPoint Web App, and OneNote Web App. Users can view and, in some cases, edit Office documents in SharePoint libraries by using a supported web browser on computers and on many mobile devices, such as Windows Phones, iPhones, iPads, Windows 8 tablets, and Android devices.


**Figure: The viewing and editing capabilities of Office Web Apps on different kinds of devices.**

![A graphic that summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices. It highlights those that are optimized for touch screens.](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "A graphic that summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices. It highlights those that are optimized for touch screens.")

## Office Web Apps Server is now installed as a stand-alone server

Office Web Apps is not installed on the same servers that run SharePoint 2013. Instead, you deploy one or more physical or virtual servers that run Office Web Apps Server. Then you configure the SharePoint 2013 farm to use the Office Web Apps Server farm to provide Office Web Apps functionality to users who create or open Office files from SharePoint libraries. For more information, see [Office Web Apps Server overview](office-web-apps-server-overview.md).

## Options for licensing Office Web Apps when used with SharePoint 2013

Office Web Apps licensing offers two options:

  - **View-only**. By default, Office Web Apps is view-only. View-only functionality is provided for free.

  - **Edit and view**. You’ll need to purchase an editing license to use the editing features of Office Web Apps with SharePoint 2013. You enable editing when you create the Office Web Apps Server farm.

If your organization licenses Office 2013 through a Volume Licensing program, you can enable Office Web Apps editing for SharePoint 2013 on-premises. This helps make sure that users have Office editing capabilities at home or in other locations where Office clients might not be installed. Editing licenses for Office Web Apps are not available for separate purchase.

For exact details about your license, refer to the Microsoft Software License Terms that is shown when you install Office Web Apps Server.

SharePoint 2013 provides new license enforcement that works with Office Web Apps. If you enable SharePoint licensing and then enable Office Web Apps editing, only the users who have the appropriate license can actually edit Office files in a browser. If no Office Web Apps editing licenses are applied for users, only viewing is supported.

For more information about how licensing works in SharePoint 2013, see [Configure licensing in SharePoint Server 2013](https://technet.microsoft.com/en-us/library/jj219627\(v=office.15\)). The EditingEnabled parameter that enables editing is described in [New-OfficeWebAppsFarm](new-officewebappsfarm.md) and [Set-OfficeWebAppsFarm](set-officewebappsfarm.md).

Files that are sent by the Share by link feature in SharePoint 2013 can be edited in Office Web Apps even when no editing license is present and when editing is disabled for the Office Web Apps Server farm.

## Use Office Mobile Viewers to access files on SharePoint sites

Office Web Apps Server provides Office Mobile Viewers to make Office Web Apps available to mobile users who access SharePoint Server sites. Office Mobile Viewers are enabled by default, but can be disabled by the SharePoint Server site administrator. When they’re enabled, users can navigate to the SharePoint Server site by using the browser on their mobile device, tap the document they want to open in the SharePoint Server library, and the document will open in the mobile browser.

You can find more details about SharePoint libraries on mobile devices in [What's new for mobile devices in SharePoint 2013](https://technet.microsoft.com/en-us/library/fp161352\(v=office.15\)) and [Overview of mobile devices and SharePoint Server 2013](https://technet.microsoft.com/en-us/library/fp161351\(v=office.15\)). Users can learn more about how to use Office Mobile Viewers on their mobile device in [Use Office Web Apps on your Android, iPhone, or Windows Phone](http://go.microsoft.com/fwlink/p/?linkid=271045). If you decide to disable Office Mobile Viewers on SharePoint 2013, use the [Remove-SPWOPIBinding](remove-spwopibinding.md) cmdlet.

## Differences between Excel Web App and Excel Services in SharePoint

Excel Web App and Excel Services in SharePoint have a lot in common, but they are not the same. Excel Services is available only in the Enterprise edition of SharePoint Server 2013. Excel Web App is available in SharePoint Server 2013 and SharePoint Foundation 2013. Both applications enable you to view workbooks in a browser window, and both enable you to interact with and explore data.

But there are certain differences between Excel Web App and Excel Services in SharePoint. For example, Excel Services supports external data connections, data models, and the ability to interact with items that use data models (such as PivotChart reports, PivotTable reports and timeline controls). Excel Services provides more business intelligence functionality than Excel Web App, but Excel Services does not enable users to create or edit workbooks in a browser window.

For details about the differences between the Excel Web App and Excel Services, see [Overview of Excel Services in SharePoint Server 2013](https://technet.microsoft.com/en-us/library/ee424405\(v=office.15\)) and [Comparing Excel Services in SharePoint to Excel Web App](http://go.microsoft.com/fwlink/p/?linkid=255460).

If your organization decides to use Excel Services instead of Excel Web App to view workbooks in the browser, you can use the Windows PowerShell **New-SPWOPISuppressionSettings** cmdlet to turn off Excel Web App for Excel workbooks. For more information, see [New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md).

## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Plan Office Web Apps (Used with SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
  

[](plan-office-web-apps-used-with-sharepoint-2013.md)

