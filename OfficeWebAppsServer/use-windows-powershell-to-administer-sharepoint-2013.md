---
title: Use Windows PowerShell to administer SharePoint 2013
TOCTitle: Use Windows PowerShell to administer SharePoint 2013
ms:assetid: ae4901b4-505a-42a9-b8d4-fca778abc12e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ee806878(v=office.15)
ms:contentKeyID: 48409073
ms.date: 10/13/2017
mtps_version: v=office.15
---

# Use Windows PowerShell to administer SharePoint 2013

 

_**Applies to:** SharePoint Foundation 2013, SharePoint Server 2013 Enterprise, SharePoint Server 2013 Standard_


**Summary:**Learn about basic Windows PowerShell cmdlets and concepts and how to use Windows PowerShell with SharePoint 2013.

In this article:

  - Overview

  - Accessing Windows PowerShell for SharePoint 2013Products

  - Permissions

  - Scripts and execution policies

  - Learning Windows PowerShell

## Overview

Windows PowerShell is a command-line shell and scripting language that provides an administrator full access to applicable application programming interfaces (APIs). Administrators can interact directly with SharePoint 2013 to manipulate web applications, site collections, sites, lists and much more. In addition, an administrator can script cmdlets (pronounced "command-lets").

Windows PowerShell 3.0 is a prerequisite for installing SharePoint 2013. It will be installed when you run the Microsoft SharePoint Products Preparation Tool if it is not already installed. By default, Windows PowerShell is located at the following path: \<%SystemRoot%\>\\System32\\WindowsPowerShell\\v1.0\\PowerShell.exe.

For a list of new features for Windows PowerShell 3.0, see [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/p/?linkid=272782)

For an interactive tool and guide that helps you learn Windows PowerShell syntax, see [Windows PowerShell Command Builder Tool](https://go.microsoft.com/fwlink/p/?linkid=229854) and [Getting Started Guide](http://www.microsoft.com/download/en/details.aspx?id=27588).

We recommend that you use Windows PowerShell when performing command-line administrative tasks. The Stsadm command-line tool has been deprecated, but is included to support compatibility with previous product versions.

## Accessing Windows PowerShell for SharePoint 2013

After you install SharePoint 2013, applicable Windows PowerShell cmdlets are available in the SharePoint 2013 Management Shell. You can manage most aspects of SharePoint 2013 in the SharePoint Management Shell. You can create new site collections, web applications, user accounts, service applications, proxies, and more. Commands that you type in the SharePoint Management Shell return SharePoint objects that are based on the Microsoft .NET Framework. You can apply these objects as input to subsequent commands or store the objects in local variables for later use.

With the SharePoint Management Shell, you do not have to register the snap-in that contains the cmdlets. Registration of the Microsoft.SharePoint.PowerShell.dll module for SharePoint 2013 cmdlets is automatic, as a result of the `Add-PSSnapin Microsoft.SharePoint.PowerShell` line in the SharePoint.ps1 file that is located in *%CommonProgramFiles%*\\Microsoft Shared\\Web Server Extensions\\15\\Config\\PowerShell\\Registration. To use the Windows PowerShell console, you must register this snap-in manually.

Whether you use the SharePoint Management Shell or the Windows PowerShell console, you can also load additional snap-ins. For more information, see [Customizing Profiles](https://go.microsoft.com/fwlink/p/?linkid=183166).

**To access the SharePoint Management Shell**

1.  Start the SharePoint Management Shell.
    
      - For Windows Server 2008 R2:
        
          - Click **Start**, click **Microsoft SharePoint 2013 Products**, and then click **SharePoint Management Shell**.
    
      - For Windows Server 2012:
        
          - On the **Start** screen, click **SharePoint Management Shell**.
            
            If **SharePoint Management Shell** is not on the **Start** screen:
        
        <!-- end list -->
        
          - Right-click **Computer**, click **All apps**, and then click **SharePoint Management Shell**.
    
    For more information about how to interact with Windows Server 2012, see [Common Management Tasks and Navigation in Windows Server 2012](https://technet.microsoft.com/en-us/library/hh831491.aspx).


> [!NOTE]
> The SharePoint 2013 Management Shell and the Windows PowerShell console also differ in the use of the <CODE>ReuseThread</CODE> option, which defines how the threading model is used. The SharePoint 2013 Management Shell's use is defined by this line, <CODE>{Host.Runspace.ThreadOptions = "ReuseThread"}</CODE>, which is in the SharePoint.ps1 file. For more information, see <A href="https://go.microsoft.com/fwlink/p/?linkid=183145">PS Thread Options</A>.



## Permissions

## On-Premises

Before you can use the **Add-SPShellAdmin** cmdlet to grant permissions for users to run SharePoint 2013 cmdlets, verify that you meet all of the following minimum requirements:

  - You must have membership in the **securityadmin** fixed server role on the SQL Server instance

  - You must have membership in the **db\_owner** fixed database role on all databases that are to be updated.

  - You must be a member of the Administrators group on the server on which you are running the Windows PowerShell cmdlet.


> [!NOTE]
> If these permissions are not satisfied, contact your Setup administrator or SQL Server administrator to request these permissions.



For additional information about Windows PowerShell permissions, see Permissions and [Add-SPShellAdmin](https://technet.microsoft.com/en-us/library/ff607596\(v=office.15\))

If you do not have membership in the **SharePoint\_Shell\_Access** role or **WSS\_Admin\_WPG** local group, use the **Add-SPShellAdmin** cmdlet to add the **WSS\_Admin\_WPG** group in all front-end web servers in the SharePoint farm and the **SharePoint\_Shell\_Access** role. If the SQL Server database does not have a **SharePoint\_Shell\_Access** role, the role is automatically created when you run the **Add-SPShellAdmin** cmdlet. After you run the **Add-SPShellAdmin** cmdlet, users can run SharePoint Windows PowerShell cmdlets in a multiple-server farm environment.


> [!NOTE]
> When you install SharePoint 2013, the user account from which you run the installation is granted the appropriate permissions to run Windows PowerShell cmdlets. If any users have not been added to run a Windows PowerShell cmdlet, you can use the <STRONG>Add-SPShellAdmin</STRONG> cmdlet to add them.



You must run the **Add-SPShellAdmin** cmdlet for all databases to which you want to grant access. If no database is specified, the farm configuration database is used. If you do specify a database, the farm content database will be included in addition to the farm configuration database that you specify.

To see a list of all of the **SPShellAdmin** cmdlets, from a Windows PowerShell command prompt, type `Get-Command -Noun SPShellAdmin`.

## SharePoint Online

Verify that you have the following administrative permissions:

  - You must be assigned the global administrator role on the SharePoint Online site on which you are running the Windows PowerShell cmdlet. For more information, see [Default administrative roles and user groups](https://go.microsoft.com/fwlink/p/?linkid=242451).
    

    > [!IMPORTANT]
    > You can use a specific group of Windows PowerShell with SharePoint Online. For more information, see <A href="https://technet.microsoft.com/en-us/library/fp161362(v=office.15)">Office 365 PowerShell for SharePoint Online</A>.



## Scripts and execution policies

Although you can use Windows PowerShell to perform a single administrative task, you can also use a script to automate a series of tasks. A script is a text file that contains one or more Windows PowerShell commands. Windows PowerShell scripts have a .ps1 file name extension.

To run scripts, the minimum required execution policy for SharePoint 2013 is RemoteSigned, although the default policy for Windows PowerShell is Restricted. If the policy is left as Restricted, the SharePoint 2013 Management Shell will change the policy for Windows PowerShell to RemoteSigned. This means that you must select **Run as administrator** to start the SharePoint 2013 Management Shell with elevated administrative permission. This change will apply to all Windows PowerShell sessions. For more information, see [ExecutionPolicy Enumeration](https://go.microsoft.com/fwlink/p/?linkid=242452).

For additional information about scripts and execution policies, see [about\_scripts](https://go.microsoft.com/fwlink/p/?linkid=144310) and [about\_Execution\_Policies](https://go.microsoft.com/fwlink/p/?linkid=193050) respectively.

## Learning Windows PowerShell

There are several Windows PowerShell learning resources for SharePoint IT professionals.

**TechNet Scripting Center**

The TechNet Scripting Center includes many resources to help you learn the basics about Windows PowerShell. It also contains script repositories with samples of scripts that are typically used with various Microsoft products. The following table shows the main learning resources.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Page</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=187813">Windows PowerShell Documentation on TechNet</a></p></td>
<td><p>This section of the TechNet Library contains web copies of the core Windows PowerShell Get-Help topics. The section also has web copies of the Windows PowerShell Getting Started document, the PowerShell.exe help, and a Windows PowerShell primer.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=187815">Scripting With Windows PowerShell</a></p></td>
<td><p>The home page for Windows PowerShell scripting learning resources.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=187817">Windows PowerShell Owner's Manual</a></p></td>
<td><p>web-based guide for getting started with Windows PowerShell.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187819">Windows PowerShell Quick Reference</a></p></td>
<td><p>Downloadable copy of the Quick Reference document that is installed with Windows PowerShell.</p></td>
</tr>
</tbody>
</table>


As you read these resources, consider that the following concepts and cmdlets are useful ones to learn before you use Windows PowerShell for SharePoint 2013:

  - [Get-Command](https://go.microsoft.com/fwlink/p/?linkid=171069)

  - [Get-Member](https://go.microsoft.com/fwlink/p/?linkid=171070)

  - [Get-Help](https://go.microsoft.com/fwlink/p/?linkid=171068)

  - [Aliasing](https://go.microsoft.com/fwlink/p/?linkid=113207)

  - [Piping and the Pipeline in Windows PowerShell](https://go.microsoft.com/fwlink/p/?linkid=187808)

  - [Cmdlet Parameter Sets](https://go.microsoft.com/fwlink/p/?linkid=187810)

  - [Foreach-Object](https://go.microsoft.com/fwlink/p/?linkid=187812)

  - [Where-Object](https://go.microsoft.com/fwlink/p/?linkid=187811)

