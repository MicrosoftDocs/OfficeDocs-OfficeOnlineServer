---
title: Office Web Apps Server overview
TOCTitle: 'Overview: Office Web Apps Server'
ms:assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219437(v=office.15)
ms:contentKeyID: 48409059
ms.date: 05/27/2017
mtps_version: v=office.15
---

# Office Web Apps Server overview

 

_**Applies to:** Office Web Apps Server_


**Summary:** Learn about Office Web Apps Server and how it provides browser-based Office functionality to supported hosts.

**Audience:** IT Professionals

Office Web Apps Server is a new Office server product that delivers browser-based versions of Word, PowerPoint, Excel, and OneNote. A single Office Web Apps Server farm can support users who access Office files through SharePoint 2013, Lync Server 2013, shared folders, and websites. The new stand-alone deployment model means that you can manage updates to your Office Web Apps Server farm independently of other Office Server products that are deployed in your organization.


> [!IMPORTANT]
> This article is part of the <A href="content-roadmap-for-office-web-apps-server.md">Content roadmap for Office Web Apps Server</A>. Use the roadmap as a starting point for articles, downloads, and videos that help you deploy and manage Office Web Apps Server.<BR><STRONG>Are you looking for help with Office Web Apps on your desktop or mobile device?</STRONG> You can find this information by searching for "Office Web Apps" on <A href="https://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</A>.



In this article:

  - About Office Web Apps Server

  - How SharePoint 2013 uses Office Web Apps Server for viewing and editing Office documents

  - How Lync Server 2013 uses Office Web Apps Server for viewing PowerPoint broadcasts

  - How Office Web Apps Server enables viewing Office files in shared folders and web sites by using Online Viewers

## About Office Web Apps Server

Office Web Apps Server is an Office server product that provides browser-based file viewing and editing services for Office files. Office Web Apps Server works with products and services that support WOPI, the Web app Open Platform Interface protocol. These products, known as hosts, include SharePoint 2013 and Lync Server 2013. An Office Web Apps Server farm can provide Office services to multiple on-premises hosts, and you can scale out the farm from one server to multiple servers as your organization’s needs grow. Although Office Web Apps Server requires dedicated servers that run no other server applications, you can install Office Web Apps Server on virtual machine instances instead.

It is easier to deploy and manage Office Web Apps within your organization now that it is a stand-alone product. If you deploy SharePoint 2013, for example, you no longer have to optimize the SharePoint infrastructure to support Office Web Apps, which in earlier versions was tightly integrated with SharePoint Server 2010. You can also apply updates to the Office Web Apps Server farm separately and at a different frequency than you update SharePoint or Lync Server. Having a stand-alone Office Web Apps Server farm also means that users can view or edit Office files that are stored outside SharePoint Server, such as those in shared folders or other websites. This functionality is provided by a feature known as Online Viewers.

The following illustration shows the differences between the previous deployment model for Office Web Apps and the new stand-alone deployment model for Office Web Apps.

**Differences between the Office Web Apps deployment models**

![Shows the difference between the previous deployment model and the new stand-alone deployment model for Office Web Apps Server](images/JJ219437.f16dd9d1-c9b7-4c8b-a8de-f1f82c0ee1e2(Office.15).gif "Shows the difference between the previous deployment model and the new stand-alone deployment model for Office Web Apps Server")

## How SharePoint 2013 uses Office Web Apps Server for viewing and editing Office documents

When used with SharePoint Server 2013, Office Web Apps Server provides updated versions of Word Web App, Excel Web App, PowerPoint Web App, and OneNote Web App. Users can view and, in some cases, edit Office documents in SharePoint libraries by using a supported web browser on computers and on many mobile devices, such as Windows Phones, iPhones, iPads, and Windows 8 tablets. Among the many new features in Office Web Apps, improved touch support and editing capabilities enable users of iPads and Windows 8 tablets to enjoy editing and viewing Office documents directly from their devices.

The following illustration summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices.

**Viewing and editing capabilities of Office Web Apps**

![A graphic that summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices. It highlights those that are optimized for touch screens.](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "A graphic that summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices. It highlights those that are optimized for touch screens.")


> [!NOTE]
> PowerPoint Broadcast is removed from SharePoint 2013. It is available through OneDrive and Lync Server 2013.



For more information about what’s new in Office Web Apps, see [How Office Web Apps work on-premises with SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md).

## How Lync Server 2013 uses Office Web Apps Server for viewing PowerPoint broadcasts

In Lync Server 2010, PowerPoint presentations are viewed in one of two ways. For users who run Lync 2010, PowerPoint presentations are displayed by using the PowerPoint 97-2003 format and they are viewed by using an embedded copy of the PowerPoint viewer. For users who run Lync Web App, PowerPoint presentations are converted to dynamic HTML files then viewed by using a combination of the customized DHTML files and Silverlight. Although generally effective, this approach did have some limitations:

  - The embedded PowerPoint Viewer (which provided a more optimal viewing experience) is available only on the Windows platform.

  - Many mobile devices (including some of the more popular mobile telephones) do not support Silverlight.
    
    Neither the PowerPoint Viewer nor the DHTML/Silverlight approach supports all the features (including slide transitions and embedded video) found in the more recent editions of PowerPoint.

To help address these issues, and to improve the overall experience of anyone who presents or views PowerPoint presentations, Lync Server 2013 uses Office Web Apps Server to handle PowerPoint presentations. Among other advantages, this new approach allows the following capabilities:

  - Higher-resolution displays and better support for PowerPoint capabilities such as animations, slide transitions, and embedded video.

  - Additional mobile devices can access these presentations. That's because Lync Server 2013 uses standard DHTML and JavaScript to broadcast PowerPoint presentations instead of customized DHTML and Silverlight.

  - Users who have appropriate privileges can scroll through a PowerPoint presentation independent of the presentation itself. For example, while Ken Myer is presenting his slide show, Pilar Ackerman can scroll through and view any slide she wishes, all without affecting Ken's presentation.

For more information about how to configure Lync Server 2013 to use Office Web Apps Server, see [Deploying Office Web Apps Server and Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902).

## How Office Web Apps Server enables users to view Office files in shared folders and websites by using Online Viewers

Online Viewers enable users to use a web browser to view Excel, PowerPoint and Word files that are stored on web servers or shared folders in an organization. Users can conveniently view Office files in a web browser without having to open a separate application. In addition, Online Viewers do not require Office 2013 to be installed on users’ computers. Online Viewers also generate the code that is required to link or embed the URL inside a webpage. You can use Online Viewers within your Intranet, or on the Internet.

Office Web Apps Server provides a page at the address http://*OfficeWebAppsServername*/op/generate.aspx that you can use to generate links to publicly available documents that have UNC or URL addresses. When a user selects a generated URL, Online Viewers enable Office Web Apps Server to get the file from its location and then render it by using Office Web Apps. The user can view the Word, Excel, or PowerPoint file in a browser with Office features intact. Formatting and layout in Word documents are preserved, data in Excel workbooks can be filtered and sorted, and animations play in PowerPoint presentations. However, be aware that Online Viewers allow users to view but not edit files, and Online Viewers can't open any files that require authentication.

You can find more about Online Viewers in [Planning for Online Viewers](plan-office-web-apps-server.md).


> [!NOTE]
> Microsoft hosts an Internet-only facing version of Create URL on <A href="http://go.microsoft.com/fwlink/?linkid=256548%26clcid=0x409">Office.com</A>.



## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Plan Office Web Apps Server](plan-office-web-apps-server.md)  
[Deploy Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

