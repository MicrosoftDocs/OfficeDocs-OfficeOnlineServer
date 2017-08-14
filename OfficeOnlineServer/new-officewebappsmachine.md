---
title: New-OfficeWebAppsMachine
ms.prod: OFFICERESOURCEKIT
ms.assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
---



# New-OfficeWebAppsMachine

Adds the current server to an existing farm.
  
    
    


```

New-OfficeWebAppsMachine [-MachineToJoin] <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]
```


## Detailed Description

The **New-OfficeWebAppsMachine** cmdlet adds the current server to an existing farm and optionally sets one or more roles on the new server.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**MachineToJoin** <br/> |Required  <br/> |System.String  <br/> |Specifies the name of any server that is already a member of the farm.  <br/> |
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Assumes the answer to any user prompt is Yes.  <br/> |
|**Roles** <br/> |Optional  <br/> |System.String[]  <br/> |Specifies one or more server roles, separated by commas, to assign to the new server. If no roles are specified, then the server is assigned all roles.  <br/> The role types are as follows:  <br/> **FrontEnd** <br/> **WordBackEnd** <br/> **ExcelBackEnd** <br/> **PowerPointBackEnd** <br/> > [!IMPORTANT]> As a best practice, we recommend that all servers in an farm run all roles. Assigning roles is not useful until the farm contains approximately 50 servers.           |
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## AutoGenParams



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**MachineToJoin** <br/> |Required  <br/> |System.String  <br/> ||
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Roles** <br/> |Optional  <br/> |System.String[]  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## Example

------------------EXAMPLE 1---------------------
  
    
    

```
New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com
```

This example adds the current server to the farm that is running on the server named server1.contoso.com.
  
    
    

## See also


#### 


  
    
    
 [Get-OfficeWebAppsMachine](get-officewebappsmachine.md)
  
    
    
 [Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)
  
    
    
 [Set-OfficeWebAppsMachine](set-officewebappsmachine.md)
