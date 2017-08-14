---
title: Set-OfficeWebAppsFarm
ms.prod: OFFICERESOURCEKIT
ms.assetid: 6b0b434f-5d19-4e63-9296-cf104b2f3da8
---



# Set-OfficeWebAppsFarm

Configures the settings of an existing farm. 
  
    
    


```

Set-OfficeWebAppsFarm [-AllowCEIP <SwitchParameter>] [-AllowHttp <SwitchParameter>] [-AllowHttpSecureStoreConnections <SwitchParameter>] [-AllowOutboundHttp <SwitchParameter>] [-CacheLocation <String>] [-CacheSizeInGB <Int32>] [-CertificateName <String>] [-ClipartEnabled <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DocumentInfoCacheSize <UInt32>] [-EditingEnabled <SwitchParameter>] [-ExcelAbortOnRefreshOnOpenFail <SwitchParameter>] [-ExcelAllowExternalData <SwitchParameter>] [-ExcelAutomaticVolatileFunctionCacheLifeTime <Int32>] [-ExcelCachingUnusedFiles <SwitchParameter>] [-ExcelChartAndImageSizeMax <Int32>] [-ExcelConcurrentDataRequestsPerSessionMax <Int32>] [-ExcelConnectionLifetime <Int32>] [-ExcelDefaultWorkbookCalcMode <File | Manual | Auto | AutoDataTables>] [-ExcelExternalDataCacheLifetime <Int32>] [-ExcelMemoryCacheThreshold <Int32>] [-ExcelPrivateBytesMax <Int32>] [-ExcelRequestDurationMax <Int32>] [-ExcelRestExternalDataEnabled <SwitchParameter>] [-ExcelSessionTimeout <Int32>] [-ExcelUdfsAllowed <SwitchParameter>] [-ExcelUnusedObjectAgeMax <Int32>] [-ExcelUseEffectiveUserName <SwitchParameter>] [-ExcelWarnOnDataRefresh <SwitchParameter>] [-ExcelWorkbookSizeMax <Int32>] [-ExternalURL <String>] [-FarmOU <String>] [-Force <SwitchParameter>] [-InternalURL <String>] [-LogLocation <String>] [-LogRetentionInDays <UInt32>] [-LogVerbosity <String>] [-MaxMemoryCacheSizeInMB <Int32>] [-MaxTranslationCharacterCount <Int32>] [-OfficeAddinEnabled <SwitchParameter>] [-OnlinePictureEnabled <SwitchParameter>] [-OnlineVideoEnabled <SwitchParameter>] [-OpenFromUncEnabled <SwitchParameter>] [-OpenFromUrlEnabled <SwitchParameter>] [-OpenFromUrlThrottlingEnabled <SwitchParameter>] [-PicturePasteDisabled <SwitchParameter>] [-Proxy <String>] [-RecycleActiveProcessCount <UInt32>] [-RemovePersonalInformationFromLogs <SwitchParameter>] [-RenderingLocalCacheLocation <String>] [-S2SCertificateName <String>] [-SSLOffloaded <SwitchParameter>] [-TranslationEnabled <SwitchParameter>] [-TranslationServiceAddress <String>] [-TranslationServiceAppId <String>] [-WhatIf [<SwitchParameter>]]

```


## Example

------------------EXAMPLE 1---------------------
  
    
    

```

Set-OfficeWebAppsFarm -ClipartEnabled:$true
```

This example enables insertion of clip art from Office.com.
  
    
    
------------------EXAMPLE 2---------------------
  
    
    



```
Set-OfficeWebAppsFarm -EditingEnabled:$true
```

This example enables edit functionality for .
  
    
    
------------------EXAMPLE 3---------------------
  
    
    



```
Set-OfficeWebAppsFarm -OpenFromUncEnabled:$false
```

This example turns off the ability to view any Office file from a UNC path.
  
    
    

## Detailed Description

The **Set-OfficeWebAppsFarm** cmdlet configures the settings of an existing farm.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowCEIP_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables Customer Experience Improvement Program (CEIP) reporting on all servers in the farm.  <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _AllowHttp_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that sites should be provisioned on port 80 for HTTP access. Use **AllowHTTP** only in environments where all computers require IPSEC (full encryption) or in test environments that do not contain sensitive files. <br/> Enabled automatically when you enable **SSLOffloaded**. <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _AllowHttpSecureStoreConnections_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that secure store connections can be made by using non-SSL connections (such as HTTP). The default is **False**. <br/> Use **AllowHTTPSecureStoreConnections** only in environments where all computers require IPSEC (full encryption) or in test environments that do not contain sensitive files. <br/> |
| _AllowOutboundHttp_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Allows outbound HTTP connections from .  <br/> |
| _CacheLocation_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the location of the global disk cache that is used to store rendered image files. The default location is **%programdata%\\Microsoft\\OfficeWebApps\\Working\\d\\**. <br/> |
| _CacheSizeInGB_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum size of the global disk cache in gigabytes.  <br/> The type must be an integer value in the range of **0** to any positive integer. The default size is **15** GB. <br/> |
| _CertificateName_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the friendly name of the certificate that uses to create HTTPS bindings.  <br/> If the specified certificate is not found or has expired, or if the specified value is associated with more than one certificate, an error is logged and the farm is not created.  <br/> > [!IMPORTANT]> This value is used on every server that joins the farm. Therefore, every server in the farm must have a certificate that has this friendly name.           You don't have to specify the **CertificateName** parameter if you are using either the **AllowHttp** or **SSLOffloaded** parameter. <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _ClipartEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables support for inserting clip art from into documents. This feature requires server-to-web communication, configured either directly or by using a proxy that you specify by using the **Proxy** parameter. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |.  <br/> |
| _DocumentInfoCacheSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of document conversion records that are stored in a memory cache.  <br/> The default value is **5000** records. <br/> |
| _EditingEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables support for editing in the browser. The default is **False**. Only set to **True** if you have the appropriate licensing to use the edit functionality. <br/> |
| _ExcelAbortOnRefreshOnOpenFail_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prevents a workbook from loading if data refresh fails. This helps prevent users from seeing out-of-date information or possibly information that they should not have access to.  <br/> |
| _ExcelAllowExternalData_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the refresh of supported external data in workbooks where workbooks contain connections to external data. The default is **True**. <br/> |
| _ExcelAutomaticVolatileFunctionCacheLifeTime_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum time, in seconds, that a computed value for a volatile function is cached for automatic recalculations. **-1**: Calculates once when the workbook loads. **0**: Always calculates. **1** to **2073600**: Caches 1 second to 24 days. <br/> |
| _ExcelCachingUnusedFiles_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enable caching of files that are no longer in use by Web Excel sessions.  <br/> |
| _ExcelChartAndImageSizeMax_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum size, in megabytes, of a chart or image that can be opened by . The value must be an integer greater than 0.  <br/> |
| _ExcelConcurrentDataRequestsPerSessionMax_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum number of concurrent external data requests allowed in each session. If a session must issue more than this number of requests, additional requests are queued.  <br/> |
| _ExcelConnectionLifetime_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the duration, in seconds, of external data connections for . The default is **1800** seconds. <br/> |
| _ExcelDefaultWorkbookCalcMode_ <br/> |Optional  <br/> |Microsoft.Office.Excel.Server.DefaultWorkbookCalcMode  <br/> |PARAMVALUE: File | Manual | Auto | AutoDataTables  <br/> |
| _ExcelExternalDataCacheLifetime_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the duration, in seconds, of the external data cache lifetime in . The default is **300** seconds. <br/> |
| _ExcelMemoryCacheThreshold_ <br/> |Optional  <br/> |System.Int32  <br/> |The percentage of the Maximum Private Bytes that can be allocated to inactive objects. When the memory cache threshold is exceeded, cached objects that are not currently in use are released. Valid values: **0** (disables caching of inactive objects); from **1** through **95**. <br/> |
| _ExcelPrivateBytesMax_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum private bytes, in megabytes, used by . When set to **-1**, the maximum private bytes use 50 percent of physical memory on the computer. <br/> The type must be **-1** or any positive integer. The default value is **-1.** <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _ExcelRequestDurationMax_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum duration, in seconds, for a single request in a session. After this time elapses, the request times out.  <br/> The type must be **-1** (no limit) or an integer in the range of **1** to **2073600**. The default value is **300**. <br/> |
| _ExcelRestExternalDataEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Allow requests from the REST API to refresh external data connections. This setting has no effect if Allow External Data is set to **None**. Check box Bool. Default is **False**. <br/> |
| _ExcelSessionTimeout_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the time, in seconds, that a session remains active in when there is no user activity. Valid values include the following:  <br/> **-1** Session never expires. <br/> **0** Session expires at the end of a single request. <br/> **1** to **2073600** Session remains active for 1 second to 24 days. The default value is **450**. <br/> |
| _ExcelUdfsAllowed_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables User Defined Functions for . The default is **False**. <br/> |
| _ExcelUnusedObjectAgeMax_ <br/> |Optional  <br/> |System.Int32  <br/> |The maximum time (in minutes) that inactive objects remain in the memory cache. Inactive objects are objects that are not used in a session. Valid values: **-1** (no maximum); from **1** through **34560** (24 days). Default is **-1**. <br/> |
| _ExcelUseEffectiveUserName_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the use of the EffectiveUserName parameter with . The default is **False**. <br/> |
| _ExcelWarnOnDataRefresh_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Turns off or on the warning dialog box that is displayed when data refreshes in .  <br/> |
| _ExcelWorkbookSizeMax_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum size, in megabytes, of a workbook that can be loaded.  <br/> The type must be an integer value in the range of **1** to **2000**. The default value is **10**. <br/> |
| _ExternalURL_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL root that clients use to access the farm from the Internet. In the case of a load-balanced, multiserver farm, the external URL is bound to the IP address of the external-facing load balancer.  <br/> An farm requires at least one URL,that isset by using either **ExternalURL** or **InternalURL**. You can also set both internal and external URLs. <br/> |
| _FarmOU_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the name of the Active Directory organizational unit (OU) that servers must be a member of to join the farm. Use this parameter to prevent unauthorized servers (that is, servers that are not in the OU) from joining an farm.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any user prompts by answering "Yes."  <br/> |
| _InternalURL_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL root that clients must use to access the farm from the intranet.  <br/> An farm requires at least one URL. It is set using either **ExternalURL** or **InternalURL**. You can also set both internal and external URLs. <br/> |
| _LogLocation_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the location on the local computer where activity logs are stored.  <br/> The location applies for every server in the farm and cannot be customized on a per-server basis. The default location is **%programdata%\\Microsoft\\OfficeWebApps\\Data\\Logs\\ULS\\.** <br/> Be sure to allow sufficient disk space on the drive where logs are stored.  <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _LogRetentionInDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the number of days that log entries are stored. Log entries older than the configured date are trimmed.  <br/> The type must be an integer value in the range of **0** to **365**. The default value is **7** days. <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _LogVerbosity_ <br/> |Optional  <br/> |System.String  <br/> |Specifies how much information is stored in the trace log files. The values are as follows:  <br/> **VerboseEX** writes low-level detail to the trace log file. Useful for traces that are likely to be high volume. <br/> **Verbose** writes low-level detail to the trace log file. <br/> **Medium** writes medium-level detail to the trace log file. <br/> **High** writes high-level detail to the trace log file. <br/> **Monitorable** writes traces that represent an unusual code path and actions that should be monitored. <br/> **Unexpected** writes traces that represent an unexpected code path and actions that should be monitored. <br/> **None** writes no trace information to the trace log file. <br/> > [!IMPORTANT]> Leaving the **LogVerbosity** at a low level for a long time will adversely affect performance.          > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _MaxMemoryCacheSizeInMB_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies, in megabytes, the maximum amount of memory that the rendering cache can use.  <br/> The type must be an integer value in the range of **0** to any positive integer. The default size is **1024** MB. <br/> |
| _MaxTranslationCharacterCount_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum number of characters a document can have in order to be translated.  <br/> The type must be an integer value. The value can be set to 0 to indicate no limit or a value from **2000** to **2,000,000**. The default value is **125,000**. <br/> |
| _OfficeAddinEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Turn on or off Office Addin functionality both in the Client UI and the Server side. The default is **False**. <br/> |
| _OnlinePictureEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the ability to insert images from Bing image search into web apps that support clip art. PicturePasteDisabled must be **False** and OpenFromUrlEnabled must be **True** before OnlinePictureEnabled can be turned on. <br/> |
| _OnlineVideoEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables the ability to insert YouTube videos into web apps that support videos. OpenFromUrlEnabled must be **True** before OnlineVideoEnabled can be turned on. <br/> |
| _OpenFromUncEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Turns on or off the ability to use Online Viewers to view Office files from a UNC path.  <br/> You must first set OpenFromUrlEnabled to True to allow Online Viewers to display files in UNC paths.  <br/> |
| _OpenFromUrlEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Turns on or off the ability to use Online Viewers to view files from a URL or UNC path.  <br/> |
| _OpenFromUrlThrottlingEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Throttles the number of Open From URL requests from any given server in a time period. The default throttling values, which are not configurable, make sure that an farm will not overwhelm a single server with requests for content to be viewed in the Online Viewers.  <br/> |
| _PicturePasteDisabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Turns off the ability for users to paste images from a web page into . The default is **False**. If **OpenFromURLEnabled** is set to **True** and **PicturePasteDisabled** is not set or set to **False**, users can paste images into . <br/> |
| _Proxy_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL of the proxy server that is configured to allow HTTP requests to external sites. Typically configured together with the **ClipartEnabled** and **TranslationEnabled** parameters. <br/> |
| _RecycleActiveProcessCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the number of files that a single or process can render before the process is recycled.  <br/> The type must be an integer value in the range of **1** to **1000**. The default value is **5**. <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _RemovePersonalInformationFromLogs_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> | Provides a best effort scrub of personal information from logs and replaces values with a SHA256 hash. Potentially scrubbed information can be: <br/>  Document names and URLs <br/>  IP addresses <br/>  Email addresses <br/>  User names <br/>  The default is **False**. Note that enabling this parameter doesn't guarantee that personal information won't be logged to the logs. <br/> |
| _RenderingLocalCacheLocation_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the location of the temporary cache for use by the and Viewing Services.  <br/> The default location is **%programdata%\\Microsoft\\OfficeWebApps\\Working\\waccache\\**. <br/> |
| _S2SCertificateName_ <br/> |Optional  <br/> |System.String  <br/> |The friendly name of the certificate to use for server-to-server authentication with .  <br/> |
| _SSLOffloaded_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates to the servers in the farm that SSL is offloaded to the load balancer. When **SSLOffloaded** is enabled, web applications are bound to port 80 (HTTP) on the local server. However, HTML that references other resources, such as CSS or images, uses HTTPS URLs for those references. <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _TranslationEnabled_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |
> [!IMPORTANT]
> Enables support for automatic document translation using Microsoft Translator, an online service that translates text between languages. The translated file is shown in the . Because Microsoft Translator is an online service, you must enable server-to-web communication directly or by using a proxy that you specify by using the **Proxy** parameter.> Microsoft Translator may collect data to improve the quality of translations. 
  
    
    

|
| _TranslationServiceAddress_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the URL of the translation server that translation requests are sent to. The default is the Microsoft Translator online service. Typically you will not use this parameter unless you must change translation services.  <br/> > [!IMPORTANT]> You must restart every server in the farm for this change to take effect.           |
| _TranslationServiceAppId_ <br/> |Optional  <br/> |System.String  <br/> |Specifies the application ID for the translation service. The default is the public application ID for . Typically you will not use this parameter unless you have negotiated with Microsoft Translator for additional services and they have provided you with a private application ID.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## AutoGenParams



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**AllowCEIP** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**AllowHttp** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**AllowHttpSecureStoreConnections** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**CacheLocation** <br/> |Optional  <br/> |System.String  <br/> ||
|**CacheSizeInGB** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**CertificateName** <br/> |Optional  <br/> |System.String  <br/> ||
|**ClipartEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**DocumentInfoCacheSize** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**EditingEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**ExcelAllowExternalData** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**ExcelConnectionLifetime** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExcelExternalDataCacheLifetime** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExcelPrivateBytesMax** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExcelRequestDurationMax** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExcelSessionTimeout** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExcelWarnOnDataRefresh** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**ExcelWorkbookSizeMax** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**ExternalURL** <br/> |Optional  <br/> |System.String  <br/> ||
|**FarmOU** <br/> |Optional  <br/> |System.String  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**InternalURL** <br/> |Optional  <br/> |System.String  <br/> ||
|**LogLocation** <br/> |Optional  <br/> |System.String  <br/> ||
|**LogRetentionInDays** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**LogVerbosity** <br/> |Optional  <br/> |System.String  <br/> ||
|**MaxMemoryCacheSizeInMB** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**MaxTranslationCharacterCount** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**OpenFromUncEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**OpenFromUrlEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**OpenFromUrlThrottlingEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**PicturePasteDisabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Proxy** <br/> |Optional  <br/> |System.String  <br/> ||
|**RecycleActiveProcessCount** <br/> |Optional  <br/> |System.Nullable  <br/> ||
|**RemovePersonalInformationFromLogs** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**RenderingLocalCacheLocation** <br/> |Optional  <br/> |System.String  <br/> ||
|**SSLOffloaded** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**TranslationEnabled** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**TranslationServiceAddress** <br/> |Optional  <br/> |System.String  <br/> ||
|**TranslationServiceAppId** <br/> |Optional  <br/> |System.String  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   

## See also


#### 


  
    
    
 [New-OfficeWebAppsFarm](new-officewebappsfarm.md)
  
    
    
 [Get-OfficeWebAppsFarm](get-officewebappsfarm.md)
