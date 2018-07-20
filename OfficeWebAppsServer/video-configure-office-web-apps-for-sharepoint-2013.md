---
title: 'Video: Configure Office Web Apps for SharePoint 2013'
TOCTitle: 'Video: Configure Office Web Apps for SharePoint 2013'
ms:assetid: 0c02633f-3839-448b-ae83-24f24c254179
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn455088(v=office.15)
ms:contentKeyID: 57419939
ms.date: 03/20/2015
mtps_version: v=office.15
---

# Video: Configure Office Web Apps for SharePoint 2013

 

_**Applies to:** Office Web Apps, Office Web Apps Server, SharePoint Foundation 2013, SharePoint Server 2013_


**Summary:** Walks you through the nine main steps for configuring an Office Web Apps Server farm to work with SharePoint 2013.

Configuring Office Web Apps for SharePoint 2013 is a fairly simple process. This video shows how to set up Office Web Apps Server and configure SharePoint 2013 to use Office Web Apps Server in a test environment.


**Watch the "Configuring Office Web Apps for SharePoint 2013" video.**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

This video covers procedures that are performed on two servers: the server that runs Office Web Apps Server, and the server that runs SharePoint 2013. These need to be separate servers, as described in [Software, hardware, and configuration requirements for Office Web Apps Server](plan-office-web-apps-server.md).

**On the server that runs Office Web Apps Server, the video shows how to:**

1\. Open the Windows PowerShell command prompt and install the required roles and services for Office Web Apps Server. See [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md). This is necessary because Office Web Apps Server won’t install if the required roles and services are missing.  
2\. Install Office Web Apps Server software from the [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/p/?linkid=256561). To download Office Web Apps Server you must have a license, under a Volume Licensing agreement, for Office Professional Plus 2013, Office Standard 2013, or Office for Mac 2011. The download is located under those Office products on the VLSC portal.  
3\. Create the Office Web Apps Server farm by using [New-OfficeWebAppsFarm](new-officewebappsfarm.md).  
4\. Verify that the Office Web Apps Server farm was created successfully by opening a browser window and going to http://*ServerName*/hosting/discovery.

**On the server that runs SharePoint 2013, the video shows how to:**

5\. Open the SharePoint 2013 Management Shell.  
6\. Create the binding between Office Web Apps Server and SharePoint 2013 by using [New-SPWOPIBinding](new-spwopibinding.md). This sets up communication between the server that runs SharePoint 2013 and the server that runs Office Web Apps Server.  
7\. View the WOPI zone of SharePoint 2013 by using [Get-SPWOPIZone](get-spwopizone.md). This step highlights the fact that the two servers are using different WOPI zones: SharePoint 2013 is using internal-https, and Office Web Apps Server is using internal-http. The zone needs to match for Office Web Apps to work correctly.  
8\. Change the WOPI zone for SharePoint 2013 by using [Set-SPWOPIZone](set-spwopizone.md) to change the WOPI zone to internal-http.  
9\. Verify that Office Web Apps is working by opening an Office document in a SharePoint 2013 document library.

For more detail about each of these steps, see the following sections in the articles [Deploy Office Web Apps Server](deploy-office-web-apps-server.md) and [Configure Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md).

  - [Prepare servers to run Office Web Apps Server](deploy-office-web-apps-server.md)

  - [Deploy a single-server Office Web Apps Server farm in a test environment](deploy-office-web-apps-server.md)

  - [Prepare to configure SharePoint 2013 to use Office Web Apps Server](configure-office-web-apps-for-sharepoint-2013.md)

  - [Configure SharePoint 2013 to use Office Web Apps Server in a test environment that uses HTTP](configure-office-web-apps-for-sharepoint-2013.md)

## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Plan Office Web Apps (Used with SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)  
[How Office Web Apps work on-premises with SharePoint 2013](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

