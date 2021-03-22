---
title: Configure Office Online Server for SharePoint Server 2016
description: Learn how to configure SharePoint Server 2016 to use Office Online Server (the next version of Office Web Apps Server).
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 9/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: a5276781-133b-413c-beca-b851e17c2081
---


# Configure Office Online Server for SharePoint Server

 **Summary:** Learn how to configure SharePoint Server to use Office Online Server (the next version of Office Web Apps Server).
  
    
    


 **Audience**: IT Professionals
  
    
    


This article picks up where  [Deploy Office Online Server](../deploy-office-online-server.md) left off. In that article, you set up the server that runs Office Online Server on-premises. In this one, you'll configure SharePoint Server to use Office Online Server. First, you'll need to run a few Microsoft PowerShell cmdlets from SharePoint Server 2016, after which users will be able to open Office files from SharePoint Server document libraries in a browser.
  
    
    
  

## Before you configure SharePoint Server to use Office Online Server
<a name="Before"> </a>

A few things to check before getting started: 
  
- These instructions also apply to SharePoint Server 2013, however SharePoint Server 2013 cannot use the Excel Online external data connectivity and data refresh functionality in Office Online Server.
    

- Install SharePoint Server 2016. See  [Install SharePoint Server](/SharePoint/install/install) for guidance.
    
  
- Make sure all SharePoint Server 2016 web applications use claims-based authentication. Office Online rendering and editing won't work on SharePoint Server 2016 web applications that use classic mode authentication. 
    
  
- To enable users to edit (not just read) Office documents in a web browser, you'll need an editing license. Also, you'll need to enable editing on the Office Online Server farm. 
    
  
- If you log on to SharePoint Server 2016 by using the System Account, you won't be able to test the connection between SharePoint Server 2016 and Office Online Server. Log on with a different account to test the connection. 
    
  
- Low memory conditions can cause Office document previews to fail in Office Online. 

- SharePoint Server 2013 cannot use the Excel Online external data connectivity and data refresh functionality in Office Online Server. That's only available with SharePoint Server 2016.

- Office Online Server uses OAuth tokens to communicate with SharePoint Server. These tokens can potentially be intercepted and replayed, providing an attacker with the same rights as the user making the request from SharePoint Server to Office Online Server. It is strongly recommended that you configure Office Online Server to use HTTPS (TLS) only.
  

## Configure SharePoint Server to use Office Online Server
<a name="ConfigureMain"> </a>

Choose one of the following sections depending on whether you want to use HTTP or HTTPS. HTTP is generally recommended only for test environments. In production environments, the more secure HTTPS protocol is the better choice.
  
    
    

### In a test environment that uses HTTP
<a name="scenario1"> </a>

For this configuration, make sure you have set up Office Online Server by following the steps in  [Deploy a single-server Office Online Server farm that uses HTTP](../deploy-office-online-server.md#scenario1). Be sure to configure the Office Online Server farm to use an internal URL and HTTP. 
  
    
    

  
    
    

#### Step 1: Create the binding between SharePoint 2016 and Office Web Apps Server

To get started, open an elevated SharePoint 2016 Management Shell. (Right-click **SharePoint 2016 Management Shell**, and then click **Run as Administrator**.)
  
    
    
Run the following command, where <WacServerName> is the fully qualified domain name (FQDN) of the URL that you set for the internal URL. This is the point of entry for Office Online Server traffic. For this test environment, you need to specify the -AllowHTTP parameter to allow SharePoint Server 2016 to receive discovery information from the Office Online Server farm by using HTTP. If you don't specify -AllowHTTP, SharePoint Server 2016 will try to use HTTPS to communicate with the Office Online Server farm, and this command won't work.
  
    
    



```

New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP
```

After running this command, you should see a list of bindings displayed at the Microsoft PowerShell command prompt.
  
    
    

#### Step 2: View the WOPI zones for the SharePoint bindings

Office Online Server uses zones to determine which URL (internal or external) and which protocol (HTTP or HTTPS) to use when it communicates with the host, in this case, SharePoint Server 2016. By default, SharePoint Server 2016 uses the **internal-https** zone. Run the following command to see what your current zone is.
  
    
    

```
Get-SPWOPIZone
```

The WOPI zone displayed by this command should be **internal-http**. If it's displayed correctly, skip to step 4. If it isn't, see the next step.
  
    
    

#### Step 3: Change the WOPI zone to internal-http

If the result from Step 3 was **internal-https**, run the following command to change the zone to **internal-http**. You need to make this change because the zone of SharePoint Server 2016 must match the zone of the Office Online Server farm.
  
    
    

```
Set-SPWOPIZone -zone "internal-http"
```

Verify that the new zone is **internal-http** by running **Get-SPWOPIZone** again.
  
    
    

#### Step 4: Change the AllowOAuthOverHttp setting in SharePoint 2016 to True
<a name="oauth"> </a>

To use Office Online with SharePoint Server 2016 over HTTP in a test environment, you need to set AllowOAuthOverHttp to **True**. Otherwise Office Online won't work. You can check the current status by running the following example.
  
    
    

```
(Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```

If this command returns **False**, run the following commands to set this to **True**.
  
    
    



```
$config = (Get-SPSecurityTokenServiceConfig)
```




```
$config.AllowOAuthOverHttp = $true
```




```
$config.Update()
```

Run the following command again to verify that the AllowOAuthOverHttp setting is now set to **True**.
  
    
    



```
(Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```


#### Step 5: Enable the Excel SOAP API
<a name="oauth"> </a>

The Excel SOAP API is needed for scheduled data refresh with Excel Online, and for Excel Web Part rendering. To enable the Excel SOAP API, you need to add the WopiLegacySoapSupport property to the SharePoint Server farm properties using by PowerShell. The input parameter is the URL to ExcelServiceInternal.asmx. This URL can address multiple OOS servers via load balancing. Simply replace the <string> with your Office Online Server path.
  
    
    
To enable the Excel SOAP API, run the following PowerShell where <URL> is the URL of your Office Online Server farm. (For example, http://OfficeOnlineServer.contoso.com.)
  
    
    



```

$Farm = Get-SPFarm
$Farm.Properties.Add("WopiLegacySoapSupport", "<URL>/x/_vti_bin/ExcelServiceInternal.asmx");
$Farm.Update();

```


#### Step 6: Verify that Office Web Apps is working
<a name="oauth"> </a>

In SharePoint Server 2016, make sure you're not logged on as System Account because you won't be able to edit or view the documents with Office Online. Go to a SharePoint Server 2016 document library that contains Office documents and view a Word, PowerPoint, Excel, or OneNote file. The document should open in a browser that displays the file by using Office Online.
  
    
    

### In a production environment that uses HTTPS
<a name="SPHTTPS"> </a>

Before you start the following procedures, make sure that you have set up Office Online Server by following the steps in  [Deploy a single-server Office Online Server farm that uses HTTPS ](../deploy-office-online-server.md#singleHTTPS) or [Deploy a multi-server, load-balanced Office Online Server farm that uses HTTPS](../deploy-office-online-server.md#multiHTTPS).
  
    
    

#### Step 1: Create the binding between SharePoint 2016 and Office Online Server

To get started, open an elevated SharePoint 2016 Management Shell. (Right-click **SharePoint 2016 Management Shell**, and then click **Run as Administrator**.)
  
    
    
Run the following command, where <WacServerName> is the fully qualified domain name (FQDN) of the URL that you set for the internal URL. This is the point of entry for Office Online Server traffic. 
  
    
    



```

New-SPWOPIBinding -ServerName <WacServerName> 
```


#### Step 2: View the WOPI zone of SharePoint 2016

Office Online Server uses zones to determine which URL (internal or external) and which protocol (HTTP or HTTPS) to use when it communicates with the host, which in this case is SharePoint Server 2016. By default, SharePoint Server 2016 uses the **internal-https** zone. Verify that this is the current zone by running the following command.
  
    
    

```
Get-SPWOPIZone
```

Take note of the WOPI zone that is displayed. 
  
    
    

#### Step 3: Change the WOPI zone if necessary

Depending on your environment, you might have to change the WOPI zone. If you have a SharePoint farm that's both internal and external, specify external. If you have a SharePoint farm that's internal only, specify internal.
  
    
    
If the results from Step 2 show that **internal-https** and the SharePoint farm is internal only, you can skip this step. If you have a SharePoint farm that's internal and external, you need to run the following command to change the zone to **external-https**.
  
    
    



```
Set-SPWOPIZone -zone "external-https"
```


#### Step 4: Enable the Excel SOAP API

The Excel SOAP API is needed for scheduled data refresh with Excel Online, and for Excel Web Part rendering. To enable the Excel SOAP API, you need to add the WopiLegacySoapSupport property to the SharePoint Server farm properties using by PowerShell. The input parameter is the URL to ExcelServiceInternal.asmx. This URL can address multiple OOS servers via load balancing. Simply replace the <string> with your Office Online Server path.
  
    
    
To enable the Excel SOAP API, run the following PowerShell where <URL> is the URL of your Office Online Server farm. (For example, https://OfficeOnlineServer.contoso.com.)
  
    
    



```

$Farm = Get-SPFarm
$Farm.Properties.Add("WopiLegacySoapSupport", "<URL>/x/_vti_bin/ExcelServiceInternal.asmx");
$Farm.Update();

```


#### Step 5: Verify that Office Web Apps is working

In SharePoint Server 2016, make sure you aren't logged on as System Account because you won't be able to edit or view the documents with Office Online. Go to a SharePoint Server 2016 document library that contains Office documents and view a Word, PowerPoint, Excel, or OneNote file. The document should open in a browser that displays the file by using Office Online.
  
    
    

## Disconnect SharePoint Server 2016 from Office Online Server
<a name="disconnect"> </a>

If, for any reason, you want to disconnect SharePoint Server 2016 from Office Online Server, use the following command example.
  
    
    

```

Remove-SPWOPIBinding -All:$true
```