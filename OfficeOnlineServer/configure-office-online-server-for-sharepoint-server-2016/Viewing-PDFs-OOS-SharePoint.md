---
title: Viewing PDF files in Office Online Server from SharePoint Server
description: Best practices for viewing PDF files hosted in SharePoint Server with Office Online Server (the next version of Office Web Apps Server).
ms.author: alumanos
author: alumanos
manager: 
ms.date: 05/04/2023
ms.audience: ITPro
ms.topic: article
ms.service: office-online-server
ms.assetid: 
---


# Viewing PDF files in Office Online Server from SharePoint Server


 **Summary:** Best practices for viewing PDF files hosted in SharePoint Server with Office Online Server (the next version of Office Web Apps Server).
  
    
  

 **Audience**: IT Professionals
  


For the best experience viewing PDF files from SharePoint Server, we recommend leveraging modern browser native PDF viewer (such as the PDF viewer built into Microsoft Edge). While Office Online Server can be used with SharePoint Server as a simple browser-based PDF reader, Edge’s native PDF Viewer is more efficient and will have fewer issues working with PDF files. 

Microsoft and Adobe have announced a partnership to further improve PDF file viewing capabilities in the Microsoft Edge browser. We highly recommend leveraging these features in Microsoft Edge rather than relying on Office Online Server to view PDF files in browser.

  
  -  [Microsoft Edge and Adobe partner to improve the PDF experience](https://techcommunity.microsoft.com/t5/microsoft-edge-insider/microsoft-edge-and-adobe-partner-to-improve-the-pdf-experience/ba-p/3733481)
    
  

## Suppress SharePoint Server hosted PDFs from opening in Office Online Server
<a name="Suppress"> </a>

By running the New-SPWOPISuppressionSetting command in the SharePoint Management Shell, *.PDF files will open using the local operating system default PDF application.

  ```
  
New-SPWOPISuppressionSetting -Extension “PDF” -Action “imagepreview”
New-SPWOPISuppressionSetting -Extension “PDF” -Action “interactivepreview”
New-SPWOPISuppressionSetting -Extension “PDF” -Action “embedview"
New-SPWOPISuppressionSetting -Extension “PDF” -Action “view"
  
  ```

Note: This information is specific to On-Premises SharePoint Server products and does not apply to SharePoint Online or Office for the Web in Microsoft 365 Cloud Subscriptions.
