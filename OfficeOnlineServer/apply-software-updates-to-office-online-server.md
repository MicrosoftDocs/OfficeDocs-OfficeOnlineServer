---
title: Apply software updates to Office Online Server
description: Explains how to apply software updates or new versions to an Office Online Server farm.
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 5/12/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
---


# Apply software updates to Office Online Server

 **Summary:** Explains how to apply software updates or new versions to an Office Online Server farm.
  
    
    


 **Audience**: IT Professionals
  
    
    


On a regular basis, Microsoft makes a series of software updates and new versions available to help improve server security, performance, and reliability. This article describes how to apply software updates or new versions to individual servers in an Office Online Server farm.
  
    
    


> [!IMPORTANT]
> **Are you looking for help with Office Online on your desktop or mobile device?** You can find this information by searching for "Office Online" on [Office.com](https://go.microsoft.com/fwlink/p/?LinkId=324961). 
  
    
    


> [!CAUTION]
> Applying Office Online Server updates or new versions by using the automatic updates process isn't supported with Office Online Server. This is because updates to an Office Online Server must be applied in a specific way, as described in this article. If Office Online Server updates are applied automatically, users may be unable to view or edit documents in Office Online. If this happens, you have to rebuild your Office Online Server farm. To rebuild a farm, you must remove the Office Online Server from the farm by using  [Remove-OfficeWebAppsMachine](/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps), uninstall Office Online Server by using Add or remove programs, and then reinstall Office Online Server by following the steps that are described in  [Deploy Office Online Server](deploy-office-online-server.md). After you have reinstalled, apply the update by following the steps that are described in this article. > It is important that you review the guidelines in  [Planning updates for Office Online Server](plan-office-online-server.md#BKMK_Updates) and establish an update process for the Office Online Server farm.
  
    
    


## Before you begin
<a name="before"> </a>

Updates that are released for Office Online Server will update Office Online Server and any Office Online Server language packs that are installed. There are no separate updates for Office Online Server language packs.
  
    
    
As part of the update process, you'll have to re-create the Office Online Server farm. To prepare to re-create the Office Online Server farm, review your current Office Online Server farm properties by running the Microsoft PowerShell cmdlet **Get-OfficeWebAppsFarm** and review the parameters for [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps). The parameters that you use for **New-OfficeWebAppsFarm** should be the same parameters that you used when you first set up the Office Online Server farm.
  
    
    
Note that when you've completed updating your farm, you need to re-add any  [data model servers](/powershell/module/officewebapps/new-officewebappsexcelbiserver?view=officewebapps-ps) that you had configured for Excel Online.
  
    
    

## Apply software updates or new versions to a single server Office Online Server farm
<a name="before"> </a>

To apply software updates or new versions to a single server Office Online Server farm, remove the Office Online Server from the farm, apply the software update or new version, and re-create the Office Online Server farm. If you have only one server in your Office Online Server farm, users won't be able to use Office Online while you are updating the server. So consider updating the Office Online Server during either non-critical or non-business hours. 
  
    
    

### To apply software updates or new versions to a single server farm


1. On the Office Online Server that you want to apply the software update to, open the Microsoft PowerShell prompt as an administrator and run the following command.
    
``` 
Remove-OfficeWebAppsMachine
```

2. If this is a new release of Office Online Server that you downloaded from the  [Volume Licensing Service Center (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561), then you must uninstall the existing version before you install the new version.
    
    (If this is an update from Microsoft Update, then there's no need to uninstall Office Online Server.)
    
  
3. Install the Office Online Server update or new version on that server. If prompted, restart the server.
    
  
4. Open the Microsoft PowerShell prompt as an administrator and run the **New-OfficeWebAppsFarm** cmdlet to re-create an Office Online Server farm. The URL you specify for **-InternalURL** is the name of the server that runs Office Online Server, such as **https://oos.contoso.com**. In this case, you would use the same name that you used for the previous Office Online Server farm. Use the same additional parameters that you used when you first created the Office Online Server farm. For example, the the **-EditingEnabled** parameter enables editing in Office Online when it is used together with SharePoint Server.
    
    The code in the following example creates a new Office Online Server farm named https://oos.contoso.com.
    


  ```
  New-OfficeWebAppsFarm -InternalURL "https://oos.contoso.com" -EditingEnabled
  ```


Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in  [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).
    
  

## Apply software updates or new versions to a multiple Office Online Server farm
<a name="before"> </a>

To apply software updates or new versions to a multiple Office Online Server farm, you first remove one of the servers from the load balancer pool and from the farm, apply the software update or new version, and create an updated Office Online Server farm. Then you remove and update the remaining servers in the Office Online Server farm, and join them to the new updated farm. You load balance traffic to the new farm when you have enough servers in the new farm to support the current traffic. By using this update process, users can open and edit documents in Office Online without disruption.
  
    
    

### To apply software updates to a multiple server farm


1. Remove the Office Online Server that you want to apply the software update to from the load balancer pool.
    
  
2. On that Office Online Server, open the Microsoft PowerShell prompt as an administrator and run the following command.
    
  ```
  Remove-OfficeWebAppsMachine
  ```

3. If this is a new release of Office Online Server that you downloaded from the  [Volume Licensing Service Center (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561), then you must uninstall the existing version before you install the new version.
    
    (If this is an update from Microsoft Update, then there's no need to uninstall Office Online Server.)
    
  
4. Install the Office Online Server update or new version on that server. If prompted, restart the server.
    
  
5. Open the Microsoft PowerShell prompt as an administrator and create an updated Office Online Server farm by using the cmdlet **New-OfficeWebAppsFarm**. The URL you specify for **-InternalURL** contains the DNS A record of the Office Online Server farm, such as **https://oos.contoso.com**. In this case, you use the same name as the existing Office Online Server farm. Use the same additional parameters that you used when you first created the Office Online Server farm. For example, the **-EditingEnabled** parameter enables editing in Office Online when it is used together with SharePoint Server.
    
    The code in the following example creates a new Office Online Server farm named https://oos.contoso.com.
    


  ```
  New-OfficeWebAppsFarm -InternalURL "https://oos.contoso.com"  -EditingEnabled
  ```


Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in  [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps).
    
  
6. Depending on how many servers that you have in the Office Online Server farm, load balance traffic to the new farm. You may delay this step until you have more updated servers to join the farm. 
    
  
7. For each remaining server in the farm, follow these steps.
    
1. Remove the next Office Online Server from the load balancer pool.
    
  
2. Install the Office Online Server update on that server. If prompted, restart the server.
    
  
3. Open the Microsoft PowerShell prompt as an administrator and run the following command. The **-MachineToJoin** parameter adds the current server to an existing Office Online Server farm. In this case, you want to add the server to the updated Office Online Server farm. So use the computer name of one of the servers in the updated Office Online Server farm.
    
  ```
  New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
  ```


## See also
<a name="before"> </a>


#### 


  
    
    
 [Remove-OfficeWebAppsMachine](/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps)
  
    
    
 [New-OfficeWebAppsMachine](/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)
  
    
    
 [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)
  
    
    
 [Get-OfficeWebAppsFarm](/powershell/module/officewebapps/get-officewebappsfarm?view=officewebapps-ps)
#### 


  
    
    
 [Office Online Server release schedule](office-online-server-release-schedule.md)