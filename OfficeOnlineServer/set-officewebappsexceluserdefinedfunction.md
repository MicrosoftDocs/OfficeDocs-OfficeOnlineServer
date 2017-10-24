---
title: Set-OfficeWebAppsExcelUserDefinedFunction
ms.assetid: 97e2c30d-425d-4d25-88ba-39121ed2d3fe
---


# Set-OfficeWebAppsExcelUserDefinedFunction

Sets properties on existing UDF definitions.
  
    
    


```

Set-OfficeWebAppsExcelUserDefinedFunction -Identity <UserDefinedFunction> [-Assembly <String>] [-AssemblyLocation <GAC | LocalFile>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enable <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Example

This example disables the UDF at c:\\myudf.dll.
  
    
    

```

Set-OfficeWebAppsExcelUserDefinedFunction -Identity c:\\myudf.dll -Enable:$false
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Office.Web.Apps.Administration.UserDefinedFunction  <br/> |The path and filename of the UDF.  <br/> |
| _Assembly_ <br/> |Optional  <br/> |System.String  <br/> |The name of the assembly.  <br/> |
| _AssemblyLocation_ <br/> |Optional  <br/> |Microsoft.Office.Web.Apps.Administration.AssemblyLocation  <br/> |The location of the assembly. Values: **LocalFile** - a local directory; **GAC** - the Global Assembly Cache. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of the assembly.  <br/> |
| _Enable_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the UDF.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   

