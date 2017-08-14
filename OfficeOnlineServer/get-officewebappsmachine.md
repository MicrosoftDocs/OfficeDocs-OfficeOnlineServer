---
title: Get-OfficeWebAppsMachine
ms.prod: OFFICERESOURCEKIT
ms.assetid: 02fadf5e-0382-4e73-8d07-e67d088b1a02
---


# Get-OfficeWebAppsMachine

Returns details about the current server that is in an farm.
  
    
    


```

Get-OfficeWebAppsMachine
```


## Detailed Description

The **Get-OfficeWebAppsMachine** cmdlet returns details about the current server that is in an farm. These details include the roles and health status of the current server and the name of the master server for the farm.
  
    
    

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
Get-OfficeWebAppsMachine
```

This example returns details about the current server that is in an farm.
  
    
    
------------------EXAMPLE 2---------------------
  
    
    



```
(Get-OfficeWebAppsFarm).Machines
```

This example returns details about all servers that are in a farm.
  
    
    

## See also


#### 


  
    
    
 [New-OfficeWebAppsMachine](new-officewebappsmachine.md)
  
    
    
 [Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)
  
    
    
 [Set-OfficeWebAppsMachine](set-officewebappsmachine.md)
