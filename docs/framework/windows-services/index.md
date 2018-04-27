---
title: 開發 Windows 服務應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cc01c836daa73b1a39ceab0b523791b6a520dc70
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="developing-windows-service-applications"></a>開發 Windows 服務應用程式
使用 Microsoft Visual Studio 或 Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK，您可以輕鬆地建立服務所建立的應用程式，安裝為服務。 這種類型的應用程式稱為 Windows 服務。 透過架構功能，您可以建立服務、 加以安裝，以及啟動、 停止及控制它們的行為。  
  
> [!WARNING]
>  C + + 的 Windows 服務範本未包含在 Visual Studio 2010。 若要建立 Windows 服務，您可以在 Visual C# 或 Visual Basic，可以與視需要現有的 c + + 程式碼交互操作，在 managed 程式碼建立服務，或您也可以使用原生 c + + 中建立 Windows 服務[ATL 專案精靈](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>本節內容  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 概略說明 Windows 服務應用程式、 服務和服務應用程式有何不同於其他常見的專案類型的存留期。  
  
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 提供 Visual Basic 和 Visual C# 中建立服務的範例。  
  
 [服務應用程式的程式設計架構](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 說明在服務程式設計中使用的語言項目。  
  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 說明建立和設定 Windows 服務使用 Windows 服務專案範本的程序。  
  
## <a name="related-sections"></a>相關章節  
 <xref:System.ServiceProcess.ServiceBase>  
 描述主要功能<xref:System.ServiceProcess.ServiceBase>類別，用來建立服務。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 說明的功能<xref:System.ServiceProcess.ServiceProcessInstaller>類別，可搭配沿著<xref:System.ServiceProcess.ServiceInstaller>安裝和解除安裝您的服務類別。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 說明的功能<xref:System.ServiceProcess.ServiceInstaller>類別，可搭配沿著<xref:System.ServiceProcess.ServiceProcessInstaller>安裝和解除安裝您的服務類別。  
  
 [NIB 從範本建立專案](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 描述專案中這一章，以及如何選擇兩者之間使用的類型。
