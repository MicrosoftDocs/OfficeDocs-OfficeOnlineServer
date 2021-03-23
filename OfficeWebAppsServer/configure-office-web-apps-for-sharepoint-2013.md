---
title: Configure Office Web Apps for SharePoint 2013
TOCTitle: Configure Office Web Apps for SharePoint 2013
ms:assetid: a5276781-133b-413c-beca-b851e17c2081
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ff431687(v=office.15)
ms:contentKeyID: 48409069
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Configure Office Web Apps for SharePoint 2013

 

_**Applies to:** SharePoint Server 2013, SharePoint Foundation 2013, Office Web Apps_


**Summary:** Explains how to configure SharePoint 2013 to use Office Web Apps.

**Audience:** IT Professionals

This article picks up where [Deploy Office Web Apps Server](deploy-office-web-apps-server.md) left off. In that article, you set up the server that runs Office Web Apps Server. In this one, you'll configure SharePoint 2013 to use Office Web Apps Server. First, you'll need to run a few Windows PowerShell cmdlets from SharePoint 2013, after which users will be able to open Office files from SharePoint 2013 document libraries in a browser.

If you're not familiar with the features of Office Web Apps Server, [check out the overview topic](office-web-apps-server-overview.md).

In this article:

  - Before configuring SharePoint 2013 to use Office Web Apps Server

  - Configure SharePoint 2013 to use Office Web Apps Server

  - Troubleshoot errors in Office Web Apps when it is used with SharePoint 2013

  - Disconnect SharePoint 2013 from Office Web Apps Server

## Before you configure SharePoint 2013 to use Office Web Apps Server

A few things to check before getting started:

  - Install SharePoint 2013. See [Install SharePoint 2013](https://technet.microsoft.com/library/cc303424\(v=office.15\)) for guidance.

  - Make sure all SharePoint 2013 web applications use claims-based authentication. Office Web Apps rendering and editing won't work on SharePoint 2013 web applications that use classic mode authentication. Learn more in [SharePoint authentication requirements for Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

  - To enable users to edit (not just read) Office documents in a web browser, you'll need an editing license. Also, you'll need to enable editing on the Office Web Apps Server farm. You can learn more about licensing requirements in [Licensing Office Web Apps for editing Office files](plan-office-web-apps-used-with-sharepoint-2013.md).

  - If you log on to SharePoint 2013 by using the System Account, you won't be able to test the connection between SharePoint 2013 and Office Web Apps Server. Log on with a different account to test the connection.

  - Low memory conditions can cause Office document previews to fail in Office Web Apps. Review the article, [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver), for SharePoint 2013. These are the same requirements used by Office Web Apps Server.

## Configure SharePoint 2013 to use Office Web Apps Server

Choose one of the following sections depending on whether you want to use HTTP or HTTPS. HTTP is generally recommended only for test environments. In production environments, the more secure HTTPS protocol is the better choice.

## In a test environment that uses HTTP

For this configuration, make sure you have set up Office Web Apps Server by following the steps in [Deploy a single-server Office Web Apps Server farm in a test environment](deploy-office-web-apps-server.md). Be sure to configure the Office Web Apps Server farm to use an internal URL and HTTP. The [Video: Configure Office Web Apps for SharePoint 2013](video-configure-office-web-apps-for-sharepoint-2013.md) shows how to set up Office Web Apps Server and configure SharePoint 2013 to use Office Web Apps Server in a test environment.

## Step 1: Open an elevated SharePoint 2013 Management Shell

Choose the procedure that corresponds to your server operating system.

**In Windows Server 2008 R2**

1.  Click **Start** \> **All Programs** \> **Microsoft SharePoint 2013 Products**.

2.  Right-click **SharePoint 2013 Management Shell**, and click **Run as administrator**.

**In Windows Server 2012**

1.  Press the Windows logo key + Q, or swipe in from the edge of the screen to show the charms, and then click **Search** to see all the applications that are installed on the computer.

2.  Right-click **SharePoint 2013 Management Shell** to display the app bar.

3.  In the app bar, click **Run as administrator**.

## Step 2: Create the binding between SharePoint 2013 and Office Web Apps Server

Run the following command, where \<WacServerName\> is the fully qualified domain name (FQDN) of the URL that you set for the internal URL. This is the point of entry for Office Web Apps Server traffic. For this test environment, you need to specify the –AllowHTTP parameter to allow SharePoint 2013 to receive discovery information from the Office Web Apps Server farm by using HTTP. If you don't specify –AllowHTTP, SharePoint 2013 will try to use HTTPS to communicate with the Office Web Apps Server farm, and this command won't work.

```PowerShell
    New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP
```
After running this command, you should see a list of bindings displayed at the Windows PowerShell command prompt.

Need help? See [New-SPWOPIBinding](/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps).

## Step 3: View the WOPI zones for the SharePoint bindings

Office Web Apps Server uses zones to determine which URL (internal or external) and which protocol (HTTP or HTTPS) to use when it communicates with the host, in this case, SharePoint 2013. By default, SharePoint Server 2013 uses the **internal-https** zone. Run the following command to see what your current zone is.

```PowerShell
    Get-SPWOPIZone
```
The WOPI zone displayed by this command should be **internal-http**. If it's displayed correctly, skip to step 5. If it isn't, see the next step.

Need help? See [Get-SPWOPIZone](/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Step 4: Change the WOPI zone to internal-http

If the result from Step 3 was **internal-https**, run the following command to change the zone to **internal-http**. You need to make this change because the zone of SharePoint 2013 must match the zone of the Office Web Apps Server farm.

```PowerShell
    Set-SPWOPIZone -zone "internal-http"
```

Verify that the new zone is **internal-http** by running **Get-SPWOPIZone** again.

Need help? See [Set-SPWOPIZone](/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps) and [Get-SPWOPIZone](/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Step 5: Change the AllowOAuthOverHttp setting in SharePoint 2013 to True

To use Office Web Apps with SharePoint 2013 over HTTP in a test environment, you need to set AllowOAuthOverHttp to **True**. Otherwise Office Web Apps won't work. You can check the current status by running the following example.

```PowerShell
    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```

If this command returns **False**, run the following commands to set this to **True**.

```PowerShell
    $config = (Get-SPSecurityTokenServiceConfig)
```
```PowerShell
    $config.AllowOAuthOverHttp = $true
```
```PowerShell
    $config.Update()
```

Run the following command again to verify that the AllowOAuthOverHttp setting is now set to **True**.

```PowerShell
    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp
```

Need help? See [Get-SPSecurityTokenServiceConfig](https://technet.microsoft.com/library/ff607642\(v=office.15\)).

## Step 6: Verify that Office Web Apps is working

In SharePoint 2013, make sure you're not logged on as System Account because you won't be able to edit or view the documents with Office Web Apps. Go to a SharePoint 2013 document library that contains Office documents and view a Word, PowerPoint, Excel, or OneNote file. The document should open in a browser that displays the file by using Office Web Apps.

If this step fails, see Troubleshooting errors in Office Web Apps.

## In a production environment that uses HTTPS

Before you start the following procedures, make sure that you have set up Office Web Apps Server by following the steps in [Deploy a single-server Office Web Apps Server farm that uses HTTPS](deploy-office-web-apps-server.md#singlehttps) or [Deploy a multi-server, load-balanced Office Web Apps Server farm that uses HTTPS](deploy-office-web-apps-server.md#multihttps).

## Step 1: Open the SharePoint 2013 Management Shell

Choose the procedure that corresponds to your server operating system.

**In Windows Server 2008 R2**

1.  Select **Start** \> **All Programs** \> **Microsoft SharePoint 2013 Products**.

2.  Right-click **SharePoint 2013 Management Shell** to display the shortcut menu, and click **Run as administrator**.

**In Windows Server 2012**

1.  Press the Windows logo key + Q, or swipe in from the edge of the screen to show the charms and then click **Search** to see all the applications that are installed on the computer.

2.  Right-click **SharePoint 2013 Management Shell** to display the app bar.

3.  In the app bar, click **Run as administrator**.

## Step 2: Create the binding between SharePoint 2013 and Office Web Apps Server

Run the following command, where \<WacServerName\> is the fully qualified domain name (FQDN) of the URL that you set for the internal URL. This is the point of entry for Office Web Apps Server traffic.

```PowerShell
    New-SPWOPIBinding -ServerName <WacServerName> 
```
Need help? See [New-SPWOPIBinding](/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps).

## Step 3: View the WOPI zone of SharePoint 2013

Office Web Apps Server uses zones to determine which URL (internal or external) and which protocol (HTTP or HTTPS) to use when it communicates with the host, which in this case is SharePoint 2013. By default, SharePoint Server 2013 uses the **internal-https** zone. Verify that this is the current zone by running the following command.

```PowerShell
    Get-SPWOPIZone
```
Take note of the WOPI zone that is displayed.

Need help? See [Get-SPWOPIZone](/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Step 4: Change the WOPI zone if necessary

Depending on your environment, you might have to change the WOPI zone. If you have a SharePoint farm that's both internal and external, specify external. If you have a SharePoint farm that's internal only, specify internal.

If the results from Step 3 show that **internal-https** and the SharePoint farm is internal only, you can skip this step. If you have a SharePoint farm that's internal and external, you need to run the following command to change the zone to **external-https**.

```PowerShell
    Set-SPWOPIZone -zone "external-https"
```

Need help? See [Set-SPWOPIZone](/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps).

## Step 5: Verify that Office Web Apps is working

In SharePoint 2013, make sure you aren't logged on as System Account because you won't be able to edit or view the documents with Office Web Apps. Go to a SharePoint 2013 document library that contains Office documents and view a Word, PowerPoint, Excel, or OneNote file. The document should open in a browser that displays the file by using Office Web Apps.

If this step fails, see Troubleshooting errors in Office Web Apps.

## Troubleshoot errors in Office Web Apps when it is used with SharePoint 2013

If Office Web Apps isn't working correctly when it is used together with SharePoint 2013, locate the symptom below and expand the heading to find troubleshooting steps.

## Problem: When you select the "new document" link in a SharePoint library, you're prompted to upload a document instead of having the option to create a new Office document. Choosing (single-clicking) an Office document opens the file in the client application. Previews of Office documents are not displayed.

Here are some troubleshooting options to try.

**Verify that claims-based authentication is used by the SharePoint web application that is used to create the new document**

Only web applications that use claims-based authentication can open files in Office Web Apps. To determine the authentication provider for a web application, follow these steps:

1.  In SharePoint 2013 Central Administration, click **Manage web applications**.

2.  Select the web application that you want to check, and click **Authentication Providers** on the ribbon.

The authentication provider must be displayed as **Claims Based Authentication** for Office Web Apps to work correctly with the web application. To resolve this issue, you can delete the web application and recreate it using claims-based authentication, or you can change the authentication method of the web application. You can find more information in [SharePoint authentication requirements for Office Web Apps](plan-office-web-apps-used-with-sharepoint-2013.md).

**Make sure the WOPI zones match on the SharePoint 2013 and the Office Web Apps Server farm.**

To do this, run the following command on the SharePoint Server:

```PowerShell
    Get-SPWopiZone 
```
The result will be one of the following:.

  - internal-https

  - internal-http

  - external-https

  - external-http

Next, run the following command on the SharePoint Server.

```PowerShell
    Get-SPWOPIBinding
```
In the output, look for **WopiZone: zone**. If the results from Get-SPWopiZone don't match the zone that is returned by Get-SPWOPIBinding, run the **Set-SPWOPIZone -Zone** cmdlet on the SharePoint Server to change the WOPI zone to match the result from Get-SPWOPIBinding. For help with using these cmdlets, see [Get-SPWOPIBinding](/powershell/module/sharepoint-server/Get-SPWOPIBinding?view=sharepoint-ps), [Set-SPWOPIBinding](/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps), and [Get-SPWOPIZone](/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps).

## Problem: You receive a "Sorry, this document can't be opened for editing" error when you try to edit an Office document in Office Web Apps.

In some situations, users that are members of Active Directory (AD) Security Groups may be unable to edit documents in the browser. The solution is to ensure the User Profile Service Application (UPA) is properly configured and fully synchronized with user and group memberships. For more information, see the KB article [SharePoint 2013 Unable to edit Office Web Apps 2013 files with users that are members of security groups](https://support.microsoft.com/kb/2908321).

## Problem: You receive a "Sorry, something went wrong" error when you try to view an Office document in Office Web Apps.

Make sure you're not logged in as System Account because you won't be able to edit or view a document. Log on as a different user and try to access Office Web Apps again.

## Problem: You receive a "Sorry, there was a problem and we can't open this document" error when you try to view an Office document in Office Web Apps.

If you set up Office Web Apps in a test environment that uses HTTP, make sure you set the AllowOAuthOverHttp setting to **True** as described in Step 5: Change the AllowOAuthOverHttp setting in SharePoint 2013 to True.

If you added domains to the Allow List by using the [New-OfficeWebAppsHost](/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps) cmdlet, make sure you're accessing Office Web Apps from a host domain that's in the Allow List. To view the host domains in the Allow List, on the Office Web Apps Server open the Windows PowerShell prompt as an administrator and run the [Get-OfficeWebAppsHost](/powershell/module/officewebapps/get-officewebappshost?view=officewebapps-ps) cmdlet. To add a domain to the Allow List, use the [New-OfficeWebAppsHost](/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps) cmdlet.

## Problem: You receive a "Sorry, Word Web App can't open this document because the service is busy. Please try again later" error when you try to view an Office document in Office Web Apps.

  - Did you install Office Web Apps Server on a domain controller, by chance? Unfortunately, Office Web Apps Server can't run on a domain controller. Office Web Apps Server must be installed on a separate server that's part of a domain. For more information, see [Software, hardware, and configuration requirements for Office Web Apps Server](plan-office-web-apps-server.md).

  - Make sure you're running SharePoint 2013 build 15.0.4420.1017 or later. On the SharePoint 2013 server, follow these steps to verify the build number:
    
    1.  Go to **Start** \> **All Programs** \> **Microsoft SharePoint 2013 Products** \> **SharePoint 2013 Central Administration**.
    
    2.  Choose **System Settings** \> **Manage servers in this farm**.
    
    Verify the **Configuration database version** is **15.0.4420.1017** or higher. If not, go to the [Update center for Office, Office servers, and related products](/officeupdates/sharepoint-updates) for more information.

## Problem: You receive a "File Not Found. The URL of the original file is not valid or the document is not publicly accessible. Verify the URL is correct, then contact the document owner" error when you try to view an Office document in Office Web Apps by using a user generated URL.

Are you trying to open a document that has a file size that is larger than 10 megabytes from a user generated URL? Make sure the document doesn't exceed 10 megabytes.

## Problem: Previews of Office documents don't appear in SharePoint 2013. Instead, they show the "This content cannot be displayed in a frame" error.

Low memory conditions can cause problems with Office document previews. Take a look at the [Hardware requirements—web servers, application servers, and single server installations](https://technet.microsoft.com/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver) to see the memory requirements for SharePoint 2013. These are the same requirements used by Office Web Apps Server.

## Problem: You receive "A data connection is set to always use connection file and {0:ExcelWebApp} does not support external connection files. The following connection failed to refresh: Data connections" error.

This happens because Office Web Apps Server doesn't support the Office Data Connection (ODC) file that stores the data connection information. To fix this problem, follow these steps:

1.  Open the workbook in an Excel client application.

2.  Click **Data** \> **Connections**.

3.  Select the data connections listed in the message, and click **Properties**.

4.  Click the **Definition** tab.

5.  Clear the **Always use connection file check box for** check box.

6.  Re-upload the workbook to the SharePoint document library.

To enable people to interact with workbooks that contain a Data Model or Power View views in a browser window, configure Excel Services in SharePoint Server to display workbooks. This requires a SharePoint administrator to run the New-SPWOPISupressionSetting cmdlet on the server where SharePoint Server is installed. For more information, see [New-SPWOPISuppressionSetting](/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps) and [Administer Excel Services in SharePoint Server 2013](https://technet.microsoft.com/library/ee681487\(v=office.15\)).

## Disconnect SharePoint 2013 from Office Web Apps Server

If, for any reason, you want to disconnect SharePoint 2013 from Office Web Apps Server, use the following command example.

```PowerShell
    Remove-SPWOPIBinding -All:$true
```
Need help? See [Remove-SPWOPIBinding](/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps).

## See also


[New-SPWOPIBinding](/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps)  
[Set-SPWOPIZone](/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[Deploy Office Web Apps Server](deploy-office-web-apps-server.md)
