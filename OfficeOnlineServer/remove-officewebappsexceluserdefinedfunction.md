---
title: Remove-OfficeWebAppsExcelUserDefinedFunction
ms.assetid: 73ba7a36-981a-4991-9121-57545505def7
---


# Remove-OfficeWebAppsExcelUserDefinedFunction

Removes an existing UDF definition.
  
    
    


```

Remove-OfficeWebAppsExcelUserDefinedFunction -Identity <UserDefinedFunction> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```


## Example

This example removes the UDF c:\\myudf.dll.
  
    
    

```

Remove-OfficeWebAppsExcelUserDefinedFunction -Identity c:\\myudf.dll
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Office.Web.Apps.Administration.UserDefinedFunction  <br/> |The path and filename of the UDF.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   

