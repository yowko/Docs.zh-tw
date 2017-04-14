---
title: "開發 Windows 服務應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 應用程式, Windows 應用程式"
  - "Service 類別, Windows 服務應用程式"
  - "ServiceInstaller 類別, Windows 服務應用程式"
  - "ServiceProcessInstaller 類別, Windows 服務應用程式"
  - "服務"
  - "Windows NT 服務"
  - "Windows 服務應用程式"
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 18
---
# 開發 Windows 服務應用程式
您可以使用 Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或 Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK，透過建立安裝為服務的應用程式，輕鬆地建立服務。  這種應用程式稱為 Windows 服務。  透過架構功能，您可以建立服務、安裝服務以及啟動、停止和控制它們的行為。  
  
> [!WARNING]
>  C\+\+ 中的 Windows 服務範本在 Visual Studio 2010 不包含。  若要建立 Windows 服務，您可以建立一個服務會在 Visual C\# 中的 Managed 程式碼或 Visual Basic 中，您可以使用 [ATL 專案精靈](../Topic/ATL%20Project%20Wizard.md)，能夠與現有 C\+\+ 程式碼 \(如果需要進行溝通，或者您可以建立在原生 C\+\+ 中的 Windows 服務。  
  
## 在本節中  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 提供 Windows 服務應用程式的概觀，服務的存留期，，以及服務應用程式與其他一般的專案類型而異。  
  
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 提供在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 和 Visual C\# 中建立服務的範例。  
  
 [服務應用程式的程式設計架構](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 說明服務程式設計所使用的語言項目。  
  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 使用 Windows 服務專案範本，描述建立及設定 Windows 服務的處理序。  
  
## 相關章節  
 <xref:System.ServiceProcess.ServiceBase>  
 說明用以建立服務之 <xref:System.ServiceProcess.ServiceBase> 類別的主要功能。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 說明 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別的功能，這個類別是與 <xref:System.ServiceProcess.ServiceInstaller> 類別一起使用，以安裝和解除安裝您的服務。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 說明 <xref:System.ServiceProcess.ServiceInstaller> 類別的功能，這個類別是與 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別一起使用，以安裝和解除安裝您的服務。  
  
 [根據範本建立專案](http://msdn.microsoft.com/zh-tw/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 說明本章所使用的專案類型及如何選擇專案類型。