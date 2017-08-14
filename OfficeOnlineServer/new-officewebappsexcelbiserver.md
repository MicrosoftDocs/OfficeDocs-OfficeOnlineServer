---
title: New-OfficeWebAppsExcelBIServer
ms.assetid: c92043fe-2aea-4770-b17b-c8098645db7a
---


# New-OfficeWebAppsExcelBIServer

Configures servers to work with . 
  
    
    

To use this feature, you must also configure each computer in your farm as an  [Analysis Services administrator](https://go.microsoft.com/fwlink/p/?LinkId=717498).
```

New-OfficeWebAppsExcelBIServer -ServerId <String>

```


## Example

This example configures the server named SSAS01 to work with .
  
    
    

```

New-OfficeWebAppsExcelBIServer -ServerID "SSAS01"
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ServerId_ <br/> |Required  <br/> |System.String  <br/> |The name of the server.  <br/> |
   

## See also


#### 


  
    
    
 [Configure an Analysis Services (data model) server for Excel Online](configure-excel-online-administrative-settings.md#SSAS)
