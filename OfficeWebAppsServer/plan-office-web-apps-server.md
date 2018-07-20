---
title: Plan Office Web Apps Server
TOCTitle: Plan Office Web Apps Server
ms:assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219435(v=office.15)
ms:contentKeyID: 48409056
ms.date: 10/10/2017
mtps_version: v=office.15
---

# Plan Office Web Apps Server

 

_**Applies to:** Office Web Apps Server_


**Summary:** Describes Office Web Apps Server requirements and prerequisites, including HTTPS, certificates, virtualization, load balancing, topologies, and security.

**Audience:** IT Professionals

Office Web Apps Server delivers browser-based versions of Office apps in an on-premises environment, giving users more flexibility and collaboration opportunities. This article describes the requirements and steps you need to take to install Office Web Apps Server in your organization.

It’s important to carefully plan so that all hosts, such as SharePoint 2013 and Lync Server 2013, can communicate with the Office Web Apps Server. For additional guidance about configuring hosts, see the following resources:

  - [Plan Office Web Apps (Used with SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md)

  - [Deploying Office Web Apps Server and Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)


> [!NOTE]
> SharePoint 2010 Products can’t be a host for Office Web Apps Server. Office Web Apps Server isn’t supported by SharePoint Foundation 2010 or SharePoint Server 2010. Office Web Apps Server also isn't supported by Exchange Server 2013.



In this article:

  - Software, hardware, and configuration requirements for Office Web Apps Server

  - Support for virtualizing Office Web Apps Server

  - Firewall requirements for Office Web Apps Server

  - Load balancer requirements for Office Web Apps Server

  - DNS requirements for Office Web Apps Server

  - Planning language packs for Office Web Apps Server

  - Topology planning for Office Web Apps Server

  - Security planning for Office Web Apps Server

  - Planning for Online Viewers with Office Web Apps Server

  - Planning updates for Office Web Apps Server

## Software, hardware, and configuration requirements for Office Web Apps Server

You can install Office Web Apps Server as a single-server Office Web Apps Server farm, or as a multi-server, load-balanced Office Web Apps Server farm. You can use physical servers or virtual machine instances, but you can’t install other server applications (such as SharePoint 2013 or SQL Server) on the same server as Office Web Apps Server.

In environments that contain actual user data, we always recommend that you use HTTPS, for which you’ll have to obtain a certificate. If you’re using multiple servers in your farm, you’ll have to configure a hardware or software load-balancing solution. You can learn more about these scenarios in the following sections.

## Hardware requirements for Office Web Apps Server

Office Web Apps Server uses the same minimum hardware requirements as SharePoint Server 2013. You can find the full set of SharePoint 2013 requirements in [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/en-us/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver).

## Supported operating systems for Office Web Apps Server

You can run Office Web Apps Server on the following operating systems:

  - The 64-bit edition of Windows Server 2008 R2 Service Pack 1 (SP1) Standard, Enterprise, or Datacenter with the [Update for Windows Server 2008 R2 x64 Edition](https://go.microsoft.com/fwlink/p/?linkid=236954) installed

  - The 64-bit edition of Windows Server 2012 Standard or Datacenter

  - The 64-bit edition of Windows Server 2012 R2. To use this operating system, you must use Office Web Apps Server Service Pack 1 (SP1).

## Domain requirements for Office Web Apps Server

All servers in the Office Web Apps Server farm must be part of a domain. They can be in the same domain (recommended) or in domains that are in the same forest. However, Office Web Apps Server won’t work if you try to install it on a domain controller.

## Server roles, services, and other software required for Office Web Apps Server

First, here are a few things you should NOT do when deploying Office Web Apps Server.

  - **Don’t install any other server applications on the server that’s running Office Web Apps Server**. This includes Exchange Server, SharePoint Server, Lync Server, and SQL Server. If you have a shortage of servers, consider running Office Web Apps Server in a virtual machine instance on one of the servers you have.

  - **Don’t install any services or roles that depend on the Web Server (IIS) role on port 80, 443, or 809** because Office Web Apps Server periodically removes web applications on these ports.

  - **Don’t install any version of Office**. If it’s already installed, you’ll need to uninstall it before you install Office Web Apps Server.

  - **Don’t install Office Web Apps Server on a domain controller**. It won’t run on a server with Active Directory Domain Services (AD DS).

Now for the items you DO need to install. See the following table for details.


> [!IMPORTANT]
> Office Web Apps Server is only available for download from the <A href="https://go.microsoft.com/fwlink/p/?linkid=256561">Volume Licensing Service Center (VLSC)</A>. To download Office Web Apps Server you must have a license, under a Volume Licensing agreement, for Office Professional Plus 2013, Office Standard 2013, or Office for Mac 2011. The download is located under those Office products on the VLSC portal.



### Downloads, server roles, and features that are required for Office Web Apps Server

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Download, server role, or feature</th>
<th>If you’re installing on Windows Server 2008 R2</th>
<th>If you’re installing on Windows Server 2012</th>
<th>If you’re installing on Windows Server 2012 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Download:</strong> Office Web Apps Server</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Download:</strong> Office Web Apps Server SP1</p></td>
<td><p>Recommended</p></td>
<td><p>Recommended</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510097">Office Web Apps Server SP1</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Download:</strong> Correct version of .NET Framework</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256560">.NET Framework 4.5</a></p></td>
<td><p>.NET framework 4.5 is already installed</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510096">.NET Framework 4.5.2</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Download:</strong> Update for Windows Server 2008 R2 x64 Edition</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=236954">Update for Windows Server 2008 R2 x64 Edition</a></p></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="odd">
<td><p><strong>Download:</strong> Windows PowerShell 3.0</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=244693">Windows PowerShell 3.0</a></p></td>
<td><p>Already installed</p></td>
<td><p>Already installed</p></td>
</tr>
<tr class="even">
<td><p><strong>Server role:</strong> Web Server (IIS)</p></td>
<td><p>Here are the minimum role services required for the <strong>Web Server (IIS)</strong> server role.</p>
<p><strong>Common HTTP Features</strong></p>
<ul>
<li><p>Static Content</p></li>
<li><p>Default Document</p></li>
</ul>
<p><strong>Application Development</strong></p>
<ul>
<li><p>ASP.NET</p></li>
<li><p>.NET Extensibility</p></li>
<li><p>ISAPI Extensions</p></li>
<li><p>ISAPI Filters</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p><strong>Security</strong></p>
<ul>
<li><p>Windows Authentication</p></li>
<li><p>Request Filtering</p></li>
</ul>
<p><strong>Management Tools</strong></p>
<ul>
<li><p>IIS Management Console</p></li>
</ul>
<p>The following options are recommended but not required:</p>
<p><strong>Performance</strong></p>
<ul>
<li><p>Static Content Compression</p></li>
<li><p>Dynamic Content Compression</p></li>
</ul></td>
<td><p>Here are the minimum role services required for the <strong>Web Server (IIS)</strong> server role.</p>
<p><strong>Management Tools</strong></p>
<ul>
<li><p>IIS Management Console</p></li>
</ul>
<p><strong>Web Server</strong></p>
<ul>
<li><p>Common HTTP Features</p></li>
<li><p>Default Document</p></li>
<li><p>Static Content</p></li>
</ul>
<p><strong>Security</strong></p>
<ul>
<li><p>Request Filtering</p></li>
<li><p>Windows Authentication</p></li>
</ul>
<p><strong>Application Development</strong></p>
<ul>
<li><p>.NET Extensibility 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI Extensions</p></li>
<li><p>ISAPI Filters</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p>The following services are recommended but not required:</p>
<p><strong>Performance</strong></p>
<ul>
<li><p>Static Content Compression</p></li>
<li><p>Dynamic Content Compression</p></li>
</ul></td>
<td><p>Here are the minimum role services required for the <strong>Web Server (IIS)</strong> server role.</p>
<p><strong>Management Tools</strong></p>
<ul>
<li><p>IIS Management Console</p></li>
</ul>
<p><strong>Web Server</strong></p>
<ul>
<li><p>Common HTTP Features</p></li>
<li><p>Default Document</p></li>
<li><p>Static Content</p></li>
</ul>
<p><strong>Security</strong></p>
<ul>
<li><p>Request Filtering</p></li>
<li><p>Windows Authentication</p></li>
</ul>
<p><strong>Application Development</strong></p>
<ul>
<li><p>.NET Extensibility 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI Extensions</p></li>
<li><p>ISAPI Filters</p></li>
<li><p>Server Side Includes</p></li>
</ul>
<p>The following services are recommended but not required:</p>
<p><strong>Performance</strong></p>
<ul>
<li><p>Static Content Compression</p></li>
<li><p>Dynamic Content Compression</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Feature:</strong> Ink and Handwriting Services</p></td>
<td><p><strong>Ink and Handwriting Services</strong></p>
<ul>
<li><p>Ink Support</p></li>
</ul></td>
<td><p><strong>Ink and Handwriting Services</strong></p>
<ul>
<li><p>Ink Support is not required.</p></li>
</ul></td>
<td><p><strong>Ink and Handwriting Services</strong></p>
<ul>
<li><p>Ink Support is not required.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Support for virtualizing Office Web Apps Server

Office Web Apps Server is fully supported when you deploy it using Windows Server Hyper-V technology. If you plan to virtualize Office Web Apps Server, follow these guidelines:

  - Install Office Web Apps Server in its own virtual machine instance. Don’t install any other server applications, such as SharePoint 2013, in this instance.

  - It’s okay to install Office Web Apps Server in a virtual machine instance hosted by a server running SharePoint 2013.

  - For multi-server Office Web Apps Server farms, each instance should be on a separate virtual machine host. This way, the Office Web Apps Server farm will still be available if one of the hosts fails.

## Firewall requirements for Office Web Apps Server

Firewalls can cause problems by blocking communication between the web browser, the servers that run Office Web Apps Server, and the servers that run SharePoint 2013. These problems can be more complicated when the servers are in different parts of a network.

Make sure the following ports aren’t blocked by firewalls on either the server that runs Office Web Apps Server or the load balancer:

  - Port 443 for HTTPS traffic

  - Port 80 for HTTP traffic

  - Port 809 for private traffic between the servers that run Office Web Apps Server (if you’re setting up a multi-server farm)

## Load balancer requirements for Office Web Apps Server

We recommend a load balancing solution when you run Office Web Apps Server on two or more servers. Just about any load balancing solution will work, including a server that runs the Web Server (IIS) role running Application Request Routing (ARR). In fact, you can run ARR on one of the servers that runs Office Web Apps Server. If you don’t have a load balancing solution, take a look at these resources for using IIS with ARR:

  - [Install Application Request Routing](https://go.microsoft.com/fwlink/?linkid=236955)

  - [Application Request Routing Help](https://go.microsoft.com/fwlink/?linkid=236956)

Ideally, try to find a load balancing solution that supports the following features:

  - Layer 7 routing

  - Enabling client affinity or front-end affinity

  - Enabling SSL offloading

If you use a load balancer, you’ll need to install the certificate on the load balancer as described under Securing Office Web Apps Server communications by using HTTPS.

## DNS requirements for Office Web Apps Server

In environments that use HTTPS and load balancing, you have to update DNS so that the fully qualified domain name (FQDN) of the certificate resolves to either the IP address of the server that runs Office Web Apps Server or to the IP address assigned to the load balancer for the Office Web Apps Server farm.

## Planning language packs for Office Web Apps Server

Office Web Apps Server 2013 Language Packs enable users to view web-based Office files in multiple languages from SharePoint 2013 document libraries, Outlook Web App (as attachment previews), and Lync 2013 (as PowerPoint broadcasts). But, this depends on the languages that are configured on the host. To view web-based Office files from hosts in multiple languages, you must have the following in place:

  - The host (such as SharePoint Server 2013 or Lync Server 2013) is configured to run applications in additional languages. The process of installing and configuring language packs on the host is independent of installing a language pack on the Office Web Apps Server farm.

  - The languages are installed and are available on all servers in the Office Web Apps Server farm.

Here’s where to [download the language packs for Office Web Apps Server](https://go.microsoft.com/fwlink/p/?linkid=263945).

## Topology planning for Office Web Apps Server

At a minimum, an Office Web Apps Server topology will include one physical or virtual machine running Office Web Apps Server, and at least one host (for example, a server running Lync Server 2013 or SharePoint 2013). And of course, you’ll need a client PC or device to connect to one of the hosts and use the Office Web Apps functionality. From that minimal topology, you can add more hosts and more servers to your Office Web Apps Server farm as required to suit the needs of your organization.

The following is a list of recommendations that you should keep in mind as your Office Web Apps Server topology gets more complex.

  - **Plan for redundancy.** If you use virtual machine instances, make sure you put them on separate virtual machine hosts for redundancy. It’s okay if other instances on the host run server applications—just don’t run other server applications on the same instance as Office Web Apps Server.

  - **Stick to one data center.** Servers in an Office Web Apps Server farm must be in the same data center. Don’t distribute them geographically. Generally you need only one farm, unless you have security needs that require an isolated network that has its own Office Web Apps Server farm.

  - **The closer the hosts, the better.** The Office Web Apps Server farm doesn’t have to be in the same data center as the hosts it serves, but for heavy editing usage, we recommend you put the Office Web Apps Server farm as close to the hosts as possible. This is less important for organizations that use Office Web Apps primarily for viewing Office files.

  - **Plan your connections.** Connect all servers in the Office Web Apps Server farm only to one another. To connect them to a broader network, do so through a reverse proxy load balancer firewall.

  - **Configure the firewall for HTTP or HTTPS requests.** Make sure the firewall allows servers running Office Web Apps Server to initiate HTTP or HTTPS requests to hosts.

  - **Plan for incoming and outgoing communications.** In an Internet-facing deployment, route all outgoing communications through a NAT device. In a multi-server farm, handle all incoming communications with a load balancer.

  - **Make sure all servers in the Office Web Apps Server farm are joined to a domain and are part of the same organizational unit (OU).** Use the **FarmOU** parameter in the [New-OfficeWebAppsFarm](new-officewebappsfarm.md) cmdlet to prevent other servers that are not in this OU from joining the farm.

  - **Use Hypertext Transfer Protocol Secure (HTTPS) for all incoming requests.**

  - **If you have IPsec deployed in the network, use it to encrypt traffic among the servers.**

  - **Plan for Office features that use the Internet.** If features such as clip art and translation services are needed, and the servers in the farm can’t initiate requests to the Internet, you’ll need to configure a proxy server for the Office Web Apps Server farm. This will allow HTTP requests to external sites.

## Security planning for Office Web Apps Server

The following information introduces security guidance for Office Web Apps Server.

## Securing Office Web Apps Server communications by using HTTPS

Office Web Apps Server can communicate with SharePoint 2013 and Lync Server 2013 by using the HTTPS protocol. In production environments, we strongly recommend that you use HTTPS. You’ll have to install an Internet Server certificate that can be assigned to the server that runs Office Web Apps Server (if you are using a single server) or to the load balancer (if you are using multiple servers that run Office Web Apps Server).

In test environments that contain no user data, you can use HTTP for SharePoint 2013 and skip the certificate requirement. Lync Server 2013 supports only HTTPS.

Certificates used by Office Web Apps Server need to meet the following requirements:

  - The certificate must come from a trusted Certificate Authority and include the fully qualified domain name (FQDN) of your Office Web Apps Server farm in the SAN (Subject Alternative Name) field. (If the FQDN is not in the SAN when you try to use the certificate, the browser will either show security warnings or won’t process the response.)

  - The certificate must have an exportable private key. On single-server farms, this option is selected by default when you use the Internet Information Services (IIS) Manager snap-in to import the certificate.

  - The Friendly name field must be unique within the Trusted Root Certificate Authorities store. If you have multiple certificates that share a Friendly Name field, farm creation will fail because the New-OfficeWebAppsFarm cmdlet won’t know which of those certificates to use.

  - Office Web Apps Server doesn’t require any special certificate properties or extensions. For example, Client Enhanced Key Usage (EKU) extensions or Server EKU extensions are not required.

  - On Windows Server 2012 or Windows Server 2012 R2, you must install the "Allow HTTP Activation" Windows Communication Foundation (WCF) feature.

The certificate must be imported as follows:

  - **For single-server farms**   You must import the certificate directly on the server that runs Office Web Apps Server. Don’t bind the certificate manually. The New-OfficeWebAppsFarm cmdlet you run later will do this for you. If you bind the certificate manually, it’ll be deleted every time the server restarts.

  - **For load-balanced farms**   If you’re offloading SSL, the certificate must be imported on the hardware load balancer. If you’re not offloading SSL, you’ll need to install the certificate on each server in the Office Web Apps Server farm.


> [!NOTE]
> Don’t use self-signed certificates except in non-critical test environments.



For more information about certificates, see [How to Obtain an SSL Certificate](https://go.microsoft.com/fwlink/p/?linkid=269700).

## Using SSL offloading for hardware load balancers

When you set up a new Office Web Apps Server farm, SSL offloading is set to Off by default. If you’re using a hardware load balancer, we recommend you set SSL offloading to On so that each Office Web Apps Server in the farm can communicate with the load balancer by using HTTP. Setting SSL offloading to On also provides the following advantages:

  - Simplified certificates management

  - Improved soft affinity

  - Improved performance

Note that when you use HTTP, traffic from the load balancer to the servers that run Office Web Apps Server isn’t encrypted, so you need to make sure the network itself is secure. Use of a private subnet can help protect traffic.

## Restrict which servers can join an Office Web Apps Server farm based on OU membership

You can prevent unauthorized servers from joining an Office Web Apps Server farm by creating an organizational unit for those servers and then specifying the FarmOU parameter when you create the farm. For more information about the FarmOU parameter, see [New-OfficeWebAppsFarm](new-officewebappsfarm.md).

## Limit host access for Office Web Apps Server by using the Allow List

The Allow List is a security feature that prevents unwanted hosts from connecting to an Office Web Apps Server farm and using it for file operations without your consent. By adding the domains that contain approved hosts to the Allow List, you can limit the hosts to which Office Web Apps Server allows file operations requests, such as file retrieval, metadata retrieval, and file changes.

You can add domains to the Allow List after you’ve created the Office Web Apps Server farm. To learn how to add domains to the Allow List, see [New-OfficeWebAppsHost](new-officewebappshost.md).


> [!IMPORTANT]
> If you do not add domains to the Allow List, Office Web Apps Server allows file requests to hosts in any domain. Don’t leave this list blank if your Office Web Apps Server farm can be accessed from the Internet. Otherwise, anyone can use your Office Web Apps Server farm to view and edit content.



## Planning for Online Viewers with Office Web Apps Server

By default, Online Viewers functionality is enabled after you install Office Web Apps Server. Review the following guidelines if you’re planning to use Online Viewers in your organization. In some cases, you might want to disable some features within Online Viewers. These guidelines refer to parameters that are set by using the Windows PowerShell cmdlets [New-OfficeWebAppsFarm](new-officewebappsfarm.md) and [Set-OfficeWebAppsFarm](set-officewebappsfarm.md).

## Security considerations for Online Viewers

Files that are intended to be viewed through a web browser by using Online Viewers must not require authentication. In other words, the files must be available publicly because Online Viewers can’t perform authentication when it is retrieving files. We strongly recommend that the Office Web Apps Server farm that you use for Online Viewers is only able to access either the intranet or the Internet, but not both. This is because Office Web Apps Server doesn’t differentiate between requests for intranet and Internet URLs. Somebody on the Internet could request an intranet URL, for example, causing a security leak if an internal document is viewed.

For the same reason, if you have set up the Office Web Apps Server to connect only to the Internet, we strongly recommend that you disable UNC support in Online Viewers. To disable UNC support, set the OpenFromUncEnabled parameter to False by using the Windows PowerShell cmdlets [New-OfficeWebAppsFarm](new-officewebappsfarm.md) (for new farms) or [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (for existing farms).

As an additional security precaution, Online Viewers are limited to viewing Office files that are 10 MB or less.

## Configuration options for Online Viewers

You can configure Online Viewers by using the following Windows PowerShell parameters in [New-OfficeWebAppsFarm](new-officewebappsfarm.md) (for new farms) or [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (for existing farms).

  - **OpenFromUrlEnabled**   Turns the Online Viewers on or off. This parameter controls Online Viewers for files that have URL and UNC paths. By default, this parameter is set to False (disabled) when you create a new Office Web Apps Server farm.

  - **OpenFromUncEnabled**   When Online Viewers are turned on (set to True by using OpenFromUrlEnabled), this parameter turns on or off the ability for Online Viewers to display files in UNC paths. By default, this parameter is set to True, but make sure OpenFromUrlEnabled is also set to True before you enable opening files from UNC paths. As described earlier, we recommend you set this parameter to False if you have set up Office Web Apps Server to connect to the Internet.

  - **OpenFromUrlThrottlingEnabled**   Throttles the number of “open from URL” requests from any given server in a time period. The default throttling values, which are not configurable, make sure that an Office Web Apps Server farm does not overwhelm a single server by sending requests for content to be viewed in the Online Viewers.

## Planning updates for Office Web Apps Server

Before deploying Office Web Apps Server, you need to decide how your organization will manage software updates to your Office Web Apps Server farm. Although software updates help improve server security, performance, and reliability, installing updates incorrectly can cause issues with the Office Web Apps Server.

Applying Office Web Apps Server updates by using the Microsoft automatic updates process isn’t supported with Office Web Apps Server. Updates to an Office Web Apps Server must be applied in a specific way, as described in [Apply software updates to Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md). If Office Web Apps Server updates are applied automatically, users might be unable to view or edit documents in Office Web Apps. If this happens, you have to rebuild your Office Web Apps Server farm.

We recommend that you manage updates by using Windows Server Update Services (WSUS) or by using System Center Configuration Manager, which uses WSUS. WSUS allows you to fully manage the distribution of updates that are released through Microsoft Update for each server in the Office Web Apps Server farm. By using WSUS, you can decide which updates can be automatically applied to the server farm and which updates, such as Office Web Apps Server updates, have to be manually applied. For more information about WSUS, see [Windows Server Update Services](https://go.microsoft.com/fwlink/p/?linkid=294822).

If you do not use WSUS or System Center Configuration Manager, set Microsoft automatic updates on each server in the Office Web Apps Server farm to **Automatically download but notify user for install**. When you’re notified of an Office Web Apps Server update, follow the steps in [Apply software updates to Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md). To have Windows updates applied and keep your servers secure, accept the Windows updates when you’re notified that updates are available.

## See also


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps Server overview](office-web-apps-server-overview.md)  
[Deploy Office Web Apps Server](deploy-office-web-apps-server.md)  
[Apply software updates to Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md)  


[Office.com (for help with Office Web Apps on your desktop or mobile device)](https://go.microsoft.com/fwlink/p/?linkid=266657)  
  

[](apply-software-updates-to-office-web-apps-server.md)

