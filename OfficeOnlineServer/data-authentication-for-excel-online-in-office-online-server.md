---
title: Data authentication for Excel Online in Office Online Server
description: Learn how Excel Online supports connections with SQL Server Analysis Services (SSAS), SQL Server databases, and OLE DB and ODBC data sources.
ms.author: samukhe
author: santanu-wac
manager: pamgreen
ms.date: 8/8/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
ms.assetid: 7ced238b-2866-4961-af1c-6b597a55ce7a
---


# Data authentication for Excel Online in Office Online Server

 **Summary** Learn how Excel Online supports connections with SQL Server Analysis Services (SSAS), SQL Server databases, and OLE DB and ODBC data sources.
  
    
    


Retrieving data from a data source requires a user to be authenticated by the data source and then authorized to access the data that is contained therein. In the case of a workbook, Excel Online authenticates to the data source on behalf of the user who is viewing it in order to refresh the data to which the workbook is connected.
  
    
    


Which authentication method Excel Online can use to retrieve data depends on the type of the underlying data source, as outlined in the following table. For data sources that support more than one authentication method, data connections must specify which one to use.
  
    
    


**Data sources and authentication methods for Excel Online**


|**Data source**|**Authentication method**|
|:-----|:-----|
|Analysis Services  <br/> | Windows authentication (integrated security) <br/>  using Kerberos Constrained Delegation <br/>  using Secure Store <br/>  using the EffectiveUserName connection string property <br/> |
|SQL Server  <br/> | One of: <br/>  Windows authentication (integrated security) <br/>  using Kerberos Constrained Delegation <br/>  using Secure Store <br/>  SQL Server Authentication <br/> |
|Custom data providers  <br/> |Varies per data source, typically a user-name and password pair stored in the connection string.  <br/> |
   

The following data sources are supported in Excel but not in Excel Online:
  
    
    


- Access databases
    
  
- Web content
    
  
- XML data
    
  
- Microsoft Azure Marketplace
    
  
- Text files
    
  

## Connecting to external data with Excel Online

Excel Online can connect to various external data sources, including SQL Server, Analysis Services, and custom OLE DB/ODBC data providers. To connect to the data source, Excel Online uses a specific data provider for each data source.
  
    
    
Connecting to a SQL Server data source can be done by using either:
  
    
    

- Windows authentication
    
  
- SQL Server Authentication
    
  
Connecting to an Analysis Services data source is done by using Windows authentication.
  
    
    
Other data sources use a connection string usually consisting of a user name and password.
  
    
    

### Data connections for Excel Online workbooks

Excel Online workbooks use one of two kinds of connections:
  
    
    

- Embedded connections
    
  
- Linked connections
    
  
Embedded connections are stored as part of the Excel workbook. Linked connections are stored externally to a workbook in Office Data Connection (ODC) files. To use a linked connection, a workbook must reference an .odc file that is also stored in the same SharePoint Server farm as the workbook. Each data connection consists of:
  
    
    

- A connection string
    
  
- A query string
    
  
- An authentication method
    
  
- Optionally, some metadata required to retrieve external data
    
  
Each kind of connection has its advantages and drawbacks discussed here. Choose the one that best suits your scenario.
  
    
    

**Comparison of data connections for Excel Online**


|**Connection type**|**Embedded connections**|**ODC files**|
|:-----|:-----|:-----|
|Advantages  <br/> | All connection information is stored in the workbook. <br/>  Embedded connections require little administrative overhead to support. <br/>  Embedded connections are easy to create. <br/> | Linked connections can be centrally stored, managed, audited, shared and access to them can be controlled by using a SharePoint document library. <br/>  Workbook authors can use existing connections without having to create queries and connection strings. <br/>  If the data connection details for a data source change, an administrator only need update one ODC file. With that change, all workbooks that refer to the ODC file will use the updated connection information when the next refresh occurs. (An example of this scenario is when the database server is moved or the database name is changed.) <br/> |
|Drawbacks  <br/> | If the data connection details for a data source change, all workbooks with embedded connections to that data source will have to be republished with updated connection information. <br/>  Embedded data connections are more difficult to audit by SharePoint administrators. <br/> | Linked connections may require the help of a SharePoint administrator to share, manage and secure. <br/>  Linked connections are saved in clear text and may contain database passwords. Extra care must be taken to help secure these files. <br/>  Requires [server-to-server authentication](configure-office-online-server-for-sharepoint-server-2016/configure-server-to-server-authentication-between-office-online-server-and-share.md) between Office Online Server and SharePoint Server. This adds configuration and administration overhead. <br/> |
   
Choose a linked data connection, by using an ODC file, for scenarios in which you must have a data connection to an enterprise-scale data source such as SQL Server or Analysis Services. Linked data connections are most useful in scenarios in which they will be shared across many users and in which administrator control of the connection is important.
  
    
    
Choose an embedded connection for scenarios where you need a data connection that will not be widely used.
  
    
    
ODC files can be centralized in a data connection library. Doing so has several advantages:
  
    
    

- Administrators can restrict write access to a data connection library to trusted data connection authors to ensure that only well tested and secure data connections are used by workbook authors.
    
  
- Administrators have a single location to manage data connections for a large group of users.
    
  
- Administrators can easily approve, audit, revert and manage data connection files by using document library versioning and workflow features.
    
  
- Data connection libraries can be reused across other Office applications such as Visio and Visio Services.
    
  
- Workbook authors only have a single location to find workbook data connections, reducing confusion and user training.
    
  

### Windows authentication

Windows authentication requires that Excel Online present to the data source a set of Windows credentials. This kind of credential is common on Windows networks and is the same credential used to log on to computers on a Windows domain. Windows credentials are considered the most secure and manageable means of controlling access to SQL Server databases. However, one obstacle to using Windows authentication with Excel Online is the Windows double hop security measure, wherein a user's credentials cannot be passed across more than one computer in a Windows network. Given that Excel Online used with SharePoint Server is a multi-tiered system, special authentication methods are required for Excel Online to retrieve data on behalf of the end-user.
  
    
    
The authentication method to choose depends on various factors as outlined in the following table. Choose the one that best suits your scenario.
  
    
    

**Comparison of authentication methods**


|****Authentication method****|**Kerberos delegation**|**Secure Store**|**Effective User Name**|
|:-----|:-----|:-----|:-----|
|**Description** <br/> |Using Kerberos constrained delegation, the workbook viewer's Windows credentials are sent to the data source directly.  <br/> |Using the Secure Store Service, the viewer's Windows credentials are mapped to another set of credentials specified in a Secure Store target application.  <br/> |Using the EffectiveUserName Global Setting, the user's domain user name is passed to Analysis Services data sources.  <br/> |
|**Data connection credentials** <br/> |The Windows credentials of the workbook viewer.  <br/> |The credentials specified in the Secure Store target application.  <br/> |The credentials of the Office Online Server process identity.  <br/> |
|**Advantages** <br/> | The Kerberos protocol is an industry standard in credentials management. <br/>  Kerberos ties into the existing Active Directory infrastructure. <br/>  Kerberos delegation permits auditing of individual accesses to a data source. <br/>  Given that the workbook viewer's identity is known, workbook creators can embed personalized database queries into workbooks. <br/> | The Secure Store Service is part of SharePoint Server and is easier to configure than Kerberos. <br/>  Mappings are flexible: a user can be mapped either 1-to-1 or many-to-1. <br/>  Non-Windows credentials can be used to connect to data sources that do not accept Windows credentials. <br/>  Mappings created for Excel Online can be re-used by other business intelligence applications such as Visio Services. <br/> | Per-user data security without the need to configure Kerberos delegation. <br/>  Minimal configuration and administrative overhead. <br/> |
|**Drawbacks** <br/> | Additional administrative effort required to configure SharePoint Server and Excel Online. <br/> | Establishing and managing mapping tables requires some administrative overhead. <br/>  Secure Store permits limited auditing. In the many-to-1 scenario, individual incoming users are mapped into the same credentials through a target application, effectively blending them into one user. <br/> | Only works with Analysis Services data sources. <br/> |
|**For the authentication operation to succeed …** <br/> | Kerberos delegation must be set up on the Office Online Server. <br/> | The Secure Store Service must be provisioned and configured on the SharePoint Server farm. It must also contain appropriate mapping information for a particular incoming user. Additionally the mapping information may need to be updated periodically to reflect password changes on the mapped account. <br/> | The **EffectiveUserName** option must be enabled in Office Online Server. <br/>  The user must be a member of the appropriate Analysis Services role. <br/> |
   

#### Kerberos delegation

Choose Kerberos delegation for secure and fast authentication to enterprise-scale relational data sources that support Windows authentication. If you plan to configure Kerberos constrained delegation, the following requirements are specific to using Kerberos constrained delegation with Excel Online in Office Online Server:
  
    
    

- The Claims to Windows Token Service must be running on each server in the Office Online Server farm and set to run as Local System.
    
  
- Each server in the Office Online Server farm must be allowed to delegate to each back-end data source as shown in the Active Directory Domain Services delegation list.
    
  
- The c2wtshost.exe.config file (located at \\Program Files\\Windows Identity Foundation\\v3.5) must be updated and the comment tags removed from  _NT AUTHORITY\\Network Service_ allowedCallers list:
<allowedCallers>
      <clear/>
      <add value="NT AUTHORITY\\Network Service" />
      <!-- <add value="NT AUTHORITY\\Local Service" /> -->
      <!-- <add value="NT AUTHORITY\\System" /> -->
      <!-- <add value="NT AUTHORITY\\Authenticated Users" /> -->
    </allowedCallers>


#### Secure Store

Choose  [Secure Store](/previous-versions/office/sharepoint-server-2010/ee806889(v=office.14)) for authentication to enterprise-scale relational data sources that may or may not support Windows Authentication. Secure Store is also useful in scenarios in which you want to control user credential mappings.
  
    
    
For information about using Secure Store with Excel Online, see:
  
    
    

-  [Configure Excel Online data refresh by using embedded data connections in Office Online Server](configure-excel-online-data-refresh-by-using-embedded-data-connections-in-office.md)
    
  
-  [Configure Excel Online data refresh by using external data connections in Office Online Server](configure-excel-online-data-refresh-by-using-external-data-connections-in-office.md)
    
  

### SQL Server Authentication

SQL Server Authentication requires that Excel Online present a SQL Server user name and password to a SQL Server data source to authenticate. Excel Online passes the connection string to the data source. The connection string must contain the user name and password.
  
    
    
If the user name and password are stored in a Secure Store target application (recommended for best security), then Excel Online will impersonate the Office Online Server network service account and when the connection is made, the SQL credentials are set as properties of the connection.
  
    
    

### Authentication against OLEDB/ODBC data sources

Authentication to third party data sources typically requires that Excel Online present a user name and password to a data source.
  
    
    
If the user name and password are stored in the workbook or in the ODC file, then Excel Online impersonates a Windows identity dependent on which option has been selected for **Excel Services authentication settings**, either in the workbook or in the ODC file.
  
    
    
If the user name and password are stored in a Secure Store target application (recommended for best security), then Excel Online impersonates the Office Online Server network service account and when the connection is made, the SQL credentials are set as properties of the connection.
  
    
    

## Data refresh in Excel Online

Excel Online supports refreshing workbooks connected to one or more of the following data sources:
  
    
    

- SQL Server
    
  
- SQL Server Analysis Services (SSAS)
    
  

> [!NOTE]
> If the data source that you plan to connect to is not in the list above, you can add support for it by creating a Custom Data Provider. This technology enables you to wrap your existing data sources into one that Excel Online can consume. 
  
    
    

External data refresh is the result of the following set of steps through Excel Online.
  
    
    

1. **Creating a workbook:** A workbook author uploads a data-connected workbook to SharePoint Server.
    
  
2. **Triggering Refresh:** The workbook viewer triggers refresh on a data-connected workbook.
    
  
3. **Data Connections:** Excel Online retrieves data connection information for each external data source in the workbook.
    
  
4. **Trusted Data Providers:** Excel Online checks to see if there is a trusted data provider it can use to retrieve data.
    
  
5. **Authentication:** Excel Online authenticates into the data source and retrieves the requested data on behalf of the workbook viewer.
    
  
6. **Workbook Refresh:** Excel Online updates the workbook based on the data source data and returns it to the viewer.
    
  
Refresh can be triggered in one of following ways from within the browser:
  
    
    

- The end-user opens the workbook (if the workbook is configured to refresh on open).
    
  
- The end-user clicks on the refresh button on an already open workbook.
    
  
If there are no previously cached versions of this workbook, any of these actions will trigger a refresh and update the workbook.
  
    
    

## See also


#### 


  
    
    
 [Configure Analysis Services and Kerberos Constrained Delegation (KCD)](/sql/analysis-services/instances/install-windows/configure-analysis-services-and-kerberos-constrained-delegation-kcd)