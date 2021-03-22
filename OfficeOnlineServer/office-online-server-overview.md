---
title: Office Online Server overview
description: Learn about Office Online Server and how it provides browser-based Office functionality to supported hosts.
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
---


# Office Online Server overview

 **Summary:** Learn about Office Online Server and how it provides browser-based Office functionality to supported hosts.
  
    
    


 **Audience**: IT Professionals
  
    
    


Office Online Server delivers browser-based versions of Word, PowerPoint, Excel, and OneNote. A single Office Online Server farm can support users who access Office files through SharePoint Server, Exchange Server, shared folders, and web sites.
  
    
    


> [!IMPORTANT]
> **Are you looking for help with Office Online on your desktop or mobile device?** You can find this information by searching for "Office Online" on [Office Support](https://go.microsoft.com/fwlink/p/?LinkId=324961). 
  
    

## About Office Online Server
<a name="about"> </a>

Office Online Server is an Office server product that provides browser-based file viewing and editing services for Office files. Office Online Server works with products and services that support WOPI, the Web app Open Platform Interface protocol. These products, known as hosts, include SharePoint Server, and Exchange Server. An Office Online Server farm can provide Office services to multiple on-premises hosts, and you can scale out the farm from one server to multiple servers as your organization's needs grow. Office Online Server requires dedicated servers that run no other server applications, however, you can install Office Online Server on virtual machines if needed.
  
    
    
With Office Online Server, users can also view Office files that are stored outside SharePoint Server, such as those in shared folders or other web sites. This functionality is provided by a feature known as Online Viewers.
  
    
    

## How SharePoint Server uses Office Online Server for viewing and editing Office documents
<a name="sharepoint"> </a>

When used with SharePoint Server 2016, Office Online Server provides Word Online, Excel Online, PowerPoint Online, and OneNote Online. Users can view and, in some cases, edit Office documents in SharePoint libraries by using a supported web browser on computers and on many mobile devices, such as Windows Phones, iPhones, iPads, and Windows tablets.
  
    
    
Note that Office Online Server only works with SharePoint web applications that use claims-based authentication.
  
    
    
The following illustration summarizes the viewing and editing capabilities of Office Online on different kinds of devices.
  
    
    

**Viewing and editing capabilities of Office Web Apps**



![A graphic that summarizes the viewing and editing capabilities of Office Web Apps on different kinds of devices. It highlights those that are optimized for touch screens.](images/WAC-SupportedViewEdit-Platforms.gif)



Excel Online includes external data connectivity and data refresh features similar to those found in Excel Services in SharePoint Server 2013. (Excel Services has been removed from SharePoint in SharePoint Server 2016 - you use Excel Online instead.)
  
    
    

## How Exchange Server and Outlook Web App use Office Online Server for previewing Office file attachments
<a name="exchange"> </a>

When Exchange Server is configured to use Office Online Server, users of Outlook Web App can preview Office file attachments by using Word Online, Excel Online, and PowerPoint Online. These previews provide rich, full-fidelity viewing of Office files and any comments within them, without downloading the files before viewing them. 
  
    
    
By default, the following file types are displayed using Office Online Server:
  
    
    

- Word documents (doc, docx, dotx, dot, dotm extensions)
    
  
- Excel documents (xls, xlsx, xlsm, xlm, xlsb extensions)
    
  
- PowerPoint documents (ppt, pptx, pps, ppsx, potx, pot, pptm, potm, ppsm extensions)
    
  

> [!NOTE]
> Office Online Server won't be used to render any attachments in IRM protected messages. 
  
    
    

Office Online integration for attachment previews is available to all Exchange Online customers. Exchange on-premises customers have to deploy Office Online Server to enable the functionality.
  
    
    
For more information about how to configure Exchange Server to use Office Online Server, see  [Office Online Server Integration](/Exchange/plan-and-deploy/install-office-online-server).
  
    
    

## How Office Online Server enables users to view Office files in shared folders and websites by using Online Viewers
<a name="onlineviewers"> </a>

Online Viewers enable users to use a web browser to view Excel, PowerPoint and Word files that are stored on web servers or shared folders in an organization. Users can conveniently view Office files in a web browser without having to open a separate application. In addition, Online Viewers do not require Office to be installed on users' computers. Online Viewers also generate the code that is required to link or embed the URL inside a webpage. You can use Online Viewers within your Intranet, or on the Internet.
  
    
    
Office Online Server provides a page at the address http:// _OfficeWebAppsServername_/op/generate.aspx that you can use to generate links to publicly available documents that have UNC or URL addresses. When a user selects a generated URL, Online Viewers enable Office Online Server to get the file from its location and then render it by using Office Online. The user can view the Word, Excel, or PowerPoint file in a browser with Office features intact. Formatting and layout in Word documents are preserved, data in Excel workbooks can be filtered and sorted, and animations play in PowerPoint presentations. However, be aware that Online Viewers allow users to view but not edit files, and Online Viewers can't open any files that require authentication.
  
    
    
You can find more about Online Viewers in  [Planning for Online Viewers with Office Online Server](plan-office-online-server.md#viewers).
  
    
    

> [!NOTE]
> Microsoft hosts an Internet-only facing version of Create URL on  [Office.com](https://office.com). 
  
    
    


## See also
<a name="onlineviewers"> </a>


#### 


  
    
    
 [Plan Office Online Server](plan-office-online-server.md)
  
    
    
 [Deploy Office Online Server](deploy-office-online-server.md)