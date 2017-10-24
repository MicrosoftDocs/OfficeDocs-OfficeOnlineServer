---
title: Set-OfficeWebAppsMachine
ms.prod: OFFICERESOURCEKIT
ms.assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
---



# Set-OfficeWebAppsMachine

Changes the settings of the current server that is in an Office Online Server farm.
  
    
    


```

Set-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-Master <String>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]
```


## Detailed Description

The **Set-OfficeWebAppsMachine** cmdlet changes the settings of the current server that is in an Office Online Server farm. The settings include the roles held by the current server and the designated master server for the farm.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
|**Master** <br/> |Optional  <br/> |System.String  <br/> |Specifies the server that stores the master farm configuration files.  <br/> If you set the local server as the master, you must run **Set-OfficeWebAppsMachine -Master** on all of the remaining servers in the Office Online Server farm to point them to the new master. <br/> |
|**Roles** <br/> |Optional  <br/> |System.String[]  <br/> |Specifies the list of server roles to assign to the local server, separated by commas.  <br/> The role types are as follows:  <br/> **All** <br/> **FrontEnd** <br/> **WordBackEnd** <br/> **ExcelBackEnd** <br/> **PowerPointBackEnd** <br/> > [!IMPORTANT]> As a best practice, we recommend that all servers in an Office Online Server farm run all roles. Assigning roles is not useful until the Office Online Server farm contains approximately 50 servers.           |
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   

## AutoGenParams



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Master** <br/> |Optional  <br/> |System.String  <br/> ||
|**Roles** <br/> |Optional  <br/> |System.String[]  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
(Get-OfficeWebAppsFarm).Machines
```

This example shows the roles held by each server in the Office Online Server farm. 
  
    
    
------------------EXAMPLE 2---------------------
  
    
    



```
Set-OfficeWebAppsMachine -Roles FrontEnd
```

This example configures the current server as a Front End server.
  
    
    
------------------EXAMPLE 3---------------------
  
    
    



```
Set-OfficeWebAppsMachine -Roles All
```

This example configures the current server to host all roles. 
  
    
    

## See also


#### 


  
    
    
 [Get-OfficeWebAppsMachine](get-officewebappsmachine.md)
  
    
    
 [New-OfficeWebAppsMachine](new-officewebappsmachine.md)
  
    
    
 [Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)
