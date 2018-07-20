---
title: Content roadmap for Office Web Apps Server
TOCTitle: 'Content roadmap: Office Web Apps Server'
ms:assetid: ddf27b4b-c4fc-4ca7-8248-1fd3730b6f3e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn135237(v=office.15)
ms:contentKeyID: 53921643
ms.date: 02/26/2016
mtps_version: v=office.15
---

# Content roadmap for Office Web Apps Server

 

_**Applies to:** Office Web Apps, Office Web Apps Server_


**Summary:** Provides a guide to the articles, downloads, and other resources that help IT professionals deploy and manage Office Web Apps Server.

**Audience:** IT Professionals

![Content roadmap for IT professionals (banner image)](images/Dn135237.38433eef-287a-455e-8dbb-6a85252a5eb8(Office.15).gif "Content roadmap for IT professionals (banner image)")

Office Web Apps Server is a new Office server product that delivers browser-based versions of Word, PowerPoint, Excel, and OneNote. SharePoint 2010 Products do not support Office Web Apps Server.

If you are an IT professional looking for information about Outlook Web App, see [What's New for Outlook Web App in Exchange 2013](http://go.microsoft.com/fwlink/?linkid=282325).


> [!IMPORTANT]
> This article is for administrators who deploy and manage Office Web Apps Server for their organizations.<BR><STRONG>Are you looking for help with Office Web Apps on your desktop or mobile device?</STRONG> You may be looking to <A href="http://go.microsoft.com/fwlink/p/?linkid=269811">get started with Office Web Apps</A>.



The following table describes resources that are available to IT professionals who deploy and manage Office Web Apps Server.

### Office Web Apps Server roadmap for IT pros

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/JJ219456.6b2d6dfa-7dc8-40fb-8335-af68b575f8cb(Office.15).png" title="Getting started" alt="Getting started" /></p></td>
<td><p><strong>Start here</strong></p></td>
<td><p>You want to deploy SharePoint 2013, Lync Server 2013, Exchange Server 2013 or you have a custom solution and you want to know how get Office Web Apps. Let us <a href="http://go.microsoft.com/fwlink/p/?linkid=294929">introduce you to Office Web Apps Server</a>. <a href="office-web-apps-server-overview.md">Office Web Apps Server</a> is an Office server product that provides browser-based file viewing and editing services for Office files. Office Web Apps Server works with products and services that support <a href="http://go.microsoft.com/fwlink/p/?linkid=299202">WOPI, the Web app Open Platform Interface protocol</a>. These products, known as hosts, include <a href="office-web-apps-server-overview.md">SharePoint 2013</a>, <a href="office-web-apps-server-overview.md">Lync Server 2013</a>, and <a href="office-web-apps-server-overview.md">Exchange Server 2013</a>. You can see a high-level overview of what Office Web Apps Server is and how it works in the <a href="http://go.microsoft.com/fwlink/p/?linkid=299305">Office Web Apps Server poster</a>.</p>
<p><strong>Office Web Apps Server Poster</strong></p>
<a href="http://go.microsoft.com/fwlink/p/?linkid=299305"><img src="images/Dn135237.2780a72e-f9df-4201-a9f8-d2811de2e0b4(Office.15).gif" title="Office Web Apps Server Overview poster" alt="Office Web Apps Server Overview poster" /></a>
<p><br />
</p>
<p>Office Web Apps Server also enables users to <a href="office-web-apps-server-overview.md">view Office files in shared folders and websites by using Online Viewers</a>.</p>
<p><br />
</p>
<p>If you have some Excel expert users and business intelligence solutions in your organization, learn about the <a href="how-office-web-apps-work-on-premises-with-sharepoint-2013.md">differences between Excel Web App and Excel Services</a> to decide which you should enable.</p>
<p><br />
</p>
<p>Office Web Apps can be used on <a href="how-office-web-apps-work-on-premises-with-sharepoint-2013.md">many devices</a> such as such as Windows Phones, iPhones, iPads, Windows 8 tablets, and Android devices.</p>
<p><br />
</p>
<p>If you have SharePoint 2013 configured to use Office Web Apps Server, users can <a href="https://technet.microsoft.com/en-us/library/ff718249(v=office.15)">co-author</a> documents in Word, PowerPoint, Excel, and OneNote Web Apps.</p>
<p><br />
</p>
<p>If you want to see how to deploy Office Web Apps Server to use with SharePoint 2013, watch the <a href="video-configure-office-web-apps-for-sharepoint-2013.md">Video: Configure Office Web Apps for SharePoint 2013</a>.</p></td>
</tr>
<tr class="even">
<td><img src="images/Dn135237.b27be6ed-1dcc-481b-a53b-c2a47da9a2df(Office.15).png" title="Plan icon" alt="Plan icon" /></td>
<td><p><strong>Plan Office Web Apps Server</strong></p></td>
<td><p>Before you deploy Office Web Apps Server, make sure that you <a href="plan-office-web-apps-server.md">plan your Office Web Apps Server deployment</a>.</p>
<p><br />
</p>
<p>Software requirements</p>
<p><br />
</p>
<ul>
<li><p>Learn about the <a href="plan-office-web-apps-server.md">software, hardware, and configuration requirements for Office Web Apps Server</a> and the <a href="https://technet.microsoft.com/en-us/ff718249(office.15)#bkmk_sw_version_req">software version requirements for co-authoring in SharePoint 2013 and SharePoint Online</a>.</p></li>
<li><p>If your users have to view documents in languages other than English, <a href="plan-office-web-apps-server.md">plan to download and install language packs for Office Web Apps Server</a>.</p></li>
</ul>
<p><br />
</p>
<p>Hardware, topology, and network planning</p>
<ul>
<li><p>Microsoft IT has deployed Office Web Apps Server by using a <a href="plan-office-web-apps-server.md">topology</a> that can support 200,000 users. By following <a href="plan-office-web-apps-server.md">the topology guidelines</a>, based on our performance tests, an Office Web Apps Server, with two Intel Xeon processors (8 cores), 8 GB of RAM, and a 60 GB hard disk, should support up to 10,000 users where most of the usage is viewing. A server that has a 16 core CPU and 16 GB of RAM should support up to 20,000 users. These results will vary depending on usage patterns and other factors such as network hardware.</p></li>
<li><p>You can <a href="plan-office-web-apps-server.md">secure Office Web Apps Server</a> communications by using HTTPS, by using SSL offloading for hardware load balancers, by restricting which servers can join an Office Web Apps Server farm based on OU membership, or by limiting host access for Office Web Apps Server by using the Allow List.</p></li>
<li><p>Office Web Apps Server requires its own server instance and can't be run with other services or applications, such as SharePoint 2013. If you are limited on hardware, you can <a href="plan-office-web-apps-server.md">virtualize Office Web Apps Server</a>.</p></li>
<li><p>We recommend a <a href="plan-office-web-apps-server.md">load balancing solution</a> when you run Office Web Apps Server on two or more servers. If you use a load balancer, you have to install the certificate on the load balancer. Certificates that are used by Office Web Apps Server have to <a href="plan-office-web-apps-server.md">meet these requirements</a>.</p></li>
<li><p><a href="plan-office-web-apps-server.md">Review the firewall requirements for Office Web Apps Server</a> to help prevent problems caused by firewalls that are blocking communication between the web browser, the servers that run Office Web Apps Server, and the servers that run SharePoint 2013.</p></li>
</ul>
<p><br />
</p>
<p>Planning for software updates</p>
<ul>
<li><p>Before deploying Office Web Apps Server, <a href="plan-office-web-apps-server.md">plan how your organization will manage software updates</a> to your Office Web Apps Server farm. You can't use the Microsoft automatic updates process to apply Office Web Apps Server updates.</p></li>
</ul>
<p><br />
</p>
<p>Planning for SharePoint</p>
<ul>
<li><p>If you'll deploy Office Web Apps Server to use with SharePoint 2013, <a href="plan-office-web-apps-used-with-sharepoint-2013.md">plan Office Web Apps when used with SharePoint 2013</a>.</p></li>
<li><p><a href="https://technet.microsoft.com/en-us/library/cc263526(v=office.15)">Browser support</a> for Office Web Apps is the same as for SharePoint 2013.</p></li>
<li><p>Office Web Apps can be used only by SharePoint 2013 web applications that use <a href="plan-office-web-apps-used-with-sharepoint-2013.md">claims-based authentication</a>.</p></li>
<li><p>Viewing files by using Office Web Apps is free, but you'll need to <a href="plan-office-web-apps-used-with-sharepoint-2013.md">purchase an editing license</a> if you want to <a href="new-officewebappsfarm.md">enable Office Web Apps for editing</a> when Office Web Apps Server is used with SharePoint 2013 on-premises.</p></li>
</ul>
<p><br />
</p>
<p>Planning for other hosts</p>
<ul>
<li><p>If you'll use Exchange Server 2013 as a host for Office Web Apps Server, <a href="http://go.microsoft.com/fwlink/p/?linkid=256611">plan to configure the integration</a>.</p></li>
<li><p>If you'll use Lync Server 2013, <a href="http://go.microsoft.com/fwlink/p/?linkid=256902">plan to configure the integration of Office Web Apps Server and Lync Server 2013</a>.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><img src="images/Dn135237.b27be6ed-1dcc-481b-a53b-c2a47da9a2df(Office.15).png" title="Plan icon" alt="Plan icon" />
<p></p></td>
<td><p><strong>Migrating from Office Web Apps in SharePoint 2010</strong></p></td>
<td><p>Are you currently using SharePoint 2010 Products and plan to migrate to SharePoint 2013? Unfortunately, SharePoint 2010 Products can't be a host for Office Web Apps Server, and Office Web Apps won’t be available after you upgrade to SharePoint 2013. Be sure to <a href="plan-office-web-apps-used-with-sharepoint-2013.md">read about SharePoint authentication requirements</a>. If you used classic mode authentication in SharePoint 2010, you’ll have to <a href="https://technet.microsoft.com/en-us/library/gg251985(v=office.15)">migrate from classic mode to claims-based authentication</a>.</p>
<p><br />
</p>
<p>One of the biggest changes is that you do not install Office Web Apps on the same servers that run SharePoint 2013. <a href="what’s-new-with-office-web-apps-when-used-with-sharepoint-2013.md">What else is new in Office Web Apps when it is used with SharePoint 2013 Products?</a></p></td>
</tr>
<tr class="even">
<td><img src="images/Dn135237.b27be6ed-1dcc-481b-a53b-c2a47da9a2df(Office.15).png" title="Plan icon" alt="Plan icon" />
<p></p></td>
<td><p><strong>Custom WOPI solutions</strong></p></td>
<td><p>If you have a custom solution and want to use that custom solution as a host for Office Web Apps, <a href="http://go.microsoft.com/fwlink/p/?linkid=294933">learn how to create a custom WOPI host</a>.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><img src="images/Dn135237.24ea1871-655b-4e47-baae-4e1d0d3f5875(Office.15).png" title="Deploy icon" alt="Deploy icon" /></td>
<td><p><strong>Deploy Office Web Apps Server</strong></p></td>
<td><p>The first step is to <a href="deploy-office-web-apps-server.md">prepare servers to run Office Web Apps Server</a>. Next <a href="deploy-office-web-apps-server.md">install Office Web Apps Server</a> and apply the latest Office Web Apps Server update. Then <a href="deploy-office-web-apps-server.md">install language packs for Office Web Apps Server</a>.</p>
<p><br />
</p>
<p>To evaluate how Office Web Apps Server works, you can <a href="deploy-office-web-apps-server.md">deploy a single-server Office Web Apps Server farm in a test environment</a>. Or, to deploy something more secure, you can <a href="deploy-office-web-apps-server.md">deploy a single-server Office Web Apps Server farm that uses HTTPS</a>. If you have to support lots of users, you can <a href="deploy-office-web-apps-server.md">deploy a multi-server, load-balanced Office Web Apps Server farm that uses HTTPS</a>.</p>
<p><br />
</p>
<p>After you've deployed Office Web Apps Server, you have to configure the host. You can <a href="configure-office-web-apps-for-sharepoint-2013.md">configure SharePoint 2013</a>, <a href="http://go.microsoft.com/fwlink/p/?linkid=256611">configure Exchange Server 2013</a> and <a href="http://go.microsoft.com/fwlink/p/?linkid=256902">configure Lync Server 2013</a> to use Office Web Apps Server.</p>
<p><br />
</p>
<p>If you want to see what's involved in deploying Office Web Apps Server to use with SharePoint 2013, watch the <a href="video-configure-office-web-apps-for-sharepoint-2013.md">Video: Configure Office Web Apps for SharePoint 2013</a>.</p></td>
</tr>
<tr class="even">
<td><img src="images/Dn135237.91a27517-9536-4d7d-837c-d58fdc94014e(Office.15).png" title="123 steps" alt="123 steps" /></td>
<td><p><strong>Use Office Web Apps</strong></p></td>
<td><p>To help your users get started, check out these resources:</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=272447">Basic tasks in Excel Web App</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=272448">Basic tasks in OneNote Web App</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=272449">Basic tasks in PowerPoint Web App</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=272446">Basic tasks in Word Web App</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><img src="images/Dn135237.5f82327f-16b3-4b96-b9c9-aa0349bf2955(Office.15).png" title="Manage icon" alt="Manage icon" /></td>
<td><p><strong>Manage Office Web Apps Server</strong></p></td>
<td><p><a href="plan-office-web-apps-server.md">Plan and establish an update process</a> for the Office Web Apps Server farm. Office Web Apps Server updates <a href="apply-software-updates-to-office-web-apps-server.md">must be applied in a specific way</a>.</p>
<p><br />
</p>
<p>You can find a list of the most recent Office Web Apps Server updates on the <a href="http://go.microsoft.com/fwlink/p/?linkid=280269">Microsoft Office Updates blog</a> and on the <a href="http://go.microsoft.com/fwlink/p/?linkid=280271">TechNet Update center for Office, Office servers, and related products</a>.</p>
<p><br />
</p>
<p>If you've deployed Office Web Apps Server to use with SharePoint 2013, the default open of Office documents will be in the browser. But, you can <a href="set-the-default-open-behavior-for-browser-enabled-documents-office-web-apps-when-used-with-sharepoint-2013.md">change this behavior so that Office documents open in a client</a>.</p>
<p><br />
</p>
<p>If your organization decides to use Excel Services instead of Excel Web App to view workbooks in the browser, you can use the Windows PowerShell cmdlet <a href="new-spwopisuppressionsetting.md">New-SPWOPISuppressionSetting</a> to turn off Excel Web App for Excel workbooks.</p>
<p><br />
</p>
<p>If you want to <a href="configure-office-web-apps-for-sharepoint-2013.md">disconnect SharePoint 2013 from Office Web Apps Server</a>, use the Windows PowerShell cmdlet <a href="remove-spwopibinding.md">Remove-SPWOPIBinding</a>.</p></td>
</tr>
<tr class="even">
<td><img src="images/Dn135237.17bfbe9e-7e0e-48dd-887b-b94f8d8f9f22(Office.15).png" title="Troubleshoot icon" alt="Troubleshoot icon" /></td>
<td><p><strong>Troubleshoot Office Web Apps Server</strong></p></td>
<td><p><a href="configure-office-web-apps-for-sharepoint-2013.md">Troubleshoot errors in Office Web Apps when it is used with SharePoint 2013</a></p></td>
</tr>
<tr class="odd">
<td><img src="images/Dn135237.e562fbf9-74bd-4ed8-a6f6-016a701da6f9(Office.15).png" title="Behind the scenes icon" alt="Behind the scenes icon" /></td>
<td><p><strong>Reference information</strong></p></td>
<td><p>Here are links to Windows PowerShell commands and other types of reference information:</p>
<p><br />
</p>
<p>Office Web Apps Server</p>
<ul>
<li><p><a href="windows-powershell-for-office-web-apps-server.md">Windows PowerShell for Office Web Apps Server</a></p></li>
</ul>
<p><br />
</p>
<p>SharePoint 2013</p>
<ul>
<li><p><a href="windows-powershell-for-office-web-apps-sharepoint-2013.md">Windows PowerShell for Office Web Apps (SharePoint 2013)</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><img src="images/Dn135237.2a3da7f0-308f-4d5a-9981-3ee16435ca5d(Office.15).png" title="Downloads" alt="Downloads" /></td>
<td><p><strong>Downloads</strong></p></td>
<td><p>Here are the downloads that are related to Office Web Apps Server:</p>
<ul>
<li><p>Download the <a href="deploy-office-web-apps-server.md">pre-requisite software for Windows Server 2008 R2</a>.</p></li>
<li><p>Download Office Web Apps Server from the <a href="http://go.microsoft.com/fwlink/p/?linkid=256561">Volume Licensing Service Center (VLSC)</a>. To download Office Web Apps Server you must have a license, under a Volume Licensing agreement, for Office Professional Plus 2013, Office Standard 2013, or Office for Mac 2011. The download is located under those Office products on the VLSC portal.</p></li>
<li><p>Download Office Web Apps Server <a href="http://go.microsoft.com/fwlink/p/?linkid=263945">language packs</a>.</p></li>
<li><p>Office Web Apps Server updates. Find the latest at <a href="http://go.microsoft.com/fwlink/p/?linkid=280269">Microsoft Office Updates blog</a> or on the <a href="http://go.microsoft.com/fwlink/p/?linkid=280271">TechNet Update center for Office, Office servers, and related products</a>.</p></li>
<li><p>Download the <a href="http://go.microsoft.com/fwlink/p/?linkid=299305">Office Web Apps Server poster</a>.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><img src="images/Dn135237.58135645-d951-4316-b55f-0d4a32f8670d(Office.15).png" title="Video (play button) icon" alt="Video (play button) icon" /></td>
<td><p><strong>Videos</strong></p></td>
<td><ul>
<li><p><a href="video-configure-office-web-apps-for-sharepoint-2013.md">Video: Configure Office Web Apps for SharePoint 2013</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><img src="images/JJ219456.6fa793ee-ede9-4476-901c-de96ea37fc3a(Office.15).png" title="Chat icon" alt="Chat icon" /></p></td>
<td><p><strong>Ask questions and provide feedback</strong></p></td>
<td><p>If you have questions about how to deploy and manage Office Web Apps Server, you can submit your questions in the <a href="http://go.microsoft.com/fwlink/p/?linkid=259426">Office 2013 and Office 365 ProPlus - Planning, Deployment, and Compatibility forum</a> on TechNet.</p></td>
</tr>
</tbody>
</table>


## See also


[Getting started guide for deploying Office 365 ProPlus](https://technet.microsoft.com/en-us/library/jj839718\(v=office.15\))  
[Roadmap for Office 2013 identity, authentication, and authorization](https://technet.microsoft.com/en-us/library/dn151329\(v=office.15\))  
[Guide to Office 2013 security](https://technet.microsoft.com/en-us/library/dn194021\(v=office.15\))

