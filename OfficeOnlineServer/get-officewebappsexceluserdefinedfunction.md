---
title: Get-OfficeWebAppsExcelUserDefinedFunction
ms.assetid: 8014bdd8-bc91-42cc-bbc1-dd9fcffbd7cf
---


# Get-OfficeWebAppsExcelUserDefinedFunction

Returns a list of currently configured UDF definitions.
  
    
    


```

Get-OfficeWebAppsExcelUserDefinedFunction [-Identity <UserDefinedFunction>]

```


## Example

This example returns a list of currently configured UDF definitions from c:\\myudf.dll.
  
    
    

```

Get-OfficeWebAppsExcelUserDefinedFunction -Identity c:\\myudf.dll
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Optional  <br/> |Microsoft.Office.Web.Apps.Administration.UserDefinedFunction  <br/> |The path and filename of the UDF.  <br/> |
   

