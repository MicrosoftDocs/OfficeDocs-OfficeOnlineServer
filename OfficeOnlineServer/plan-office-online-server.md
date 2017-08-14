---
title: Plan Office Online Server
ms.prod: OFFICERESOURCEKIT
ms.assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
---


# Plan Office Online Server
 **Summary:** Describes requirements and prerequisites, including HTTPS, certificates, virtualization, load balancing, topologies, and security.
 **Audience**: IT Professionals
  
    
    

 delivers browser-based versions of apps in an on-premises environment, giving users more flexibility and collaboration opportunities. This article describes the requirements and steps you need to take to install in your organization.
It's important to carefully plan so that all hosts, such as and can communicate with .
  
    
    

Check the  [Office Online Server version compatibility list](office-online-server.md#version) to ensure that your hosts are compatible.In this article:
-  [Software, hardware, and configuration requirements for Office Online Server](plan-office-online-server.md#software)
    
  
-  [Support for virtualizing Office Online Server](plan-office-online-server.md#virtualization)
    
  
-  [Firewall requirements for Office Online Server](plan-office-online-server.md#firewall)
    
  
-  [Load balancer requirements for Office Online Server](plan-office-online-server.md#loadbalancer)
    
  
-  [DNS requirements for Office Online Server](plan-office-online-server.md#DNS)
    
  
-  [Planning language packs for Office Online Server](plan-office-online-server.md#language)
    
  
-  [Topology planning for Office Online Server](plan-office-online-server.md#topology)
    
  
-  [Security planning for Office Online Server](plan-office-online-server.md#security)
    
  
-  [Planning for Online Viewers with Office Online Server](plan-office-online-server.md#viewers)
    
  
-  [Planning updates for Office Online Server](plan-office-online-server.md#BKMK_Updates)
    
  

## Software, hardware, and configuration requirements for Office Online Server
<a name="software"> </a>

You can install as a single-server farm, or as a multi-server, load-balanced farm. You can use physical servers or virtual machines. 
  
    
    
In environments that contain actual user data, we always recommend that you use HTTPS, for which you have to obtain a certificate. If you're using multiple servers in your farm, you have to configure a hardware or software load-balancing solution. You can learn more about these scenarios in the following sections.
  
    
    

### Hardware requirements for Office Online Server

 uses the same minimum hardware requirements as .
  
    
    

### Supported operating systems for Office Online Server

You can run on the following operating systems:
  
    
    

- The 64-bit edition of R2
    
  
- The 64-bit edition of Windows Server 2016 ( April 2017 or later required)
    
  

### Domain requirements for Office Online Server

All servers in the farm must be part of a domain. They can be in the same domain (recommended) or in domains that are in the same forest.
  
    
    
If you plan to use any features that utilize external data access (such as Data Models, Power Pivot, or Power View), must reside in the same Active Directory forest as its users as well as any external data sources that you plan to access using Windows-based authentication.
  
    
    

### Support schedule and upgrade requirements

Microsoft releases a new build of every six months or so. Once a new build has been released, critical updates are no longer produced for the previous build. We highly recommend that you update your farm as new builds are released. For more information, see  [Office Online Server release schedule](office-online-server-release-schedule.md).
  
    
    

### Compatibility with other workloads and services

Here are a few things to be aware of when you install .
  
    
    

- **Don't install any other server applications on the server that's running**. This includes , , , and . If you have a shortage of servers, consider running in a virtual machine on one of the servers you have.
    
  
- **Don't install any services or roles that depend on the Web Server (IIS) role on port 80, 443, or 809** because periodically removes web applications on these ports.
    
  
- **Don't install any version of Office**. If it's already installed, you'll need to uninstall it before you install .
    
  
- **Don't install on a domain controller**. It won't run on a server with Active Directory Domain Services (AD DS).
    
  

## Support for virtualizing Office Online Server
<a name="virtualization"> </a>

 is supported when you deploy it using or other virtualization technology in your on-premises datacenter. If you plan to virtualize , follow these guidelines:
  
    
    

- Install in its own virtual machine. Don't install any other server applications, such as , in this virtual machine. 
    
  
- When using for multi-server farms, each virtual machine should be on a separate virtual machine host. This way, the farm will still be available if one of the hosts fails.
    
  

## Firewall requirements for Office Online Server
<a name="firewall"> </a>

Firewalls can cause problems by blocking communication between the web browser, the servers that run , and the servers that run . These problems can be more complicated when the servers are in different parts of a network.
  
    
    
Make sure the following ports aren't blocked by firewalls on either the server that runs or the load balancer:
  
    
    

- Port 443 for HTTPS traffic
    
  
- Port 80 for HTTP traffic
    
  
- Port 809 for private traffic between the servers that run (if you're setting up a multi-server farm)
    
  

## Load balancer requirements for Office Online Server
<a name="loadbalancer"> </a>

We recommend a load balancing solution when you run on two or more servers. Just about any load balancing solution will work, including a server that runs the Web Server (IIS) role running Application Request Routing (ARR). In fact, you can run ARR on one of the servers that runs .
  
    
    
Ideally, try to find a load balancing solution that supports the following features:
  
    
    

- Layer 7 routing
    
  
- Enabling client affinity or front-end affinity
    
  
- Enabling SSL offloading
    
  
If you use a load balancer, you'll need to install the certificate on the load balancer as described under  [Securing Office Online Server communications by using HTTPS ](plan-office-online-server.md#certificate).
  
    
    

## DNS requirements for Office Online Server
<a name="DNS"> </a>

In environments that use HTTPS and load balancing, you have to update DNS so that the fully qualified domain name (FQDN) of the certificate resolves to either the IP address of the server that runs or to the IP address assigned to the load balancer for the farm.
  
    
    

## Planning language packs for Office Online Server
<a name="language"> </a>

 Language Packs enable users to view web-based files in multiple languages from document libraries, (as attachment previews), and (as broadcasts). But, this depends on the languages that are configured on the host. To view web-based files from hosts in multiple languages, you must have the following in place:
  
    
    

- The host (such as or ) is configured to run applications in additional languages. The process of installing and configuring language packs on the host is independent of installing a language pack on the farm.
    
  
- The languages are installed and are available on all servers in the farm.
    
  
Here's where to  [download the language packs for Office Web Apps Server](http://go.microsoft.com/fwlink/p/?LinkId=798136).
  
    
    

## Topology planning for Office Online Server
<a name="topology"> </a>

At a minimum, an topology will include one physical or virtual machine running , and at least one host (for example, a server running or ). And of course, you'll need a client PC or device to connect to one of the hosts and use the functionality. From that minimal topology, you can add more hosts and more servers to your farm as required to suit the needs of your organization.
  
    
    
The following is a list of recommendations that you should keep in mind as your topology gets more complex.
  
    
    

- **Plan for redundancy.** If you use virtual machines, make sure you put them on separate virtual machine hosts for redundancy.
    
  
- **Stick to one data center.** Servers in an farm must be in the same data center. Don't distribute them geographically. Generally you need only one farm, unless you have security needs that require an isolated network that has its own farm.
    
  
- **The closer the hosts, the better.** The farm doesn't have to be in the same data center as the hosts it serves, but for heavy editing usage, we recommend you put the farm as close to the hosts as possible. This is less important for organizations that use primarily for viewing files.
    
  
- **Plan your connections.** Connect all servers in the farm only to one another. To connect them to a broader network, do so through a reverse proxy load balancer firewall.
    
  
- **Configure the firewall for HTTP or HTTPS requests.** Make sure the firewall allows servers running to initiate HTTP or HTTPS requests to hosts.
    
  
- **Plan for incoming and outgoing communications.** In an Internet-facing deployment, route all outgoing communications through a NAT device. In a multi-server farm, handle all incoming communications with a load balancer.
    
  
- **Make sure all servers in the farm are joined to a domain and are part of the same organizational unit (OU).** Use the **FarmOU** parameter in the [New-OfficeWebAppsFarm](new-officewebappsfarm.md) cmdlet to prevent other servers that are not in this OU from joining the farm.
    
  
- **Use Hypertext Transfer Protocol Secure (HTTPS) for all incoming requests.**
    
  
- **If you have IPsec deployed in the network, use it to encrypt traffic among the servers.**
    
  
- **Plan for Office features that use the Internet.** If features such as clip art and translation services are needed, and the servers in the farm can't initiate requests to the Internet, you'll need to configure a proxy server for the farm. This will allow HTTP requests to external sites.
    
  

## Plan Excel Online external data connectivity
<a name="topology"> </a>

 includes external data connectivity and data refresh features similar to those found in in SharePoint Server 2013. has been removed from SharePoint in - you use instead.
  
    
    
Data refresh for embedded data connections works with a standard installation. However, more advanced features, including Office Data Connection (ODC) file support and the IT Management Dashboard (part of SQL Server Power Pivot for SharePoint) require that you  [configure server-to-server authentication between Office Online Server and SharePoint Server 2016](configure-server-to-server-authentication-between-office-online-server-and-share.md).
  
    
    

## Security planning for Office Online Server
<a name="security"> </a>

The following information introduces security guidance for . 
  
    
    

### Securing Office Online Server communications by using HTTPS
<a name="certificate"> </a>

 can communicate with , , and by using the HTTPS protocol. In production environments, we strongly recommend that you use HTTPS. You'll have to install an Internet Server certificate that can be assigned to the server that runs (if you are using a single server) or to the load balancer (if you are using multiple servers that run ).
  
    
    
In test environments that contain no user data, you can use HTTP for and and skip the certificate requirement. supports only HTTPS.
  
    
    
Certificates used by need to meet the following requirements:
  
    
    

- The certificate must come from a trusted Certificate Authority and include the fully qualified domain name (FQDN) of your farm in the SAN (Subject Alternative Name) field. (If the FQDN is not in the SAN when you try to use the certificate, the browser will either show security warnings or won't process the response.)
    
  
- The certificate must have an exportable private key. On single-server farms, this option is selected by default when you use the Manager snap-in to import the certificate.
    
  
- The Friendly name field must be unique within the Trusted Root Certificate Authorities store. If you have multiple certificates that share a Friendly Name field, farm creation will fail because the New-OfficeWebAppsFarm cmdlet won't know which of those certificates to use.
    
  
-  doesn't require any special certificate properties or extensions. For example, Client Enhanced Key Usage (EKU) extensions or Server EKU extensions are not required.
    
  
- You must install the "Allow HTTP Activation" Windows Communication Foundation (WCF) feature on .
    
    
    
  
The certificate must be imported as follows:
  
    
    

- **For single-server farms** You must import the certificate directly on the server that runs . Don't bind the certificate manually. The New-OfficeWebAppsFarm cmdlet you run later will do this for you. If you bind the certificate manually, it'll be deleted every time the server restarts.
    
  
- **For load-balanced farms** If you're offloading SSL, the certificate must be imported on the hardware load balancer. If you're not offloading SSL, you'll need to install the certificate on each server in the farm.
    
  

> [!NOTE]
> Don't use self-signed certificates except in non-critical test environments. 
  
    
    


### Using SSL offloading for hardware load balancers
<a name="certificate"> </a>

When you set up a new farm, SSL offloading is set to Off by default. If you're using a hardware load balancer, we recommend you set SSL offloading to On so that each in the farm can communicate with the load balancer by using HTTP. Setting SSL offloading to On also provides the following advantages:
  
    
    

- Simplified certificates management
    
  
- Improved soft affinity
    
  
- Improved performance
    
  
Note that when you use HTTP, traffic from the load balancer to the servers that run isn't encrypted, so you need to make sure the network itself is secure. Use of a private subnet can help protect traffic.
  
    
    

### Restrict which servers can join an Office Online Server farm based on OU membership
<a name="certificate"> </a>

You can prevent unauthorized servers from joining an farm by creating an organizational unit for those servers and then specifying the FarmOU parameter when you create the farm. For more information about the FarmOU parameter, see  [New-OfficeWebAppsFarm](new-officewebappsfarm.md).
  
    
    

### Limit host access for Office Online Server by using the Allow List
<a name="certificate"> </a>

The Allow List is a security feature that prevents unwanted hosts from connecting to an farm and using it for file operations without your consent. By adding the domains that contain approved hosts to the Allow List, you can limit the hosts to which allows file operations requests, such as file retrieval, metadata retrieval, and file changes. 
  
    
    
You can add domains to the Allow List after you've created the farm. To learn how to add domains to the Allow List, see  [New-OfficeWebAppsHost](new-officewebappshost.md).
  
    
    

> [!IMPORTANT]
> If you do not add domains to the Allow List, allows file requests to hosts in any domain. Don't leave this list blank if your farm can be accessed from the Internet. Otherwise, anyone can use your farm to view and edit content. 
  
    
    


## Planning for Online Viewers with Office Online Server
<a name="viewers"> </a>

By default, Online Viewers functionality is enabled after you install . Review the following guidelines if you're planning to use Online Viewers in your organization. In some cases, you might want to disable some features within Online Viewers. These guidelines refer to parameters that are set by using the cmdlets  [New-OfficeWebAppsFarm](new-officewebappsfarm.md) and [Set-OfficeWebAppsFarm](set-officewebappsfarm.md).
  
    
    

### Security considerations for Online Viewers

Files that are intended to be viewed through a web browser by using Online Viewers must not require authentication. In other words, the files must be available publicly because Online Viewers can't perform authentication when it is retrieving files. We strongly recommend that the farm that you use for Online Viewers is only able to access either the intranet or the Internet, but not both. This is because doesn't differentiate between requests for intranet and Internet URLs. Somebody on the Internet could request an intranet URL, for example, causing a security leak if an internal document is viewed.
  
    
    
For the same reason, if you have set up the to connect only to the Internet, we strongly recommend that you disable UNC support in Online Viewers. To disable UNC support, set the OpenFromUncEnabled parameter to False by using the cmdlets  [New-OfficeWebAppsFarm](new-officewebappsfarm.md) (for new farms) or [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (for existing farms).
  
    
    
As an additional security precaution, Online Viewers are limited to viewing files that are 10 MB or less.
  
    
    

### Configuration options for Online Viewers


  
    
    
You can configure Online Viewers by using the following parameters in  [New-OfficeWebAppsFarm](new-officewebappsfarm.md) (for new farms) or [Set-OfficeWebAppsFarm](set-officewebappsfarm.md) (for existing farms).
  
    
    

- **OpenFromUrlEnabled** Turns the Online Viewers on or off. This parameter controls Online Viewers for files that have URL and UNC paths. By default, this parameter is set to False (disabled) when you create a new farm.
    
  
- **OpenFromUncEnabled** When Online Viewers are turned on (set to True by using OpenFromUrlEnabled), this parameter turns on or off the ability for Online Viewers to display files in UNC paths. By default, this parameter is set to True, but make sure OpenFromUrlEnabled is also set to True before you enable opening files from UNC paths. As described earlier, we recommend you set this parameter to False if you have set up to connect to the Internet.
    
  
- **OpenFromUrlThrottlingEnabled** Throttles the number of "open from URL" requests from any given server in a time period. The default throttling values, which are not configurable, make sure that an farm does not overwhelm a single server by sending requests for content to be viewed in the Online Viewers.
    
  

## Planning updates for Office Online Server
<a name="BKMK_Updates"> </a>

Before deploying , you need to decide how your organization will manage software updates to your farm. Although software updates help improve server security, performance, and reliability, installing updates incorrectly can cause issues with the . 
  
    
    
Applying updates by using the Microsoft automatic updates process isn't supported with . Updates to an must be applied in a specific way, as described in  [Apply software updates to Office Online Server](apply-software-updates-to-office-online-server.md). If updates are applied automatically, users might be unable to view or edit documents in . If this happens, you have to rebuild your farm. 
  
    
    
We recommend that you manage updates by using Update Services (WSUS) or by using System Center , which uses WSUS. WSUS allows you to fully manage the distribution of updates that are released through Microsoft Update for each server in the farm. By using WSUS, you can decide which updates can be automatically applied to the server farm and which updates, such as updates, have to be manually applied. For more information about WSUS, see  [Windows Server Update Services](https://go.microsoft.com/fwlink/p/?LinkId=294822).
  
    
    
If you do not use WSUS or System Center , set Microsoft automatic updates on each server in the farm to **Automatically download but notify user for install**. When you're notified of an update, follow the steps in  [Apply software updates to Office Online Server](apply-software-updates-to-office-online-server.md). To have Windows updates applied and keep your servers secure, accept the Windows updates when you're notified that updates are available.
  
    
    

  
    
    

## See also
<a name="BKMK_Updates"> </a>


#### 


  
    
    
 [Office Online Server overview](office-online-server-overview.md)
  
    
    
 [Deploy Office Online Server](deploy-office-online-server.md)
