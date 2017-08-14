---
title: Deploy Office Online Server
ms.prod: OFFICERESOURCEKIT
ms.assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
---


# Deploy Office Online Server
 **Summary:** Explains how to deploy on-premises for use by , , and .
 **Audience**: IT Professionals
  
    
    

 is the next version of Office Web Apps Server. Deploying involves installing some prerequisite software and running a few commands, but overall the process is designed to be pretty straightforward. This article walks you through the procedures to get your servers ready, then gives you the commands to configure the on-premises farm.
In this article:
  
    
    


-  [Prepare servers to run Office Online Server](deploy-office-online-server.md#prerequisites)
    
  
-  [Deploy the Office Online Server farm](deploy-office-online-server.md#DeploymentTypes)
    
  
-  [If you see "500 Web Service Exceptions" or "500.21 - Internal Server Error" messages](deploy-office-online-server.md#ErrorMessages)
    
  

## Prepare servers to run Office Online Server
<a name="prerequisites"> </a>

Perform these procedures on all servers that will run . This server must be or Windows Server 2016. (Note that Windows Server 2016 requires April 2017 or later.)
  
    
    

### Step 1: Install prerequisite software for Office Online Server
<a name="installrequirements"> </a>


### To install Office Online Server


1. Open the prompt as an administrator and run this command to install the required roles and services. 
    
    **:**
    


  ```
  
Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation

  ```


    
  
    
    

    
    **Windows Server 2016:**
    


  ```
  
Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,NET-Framework-Features,NET-Framework-45-Features,NET-Framework-Core,NET-Framework-45-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
  ```


    
  
    
    

    
    If prompted, restart the server.
    
  
2. Install the following software:
    
  -  [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=510096)
    
  
  -  [Visual C++ Redistributable Packages for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)
    
  
  -  [Visual C++ Redistributable for Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=620071)
    
  
  -  [Microsoft.IdentityModel.Extention.dll](https://go.microsoft.com/fwlink/p/?LinkId=620072)
    
  

### Step 2: Install Office Online Server
<a name="installwacserver"> </a>

Next, we'll install .
  
    
    
If you plan to use any features that utilize external data access (such as Data Models, Power Pivot, or Power View), note that must reside in the same Active Directory forest as its users as well as any external data sources that you plan to access using Windows-based authentication.
  
    
    
Complete these steps on any servers that will run .
  
    
    

### To install Office Online Server


1. Download from the  [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/p/?LinkId=256561). The download is located under those products on the VLSC portal.
    
  
2. Run Setup.exe.
    
  
3. On the **Read the Microsoft Software License Terms** page, select **I accept the terms of this agreement** and click **Continue**. 
    
  
4. On the **Choose a file location** page, select the folder where you want the files to be installed (for example, C:\\Program Files\\Microsoft Office Web Apps) and select **Install Now**. If the folder you specified doesn't exist, Setup creates it for you.
    
    We recommend that you install on the system drive.
    
  
5. When Setup finishes installing , choose **Close**.
    
  
6. If you're planning to use Kerberos Constrained Delegation with , then, in **Services**, set the **Claims to Windows Token Service** [to start automatically](https://go.microsoft.com/fwlink/p/?LinkId=620769) on this server.
    
  
If you plan to use Kerberos Constrained Delegation with , be sure to add each server in the farm to the Active Directory Domain Services delegation list.
  
    
    

### Step 3: Install language packs for Office Web Apps Server
<a name="installlangpack"> </a>

 Language Packs let users view web-based files in multiple languages, whether they're opened from document libraries or
  
    
    
To install the language packs, follow these steps.
  
    
    

1. Download the Language Packs from the  [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=798136).
    
  
2. Run **wacserverlanguagepack.exe**.
    
  
3. In the Language Pack Wizard, on the **Read the Microsoft Software License Terms** page, select **I accept the terms of this agreement** and select **Continue**.
    
  
4. When Setup finishes installing , choose **Close**.
    
  

> [!IMPORTANT]
>  To install language packs after the farm is created, you must remove a server from the farm, install the language pack on it, and then add the server back to the farm.>  For a language pack to work correctly, you'll need to install it on all servers in the farm.
  
    
    


## Deploy the Office Online Server farm
<a name="DeploymentTypes"> </a>

Follow the procedures in one of the following three sections, based on what kind of farm you want to create.
  
    
    

> [!TIP]
> If doesn't recognize the **New-OfficeWebAppsFarm** cmdlet when you run it, you may need to import the **OfficeWebApps** module. Use this command:>  `Import-Module -Name OfficeWebApps`
  
    
    


### Deploy a single-server Office Online Server farm that uses HTTP
<a name="scenario1"> </a>

If you're only deploying for testing or internal use, and you don't need to provide functionality to , this procedure is for you. Here, you'll install a single-server farm that uses HTTP. You won't need a certificate or load balancer, but you will need a dedicated physical server or virtual machine instance that isn't running any other server application. 
  
    
    
You can use this farm to provide functionality to and .
  
    
    

#### Step 1: Create the Office Online Server farm

Use the **New-OfficeWebAppsFarm** command to create a new farm that consists of a single server, as shown in the following example.
  
    
    

```
New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled
```

 **Parameters**
  
    
    

- **-InternalURL** is the name of the server that runs , such as **http://servername**.
    
  
- **-AllowHttp** configures the farm to use HTTP.
    
  
- **-EditingEnabled** enables editing in when used with . This parameter isn't used by or because those hosts don't support editing.
    
  

#### Step 2: Verify that the Office Online Server farm was created successfully

After the farm is created, details about the farm are displayed in the prompt. To verify that is installed and configured correctly, use a web browser to access the discovery URL, as shown in the following example. The discovery URL is the  _InternalUrl_ parameter you specified when you configured your farm, followed by **/hosting/discovery**, for example:
  
    
    

```
http://servername/hosting/discovery
```

If is working as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example.
  
    
    



```
<?xml version="1.0" encoding="utf-8" ?>
- <wopi-discovery>
- <net-zone name="internal-http">
- <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
<action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" /> 
<action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" /> 
<action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" /> 
<action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" /> 

```


#### Step 3: Configure Secure Store access (optional)

If you're planning to use the Secure Store service in SharePoint Server in an HTTP environment, there's a parameter that you need to set to enable this. (If you're not planning to use Secure Store in SharePoint Server with Excel Online, you can skip this step.)
  
    
    
When attempts to refresh data in a workbook or ODC file that is stored in an HTTP path, that data refresh will fail if you have not configured to allow Secure Store connections over HTTP.
  
    
    
Use the Set-OfficeWebAppsFarm cmdlet to configure the Secure Store over HTTP settings:
  
    
    



```

Set-OfficeWebAppsFarm -AllowHttpSecureStoreConnections:$true
```

Keep in mind that the contents of the workbook or ODC file will be transmitted in clear text over HTTP. Data connected workbooks and ODC files contain database connection information, and can contain passwords.
  
    
    

#### Step 4: Configure the host

The farm is now ready to provide functionality to hosts over HTTP. Visit the following articles for more information about how to configure hosts. 
  
    
    

-  [Configure Office Online Server for SharePoint Server 2016](configure-office-online-server-for-sharepoint-server-2016.md)
    
  
-  [Office Online Server integration with Exchange](https://go.microsoft.com/fwlink/p/?LinkId=620075)
    
  

### Deploy a single-server Office Online Server farm that uses HTTPS
<a name="singleHTTPS"> </a>

For most production environments, we strongly recommend the use of HTTPS for its security features. Also, HTTPS is required if you want to provide functionality to , which lets users view broadcasts in a browser. Here's how to install a single-server farm that uses HTTPS. You'll need to install a certificate on the server. 
  
    
    
This farm will provide functionality to , , and .
  
    
    

#### Step 1: Create the Office Online Server farm

Use the **New-OfficeWebAppsFarm** command to create a new farm that consists of a single server, as shown in the following example.
  
    
    

```
New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled
```

 **Parameters**
  
    
    

- **-InternalURL** is the fully qualified domain name (FQDN) of the server that runs , such as **http://servername.contoso.com**.
    
  
- **-ExternalURL** is the FQDN that can be accessed on the Internet.
    
  
- **-CertificateName** is the friendly name of the certificate.
    
  
- **-EditingEnabled** is optional and enables editing in when used with . This parameter isn't used by or because those hosts don't support editing.
    
  

  
    
    

#### Step 2: Verify that the Office Online Server farm was created successfully

After the farm is created, details about the farm are displayed in the prompt. To verify that is installed and configured correctly, use a web browser to access the discovery URL, as shown in the following example. The discovery URL is the  _InternalUrl_ parameter you specified when you configured your farm, followed by **/hosting/discovery**, for example:
  
    
    

```
https://server.contoso.com/hosting/discovery
```

If works as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example:
  
    
    



```
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" 
default="true" ext="xls"/><action name="view"
 

```


> [!NOTE]
> Depending on the security settings of your web browser, you might see a message that prompts you to select **Show all content** before the contents of the discovery XML file are displayed.
  
    
    


#### Step 3: Configure the host

The farm is now ready to provide functionality to hosts over HTTPS. Visit the following articles for more information about how to configure hosts. 
  
    
    

-  [Configure Office Online Server for SharePoint Server 2016](configure-office-online-server-for-sharepoint-server-2016.md)
    
  
-  [Office Online Server integration with Exchange](https://go.microsoft.com/fwlink/p/?LinkId=620075)
    
  

### Deploy a multi-server, load-balanced Office Online Server farm that uses HTTPS
<a name="multiHTTPS"> </a>

If you anticipate lots of traffic to your farm, and you want it to be available over the Internet as well as on your internal network, this type of topology is the way to go. This section shows how to install a multi-server farm that uses a load balancer and HTTPS.
  
    
    
Before you begin, make sure your load balancer is configured. Also, you'll need to install a certificate on the load balancer. This farm will provide functionality to , , and .
  
    
    

#### Step 1: Create the Office Online Server farm on the first server

Use the **New-OfficeWebAppsFarm** command to create a new farm on the first server, as shown in the following example.
  
    
    

```

New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled
```

 **Parameters**
  
    
    

- **-InternalURL** is the fully qualified domain name (FQDN) of the server that runs , such as **http://servername.contoso.com**.
    
  
- **-ExternalURL** is the FQDN name that can be accessed on the Internet.
    
  
- **-SSLOffloaded** enables offloading SSL termination to the load balancer.
    
  
- **-EditingEnabled** is optional and enables editing in when used with . This parameter isn't used by or because those hosts don't support editing.
    
  

#### Step 2: Add more servers to the farm

After the first server is running , run the **New-OfficeWebAppsMachine** command on each server you want to add to the farm. For the **-MachineToJoin** parameter, use the computer name of a server that's already in the farm. For example, if server1.contoso.com is already in the farm, use the following:
  
    
    

```
New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
```


#### Step 3: Verify that the Office Online Server farm was created successfully

After the farm is created, details about the farm are displayed in the prompt. To verify that is installed and configured correctly, use a web browser to access the discovery URL, as shown in the following example. The discovery URL is the  _InternalUrl_ parameter you specified when you configured your farm, followed by **/hosting/discovery**. For example:
  
    
    

```
https://server.contoso.com/hosting/discovery
```

If works as expected, you should see a Web Application Open Platform Interface Protocol (WOPI)-discovery XML file in your web browser. The first few lines of that file should resemble the following example:
  
    
    



```
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&amp;><rs=DC_LLCC&amp;>" default="true" ext="xlsb"/> 

```


> [!NOTE]
> Depending on the security settings of your web browser, you might see a message that prompts you to select **Show all content** before the contents of the discovery XML file are displayed.
  
    
    


#### Step 4: Configure the host

The farm is now ready to provide functionality to hosts over HTTPS. Visit the following articles for more information about how to configure hosts. 
  
    
    

-  [Configure Office Online Server for SharePoint Server 2016](configure-office-online-server-for-sharepoint-server-2016.md)
    
  
-  [Office Online Server integration with Exchange](https://go.microsoft.com/fwlink/p/?LinkId=620075)
    
  

## If you see "500 Web Service Exceptions" or "500.21 - Internal Server Error" messages
<a name="ErrorMessages"> </a>

If features of the .NET Framework 4.6 were installed and then removed, you might see "500 Web Service Exceptions" or "500.21 - Internal Server Error" messages when you run OfficeWebApps cmdlets. To fix this, run the following sample commands from an elevated command prompt to clean up settings that could prevent from functioning correctly:
  
    
    
 **For Windows Server 2012 R2 or Windows Server 2016**
  
    
    



```

Add-WindowsFeature NET-Framework-45-Core, NET-Framework-45-ASPNET, Web-Asp-Net45
```


## See also
<a name="ErrorMessages"> </a>


#### 


  
    
    
 [Apply software updates to Office Online Server](apply-software-updates-to-office-online-server.md)
  
    
    
 [Office Online Server release schedule](office-online-server-release-schedule.md)
