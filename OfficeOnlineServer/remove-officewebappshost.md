---
title: Remove-OfficeWebAppsHost
ms.prod: OFFICERESOURCEKIT
ms.assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
---


# Remove-OfficeWebAppsHost

Removes a host domain from the Allow List for an farm.
  
    
    


```

Remove-OfficeWebAppsHost -Domain <String>
```


## Detailed Description

The **Remove-OfficeWebAppsHost** cmdlet removes the specified host domain from the Allow List. The Allow List contains the host domains to which allows file operations requests.
  
    
    

> [!CAUTION]
> If there are no domains on the Allow List, allows file requests to hosts in any domain. Do not leave this list blank if your farm is accessible from the Internet. Otherwise anyone can use your farm to view and edit content. 
  
    
    


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Domain** <br/> |Required  <br/> |System.String  <br/> |Specifies the host domain to remove from the Allow List.  <br/> |
   

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
Remove-OfficeWebAppsHost -domain "contoso.com"
```

This example removes the domain contoso.com from the Allow List. 
  
    
    

## See also


#### 


  
    
    
 [New-OfficeWebAppsHost](new-officewebappshost.md)
  
    
    
 [Get-OfficeWebAppsHost](get-officewebappshost.md)
