---
title: Get-OfficeWebAppsFarm
ms.prod: OFFICERESOURCEKIT
ms.assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
---


# Get-OfficeWebAppsFarm

Returns details about the OfficeWebAppsFarm object that the current server is a member of. 
  
    
    


```

Get-OfficeWebAppsFarm
```


## Detailed Description

The **Get-OfficeWebAppsFarm** cmdlet returns details about the OfficeWebAppsFarm object that the current server is a member of. This object represents a group of servers that work as a unit to provide web-based editing and viewing of documents. No parameters are used with the **Get-OfficeWebAppsFarm** cmdlet.
  
    
    

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
Get-OfficeWebAppsFarm
```

This example returns details about the OfficeWebAppsFarm object.
  
    
    
------------------EXAMPLE 2---------------------
  
    
    



```
(Get-OfficeWebAppsFarm).Machines
```

This example returns details about the servers that are members of the farm. These details include the health status and roles held by each server.
  
    
    

## See also


#### 


  
    
    
 [New-OfficeWebAppsFarm](new-officewebappsfarm.md)
  
    
    
 [Set-OfficeWebAppsFarm](set-officewebappsfarm.md)
  
    
    
 [Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)
