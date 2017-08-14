---
title: Get-OfficeWebAppsHost
ms.prod: OFFICERESOURCEKIT
ms.assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
---


# Get-OfficeWebAppsHost

Returns the list of host domains that are on the Allow List for an farm.
  
    
    


```

Get-OfficeWebAppsHost
```


## Detailed Description

The **Get-OfficeWebAppsHost** cmdlet returns the list of host domains to which allows file operations requests, such as file retrieval, metadata retrieval, and file changes. This list, known as the Allow List, is a security feature that prevents unwanted hosts from connecting to an farm and using it for file operations without your knowledge.
  
    
    
The wildcard * is assumed for any domain that appears on the Allow List so that requests to all subdomains are also allowed. For example, if the domain contoso.com is on the Allow List, then also allows requests to the domains corp.contoso.com and dev.contoso.com. Requests to other domains (such as fabrikam.com) are not allowed.
  
    
    

> [!CAUTION]
> If there are no domains on the Allow List, allows file requests to hosts in any domain. Do not leave this list blank if your farm is accessible from the Internet. Otherwise anyone can use your farm to view and edit content. 
  
    
    


## Example

------------------EXAMPLE 1---------------------
  
    
    

```
Get-OfficeWebAppsHost
```

This example returns the host domains that are on the Allow List.
  
    
    

## See also


#### 


  
    
    
 [New-OfficeWebAppsHost](new-officewebappshost.md)
  
    
    
 [Remove-OfficeWebAppsHost](remove-officewebappshost.md)
