---
title: Deploy Office Web Apps Server
TOCTitle: Deploy Office Web Apps Server
ms:assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219455(v=office.15)
ms:contentKeyID: 48409082
ms.date: 10/05/2017
mtps_version: v=office.15
---

# Deploy Office Web Apps Server

 

_**Applies to:** Office Web Apps Server_


**Summary:** Explains how to deploy Office Web Apps Server on-premises for use by SharePoint 2013 and Lync Server 2013.

**Audience:** IT Professionals

Note that this article covers installing Office Web Apps Server for your business. If you're looking for help with your personal copy of Office or Office Web Apps, see <https://support.office.com>.

Deploying [Office Web Apps Server](office-web-apps-server-overview.md) involves installing some prerequisite software and running a few Windows PowerShell commands, but overall the process is designed to be pretty straightforward. This article walks you through the procedures to get your servers ready, then gives you the Windows PowerShell commands to configure the Office Web Apps Server farm.

In this article:

  - Watch a video to see how it's done

  - Review these resources before you begin

  - Prepare servers to run Office Web Apps Server

  - Deploy the Office Web Apps Server farm

  - If you see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages

## Watch a video to see how it's done

Watch the following video to see how to set up Office Web Apps Server in a test environment. You'll also see a preview of how to configure SharePoint 2013 to use Office Web Apps Server.

**Set up Office Web Apps Server in a test environment**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

## Review these resources before you begin

Make sure you've taken a look at these resources before getting started:

  - For details about hardware and software requirements, [take a look at the planning guidelines](plan-office-web-apps-server.md).

  - By default, Office Web Apps Server lets you view Office files but not edit them. To edit files, you'll need an editing license, which you can learn about in [Plan Office Web Apps (Used with SharePoint 2013)](plan-office-web-apps-used-with-sharepoint-2013.md) and [Configure licensing in SharePoint Server 2013](https://technet.microsoft.com/library/jj219627\(v=office.15\)).


> [!NOTE]
> You can complete tasks in all Office 2013 suites by using a mouse, keyboard shortcuts, or touch. For information about how to use keyboard shortcuts and touch with Office products and services, see <A href="https://go.microsoft.com/fwlink/p/?linkid=249150">Keyboard shortcuts</A> and <A href="https://go.microsoft.com/fwlink/p/?linkid=253163">Office Touch Guide</A>.



## Prepare servers to run Office Web Apps Server

Perform these procedures on all servers that will run Office Web Apps Server.

**Figure: The steps to prepare servers for Office Web Apps Server**

![The three main steps to prepare servers for Office Web Apps Server.](images/JJ219455.af2a4690-4f8b-42c3-aab5-f7066bc0a936(Office.15).gif "The three main steps to prepare servers for Office Web Apps Server.") 

## Step 1: Install prerequisite software for Office Web Apps Server

Windows Server 2008 R2, Windows Server 2012, and Windows Server 2012 R2 have slightly different prerequisites, so select the appropriate procedure below to install the correct ones for your operating system.

**On Windows Server 2008 R2**

1.  Install the following software:
    
      - [Windows Server 2008 R2 Service Pack 1](https://go.microsoft.com/fwlink/p/?linkid=252370)
    
      - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=256560)
    
      - [Windows PowerShell 3.0](https://go.microsoft.com/fwlink/p/?linkid=244693)
    
      - [Platform update for Windows 7 SP1 and Windows Server 2008 R2 SP1 (KB2670838)](https://go.microsoft.com/fwlink/p/?linkid=293629)

2.  Open the Windows PowerShell prompt as an administrator and run these commands to install the required roles and services.
    
    ```PowerShell
        Import-Module ServerManager
    ```
    
    Then, run this command:
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,Web-Security,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Console,Ink-Handwriting,IH-Ink-Support,NET-Framework,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-Win-CFAC
    ```
    
    If prompted, restart the server.

**On Windows Server 2012**

1.  Open the Windows PowerShell prompt as an administrator and run this command to install the required roles and services.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```
    
    If prompted, restart the server.

**On Windows Server 2012 R2**

1.  Install the following software:
    
      - [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?linkid=510096)

2.  Open the Windows PowerShell prompt as an administrator and run this command to install the required roles and services.
    
    ```PowerShell
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    ```
    
    If prompted, restart the server.

## Step 2: Install Office Web Apps Server and related updates

Complete these steps on any servers that will run Office Web Apps Server.

1.  Download Office Web Apps Server from the [Volume Licensing Service Center (VLSC)](https://go.microsoft.com/fwlink/p/?linkid=256561). To download Office Web Apps Server you must have a license, under a Volume Licensing agreement, for Office Professional Plus 2013, Office Standard 2013, or Office for Mac 2011. The download is located under those Office products on the VLSC portal.

2.  Do one of the following:
    
      - For Windows Server 2012 or Windows Server 2012 R2, open the .img file directly and run **Setup.exe**.
    
      - For Windows Server 2008 R2 SP1, use a program that can mount or extract .img files, then run **Setup.exe**.

3.  On the **Read the Microsoft Software License Terms** page, select **I accept the terms of this agreement** and click **Continue**.

4.  On the **Choose a file location** page, select the folder where you want the Office Web Apps Server files to be installed (for example, C:\\Program Files\\Microsoft Office Web Apps) and select **Install Now**. If the folder you specified doesn't exist, Setup creates it for you.
    
    We recommend that you install Office Web Apps Server on the system drive.

5.  When Setup finishes installing Office Web Apps Server, choose **Close**.

6.  Download and install [Office Web Apps Server SP1](https://go.microsoft.com/fwlink/p/?linkid=510097) (Recommended for Windows Server 2012 and Windows Server 2008 R2 SP1. Required for Windows Server 2012 R2.)
    

    > [!NOTE]
    > If you are applying Office Web Apps Server SP1 at a later time, follow the directions in <A href="apply-software-updates-to-office-web-apps-server.md">Apply software updates to Office Web Apps Server</A>.



7.  Check for the most current Office Web Apps Server updates by reviewing the list on the [TechNet Update center for Office, Office servers, and related products](/office/).
    

    > [!NOTE]
    > If you did not install Office Web Apps Server SP1, apply <A href="https://go.microsoft.com/fwlink/p/?linkid=296579">KB2810007</A>.



## Step 3: Install language packs for Office Web Apps Server

Office Web Apps Server 2013 Language Packs let users view web-based Office files in multiple languages, whether they're opened from SharePoint 2013 document libraries, Outlook Web Access (as attachment previews), and Lync 2013 (as PowerPoint broadcasts). Learn more about how the language packs work in [Planning language packs for Office Web Apps Server](plan-office-web-apps-server.md).

To install the language packs, follow these steps.


1.  Download the Office Web Apps Server Language Packs from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=263945).

2.  Run **WebAppsServerLP\_en-us\_x64.exe**.

3.  In the Office Web Apps Server Language Pack 2013 Wizard, on the **Read the Microsoft Software License Terms** page, select **I accept the terms of this agreement** and select **Continue**.

4.  When Setup finishes installing Office Web Apps Server, choose **Close**.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>To install language packs after the Office Web Apps Server farm is created, you must remove a server from the farm, install the language pack on it, and then add the server back to the farm.</P>
> <LI>
> <P>For a language pack to work correctly, you'll need to install it on all servers in the farm.</P></LI></UL>



## Deploy the Office Web Apps Server farm

Follow the procedures in one of the following three sections, based on what kind of Office Web Apps Server farm you want to create.


> [!TIP]
> If Windows PowerShell doesn't recognize the <STRONG>New-OfficeWebAppsFarm</STRONG> cmdlet when you run it, you may need to import the <STRONG>OfficeWebApps</STRONG> module. Use this command:<BR><CODE>Import-Module -Name OfficeWebApps</CODE>



## Deploy a single-server Office Web Apps Server farm that uses HTTP

If you're only deploying Office Web Apps Server for testing or internal use, and you don't need to provide Office Web Apps Server functionality to Lync Server 2013, this procedure is for you. Here, you'll install a single-server Office Web Apps Server farm that uses HTTP. You won't need a certificate or load balancer, but you will need a dedicated physical server or virtual machine instance that isn't running any other server application.

You can use this Office Web Apps Server farm to provide Office Web Apps functionality to SharePoint 2013.

**Figure: The steps to deploy Office Web Apps Server**

![The three main steps to deploy a single-server Office Web Apps Server farm.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "The three main steps to deploy a single-server Office Web Apps Server farm.")

## Step 1: Create the Office Web Apps Server farm

Use the **New-OfficeWebAppsFarm** command to create a new Office Web Apps Server farm that consists of a single server, as shown in the following example.

```PowerShell
    New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled
```

**Parameters**

  - **–InternalURL** is the name of the server that runs Office Web Apps Server, such as **http://servername**.

  - **–AllowHttp** configures the farm to use HTTP.

  - **–EditingEnabled** enables editing in Office Web Apps when used with SharePoint 2013. This parameter isn't used by Lync Server 2013 because that host doesn't support editing.

Additional parameters that configure translation services, proxy servers, ClipArt support, and Online Viewers are described in [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

If you see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages

## Step 2: Verify that the Office Web Apps Server farm was created successfully

After the farm is created, details about the farm are displayed in the Windows PowerShell prompt. To verify that Office Web Apps Server is installed and configured correctly, use a web browser to access the Office Web Apps Server discovery URL, as shown in the following example. The discovery URL is the *InternalUrl* parameter you specified when you configured your Office Web Apps Server farm, followed by **/hosting/discovery**, for example:

```
    http://servername/hosting/discovery
```

If Office Web Apps Server is working as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example.

```XML 
    <?xml version="1.0" encoding="utf-8" ?> 
    - <wopi-discovery>
    - <net-zone name="internal-http">
    - <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
    <action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```

## Step 3: Configure the host

The farm is now ready to provide Office Web Apps functionality to hosts over HTTP. Visit [Configure Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md) for more information about how to configure hosts.


## Deploy a single-server Office Web Apps Server farm that uses HTTPS
<a name="singlehttps"> </a>

For most production environments, we strongly recommend the use of HTTPS for its security features. Also, HTTPS is required if you want to provide Office Web Apps Server functionality to Lync Server 2013, which lets users view PowerPoint broadcasts in a browser. Here's how to install a single-server Office Web Apps Server farm that uses HTTPS. You'll need to install a certificate on the server as described in [Securing Office Web Apps Server communications by using HTTPS](plan-office-web-apps-server.md).

This Office Web Apps Server farm will provide Office Web Apps functionality to SharePoint 2013 and Lync Server 2013.

**Figure: The steps to deploy Office Web Apps Server**

![The three main steps to deploy a single-server Office Web Apps Server farm.](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "The three main steps to deploy a single-server Office Web Apps Server farm.")

## Step 1: Create the Office Web Apps Server farm

Use the **New-OfficeWebAppsFarm** command to create a new Office Web Apps Server farm that consists of a single server, as shown in the following example.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled
```

**Parameters**

  - **–InternalURL** is the fully qualified domain name (FQDN) of the server that runs Office Web Apps Server, such as **http://servername.contoso.com**.

  - **–ExternalURL** is the FQDN that can be accessed on the Internet.

  - **–CertificateName** is the friendly name of the certificate.

  - **–EditingEnabled** is optional and enables editing in Office Web Apps when used with SharePoint 2013. This parameter isn't used by Lync Server 2013 because that host doesn't support editing.

Additional parameters that configure translation services, proxy servers, ClipArt support, and Online Viewers are described in [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

If you see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages

## Step 2: Verify that the Office Web Apps Server farm was created successfully

After the farm is created, details about the farm are displayed in the Windows PowerShell prompt. To verify that Office Web Apps Server is installed and configured correctly, use a web browser to access the Office Web Apps Server discovery URL, as shown in the following example. The discovery URL is the *InternalUrl* parameter you specified when you configured your Office Web Apps Server farm, followed by **/hosting/discovery**, for example:

```
    https://server.contoso.com/hosting/discovery
```

If Office Web Apps Server works as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="xls"/><action name="view" 
```

> [!NOTE]
> Depending on the security settings of your web browser, you might see a message that prompts you to select <STRONG>Show all content</STRONG> before the contents of the discovery XML file are displayed.

## Step 3: Configure the host

The farm is now ready to provide Office Web Apps functionality to hosts over HTTPS. Visit the following articles for more information about how to configure hosts.

  - [Configure Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Deploying Office Web Apps Server and Lync Server 2013](/previous-versions/office/lync-server-2013/lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013)

## Deploy a multi-server, load-balanced Office Web Apps Server farm that uses HTTPS
<a name="multihttps"> </a>

If you anticipate lots of traffic to your Office Web Apps Server farm, and you want it to be available over the Internet as well as on your internal network, this type of topology is the way to go. This section shows how to install a multi-server Office Web Apps Server farm that uses a load balancer and HTTPS. If you're interested, [read more about this topology](plan-office-web-apps-server.md).

Before you begin, make sure your load balancer is configured as described in [Load balancer requirements for Office Web Apps Server](plan-office-web-apps-server.md). Also, you'll need to install a certificate on the load balancer as described in [Securing Office Web Apps Server communications by using HTTPS](plan-office-web-apps-server.md). This Office Web Apps Server farm will provide Office Web Apps functionality to SharePoint 2013 andLync Server 2013.

**Figure: The steps to deploy Office Web Apps Server**

![The four main steps to deploy a multi-server Office Web Apps Server farm.](images/JJ219455.4c4b31cb-961b-4efd-b755-a18bdcb5c191(Office.15).gif "The four main steps to deploy a multi-server Office Web Apps Server farm.")

## Step 1: Create the Office Web Apps Server farm on the first server

Use the **New-OfficeWebAppsFarm** command to create a new Office Web Apps Server farm on the first server, as shown in the following example.

```PowerShell
    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled
```

**Parameters**

  - **–InternalURL** is the fully qualified domain name (FQDN) of the server that runs Office Web Apps Server, such as **http://servername.contoso.com**.

  - **–ExternalURL** is the FQDN name that can be accessed on the Internet.

  - **-SSLOffloaded** enables offloading SSL termination to the load balancer.

  - **–EditingEnabled** is optional and enables editing in Office Web Apps when used with SharePoint 2013. This parameter isn't used by Lync Server 2013 because that host doesn't support editing.

Other parameters that configure translation services, proxy servers, ClipArt support, and Online Viewers are described in [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).

If you see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages

## Step 2: Add more servers to the farm

After the first server is running Office Web Apps Server, run the **New-OfficeWebAppsMachine** command on each server you want to add to the Office Web Apps Server farm. For the **–MachineToJoin** parameter, use the computer name of a server that's already in the Office Web Apps Server farm. For example, if server1.contoso.com is already in the farm, use the following:

```PowerShell
    New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
```

Want more information about these parameters? You can find them in [New-OfficeWebAppsMachine](/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps).

## Step 3: Verify that the Office Web Apps Server farm was created successfully

After the farm is created, details about the farm are displayed in the Windows PowerShell prompt. To verify that Office Web Apps Server is installed and configured correctly, use a web browser to access the Office Web Apps Server discovery URL, as shown in the following example. The discovery URL is the *InternalUrl* parameter you specified when you configured your Office Web Apps Server farm, followed by **/hosting/discovery**. For example:

```
    https://server.contoso.com/hosting/discovery
```

If Office Web Apps Server works as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example:

```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xlsb"/> 
```

> [!NOTE]
> Depending on the security settings of your web browser, you might see a message that prompts you to select <STRONG>Show all content</STRONG> before the contents of the discovery XML file are displayed.

## Step 4: Configure the host

The farm is now ready to provide Office Web Apps functionality to hosts over HTTPS. Visit the following articles for more information about how to configure hosts.

  - [Configure Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [Deploying Office Web Apps Server and Lync Server 2013](/previous-versions/office/lync-server-2013/lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013)

## If you see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages

If features of the .NET Framework 3.5 were installed and then removed, you might see "500 Web Service Exceptions" or "500.21 – Internal Server Error" messages when you run OfficeWebApps cmdlets. To fix this, run the following sample commands from an elevated command prompt to clean up settings that could prevent Office Web Apps Server from functioning correctly:

**For Windows Server 2008 R2**

```PowerShell
    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -iru
```

```PowerShell
    iisreset /restart /noforce
```

**For Windows Server 2012 or Windows Server 2012 R2**

```PowerShell
    dism /online /enable-feature /featurename:IIS-ASPNET45
```

## See also


[New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Plan Office Web Apps Server](plan-office-web-apps-server.md)  
[Configure Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)  


[Deploying Office Web Apps Server and Lync Server 2013](/previous-versions/office/lync-server-2013/lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013)  
