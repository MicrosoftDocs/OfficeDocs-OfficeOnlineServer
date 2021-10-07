---
title: Enable TLS 1.1 and TLS 1.2 support in Office Online Server
description: This article describes how to enable Transport Layer Security (TLS) protocol versions 1.1 and 1.2 in Office Online Server.
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 11/16/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: b06dd801-736a-4621-8945-894449794f51
---


# Enable TLS 1.1 and TLS 1.2 onwards support in Office Online Server

 **Summary:** This article describes how to enable Transport Layer Security (TLS) protocol versions 1.1 and 1.2 onwards in Office Online Server.
  
    
    


To enable TLS protocol versions 1.1 and 1.2 onwards in your Office Online Server environment, you need to configure settings on each server in your Office Online Server farm.
  
    
    


The configuration process involves setting a number of registry keys to turn security protocols on or off. While you can make these updates to the registry manually or by using a .reg file, we recommend that you create group policy objects to manage these settings, particularly if you are configuring these protocols across your organization.
  
    
    


The basic steps covered in this article are:
  
    
    


- Enable strong cryptography in .NET Framework.  
<br>NOTE :- As of the July 2021 cumulative security update (https://support.microsoft.com/topic/description-of-the-security-update-for-office-online-server-july-13-2021-kb5001973-d9f20977-c147-4022-9087-5f90380e39f5), this step is not required. Anyone who applies this patch can skip this step. <br>

    
- (Optional) Disable earlier versions of SSL and TLS
    
  

Note that using TLS 1.1 and TLS 1.2 onwards with Office Online Server requires that TLS 1.1 and TLS 1.2 onwards be enabled on Windows Server for each computer in your Office Online Server farm. They are enabled by default for Windows Server 2012 R2.
  
    
    


Follow these steps on each server in your Office Online Server farm.
  
    
    


## Enable strong cryptography in .NET Framework 4.5 or higher
NOTE :- As of the July 2021 cumulative security update (https://support.microsoft.com/topic/description-of-the-security-update-for-office-online-server-july-13-2021-kb5001973-d9f20977-c147-4022-9087-5f90380e39f5), this step is not required. Anyone who applies this patch can skip this step.

Using TLS 1.1 and TLS 1.2 onwards with Office Online Server requires strong cryptography in .NET Framework 4.5 or higher. To enable strong cryptography in .NET Framework 4.5 or higher, add the following registry keys:
  
    
    

```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.30319]
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.30319]
"SchUseStrongCrypto"=dword:00000001

```


## Disable earlier versions of SSL and TLS in Windows Schannel

SSL and TLS support are enabled or disabled in Windows Schannel by editing the Windows Registry. Each SSL and TLS protocol version can be enabled or disabled independently. You don't need to enable or disable one protocol version to enable or disable another protocol version.
  
    
    

> [!IMPORTANT]
> Microsoft recommends disabling SSL 2.0 and SSL 3.0 due to serious security vulnerabilities in those protocol versions. >  Customers may also choose to disable TLS 1.0 and TLS 1.1 to ensure that only the newest protocol version is used. However, this may cause compatibility issues with software that doesn't support the newest TLS protocol version. Customers should test such a change before performing it in production.
  
    
    

The **Enabled** registry value defines whether the protocol version can be used. If the value is set to 0, the protocol version cannot be used, even if it is enabled by default or if the application explicitly requests that protocol version. If the value is set to 1, the protocol version can be used if enabled by default or if the application explicitly requests that protocol version. If the value is not defined, it will use a default value determined by the operating system.
  
    
    
The **DisabledByDefault** registry value defines whether the protocol version is used by default. This setting only applies when the application doesn't explicitly request the protocol versions to be used. If the value is set to 0, the protocol version will be used by default. If the value is set to 1, the protocol version will not be used by default. If the value is not defined, it will use a default value determined by the operating system.
  
    
    
To disable SSL 2.0 support in Windows Schannel, add the following registry keys:
  
    
    



```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\SSL 2.0\\Client]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\SSL 2.0\\Server]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000
```

To disable SSL 3.0 support in Windows Schannel, add the following registry keys:
  
    
    



```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\SSL 3.0\\Client]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\SSL 3.0\\Server]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000
```

To disable TLS 1.0 support in Windows Schannel, add the following registry keys:
  
    
    



```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\TLS 1.0\\Client]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\TLS 1.0\\Server]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000
```

To disable TLS 1.1 support in Windows Schannel, add the following registry keys:
  
    
    



```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\TLS 1.1\\Client]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000

[HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Protocols\\TLS 1.1\\Server]
"DisabledByDefault"=dword:00000001
"Enabled"=dword:00000000
```


