---
title: Configure Excel Online administrative settings
ms.prod: SHAREPOINT
ms.assetid: 9cb81758-9d0b-4970-9ca0-a75eedf6093b
---


# Configure Excel Online administrative settings
 **Summary:** Configure administrative settings for workbooks rendered in .
There are several settings that you can use to customize . These settings help you adjust the resource usage of your farm and enforce some of your organization's governance policies.
  
    
    

In , most of these settings are available as parameters for the New-OfficeWebAppsFarm and Set-OfficeWebAppsFarm cmdlets, and there is an additional cmdlet (OfficeWebAppsExcelBIServer) that configures access to servers. (Note that this is a subset of the settings that were available in Excel Services in SharePoint Server 2013.)
Here's what you can do:
  
    
    


-  [Prevent a workbook from loading in Excel Online if data refresh fails](configure-excel-online-administrative-settings.md#ExcelAbortOnRefreshOnOpenFail)
    
  
-  [Set the Excel Online cache time for volatile functions](configure-excel-online-administrative-settings.md#ExcelAutomaticVolativeFunctionCacheLifetime)
    
  
-  [Set the number of Excel Online data requests per session](configure-excel-online-administrative-settings.md#ExcelConcurrentDataRequestsPerSessionMax)
    
  
-  [Set the Excel Online workbook calculation mode](configure-excel-online-administrative-settings.md#ExcelDefaultWorkbookCalcMode)
    
  
-  [Set the maximum Excel Online image size](configure-excel-online-administrative-settings.md#ExcelChartAndImagesSizeMax)
    
  
-  [Configure an Analysis Services (data model) server for Excel Online](configure-excel-online-administrative-settings.md#SSAS)
    
  
-  [Configure Analysis Services EffectiveUserName in Excel Online](configure-excel-online-administrative-settings.md#EffectiveUserName)
    
  

## Prevent a workbook from loading in Excel Online if data refresh fails
<a name="ExcelAbortOnRefreshOnOpenFail"> </a>

By default, doesn't load files if an automatic data refresh operation fails when someone opens the file. This helps prevent users from seeing out-of-date information or possibly information that they should not have access to.
  
    
    
The load fails only in the following conditions:
  
    
    

- The user has read-only permissions for the file in .
    
  
- There are data connections in the workbook file that are automatically refreshed when someone opens the workbook.
    
  
 **Syntax:** Set-OfficeWebAppsFarm -ExcelAbortOnRefreshOnOpenFail
  
    
    
 **Default:** True
  
    
    
 **Example:**
  
    
    



```

Set-OfficeWebAppsFarm -ExcelAbortOnRefreshOnOpenFail:$false
```


## Set the Excel Online cache time for volatile functions
<a name="ExcelAutomaticVolativeFunctionCacheLifetime"> </a>

You can specify the maximum time, in seconds, that a computed value for a volatile function is cached for automatic recalculations. Valid values are:
  
    
    

- -1: Calculates once when the workbook loads.
    
  
- 0: Always calculates.
    
  
- 1 to 2073600: Caches 1 second to 24 days.
    
  
The value must be an integer from -1 to 2073600.
  
    
    
 **Syntax:** Set-OfficeWebAppsFarm -ExcelAutomaticVolativeFunctionCacheLifetime
  
    
    
 **Default:** 300
  
    
    
 **Example:**
  
    
    



```

Set-OfficeWebAppsFarm -ExcelAutomaticVolativeFunctionCacheLifetime:500
```


## Set the number of Excel Online data requests per session
<a name="ExcelConcurrentDataRequestsPerSessionMax"> </a>

You can specify the maximum number of concurrent external data requests allowed in each session. If a session must issue more than this number of requests, additional requests are queued. The scope of this setting is the logical server. The value must be a positive integer.
  
    
    
 **Syntax:** Set-OfficeWebAppsFarm -ExcelConcurrentDataRequestsPerSessionMax
  
    
    
 **Default:** 5
  
    
    
 **Example:**
  
    
    



```
Set-OfficeWebAppsFarm -ExcelConcurrentDataRequestsPerSessionMax:10
```


## Set the Excel Online workbook calculation mode
<a name="ExcelDefaultWorkbookCalcMode"> </a>

You can specify the calculation mode of workbooks rendered in . The available values are:  _File_,  _Manual_,  _Auto_, and  _AutoDataTables_ (automatic except data tables). Settings other than _File_ override the workbook settings.
  
    
    
 **Syntax:** Set-OfficeWebAppsFarm -ExcelDefaultWorkbookCalcMode
  
    
    
 **Default:** File
  
    
    
 **Example:**
  
    
    



```
Set-OfficeWebAppsFarm -ExcelDefaultWorkbookCalcMode:Auto
```


## Set the maximum Excel Online image size
<a name="ExcelChartAndImagesSizeMax"> </a>

You can specify the maximum size, in megabytes, of a chart or image that can be opened by . The value must be an integer greater than 0.
  
    
    
 **Syntax:** Set-OfficeWebAppsFarm -ExcelChartAndImagesSizeMax
  
    
    
 **Default:** 1
  
    
    
 **Example:**
  
    
    



```

Set-OfficeWebAppsFarm -ExcelChartAndImagesSizeMax:5
```


## Configure an Analysis Services (data model) server for Excel Online
<a name="SSAS"> </a>

You can configure servers to work with by using the OfficeWebAppsExcelBIServer cmdlets:
  
    
    

- **New-OfficeWebAppsExcelBIServer** Adds an server location to the Allow List for Excel Calculation Services in for advanced BI functionality.
    
  
- **Get-OfficeWebAppsExcelBIServer** Gets the servers in the Allow List.
    
  
- **Remove-OfficeWebAppsExcelBIServer** Removes a server from the Allow List.
    
  
To use this feature, you must also configure each computer in your farm as an  [Analysis Services administrator](https://go.microsoft.com/fwlink/p/?LinkId=717498).
  
    
    
The New and Remove cmdlets take a parameter of -ServerID, which is the server name of the server that you want to add or remove.
  
    
    
 **Examples:**
  
    
    



```

New-OfficeWebAppsExcelBIServer -ServerID "SSAS01"
```




```
Remove-OfficeWebAppsExcelBIServer -ServerID "SSAS01"
```

The OfficeWebAppsExcelBIServer cmdlets also support  [common parameters](https://go.microsoft.com/fwlink/?LinkID=113216).
  
    
    

## Configure Analysis Services EffectiveUserName in Excel Online
<a name="EffectiveUserName"> </a>

EffectiveUserName is a connection string property that contains the name of the user who is accessing a report. In , you can use this property in conjunction with to pass the identity of the user who is viewing the report to . This allows per-user identity without the need to configure Kerberos constrained delegation.
  
    
    
To enable this option, you need to use the SQL Server 2016 version of . The actual data source can be in an earlier version of .
  
    
    
To configure this option, you have to do the following:
  
    
    

- Configure each computer in your farm as an  [Analysis Services administrator](https://go.microsoft.com/fwlink/p/?LinkId=717498).
    
  
- Use to enable EffectiveUserName in (described below).
    
  
The Set-OfficeWebAppsFarm is used to enable or disable EffectiveUserName in .
  
    
    
To enable EffectiveUserName in , run the following command:
  
    
    



```
Set-OfficeWebAppsFarm -ExcelUseEffectiveUserName:$True
```

To disable EffectiveUserName in , run the following command:
  
    
    



```
Set-OfficeWebAppsFarm -ExcelUseEffectiveUserName:$False
```


## Working with large workbooks
<a name="LargeWorkbooks"> </a>

When opening a workbook in , there is a time limit of one minute before will time out and fail to load the workbook. Occasionally, this time limit may not be enough to load large workbooks. If you run into problems loading large workbooks, you can adjust the timeout value.
  
    
    
To change the timeout value, you must update the settings.xml file on each computer running . (This file is normally located at C:\\ProgramData\\Microsoft\\OfficeWebApps\\Data\\FarmState\\settings.xml.)
  
    
    
Add the following value to the settings.xml file, where  *TimeoutValue*  is the timeout value in milliseconds:
  
    
    



```
<Setting Name="FBDirectReadTimeoutInMilliseconds" DataType="System.Int32">
    <StringValue>TimeoutValue</StringValue>
</Setting>

```

Note that a timeout value of 0 will make the timeout indefinite. This is not recommended as it increases the risk of a denial-of-service attack.
  
    
    

