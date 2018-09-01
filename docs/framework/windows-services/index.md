---
title: 開發 Windows 服務應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: 2c7fb148b96d5ff9804bcb0bb7c842c475c0f117
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385977"
---
# <a name="developing-windows-service-applications"></a>開發 Windows 服務應用程式
您可以使用 Microsoft Visual Studio 或 Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK，藉由建立要安裝為服務的應用程式，以輕鬆地建立服務。 這種類型的應用程式稱為 Windows 服務。 您可以使用架構功能，以建立服務、安裝服務，以及啟動、停止及控制服務的行為。  
  
> [!WARNING]
>  Visual Studio 2010 並未隨附適用於 C++ 的 Windows 服務範本。 若要建立 Windows 服務，可以在 Visual C# 或 Visual Basic 的受控程式碼中建立服務，其可視需要與現有的 C++ 程式碼交互操作，或者，可以使用 [ATL 專案精靈](/cpp/atl/reference/atl-project-wizard)，在原生 C++ 中建立 Windows 服務。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 提供 Windows 服務應用程式、服務存留期，以及服務應用程式與其他常見專案類型有何不同的概觀。  
  
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 提供在 Visual Basic 和 Visual C# 中建立服務的範例。  
  
 [服務應用程式的程式設計架構](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 說明服務程式設計中所使用的語言元素。  
  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 描述使用 Windows 服務專案範本來建立和設定 Windows 服務的程序。  
  
## <a name="related-sections"></a>相關章節  
 <xref:System.ServiceProcess.ServiceBase>  
 描述用來建立服務的 <xref:System.ServiceProcess.ServiceBase> 類別主要功能。  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 描述 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceInstaller> 類別搭配使用來安裝和解除安裝您的服務。  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 描述 <xref:System.ServiceProcess.ServiceInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別搭配使用來安裝和解除安裝您的服務。  
  
 [NIB 根據範本建立專案](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) \(機器翻譯\)  
 描述本章所使用的專案類型，以及如何在兩者之間進行選擇。
