---
title: Set-OfficeWebAppsFarm
TOCTitle: Set-OfficeWebAppsFarm
ms:assetid: 6b0b434f-5d19-4e63-9296-cf104b2f3da8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ219442(v=office.15)
ms:contentKeyID: 48409065
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Set-OfficeWebAppsFarm

 

_**Applies to:** Office Web Apps Server_


Configures the settings of an existing Office Web Apps Server farm.

## Syntax

```PowerShell
Set-OfficeWebAppsFarm 
    [-AllowCEIP <SwitchParameter>] 
    [-AllowHttp <SwitchParameter>] 
    [-AllowHttpSecureStoreConnections <SwitchParameter>] 
    [-CacheLocation <String>] 
    [-CacheSizeInGB <Nullable>]
    [-CertificateName <String>] 
    [-ClipartEnabled <SwitchParameter>] 
    [-Confirm [<SwitchParameter>]] 
    [-DocumentInfoCacheSize <Nullable>] 
    [-EditingEnabled <SwitchParameter>] 
    [-ExcelAllowExternalData <SwitchParameter>] 
    [-ExcelConnectionLifetime <Nullable>] 
    [-ExcelExternalDataCacheLifetime <Nullable>]
    [-ExcelPrivateBytesMax <Nullable>] 
    [-ExcelRequestDurationMax <Nullable>] 
    [-ExcelSessionTimeout <Nullable>] 
    [-ExcelWarnOnDataRefresh <SwitchParameter>] 
    [-ExcelWorkbookSizeMax <Nullable>] 
    [-ExternalURL <String>] [-FarmOU <String>] 
    [-Force <SwitchParameter>] 
    [-InternalURL <String>] 
    [-LogLocation <String>] 
    [-LogRetentionInDays <Nullable>] 
    [-LogVerbosity <String>] 
    [-MaxMemoryCacheSizeInMB <Nullable>] 
    [-MaxTranslationCharacterCount <Nullable>] 
    [-OpenFromUncEnabled <SwitchParameter>] 
    [-OpenFromUrlEnabled <SwitchParameter>]  
    [-OpenFromUrlThrottlingEnabled <SwitchParameter>] 
    [-PicturePasteDisabled <SwitchParameter>] 
    [-Proxy <String>] 
    [-RecycleActiveProcessCount <Nullable>] 
    [-RemovePersonalInformationFromLogs <SwitchParameter>] 
    [-RenderingLocalCacheLocation <String>] 
    [-SSLOffloaded <SwitchParameter>] 
    [-TranslationEnabled <SwitchParameter>] 
    [-TranslationServiceAddress <String>] 
    [-TranslationServiceAppId <String>] 
    [-WhatIf [<SwitchParameter>]]
```    

## Detailed Description

The **Set-OfficeWebAppsFarm** cmdlet configures the settings of an existing Office Web Apps Server farm.

## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AllowCEIP</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables Customer Experience Improvement Program (CEIP) reporting on all servers in the Office Web Apps Server farm.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the Office Web Apps Server farm for this change to take effect.


</div></td>
</tr>
<tr class="even">
<td><p><strong>AllowHttp</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indicates that IIS sites should be provisioned on port 80 for HTTP access. Use <strong>AllowHTTP</strong> only in environments where all computers require IPSEC (full encryption) or in test environments that do not contain sensitive files.</p>
<p>Enabled automatically when you enable <strong>SSLOffloaded</strong>.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHttpSecureStoreConnections</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indicates that secure store connections can be made by using non-SSL connections (such as HTTP). The default is <strong>False</strong>.</p>
<p>Use <strong>AllowHTTPSecureStoreConnections</strong> only in environments where all computers require IPSEC (full encryption) or in test environments that do not contain sensitive files.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheLocation</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the location of the global disk cache that is used to store rendered image files. The default location is <strong>%programdata%\Microsoft\OfficeWebApps\Working\d\</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheSizeInGB</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum size of the global disk cache in gigabytes.</p>
<p>The type must be an integer value in the range of <strong>0</strong> to any positive integer. The default size is <strong>15</strong> GB.</p></td>
</tr>
<tr class="even">
<td><p><strong>CertificateName</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the friendly name of the certificate that Office Web Apps Server uses to create HTTPS bindings.</p>
<p>If the specified certificate is not found or has expired, or if the specified value is associated with more than one certificate, an error is logged and the farm is not created.</p>
<div class="alert">

> [!IMPORTANT]
> This value is used on every server that joins the Office Web Apps Server farm. Therefore, every server in the farm must have a certificate that has this friendly name.


</div>
<p>You don’t have to specify the <strong>CertificateName</strong> parameter if you are using either the <strong>AllowHttp</strong> or <strong>SSLOffloaded</strong> parameter.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>ClipartEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables support for inserting clip art from Office.com into Office documents. This feature requires server-to-web communication, configured either directly or by using a proxy that you specify by using the <strong>Proxy</strong> parameter.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DocumentInfoCacheSize</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum number of document conversion records that are stored in a memory cache.</p>
<p>The default value is <strong>5000</strong> records.</p></td>
</tr>
<tr class="even">
<td><p><strong>EditingEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables support for editing in the browser. The default is <strong>False</strong>. Only set to <strong>True</strong> if you have the appropriate licensing to use the edit functionality.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelAllowExternalData</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables the refresh of supported external data in Excel Web App workbooks where workbooks contain connections to external data. The default is <strong>True</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelConnectionLifetime</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the duration, in seconds, of external data connections for Excel Web App. The default is <strong>1800</strong> seconds.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelExternalDataCacheLifetime</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the duration, in seconds, of the external data cache lifetime in Excel Web App. The default is <strong>300</strong> seconds.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelPrivateBytesMax</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum private bytes, in megabytes, used by Excel Web App. When set to <strong>-1</strong>, the maximum private bytes use 50 percent of physical memory on the computer.</p>
<p>The type must be <strong>-1</strong> or any positive integer. The default value is <strong>-1.</strong></p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelRequestDurationMax</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum duration, in seconds, for a single request in a session. After this time elapses, the request times out.</p>
<p>The type must be <strong>-1</strong> (no limit) or an integer in the range of <strong>1</strong> to <strong>2073600</strong>. The default value is <strong>300</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelSessionTimeout</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the time, in seconds, that a session remains active in Excel Web App when there is no user activity. Valid values include the following:</p>
<p><strong>-1</strong> Session never expires.</p>
<p><strong>0</strong> Session expires at the end of a single request.</p>
<p><strong>1</strong> to <strong>2073600</strong> Session remains active for 1 second to 24 days. The default value is <strong>450</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelWarnOnDataRefresh</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Turns off or on the warning dialog box that is displayed when data refreshes in Excel Web App.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelWorkbookSizeMax</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum size, in megabytes, of a workbook that can be loaded.</p>
<p>The type must be an integer value in the range of <strong>1</strong> to <strong>2000</strong>. The default value is <strong>10</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalURL</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the URL root that clients use to access the Office Web Apps Server farm from the Internet. In the case of a load-balanced, multiserver Office Web Apps Server farm, the external URL is bound to the IP address of the external-facing load balancer.</p>
<p>An Office Web Apps Server farm requires at least one URL,that isset by using either <strong>ExternalURL</strong> or <strong>InternalURL</strong>. You can also set both internal and external URLs.</p></td>
</tr>
<tr class="even">
<td><p><strong>FarmOU</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the name of the Active Directory organizational unit (OU) that servers must be a member of to join the Office Web Apps Server farm. Use this parameter to prevent unauthorized servers (that is, servers that are not in the OU) from joining an Office Web Apps Server farm.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any user prompts by answering &quot;Yes.&quot;</p></td>
</tr>
<tr class="even">
<td><p><strong>InternalURL</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the URL root that clients must use to access the Office Web Apps Server farm from the intranet.</p>
<p>An Office Web Apps Server farm requires at least one URL. It is set using either <strong>ExternalURL</strong> or <strong>InternalURL</strong>. You can also set both internal and external URLs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLocation</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the location on the local computer where activity logs are stored.</p>
<p>The location applies for every server in the farm and cannot be customized on a per-server basis. The default location is <strong>%programdata%\Microsoft\OfficeWebApps\Data\Logs\ULS\.</strong></p>
<p>Be sure to allow sufficient disk space on the drive where logs are stored.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="even">
<td><p><strong>LogRetentionInDays</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the number of days that log entries are stored. Log entries older than the configured date are trimmed.</p>
<p>The type must be an integer value in the range of <strong>0</strong> to <strong>365</strong>. The default value is <strong>7</strong> days.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>LogVerbosity</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies how much information is stored in the trace log files. The values are as follows:</p>
<p><strong>VerboseEX</strong> writes low-level detail to the trace log file. Useful for traces that are likely to be high volume.</p>
<p><strong>Verbose</strong> writes low-level detail to the trace log file.</p>
<p><strong>Medium</strong> writes medium-level detail to the trace log file.</p>
<p><strong>High</strong> writes high-level detail to the trace log file.</p>
<p><strong>Monitorable</strong> writes traces that represent an unusual code path and actions that should be monitored.</p>
<p><strong>Unexpected</strong> writes traces that represent an unexpected code path and actions that should be monitored.</p>
<p><strong>None</strong> writes no trace information to the trace log file.</p>
<div class="alert">

> [!IMPORTANT]
> Leaving the <STRONG>LogVerbosity</STRONG> at a low level for a long time will adversely affect performance.


</div>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="even">
<td><p><strong>MaxMemoryCacheSizeInMB</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies, in megabytes, the maximum amount of memory that the rendering cache can use.</p>
<p>The type must be an integer value in the range of <strong>0</strong> to any positive integer. The default size is <strong>1024</strong> MB.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxTranslationCharacterCount</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the maximum number of characters a document can have in order to be translated.</p>
<p>The type must be an integer value. The value can be set to 0 to indicate no limit or a value from <strong>2000</strong> to <strong>2,000,000</strong>. The default value is <strong>125,000</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUncEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Turns on or off the ability to use Online Viewers to view Office files from a UNC path.</p>
<p>You must first set OpenFromUrlEnabled to True to allow Online Viewers to display files in UNC paths.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OpenFromUrlEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Turns on or off the ability to use Online Viewers to view Officefiles from a URL or UNC path.</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUrlThrottlingEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Throttles the number of Open From URL requests from any given server in a time period. The default throttling values, which are not configurable, make sure that an Office Web Apps Server farm will not overwhelm a single server with requests for content to be viewed in the Online Viewers.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PicturePasteDisabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Turns off the ability for users to paste images from a web page into Office Web Apps. The default is <strong>False</strong>. If <strong>OpenFromURLEnabled</strong> is set to <strong>True</strong> and <strong>PicturePasteDisabled</strong> is not set or set to <strong>False</strong>, users can paste images into Office Web Apps.</p></td>
</tr>
<tr class="even">
<td><p><strong>Proxy</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the URL of the proxy server that is configured to allow HTTP requests to external sites. Typically configured together with the <strong>ClipartEnabled</strong> and <strong>TranslationEnabled</strong> parameters.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecycleActiveProcessCount</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Nullable</p></td>
<td><p>Specifies the number of files that a single Word or PowerPoint process can render before the process is recycled.</p>
<p>The type must be an integer value in the range of <strong>1</strong> to <strong>1000</strong>. The default value is <strong>5</strong>.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="even">
<td><p><strong>RemovePersonalInformationFromLogs</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Provides a best effort scrub of personal information from Office Web Apps Server logs and replaces values with a SHA256 hash. Potentially scrubbed information can be:</p>
<ul>
<li><p>Document names and URLs</p></li>
<li><p>IP addresses</p></li>
<li><p>Email addresses</p></li>
<li><p>User names</p></li>
</ul>
<p>The default is <strong>False</strong>. Note that enabling this parameter doesn't guarantee that personal information won't be logged to the Office Web Apps Server logs.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RenderingLocalCacheLocation</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the location of the temporary cache for use by the Word and PowerPoint Viewing Services.</p>
<p>The default location is <strong>%programdata%\Microsoft\OfficeWebApps\Working\waccache\</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SSLOffloaded</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Indicates to the servers in the Office Web Apps Server farm that SSL is offloaded to the load balancer. When <strong>SSLOffloaded</strong> is enabled, web applications are bound to port 80 (HTTP) on the local server. However, HTML that references other resources, such as CSS or images, uses HTTPS URLs for those references.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationEnabled</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><div class="alert">

> [!IMPORTANT]
> Enables support for automatic document translation using Microsoft Translator, an online service that translates text between languages. The translated file is shown in the Word Web App. Because Microsoft Translator is an online service, you must enable server-to-web communication directly or by using a proxy that you specify by using the <STRONG>Proxy</STRONG> parameter.<BR>Microsoft Translator may collect data to improve the quality of translations.


</div></td>
</tr>
<tr class="even">
<td><p><strong>TranslationServiceAddress</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the URL of the translation server that translation requests are sent to. The default is the Microsoft Translator online service. Typically you will not use this parameter unless you must change translation services.</p>
<div class="alert">

> [!IMPORTANT]
> You must restart every server in the Office Web Apps Server farm for this change to take effect.


</div></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationServiceAppId</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the application ID for the translation service. The default is the public application ID for Office Web Apps. Typically you will not use this parameter unless you have negotiated with Microsoft Translator for additional services and they have provided you with a private application ID.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: <strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## Input Types

## Return Types

## Example

\------------------EXAMPLE 1---------------------

```PowerShell
Set-OfficeWebAppsFarm -ClipartEnabled:$true
```

This example enables insertion of clip art from Office.com.

\------------------EXAMPLE 2---------------------

```PowerShell
Set-OfficeWebAppsFarm -EditingEnabled:$true
```

This example enables edit functionality for Office Web Apps.

\------------------EXAMPLE 3---------------------

```PowerShell
Set-OfficeWebAppsFarm -OpenFromUncEnabled:$false
```

This example turns off the ability to view any Office file from a UNC path.

## See also


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Content roadmap for Office Web Apps Server](content-roadmap-for-office-web-apps-server.md)  
[Deploy the infrastructure: Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

