---
title: Remove-OfficeWebAppsExcelBIServer
ms.assetid: 724eab67-9622-485a-85ee-ade766b99da3
---


# Remove-OfficeWebAppsExcelBIServer

Removes an instance of from the Allow List of BI servers to be used with .
  
    
    


```

Remove-OfficeWebAppsExcelBIServer -ServerId <String>

```


## Example

This example removes the server named SSAS01 from the Allow List.
  
    
    

```

Remove-OfficeWebAppsExcelBIServer -ServerID "SSAS01"
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ServerId_ <br/> |Required  <br/> |System.String  <br/> |The name of the server.  <br/> |
   

