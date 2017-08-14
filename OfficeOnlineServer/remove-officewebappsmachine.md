---
title: Remove-OfficeWebAppsMachine
ms.prod: OFFICERESOURCEKIT
ms.assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
---


# Remove-OfficeWebAppsMachine

Removes the current server from the farm.
  
    
    


```

Remove-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```


## Detailed Description

The **Remove-OfficeWebAppsMachine** cmdlet removes the current server from the farm. As part of this process, the cmdlet removes the web applications and shuts down the services that are related to . If you cannot run the **Remove-OfficeWebAppsMachine** cmdlet from the server that you want to remove, use the **Repair-OfficeWebAppsFarm** cmdlet from any other server in the farm.
  
    
    

> [!NOTE]
> If the local server is designated as the master server in the farm, you cannot remove it from the farm until you assign a different server as master by using the **Set-OfficeWebAppsMachine** cmdlet, or until you remove all other servers from the farm.
  
    
    


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## AutoGenParams



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
Remove-OfficeWebAppsMachine
```

This example removes the current server from the farm.
  
    
    

## See also


#### 


  
    
    
 [Get-OfficeWebAppsMachine](get-officewebappsmachine.md)
  
    
    
 [New-OfficeWebAppsMachine](new-officewebappsmachine.md)
  
    
    
 [Set-OfficeWebAppsMachine](set-officewebappsmachine.md)
  
    
    
 [Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)
