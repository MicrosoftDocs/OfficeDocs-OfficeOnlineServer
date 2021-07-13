---
title: Plan Office Online Server
description: Describes Office Online Server requirements and prerequisites, including HTTPS, certificates, virtualization, load balancing, topologies, and security.
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 5/12/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
---


# Plan Office Online Server

 **Summary:** Describes Office Online Server requirements and prerequisites, including HTTPS, certificates, virtualization, load balancing, topologies, and security.

 **Audience**: IT Professionals

Office Online Server delivers browser-based versions of Office apps in an on-premises environment, giving users more flexibility and collaboration opportunities. This article describes the requirements and steps you need to take to install Office Online Server in your organization.

It's important to carefully plan so that all hosts, such as SharePoint Server and Exchange Server can communicate with Office Online Server.

Check the  [Office Online Server version compatibility list](office-online-server.md#version) to ensure that your hosts are compatible.

## Software, hardware, and configuration requirements for Office Online Server
<a name="software"> </a>

You can install Office Online Server as a single-server farm, or as a multi-server, load-balanced farm. You can use physical servers or virtual machines.
  
In environments that contain actual user data, we always recommend that you use HTTPS, for which you have to obtain a certificate. If you're using multiple servers in your farm, you have to configure a hardware or software load-balancing solution. You can learn more about these scenarios in the following sections.

### Hardware requirements for Office Online Server

Office Online Server uses the same [minimum hardware requirements as SharePoint Server 2016](/sharepoint/install/hardware-and-software-requirements).

### Supported operating systems for Office Online Server

You can run Office Online Server on the following operating systems:

- The 64-bit edition of Windows Server 2012 R2

- The 64-bit edition of Windows Server 2016 (Office Online Server November 2018 or later required).
    
> [!NOTE]
> Office Online Server only supports the "Server with Desktop Experience" installation option of Windows Server 2016. For additional information about Windows Server offerings, see [Windows Server Semi-annual Channel Overview](/windows-server/get-started/semi-annual-channel-overview).


### Domain requirements for Office Online Server

All servers in the Office Online Server farm must be part of a domain. They can be in the same domain (recommended) or in domains that are in the same forest.

If you plan to use any Excel Online features that utilize external data access (such as Data Models, Power Pivot, or Power View), Office Online Server must reside in the same Active Directory forest as its users as well as any external data sources that you plan to access using Windows-based authentication.

### Support schedule and upgrade requirements

Microsoft releases a new build of Office Online Server every six months or so. Once a new build has been released, critical updates are no longer produced for the previous build. We highly recommend that you update your Office Online Server farm as new builds are released. For more information, see  [Office Online Server release schedule](office-online-server-release-schedule.md).

### Compatibility with other workloads and services

Here are a few things to be aware of when you install Office Online Server.

- **Don't install any other server applications on the server that's running Office Online Server**. This includes Exchange Server, SharePoint Server, Skype for Business Server, and SQL Server. If you have a shortage of servers, consider running Office Online Server in a virtual machine on one of the servers you have.

- **Don't install any services or roles that depend on the Web Server (IIS) role on port 80, 443, or 809** because Office Online Server periodically removes web applications on these ports.

- **Don't install any version of Office**. If it's already installed, you'll need to uninstall it before you install Office Online Server.

- **Don't install Office Online Server on a domain controller**. It won't run on a server with Active Directory Domain Services (AD DS).

## Support for virtualizing Office Online Server
<a name="virtualization"> </a>

Office Online Server is supported when you deploy it using Windows Server Hyper-V or other virtualization technology in your on-premises datacenter. If you plan to virtualize Office Online Server, follow these guidelines: 

- Install Office Online Server in its own virtual machine. Don't install any other server applications, such as SharePoint Server, in this virtual machine.

- When using Hyper-V for multi-server Office Online Server farms, each virtual machine should be on a separate virtual machine host. This way, the Office Online Server farm will still be available if one of the hosts fails.

## Firewall requirements for Office Online Server
<a name="firewall"> </a>

Firewalls can cause problems by blocking communication between the web browser, the servers that run Office Online Server, and the servers that run SharePoint Server. These problems can be more complicated when the servers are in different parts of a network.
  
Make sure the following ports aren't blocked by firewalls on either the server that runs Office Online Server or the load balancer:

- Port 443 for HTTPS traffic

- Port 80 for HTTP traffic

- Port 809 for private traffic between the servers that run Office Online Server (if you're setting up a multi-server farm)

## Load balancer requirements for Office Online Server
<a name="loadbalancer"> </a>

We recommend a load balancing solution when you run Office Online Server on two or more servers. Just about any load balancing solution will work, including a server that runs the Web Server (IIS) role running Application Request Routing (ARR). In fact, you can run ARR on one of the servers that runs Office Online Server.

Ideally, try to find a load balancing solution that supports the following features:

- Layer 7 routing

- Enabling client affinity or front-end affinity

If you use a load balancer, you'll need to install the certificate on the load balancer as described under  [Securing Office Online Server communications by using HTTPS ](plan-office-online-server.md#certificate).

## DNS requirements for Office Online Server
<a name="DNS"> </a>

In environments that use HTTPS and load balancing, you have to update DNS so that the fully qualified domain name (FQDN) of the certificate resolves to either the IP address of the server that runs Office Online Server or to the IP address assigned to the load balancer for the Office Online Server farm.

## Planning language packs for Office Online Server
<a name="language"> </a>

Office Online Server Language Packs enable users to view web-based Office files in multiple languages from SharePoint Server document libraries, Outlook Web App (as attachment previews), and Skype for Business Server (as PowerPoint broadcasts). But, this depends on the languages that are configured on the host. To view web-based Office files from hosts in multiple languages, you must have the following in place:

- The host (such as SharePoint Server or Exchange Server) is configured to run applications in additional languages. The process of installing and configuring language packs on the host is independent of installing a language pack on the Office Online Server farm.

- The languages are installed and are available on all servers in the Office Online Server farm.

Here's where to  [download the language packs for Office Web Apps Server](https://go.microsoft.com/fwlink/p/?LinkId=798136).

## Topology planning for Office Online Server
<a name="topology"> </a>

At a minimum, an Office Online Server topology will include one physical or virtual machine running Office Online Server, and at least one host (for example, a server running Exchange Server or SharePoint Server). And of course, you'll need a client PC or device to connect to one of the hosts and use the functionality. From that minimal topology, you can add more hosts and more servers to your Office Online Server farm as required to suit the needs of your organization.
    
The following is a list of recommendations that you should keep in mind as your Office Online Server topology gets more complex.

- **Plan for redundancy.** If you use virtual machines, make sure you put them on separate virtual machine hosts for redundancy.

- **Stick to one data center.** Servers in an Office Online Server farm must be in the same data center. Don't distribute them geographically. Generally you need only one farm, unless you have security needs that require an isolated network that has its own Office Online Server farm.

- **The closer the hosts, the better.** The Office Online Server farm doesn't have to be in the same data center as the hosts it serves, but for heavy editing usage, we recommend you put the Office Online Server farm as close to the hosts as possible. This is less important for organizations that use Office Online primarily for viewing Office files.

- **Plan your connections.** Connect all servers in the Office Online Server farm only to one another. To connect them to a broader network, do so through a reverse proxy load balancer firewall.

- **Configure the firewall for HTTP or HTTPS requests.** Make sure the firewall allows servers running Office Online Server to initiate HTTP or HTTPS requests to hosts.

- **Plan for incoming and outgoing communications.** In an Internet-facing deployment, route all outgoing communications through a NAT device. In a multi-server farm, handle all incoming communications with a load balancer.

- **Make sure all servers in the Office Online Server farm are joined to a domain and are part of the same organizational unit (OU).** Use the **FarmOU** parameter in the [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) cmdlet to prevent other servers that are not in this OU from joining the farm.

- **Use Hypertext Transfer Protocol Secure (HTTPS) for all incoming requests.**  

- **If you have IPsec deployed in the network, use it to encrypt traffic among the servers.**

- **Plan for Office features that use the Internet.** If features such as clip art and translation services are needed, and the servers in the farm can't initiate requests to the Internet, you'll need to configure a proxy server for the Office Online Server farm. This will allow HTTP requests to external sites.

## Plan Excel Online external data connectivity
<a name="topology"> </a>

Excel Online includes external data connectivity and data refresh features similar to those found in Excel Services in SharePoint Server 2013. Excel Services has been removed from SharePoint in SharePoint Server 2016 - you use Excel Online instead.

Data refresh for embedded data connections works with a standard Office Online Server installation. However, more advanced features, including Office Data Connection (ODC) file support and the IT Management Dashboard (part of SQL Server Power Pivot for SharePoint) require that you  [configure server-to-server authentication between Office Online Server and SharePoint Server 2016](configure-office-online-server-for-sharepoint-server-2016/configure-server-to-server-authentication-between-office-online-server-and-share.md).

## Security planning for Office Online Server
<a name="security"> </a>

The following information introduces security guidance for Office Online Server.

### Securing Office Online Server communications by using HTTPS
<a name="certificate"> </a>

Office Online Server can communicate with SharePoint Server, Skype for Business Server, and Exchange Server by using the HTTPS protocol. In production environments, we strongly recommend that you use HTTPS. You'll have to install an Internet Server certificate that can be assigned to the server that runs Office Online Server (if you are using a single server) or to the load balancer (if you are using multiple servers that run Office Online Server).

In test environments that contain no user data, you can use HTTP for SharePoint Server and Exchange Server and skip the certificate requirement. Skype for Business Server supports only HTTPS.

Certificates used by Office Online Server need to meet the following requirements:

- The certificate must come from a trusted Certificate Authority and include the fully qualified domain name (FQDN) of your Office Online Server farm in the SAN (Subject Alternative Name) field. (If the FQDN is not in the SAN when you try to use the certificate, the browser will either show security warnings or won't process the response.)

- The certificate must have an exportable private key. On single-server farms, this option is selected by default when you use the Internet Information Services (IIS) Manager snap-in to import the certificate.

- The Friendly name field must be unique within the Trusted Root Certificate Authorities store. If you have multiple certificates that share a Friendly Name field, farm creation will fail because the New-OfficeWebAppsFarm cmdlet won't know which of those certificates to use.

- Office Online Server doesn't require any special certificate properties or extensions. For example, Client Enhanced Key Usage (EKU) extensions or Server EKU extensions are not required.

- You must install the "Allow HTTP Activation" Windows Communication Foundation (WCF) feature on Windows Server.

The certificate must be imported as follows:

- **For single-server farms** You must import the certificate directly on the server that runs Office Online Server. Don't bind the certificate manually. The New-OfficeWebAppsFarm cmdlet you run later will do this for you. If you bind the certificate manually, it'll be deleted every time the server restarts.

- **For load-balanced farms** If you're offloading SSL, the certificate must be imported on the hardware load balancer. If you're not offloading SSL, you'll need to install the certificate on each server in the Office Online Server farm.

> [!NOTE]
> Don't use self-signed certificates except in non-critical test environments.

### Using SSL offloading for hardware load balancers
<a name="certificate"> </a>

When you set up a new Office Online Server farm, SSL offloading is set to Off by default. If you're using a hardware load balancer, we recommend you set SSL offloading to On so that each Office Online Server in the farm can communicate with the load balancer by using HTTP. Setting SSL offloading to On also provides the following advantages:

- Simplified certificates management

- Improved soft affinity

- Improved performance

> [!NOTE] 
> When you use HTTP, traffic from the load balancer to the servers that run Office Online Server isn't encrypted, so you need to make sure the network itself is secure. Use of a private subnet can help protect traffic.

### Restrict which servers can join an Office Online Server farm based on OU membership
<a name="certificate"> </a>

You can prevent unauthorized servers from joining an Office Online Server farm by creating an organizational unit for those servers and then specifying the FarmOU parameter when you create the farm. For more information about the FarmOU parameter, see  [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

### Limit host access for Office Online Server by using the Allow List
<a name="certificate"> </a>

The Allow List is a security feature that prevents unwanted hosts from connecting to an Office Online Server farm and using it for file operations without your consent. By adding the domains that contain approved hosts to the Allow List, you can limit the hosts to which Office Online Server allows file operations requests, such as file retrieval, metadata retrieval, and file changes.

You can add domains to the Allow List after you've created the Office Online Server farm. To learn how to add domains to the Allow List, see  [New-OfficeWebAppsHost](/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps).

> [!IMPORTANT]
> If you do not add domains to the Allow List, Office Online Server allows file requests to hosts in any domain. Don't leave this list blank if your Office Online Server farm can be accessed from the Internet. Otherwise, anyone can use your Office Online Server farm to view and edit content.

## Planning for Online Viewers with Office Online Server
<a name="viewers"> </a>

By default, Online Viewers functionality is enabled after you install Office Online Server. Review the following guidelines if you're planning to use Online Viewers in your organization. In some cases, you might want to disable some features within Online Viewers. These guidelines refer to parameters that are set by using the Microsoft PowerShell cmdlets  [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) and [Set-OfficeWebAppsFarm](/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps).

### Security considerations for Online Viewers

Files that are intended to be viewed through a web browser by using Online Viewers must not require authentication. In other words, the files must be available publicly because Online Viewers can't perform authentication when it is retrieving files. We strongly recommend that the Office Online Server farm that you use for Online Viewers is only able to access either the intranet or the Internet, but not both. This is because Office Online Server doesn't differentiate between requests for intranet and Internet URLs. Somebody on the Internet could request an intranet URL, for example, causing a security leak if an internal document is viewed.

For the same reason, if you have set up the Office Online Server to connect only to the Internet, we strongly recommend that you disable UNC support in Online Viewers. To disable UNC support, set the OpenFromUncEnabled parameter to False by using the Microsoft PowerShell cmdlets  [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (for new farms) or [Set-OfficeWebAppsFarm](/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (for existing farms).

As an additional security precaution, Online Viewers are limited to viewing Office files that are 10 MB or less.

### Configuration options for Online Viewers

You can configure Online Viewers by using the following Microsoft PowerShell parameters in [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (for new farms) or [Set-OfficeWebAppsFarm](/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (for existing farms).

- **OpenFromUrlEnabled** Turns the Online Viewers on or off. This parameter controls Online Viewers for files that have URL and UNC paths. By default, this parameter is set to False (disabled) when you create a new Office Online Server farm.

- **OpenFromUncEnabled** When Online Viewers are turned on (set to True by using OpenFromUrlEnabled), this parameter turns on or off the ability for Online Viewers to display files in UNC paths. By default, this parameter is set to True, but make sure OpenFromUrlEnabled is also set to True before you enable opening files from UNC paths. As described earlier, we recommend you set this parameter to False if you have set up Office Online Server to connect to the Internet.

- **OpenFromUrlThrottlingEnabled** Throttles the number of "open from URL" requests from any given server in a time period. The default throttling values, which are not configurable, make sure that an Office Online Server farm does not overwhelm a single server by sending requests for content to be viewed in the Online Viewers.

## Planning updates for Office Online Server
<a name="BKMK_Updates"> </a>

Before deploying Office Online Server, you need to decide how your organization will manage software updates to your Office Online Server farm. Although software updates help improve server security, performance, and reliability, installing updates incorrectly can cause issues with the Office Online Server.

Applying Office Online Server updates by using the Microsoft automatic updates process isn't supported with Office Online Server. Updates to an Office Online Server must be applied in a specific way, as described in  [Apply software updates to Office Online Server](apply-software-updates-to-office-online-server.md). If Office Online Server updates are applied automatically, users might be unable to view or edit documents in Office Online. If this happens, you have to rebuild your Office Online Server farm.

We recommend that you manage updates by using Windows Server Update Services (WSUS) or by using Microsoft Endpoint Configuration Manager, which uses WSUS. WSUS allows you to fully manage the distribution of updates that are released through Microsoft Update for each server in the Office Online Server farm. By using WSUS, you can decide which updates can be automatically applied to the server farm and which updates, such as Office Online Server updates, have to be manually applied. For more information about WSUS, see  [Windows Server Update Services](/windows/deployment/deploy-whats-new).

If you do not use WSUS or Microsoft Endpoint Configuration Manager, set Microsoft automatic updates on each server in the Office Online Server farm to **Automatically download but notify user for install**. When you're notified of an Office Online Server update, follow the steps in  [Apply software updates to Office Online Server](apply-software-updates-to-office-online-server.md). To have Windows updates applied and keep your servers secure, accept the Windows updates when you're notified that updates are available.
  
## ULS Logs Changes from 2018 Update

The 2018 update of Office Online Server will see a few changes on the format of ULS logs, detailed below:

|**Column**|**Changes**|
|:----|:----|
|TimestampUtc|<ul><li>**Date format changed** for MM/dd/yyyy to yyyy-MM-dd to make sorting more natural</li><li>Time is now always written in **UTC**</li><li>Column name changed from Timestamp to TimestampUtc</li><li>Timestamps no longer have a trailing ' ' or '*' indicating continuations (see Message column below)</li></ul>|
|Process|<ul><li>Process name is no longer truncated to 32 characters</li><li>ProxyTraceTag no longer appends the process ID that sent the proxied trace</li><li>IIS W3WP processes get the AppPool ID appended. Ex: w3wp.exe#StatusViewer-status-MSOSP80 (0x631C)</li></ul>|
|ThreadId|<ul><li>Column name changed from TID to ThreadId</li></ul>|
|Area|<ul><li>Area is no longer truncated to 32 characters</li></ul>|
|Category|<ul><li>Category is no longer truncated to 32 characters</li></ul>|
|EventId|<ul><li>Column name changed from EventID to EventId</li></ul>|
|Level|(no changes)|
|Message|<ul><li>Message length has been expanded from 800 to 31000 characters in size</li><li>**Messages over 31000 characters are truncated**, not continued in a second message</li><li>Since messages don't continue, there are no '...'s</li></ul>|
|Correlation|<ul><li>**Correlations use a new stack** that pushes/pops/peeks appropriately</li><li>Correlation Stack no longer has a max depth of 32</li><li>Correlations can follow Tasks across threads, and cross AppDomain boundaries</li></ul>|    

## See also
<a name="BKMK_Updates"> </a>

 [Office Online Server overview](office-online-server-overview.md)

 [Deploy Office Online Server](deploy-office-online-server.md)