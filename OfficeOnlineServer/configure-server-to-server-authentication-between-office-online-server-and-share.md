---
title: Configure server-to-server authentication between Office Online Server and SharePoint Server 2016
ms.prod: SHAREPOINT
ms.assetid: 84c08727-b496-48b6-b54b-a366fad151d7
---


# Configure server-to-server authentication between Office Online Server and SharePoint Server 2016
 **Summary:** Configure server-to-server authentication between and .
Server-to-server authentication between and establishes trust between the two servers. This trust is a necessary prerequisite for some features, such as Office Data Connection (ODC) file support and the IT Management Dashboard, which is part of . This article guides you through the steps to set up this trust.
  
    
    

To configure server-to-server authentication, your farm and farm must be in the same Active Directory forest. You also must have a User Profile service application configured on the farm.
The basic actions required for configuring server-to-server authentication are:
  
    
    


1.  [Import the certificate to Office Online Server](configure-server-to-server-authentication-between-office-online-server-and-share.md#ImportCerts)
    
  
2.  [Export the certificate for use on SharePoint Server](configure-server-to-server-authentication-between-office-online-server-and-share.md#ExportCerts)
    
  
3.  [Configure Office Online Server to use the certificate for server-to-server authentication](configure-server-to-server-authentication-between-office-online-server-and-share.md#ConfigureWAC)
    
  
4.  [Configure SharePoint Server to use the certificate for server-to-server authentication](configure-server-to-server-authentication-between-office-online-server-and-share.md#ConfigureSharePoint)
    
  
You'll start with importing the certificate to .
## Import the certificate to Office Online Server
<a name="ImportCerts"> </a>

The first step is to import your certificate for use by . Follow the  *Import your certificate*  and *Grant network service permission to use the key*  procedures on each server in your farm.
  
    
    

### Import your certificate

You can use either a private key SSL certificate or a self-signed certificate. We highly recommend using a private key SSL certificate. The following sections provide procedures for both. Choose the one the you are using.
  
    
    

#### Use a private key SSL certificate

Install the certificate on each server running .
  
    
    

### To install the certificate on Server


1. On the server running , open .
    
  
2. In the left pane, click the server name.
    
  
3. Double-click **Server Certificates**.
    
  
4. In the **Actions** pane, click **Import**.
    
  
5. Type the  *path*  and *file name*  of the SSL certificate that you want to use.
    
  
6. In the **Password** box, type the *password*  for the certificate.
    
  
7. In the **Select Certificate Store** drop-down list, make sure **Personal** is selected.
    
  
8. Click **OK**.
    
  
Repeat this procedure on each server running .
  
    
    

#### Use a self-signed certificate

If you're using a self-signed certificate, you need to add it to the Trusted Root Certification Authorities.
  
    
    

### To import the certificate to the Trusted Root Certification Authorities


1. Open the Microsoft Management Console.
    
  
2. On the **File** menu, choose **Add/Remove Snap-in**.
    
  
3. Choose **Certificates**, and then click **Add**.
    
  
4. Choose the **Computer account** option, click **Next**, and then click **Finish**.
    
  
5. Click **OK**.
    
  
6. Expand **Certificates (Local Computer)**, right-click **Trusted Root Certification Authorities**, click **All Tasks**, and then click **Import**.
    
  
7. Click **Next**.
    
  
8. Browse to the location of the certificate, select it, and then click **Next**.
    
  
9. Type the certificate password, click **Next**, and then click **Finish**.
    
  
Keep the Microsoft Management Console open for the next procedure.
  
    
    

### Grant network service permission to use the key

Next, use the Microsoft Management Console (MMC) to grant the network service permissions to use the private key.
  
    
    

### To grant network service permissions to use the private key


1. Open the Microsoft Management Console.
    
  
2. On the **File** menu, choose **Add/Remove Snap-in**.
    
  
3. Choose **Certificates**, and then click **Add**.
    
  
4. Choose the **Computer account** option, click **Next**, and then click **Finish**.
    
  
5. Click **OK**.
    
  
6. Expand **Certificates (Local Computer)**, expand **Personal**, and then click **Certificates**.
    
  
7. Right-click the certificate that you just imported, click **All Tasks**, and then click **Manage Private Keys**.
    
  
8. In the **Permissions** dialog box, click **Add**.
    
  
9. Type Network Service, and then click **OK**.
    
  
10. Click **OK**.
    
  
Be sure you follow the  *Import your certificate*  and *Grant network service permission to use the key*  procedures on each server in your farm.
  
    
    
Keep the Microsoft Management Console open for the next procedure. 
  
    
    

## Export the certificate for use on SharePoint Server
<a name="ExportCerts"> </a>

The next step is to export the certificate so that you can use it to register as a trusted token issuer.
  
    
    

### To export the certificate for use with


1. Right-click the certificate that you just imported, click **All Tasks**, and then click **Export**.
    
  
2. On the Welcome page, click **Next**.
    
  
3. Choose the **No, do not export the private key** option, and then click **Next**.
    
  
4. Choose the **DER encoded binary X.509 (.CER)** option, and then click **Next**.
    
  
5. Type the  *path*  and *name*  of the file that you want to export, and then click **Next**.
    
  
6. Click **Finish**, and then click **OK**.
    
  
Copy the certificate file that you created to a location where you can access it from .
  
    
    
Next, you need to specify this certificate as the S2S certificate for .
  
    
    

## Configure Office Online Server to use the certificate for server-to-server authentication
<a name="ConfigureWAC"> </a>


### To specify the S2S certificate for


1. Open a window as Administrator.
    
  
2. Type the following where <friendlyName> is the friendly name of the certificate that you're using.
    
  ```
  
Set-OfficeWebAppsFarm -S2SCertificateName "<friendlyName>" -Confirm:$false -Force
  ```

 **Using HTTP with Office Online Server**
  
    
    
If you're using HTTP instead of HTTPS for your farm, you have to allow outbound HTTP connections from . (If you're using SSL, you can skip this procedure.)
  
    
    
To enable outbound HTTP connections from , run the following command:
  
    
    



```
Set-OfficeWebAppsFarm -AllowOutboundHttp:$True
```




```
iisreset
```

 **Using HTTP paths with ODC files**
  
    
    
If you plan to store ODC files in an HTTP path, you have to configure to allow Secure Store connections over HTTP.
  
    
    

> [!IMPORTANT]
> When you use Secure Store connections over HTTP, the contents of the ODC file are passed in clear text. ODC files contain database connection information and can contain passwords. 
  
    
    

To enable to use HTTP paths with Secure Store, run the following command:
  
    
    



```
Set-OfficeWebAppsFarm -AllowHttpSecureStoreConnections:$true
```




```
iisreset
```


## Configure SharePoint Server to use the certificate for server-to-server authentication
<a name="ConfigureSharePoint"> </a>

You need to register and as trusted token issuers. This is done through . Here are the parameters that you'll use:
  
    
    

- **<SPSiteURL>** - The URL of your top-level site collection.
    
  
- **<CertificateIssuer>** - The name of the certificate issuer. You can find this by viewing the **Details** tab of the certificate in IIS Manager.
    
  
- **<X509Certificate>** - The path and file name of the certificate file that you exported.
    
  
- **<RegisteredIssuer>** - The GUID of the trusted token issuer. is 67e3df25-268a-4324-a550-0de1c7f97287@bd2372e4-0a11-495c-9541-8377c6def195 and is 67e3df25-268a-4324-a550-0de1c7f97287@ffab2d74-c6ae-4375-819a-8555d49b699a
    
  
Perform the following procedure twice - once for each <RegisteredIssuer> GUID.
  
    
    
Perform this procedure on a Front-end server in your farm.
  
    
    

### To register a trusted token issuer


1. Open the as Administrator.
    
  
2. Run the following script using the parameters noted above:
    
  ```
  $wac=New-SPTrustedSecurityTokenIssuer -Name <CertificateIssuer> -Certificate <X509Certificate> -RegisteredIssuerName <RegisteredIssuer>
  ```


  ```
  $app=Get-SPAppPrincipal -Site <SPSiteURL> -NameIdentifier $wac.NameId
  ```


  ```
  $site=Get-SPSite <SPSiteURL>
  ```


  ```
  Set-SPAppPrincipalPermission -appPrincipal $app -Site $site.RootWeb -Scope sitesubscription -Right fullcontrol -EnableAppOnlyPolicy
  ```

3. If you're using a self-signed certificate, run the following command:
    
  ```
  New-SPTrustedRootAuthority -Name <CertificateIssuer> -Certificate <X509Certificate>
  ```


