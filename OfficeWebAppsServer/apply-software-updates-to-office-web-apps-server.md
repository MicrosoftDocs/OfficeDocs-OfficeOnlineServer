---
title: Apply software updates to Office Web Apps Server
TOCTitle: Apply software updates to Office Web Apps Server
ms:assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ966220(v=office.15)
ms:contentKeyID: 51438566
ms.date: 04/07/2015
mtps_version: v=office.15
---

# Apply software updates to Office Web Apps Server

 

_**Applies to:** Office Web Apps Server_

**Summary:** Explains how to apply software updates to an Office Web Apps Server farm.

**Audience:** IT Professionals

After a new release of Office Web Apps Server, Microsoft makes a series of software updates available to help improve server security, performance, and reliability. This article describes how to apply software updates to individual servers in an Office Web Apps Server farm.


> [!IMPORTANT]
> This article is part of the <A href="content-roadmap-for-office-web-apps-server.md">Content roadmap for Office Web Apps Server</A>. Use the roadmap as a starting point for articles, downloads, and videos that help you deploy and manage Office Web Apps Server.<BR><STRONG>Are you looking for help with Office Web Apps on your desktop or mobile device?</STRONG> You can find this information by searching for "Office Web Apps" on <A href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</A>.




> [!WARNING]
> Applying Office Web Apps Server updates by using the automatic updates process isn’t supported with Office Web Apps Server. This is because updates to an Office Web Apps Server must be applied in a specific way, as described in this article. If Office Web Apps Server updates are applied automatically, users may be unable to view or edit documents in Office Web Apps. If this happens, you have to rebuild your Office Web Apps Server farm. To rebuild a farm, you must remove the Office Web Apps Server from the farm by using <A href="remove-officewebappsmachine.md">Remove-OfficeWebAppsMachine</A>, uninstall Office Web Apps Server by using Add or remove programs, and then reinstall Office Web Apps Server by following the steps that are described in <A href="deploy-office-web-apps-server.md">Deploy Office Web Apps Server</A>. After you have reinstalled, apply the update by following the steps that are described in this article.<BR>It is important that you review the guidelines in <A href="plan-office-web-apps-server.md">Planning updates for Office Web Apps Server</A> and establish an update process for the Office Web Apps Server farm.



## Before you begin

You can find the most recent list of updates available for Office Web Apps Server on the [Microsoft Office Updates blog](http://go.microsoft.com/fwlink/p/?linkid=280269) and on the [TechNet Update center for Office, Office servers, and related products](http://go.microsoft.com/fwlink/p/?linkid=280271).

Updates that are released for Office Web Apps Server will update Office Web Apps Server and any Office Web Apps Server language packs that are installed. There are no separate updates for Office Web Apps Server language packs.

As part of the update process, you'll have to re-create the Office Web Apps Server farm. To prepare to re-create the Office Web Apps Server farm, review your current Office Web Apps Server farm properties by running the Windows PowerShell cmdlet **Get-OfficeWebAppFarm** and review the parameters for [New-OfficeWebAppsFarm](new-officewebappsfarm.md). The parameters that you use for **New-OfficeWebAppsFarm** should be the same parameters that you used when you first set up the Office Web Apps Server farm.


> [!NOTE]
> You can complete tasks in this article by using a mouse, keyboard shortcuts, or touch. For more information, see the following resources: 
> <UL>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=249150">Keyboard shortcuts</A></P>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=249151">Touch</A></P></LI></UL>



## Apply software updates to a single server Office Web Apps Server farm

To apply software updates to a single server Office Web Apps Server farm, remove the Office Web Apps Server from the farm, apply the software update, and re-create the Office Web Apps Server farm. If you have only one server in your Office Web Apps Server farm, users won’t be able to use Office Web Apps while you are updating the server. So consider updating the Office Web Apps Server during either non-critical or non-business hours.

**To apply software updates to a single server farm**

1.  If the update hasn’t been downloaded to the Office Web Apps Server already, download the Office Web Apps Server update that you want to apply from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=280274).

2.  On the Office Web Apps Server that you want to apply the software update to, open the Windows PowerShell prompt as an administrator and run the following command.

    ```PowerShell
        Remove-OfficeWebAppsMachine
	```
3.  Install the Office Web Apps Server update on that server. If prompted, restart the server.

4.  Open the Windows PowerShell prompt as an administrator and run the **New-OfficeWebAppsFarm** cmdlet to re-create an Office Web Apps Server farm. The URL you specify for **–InternalURL** is the name of the server that runs Office Web Apps Server, such as **http://Contoso-WAC**. In this case, you would use the same name that you used for the previous Office Web Apps Server farm. Use the same additional parameters that you used when you first created the Office Web Apps Server farm. For example, the **–AllowHttp** parameter configures the farm to use HTTP, and the **–EditingEnabled** parameter enables editing in Office Web Apps when it is used together with SharePoint 2013. The **–EditingEnabled** parameter is not used by Lync Server 2013 or Exchange Server 2013 because those hosts don't support editing.
    
    The code in the following example creates a new Office Web Apps Server farm named http://Contoso-WAC.

    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in [New-OfficeWebAppsFarm](new-officewebappsfarm.md).

## Apply software updates to a multiple Office Web Apps Server farm

To apply software updates to a multiple Office Web Apps Server farm, you first remove one of the servers from the load balancer pool and from the farm, apply the software update, and create an updated Office Web Apps Server farm. Then you remove and update the remaining servers in the Office Web Apps Server farm, and join them to the new updated farm. You load balance traffic to the new farm when you have enough servers in the new farm to support the current traffic. By using this update process, users can open and edit documents in Office Web Apps without disruption.

**To apply software updates to a multiple server farm**

1.  Download Office Web Apps Server update that you want to apply from the [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=280274) to a network location available to the Office Web Apps Server farm.

2.  Remove the Office Web Apps Server that you want to apply the software update to from the load balancer pool.

3.  On that Office Web Apps Server, open the Windows PowerShell prompt as an administrator and run the following command.

    ```PowerShell
        Remove-OfficeWebAppsMachine
	```
4.  Install the Office Web Apps Server update on that server. If prompted, restart the server.

5.  Open the Windows PowerShell prompt as an administrator and create an updated Office Web Apps Server farm by using the cmdlet **New-OfficeWebAppsFarm**. The URL you specify for **–InternalURL** is the name of the server that runs Office Web Apps Server, such as **http://Contoso-WAC**. In this case, you use the same name as the existing Office Web Apps Server farm. Use the same additional parameters that you used when you first created the Office Web Apps Server farm. For example, the **–AllowHttp** parameter configures the farm to use HTTP, and the **–EditingEnabled** parameter enables editing in Office Web Apps when it is used together with SharePoint 2013. The **–EditingEnabled** parameter is not used by Lync Server 2013 or Exchange Server 2013 because those hosts don't support editing.
    
    The code in the following example creates a new Office Web Apps Server farm named http://Contoso-WAC.

    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in [New-OfficeWebAppsFarm](new-officewebappsfarm.md).

6.  Depending on how many servers that you have in the Office Web Apps Server farm, load balance traffic to the new farm. You may delay this step until you have more updated servers to join the farm.

7.  For each remaining server in the farm, follow these steps.
    
    1.  Remove the next Office Web Apps Server from the load balancer pool.
    
    2.  Install the Office Web Apps Server update on that server. If prompted, restart the server.
    
    3.  Open the Windows PowerShell prompt as an administrator and run the following command. The **–MachineToJoin** parameter adds the current server to an existing Office Web Apps Server farm. In this case, you want to add the server to the updated Office Web Apps Server farm. So use the computer name of the one of the servers in the updated Office Web Apps Server farm.
    
        ```PowerShell
            New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
		```
## See also


[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
  

[](content-roadmap-for-office-web-apps-server.md)

