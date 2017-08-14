---
title: Repair-OfficeWebAppsFarm
ms.prod: OFFICERESOURCEKIT
ms.assetid: 083d8e25-ce82-4884-9bbc-06375185011c
---


# Repair-OfficeWebAppsFarm

Removes all servers flagged as unhealthy from an farm.
  
    
    


```

Repair-OfficeWebAppsFarm [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```


## Detailed Description

The **Repair-OfficeWebAppsFarm** cmdlet removes all servers flagged as unhealthy from a farm. This cmdlet updates the farm topology but does not clean up services and web applications on the servers that are removed. For this reason, we recommend making every effort to run the **Remove-OfficeWebAppsMachine** cmdlet from the unhealthy servers so that they are cleanly removed from the farm. Use the **Repair-OfficeWebAppsFarm** cmdlet only if the unhealthy servers have failed and you cannot run the **Remove-OfficeWebAppsMachine** cmdlet directly on them.
  
    
    
If there are multiple unhealthy servers, you are prompted before each server is removed. If there are no unhealthy servers, this cmdlet does nothing. 
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Assumes the answer to any user prompt is Yes.  <br/> |
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## AutoGenParams



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
(Get-OfficeWebAppsFarm).Machines
```

This example displays the health status of all servers in the farm.
  
    
    
------------------EXAMPLE 2---------------------
  
    
    



```
Repair-OfficeWebAppsFarm
```

This example removes all unhealthy servers from the farm.
  
    
    

## See also


#### 


  
    
    
 [New-OfficeWebAppsFarm](new-officewebappsfarm.md)
  
    
    
 [Set-OfficeWebAppsFarm](set-officewebappsfarm.md)
  
    
    
 [Get-OfficeWebAppsFarm](get-officewebappsfarm.md)
