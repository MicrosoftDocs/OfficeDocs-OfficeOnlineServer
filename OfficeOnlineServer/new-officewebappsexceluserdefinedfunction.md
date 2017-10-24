---
title: New-OfficeWebAppsExcelUserDefinedFunction
ms.assetid: 2cba89ed-f447-42a4-9022-dd3a6d1dcb93
---


# New-OfficeWebAppsExcelUserDefinedFunction

Creates a definition for a UDF binary.
  
    
    


```

New-OfficeWebAppsExcelUserDefinedFunction -Assembly <String> [-AssemblyLocation <GAC | LocalFile>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enable <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Example

------------------EXAMPLE 1---------------------
  
    
    

```

New-OfficeWebAppsExcelUserDefinedFunction -Assembly c:\\myudf.dll -AssemblyLocation LocalFile -Enable:$true -Description "My Server UDFs"
```

------------------EXAMPLE 2---------------------
  
    
    



```
New-OfficeWebAppsExcelUserDefinedFunction -Assembly "CompanyName.Hierarchichal.MyUdfNamespace.MyUdfClassName.dll, Version=1.1.0.0, Culture=en, PublicKeyToken=e8123117d7ba9ae38" -AssemblyLocation GAC -Enable:$true -Description "My GAC Server UDFs"
```


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Assembly_ <br/> |Required  <br/> |System.String  <br/> |The name of the assembly.  <br/> |
| _AssemblyLocation_ <br/> |Optional  <br/> |Microsoft.Office.Web.Apps.Administration.AssemblyLocation  <br/> |The location of the assembly. Values: **LocalFile** - a local directory; **GAC** - the Global Assembly Cache. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Description of the UDF.  <br/> |
| _Enable_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the UDF.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   

