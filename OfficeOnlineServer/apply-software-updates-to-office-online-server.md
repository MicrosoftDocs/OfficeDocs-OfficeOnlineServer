---
title: Apply software updates to Office Online Server
ms.prod: OFFICERESOURCEKIT
ms.assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
---


# Apply software updates to Office Online Server
 **Summary:** Explains how to apply software updates or new versions to an farm.
 **Audience**: IT Professionals
  
    
    

On a regular basis, Microsoft makes a series of software updates and new versions available to help improve server security, performance, and reliability. This article describes how to apply software updates or new versions to individual servers in an farm. 
> [!IMPORTANT]
> **Are you looking for help with on your desktop or mobile device?** You can find this information by searching for "" on [Office.com](https://go.microsoft.com/fwlink/p/?LinkId=324961). 
  
    
    


> [!CAUTION]
> Applying updates or new versions by using the automatic updates process isn't supported with . This is because updates to an must be applied in a specific way, as described in this article. If updates are applied automatically, users may be unable to view or edit documents in . If this happens, you have to rebuild your farm. To rebuild a farm, you must remove the from the farm by using  [Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md), uninstall by using Add or remove programs, and then reinstall by following the steps that are described in  [Deploy Office Online Server](deploy-office-online-server.md). After you have reinstalled, apply the update by following the steps that are described in this article. > It is important that you review the guidelines in  [Planning updates for Office Online Server](plan-office-online-server.md#BKMK_Updates) and establish an update process for the farm.
  
    
    


## Before you begin
<a name="before"> </a>

Updates that are released for will update and any language packs that are installed. There are no separate updates for language packs.
  
    
    
As part of the update process, you'll have to re-create the farm. To prepare to re-create the farm, review your current farm properties by running the cmdlet **Get-OfficeWebAppsFarm** and review the parameters for [New-OfficeWebAppsFarm](new-officewebappsfarm.md). The parameters that you use for **New-OfficeWebAppsFarm** should be the same parameters that you used when you first set up the farm.
  
    
    
Note that when you've completed updating your farm, you need to re-add any  [data model servers](new-officewebappsexcelbiserver.md) that you had configured for .
  
    
    

## Apply software updates or new versions to a single server Office Online Server farm
<a name="before"> </a>

To apply software updates or new versions to a single server farm, remove the from the farm, apply the software update or new version, and re-create the farm. If you have only one server in your farm, users won't be able to use while you are updating the server. So consider updating the during either non-critical or non-business hours. 
  
    
    

### To apply software updates or new versions to a single server farm


1. On the that you want to apply the software update to, open the prompt as an administrator and run the following command.
    
  ```
  
Remove-OfficeWebAppsMachine
  ```

2. If this is a new release of that you downloaded from the  [Volume Licensing Service Center (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561), then you must uninstall the existing version before you install the new version.
    
    (If this is an update from Microsoft Update, then there's no need to uninstall .)
    
  
3. Install the update or new version on that server. If prompted, restart the server.
    
  
4. Open the prompt as an administrator and run the **New-OfficeWebAppsFarm** cmdlet to re-create an farm. The URL you specify for **-InternalURL** is the name of the server that runs , such as **https://Contoso-OOS**. In this case, you would use the same name that you used for the previous farm. Use the same additional parameters that you used when you first created the farm. For example, the the **-EditingEnabled** parameter enables editing in when it is used together with .
    
    The code in the following example creates a new farm named https://Contoso-OOS.
    


  ```
  New-OfficeWebAppsFarm -InternalURL "https://Contoso-OOS" -EditingEnabled
  ```


    Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in  [New-OfficeWebAppsFarm](new-officewebappsfarm.md).
    
  

## Apply software updates or new versions to a multiple Office Online Server farm
<a name="before"> </a>

To apply software updates or new versions to a multiple farm, you first remove one of the servers from the load balancer pool and from the farm, apply the software update or new version, and create an updated farm. Then you remove and update the remaining servers in the farm, and join them to the new updated farm. You load balance traffic to the new farm when you have enough servers in the new farm to support the current traffic. By using this update process, users can open and edit documents in without disruption.
  
    
    

### To apply software updates to a multiple server farm


1. Remove the that you want to apply the software update to from the load balancer pool.
    
  
2. On that , open the prompt as an administrator and run the following command.
    
  ```
  Remove-OfficeWebAppsMachine
  ```

3. If this is a new release of that you downloaded from the  [Volume Licensing Service Center (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561), then you must uninstall the existing version before you install the new version.
    
    (If this is an update from Microsoft Update, then there's no need to uninstall .)
    
  
4. Install the update or new version on that server. If prompted, restart the server.
    
  
5. Open the prompt as an administrator and create an updated farm by using the cmdlet **New-OfficeWebAppsFarm**. The URL you specify for **-InternalURL** is the name of the server that runs , such as **https://Contoso-OOS**. In this case, you use the same name as the existing farm. Use the same additional parameters that you used when you first created the farm. For example, the **-EditingEnabled** parameter enables editing in when it is used together with .
    
    The code in the following example creates a new farm named https://Contoso-OOS.
    


  ```
  New-OfficeWebAppsFarm -InternalURL "https://Contoso-OOS"  -EditingEnabled
  ```


    Additional parameters that configure translation services, proxy servers, clipart support, and Online Viewers are described in  [New-OfficeWebAppsFarm](new-officewebappsfarm.md).
    
  
6. Depending on how many servers that you have in the farm, load balance traffic to the new farm. You may delay this step until you have more updated servers to join the farm. 
    
  
7. For each remaining server in the farm, follow these steps.
    
1. Remove the next from the load balancer pool.
    
  
2. Install the update on that server. If prompted, restart the server.
    
  
3. Open the prompt as an administrator and run the following command. The **-MachineToJoin** parameter adds the current server to an existing farm. In this case, you want to add the server to the updated farm. So use the computer name of one of the servers in the updated farm.
    
  ```
  New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
  ```


## See also
<a name="before"> </a>


#### 


  
    
    
 [Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)
  
    
    
 [New-OfficeWebAppsMachine](new-officewebappsmachine.md)
  
    
    
 [New-OfficeWebAppsFarm](new-officewebappsfarm.md)
  
    
    
 [Get-OfficeWebAppsFarm](get-officewebappsfarm.md)
#### 


  
    
    
 [Office Online Server release schedule](office-online-server-release-schedule.md)
