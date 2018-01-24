---
title: ".NET Framework 開發指南"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d7950ae39ada3e1e0e070967f8d578fc3371126
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="net-framework-development-guide"></a>.NET Framework 開發指南
本節說明如何建立、設定、偵錯、保護和部署 .NET Framework 應用程式。 本節也提供有關技術領域的資訊，例如動態程式設計、互通性、擴充性、記憶體管理和執行緒。  
  
## <a name="in-this-section"></a>本節內容  
 [應用程式基本概念](../../docs/standard/application-essentials.md)  
 提供基本應用程式開發工作的相關資訊，例如應用程式定義域和組件的程式設計、使用屬性、格式設定和分析基底類型、使用集合、處理事件和例外狀況、使用檔案和資料流，以及使用泛型。  
  
 [資料與模型化](../../docs/framework/data/index.md)  
 提供如何使用 ADO.NET、Language Integrated Query (LINQ)、WCF 資料服務和 XML 來存取資料的相關資訊。  
  
 [用戶端應用程式](../../docs/framework/develop-client-apps.md)  
 說明如何使用 Windows Presentation Foundation (WPF) 或 Windows Form 建立 Windows 架構應用程式。  
  
 [使用 ASP.NET 的 Web 應用程式](../../docs/framework/develop-web-apps-with-aspnet.md)  
 提供有關使用 ASP.NET，以最少程式碼建置企業級 Web 應用程式之資訊的連結。  
  
 [使用 WCF 以服務為導向的應用程式](../../docs/framework/wcf/index.md)  
 說明如何使用 Windows Communication Foundation (WCF) 建立安全、可靠的服務導向應用程式。  
  
 [使用 Windows Workflow Foundation 建立工作流程](windows-workflow-foundation/index.md)     
 提供使用 Windows Workflow Foundation (WF) 程式撰寫模型、範例和工具的相關資訊。  

 [Windows 服務應用程式](../../docs/framework/windows-services/index.md)  
 說明如何使用 Visual Studio 及 .NET Framework 建立要安裝為服務的應用程式，以及啟動、停止及控制其行為。  
  
 [平行處理和並行機制](../../docs/standard/parallel-processing-and-concurrency.md)  
 提供有關 Managed 執行緒、平行程式設計和非同步程式設計模式的資訊。  
  
 [以 .NET Framework 進行網路程式設計](../../docs/framework/network-programming/index.md)  
 說明可以讓您迅速方便地整合到您應用程式之有層次、可擴充及受管理的網際網路服務實作。  
  
 [設定 .NET Framework 應用程式](configure-apps/index.md)    
 說明如何直接使用組態檔變更設定，而無須重新編譯您的 .NET Framework 應用程式。  
  
 [使用 .NET Native 編譯應用程式](../../docs/framework/net-native/index.md)  
 說明如何使用 [!INCLUDE[net_native](../../includes/net-native-md.md)] 預先編譯技術，建置及部署「Windows 市集」的應用程式。 [!INCLUDE[net_native](../../includes/net-native-md.md)] 會編譯以 Managed 程式碼 (C#) 所撰寫，並以 .NET Framework 做為機器碼的應用程式。  
  
 [安全性](../../docs/standard/security/index.md)  
 提供 .NET Framework 中，可加強應用程式開發安全性的類別及服務的相關資訊。  
  
 [偵錯、追蹤和程式碼剖析](../../docs/framework/debug-trace-profile/index.md)  
 說明如何測試、最佳化及分析 .NET Framework 應用程式與應用程式的環境。 本章節包含可供系統管理員和開發者使用的資訊。  
  
 [進行多平台開發](../../docs/standard/cross-platform/index.md)  
 提供如何使用 .NET Framework ，建置可以讓多種平台與裝置 (例如電話、桌面與 Web) 共用之組件的資訊。  
  
 [部署](../../docs/framework/deployment/index.md)  
 說明如何封裝及散發 .NET Framework 應用程式，同時也加入開發人員與系統管理員適用的部署指南。  
  
 [效能](../../docs/framework/performance/index.md)  
 提供有關快取、延遲初始設定、可靠性和 ETW 事件的資訊。  
  
 <!--zz [Advanced Reading for the .NET Framework](http://msdn.microsoft.com/library/faae8083-fecb-4514-b133-b0a5a32a7c3c)  
 Provides information about advanced development tasks and techniques in the .NET Framework, including extensibility, interoperability, and reflection. Also includes the reference topics for unmanaged APIs that can be used by managed apps, such as runtime hosts, compilers, disassemblers, debuggers, and profilers.  --> 
  
## <a name="reference"></a>參考資料  
 [.NET Framework 類別庫](/dotnet/api/?view=netframework-4.7)  
 為每個包含在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間的類別提供語法、程式碼範例和用法資訊。  
  
## <a name="related-sections"></a>相關章節  
 [快速入門](../../docs/framework/get-started/index.md)  
 提供 .NET Framework 的完整概觀與其他資源的連結。  
  
 [新功能](../../docs/framework/whats-new/index.md)  
 描述最新版 .NET Framework 中重要的新功能與變更。 包含新類型、汰換類型與成員的清單，並提供如何移轉您在舊版 .NET Framework 上之應用程式的指南。  
  
 [工具](../../docs/framework/tools/index.md)  
 說明如何應用 .NET Framework 技術，協助您開發、設定及部署應用程式的工具。  
  
 [.NET Framework 範例](http://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)  
 提供 MSDN 程式碼範例庫中之範例應用程式的連結，以示範 .NET Framework 技術。
