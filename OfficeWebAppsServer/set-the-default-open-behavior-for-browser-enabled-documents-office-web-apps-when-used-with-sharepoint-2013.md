---
title: Set the default open behavior for browser-enabled documents (Office Web Apps when used with SharePoint 2013)
TOCTitle: Set the default open behavior for browser enabled documents
ms:assetid: e27e0bc8-5fb5-4bb1-8157-d7c90654175e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ee837425(v=office.15)
ms:contentKeyID: 50117655
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Set the default open behavior for browser-enabled documents (Office Web Apps when used with SharePoint 2013)

 

_**Applies to:** SharePoint Server 2013, SharePoint Foundation 2013, Office Web Apps_


**Summary:** Explains how to configure the default open behavior for Office documents in SharePoint site collections and document libraries.

**Audience:** IT Professionals

To open a document in a SharePoint 2013 document library, you just click its title. What happens next (whether the file opens in a client application or in the browser) depends on several factors, such as what type of file it is, how you’ve set up your Office Web Apps Server farm, and how you’ve set the OpenInClient feature settings of the library or site collection. The following steps show how to configure the default open behavior for Office documents where you have SharePoint 2013 configured to use Office Web Apps Server.

## Set how documents are opened from SharePoint 2013 libraries

By default, after you configure SharePoint 2013 to use Office Web Apps Server, clicking a Word, PowerPoint, Excel, or OneNote file opens it in the browser. PDF documents open in the Word Web App. There are two ways to change the default behavior so that files open in the client applications (or the default PDF reader) instead:

  - **For the SharePoint 2013 farm**   You can adjust the default open behavior on a per-file-type basis for the SharePoint 2013 farm by using the [New-SPWOPIBinding](new-spwopibinding.md) and [Set-SPWOPIBinding](set-spwopibinding.md) Windows PowerShell cmdlets. These cmdlets can also be used to [adjust the behavior of PDF documents](http://go.microsoft.com/fwlink/p/?linkid=330246).

  - **In site collections or document libraries**   Site collection administrators and users can use the OpenInClient feature in SharePoint 2013 to specify whether Office files will be opened in the client application or in the browser. Users can change this setting in the document library properties, and site collection administrators can change it in Site Collection Administration or by using the [Enable-SPFeature](https://technet.microsoft.com/en-us/library/ff607803\(v=office.15\)) cmdlet to enable the OpenInClient feature. See the next section for several different methods to enable the OpenInClient feature.

In general, the OpenInClient feature overrides any WOPI bindings you’ve set between SharePoint 2013 and Office Web Apps Server. In other words, if the OpenInClient feature of a SharePoint 2013 library or site collection is enabled, documents will open in the client application even if you've configured the SharePoint 2013 server to use Office Web Apps Server.


> [!NOTE]
> Configuring the default open behavior for browser-enabled documents won’t affect whether users can use the <STRONG>Check Out</STRONG> and <STRONG>Send To</STRONG> features in SharePoint 2013 to download documents. For information about how to configure check out, download, and view permissions in SharePoint 2013, see <A href="https://technet.microsoft.com/en-us/library/cc262939(v=office.15)">Permissions planning for sites and content in SharePoint 2013</A>.



## Set the OpenInClient feature for a document library or site collection

Use one of the following procedures to set the OpenInClient feature in SharePoint 2013.


> [!NOTE]
> Some of these procedures use the SharePoint 2013 Management Shell to run SharePoint cmdlets. If you choose to use the Windows PowerShell console, you must add the Microsoft.SharePoint.PowerShell snap-in by using the <STRONG>Add-PSSnapin</STRONG> cmdlet. For more information about how to use Windows PowerShell with SharePoint 2013, see <A href="use-windows-powershell-to-administer-sharepoint-2013.md">Use Windows PowerShell to administer SharePoint 2013</A>.




> [!NOTE]
> You can complete tasks in Office 2013 suites by using a mouse, keyboard shortcuts, or touch. For information about how to use keyboard shortcuts and touch with Office products and services, see <A href="http://go.microsoft.com/fwlink/p/?linkid=249150">Keyboard Shortcuts</A> and <A href="http://go.microsoft.com/fwlink/p/?linkid=253163">Office Touch Guide</A>.



 **Set the OpenInClient feature for site collections**

1.  In the SharePoint site collection, choose the **Settings** icon \> **Site Settings**.

2.  On the **Site Settings** page, under **Site Collection Administration**, choose **Site Collection Features**.

3.  On the **Features** page, for the **Open Documents in Client Applications by Default** feature, choose **Activate** to enable the OpenInClient feature (documents will open in the client application), or **Deactivate** to disable the OpenInClient feature (documents will open in the browser).

 **Set the default open behavior for site collections by using Windows PowerShell**

1.  First, make sure you have the following memberships:
    
      - **securityadmin** fixed server role on the SQL Server instance.
    
      - **db\_owner** fixed database role on all databases that are to be updated.
    
      - Administrators group on the server on which you are running Windows PowerShell cmdlets.
    
    Also, take a look at [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) and add any other required memberships.
    
    An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.
    

    > [!NOTE]
    > If you don’t have permissions, contact your Setup administrator or SQL Server administrator to request them. For additional information about Windows PowerShell permissions, see <A href="use-windows-powershell-to-administer-sharepoint-2013.md">Permissions</A> and <A href="https://technet.microsoft.com/en-us/library/ff607596(v=office.15)">Add-SPShellAdmin</A>.



2.  Open an elevated SharePoint 2013 Management Shell:
    
    **In Windows Server 2008**
    
    1.  On the **Start** menu, select **All Programs**.
    
    2.  Select **Microsoft SharePoint 2013 Products**.
    
    3.  Choose **SharePoint 2013 Management Shell** and display the shortcut menu (right-click).
    
    4.  From the shortcut menu, choose **Run as administrator**.
    
    **In Windows Server 2012**
    
    1.  Swipe in from the edge of the screen to show the charms and choose **Search** to see all the applications that are installed on the computer.
    
    2.  Choose (right-click) **SharePoint 2013 Management Shell** to display the app bar.
    
    3.  In the app bar, select **Run as administrator**.

3.  At the Windows PowerShell command prompt, type one of the following commands:
    
      - To enable the OpenInClient feature for a specific site collection (to open documents in the client application), type this command:
        
           ```PowerShell
           Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
           ```
        
        where \<SiteCollURL\> is the URL of the site collection.
    
      - To enable the OpenInClient feature for all site collections (to open documents in the client application), type this command:
        
           ```PowerShell
            Get-SPSite -limit ALL |foreach{ Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
           ```
    
      - To disable the OpenInClient feature for a specific site collection (to open documents in the browser), type this command:
        
           ```PowerShell
            Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
           ```
        
        where \<SiteCollURL\> is the URL of the site collection.
    
      - To disable the OpenInClient feature for all site collections (to open documents in the browser), type this command:
        
           ```PowerShell
            Get-SPSite -limit ALL |foreach{ Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
           ```

 **Set the default open behavior for a document library by using the document library settings page**

1.  On the document library page, choose the **Library** tab.

2.  In the **Settings** group, choose **Library Settings**.

3.  On the **Document Library Settings** page, choose **Advanced settings**.

4.  On the **Advanced Settings** page, in **Opening Document in the Browser**, select one of the following options:
    
      - **Open in the client application**   When a user chooses a document in this library, the document will open in the corresponding client application if it's available.
    
      - **Open in the browser**   When a user chooses a document in this library, the document will open in the web browser in the web app for that document type. When the document is opened in the web app, the user can then decide to open the document in the client application.
    
      - **Use the server default**   When a user chooses a document in this library, the document will open by using the default open behavior specified for the server running SharePoint 2013.

 **Set the default open behavior for IRM-protected document libraries by using Windows PowerShell**

1.  First, make sure you have the following memberships:
    
      - **securityadmin** fixed server role on the SQL Server instance.
    
      - **db\_owner** fixed database role on all databases that are to be updated.
    
      - Administrators group on the server on which you are running Windows PowerShell cmdlets.
    
    Also, take a look at [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050) and add any other required memberships.
    
    An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.
    

    > [!NOTE]
    > If you don’t have permissions, contact your Setup administrator or SQL Server administrator to request them. For additional information about Windows PowerShell permissions, see <A href="use-windows-powershell-to-administer-sharepoint-2013.md">Permissions</A> and <A href="https://technet.microsoft.com/en-us/library/ff607596(v=office.15)">Add-SPShellAdmin</A>.



2.  Open an elevated SharePoint 2013 Management Shell:
    
    **In Windows Server 2008**
    
    1.  On the **Start** menu, select **All Programs**.
    
    2.  Select **Microsoft SharePoint 2013 Products**.
    
    3.  Choose **SharePoint 2013 Management Shell** and display the shortcut menu (right-click).
    
    4.  From the shortcut menu, choose **Run as administrator**.
    
    **In Windows Server 2012**
    
    1.  Swipe in from the edge of the screen to show the charms and choose **Search** to see all the applications that are installed on the computer.
    
    2.  Choose (right-click) **SharePoint 2013 Management Shell** to display the app bar.
    
    3.  In the app bar, select **Run as administrator**.

3.  At the Windows PowerShell command prompt, type this command:
    
       ```PowerShell
        Get-SPWeb -site <SiteCollURL> | % {$_.Lists} | where {$_.IrmEnabled -eq $true} | % {$_.DefaultItemOpen =[Microsoft.Sharepoint.DefaultItemOpen]::<DefaultItemOpenSetting>; $_.Update()}
       ```
    
    where:
    
      - \<SiteCollURL\> is the URL of the site collection where the document libraries reside.
    
      - \<DefaultItemOpenSetting\> is a **DefaultItemOpen** enumeration value that specifies the default open behavior. Use **PreferClient** to open documents in their associated client applications (if available). Use **Browser** to open documents in the browser.

## See also


[Get-SPWOPIBinding](get-spwopibinding.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Use Windows PowerShell to administer SharePoint 2013](use-windows-powershell-to-administer-sharepoint-2013.md)  
[Office Web Apps Server](office-web-apps-server.md)  


[Get-SPWeb](https://technet.microsoft.com/en-us/library/ff607807\(v=office.15\))  
[Get-SPSite](https://technet.microsoft.com/en-us/library/ff607950\(v=office.15\))  
[Get-SPFeature](https://technet.microsoft.com/en-us/library/ff607945\(v=office.15\))

