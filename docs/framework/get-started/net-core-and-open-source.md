---
title: ".NET 的核心和開放原始碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: db4689ee58b48fad2e3696e5e64aa187710f4868
ms.contentlocale: zh-tw
ms.lasthandoff: 08/05/2017

---
# <a name="net-core-and-open-source"></a>.NET 的核心和開放原始碼
本主題概要說明什麼是 .NET Core，並說明如何尋找更多資訊。 若要尋找 .NET Core 主題的完整清單，請瀏覽 [.NET Core 指南](../../core/index.md)。
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>什麼是 .NET Core？  
 .NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作。 它包含與 .NET Framework 相同的許多 API (但 .NET Core 是較小的集合)，並包含支援各種作業系統和晶片目標的執行階段、架構、編譯器和工具元件。 .NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。 它可用於裝置、雲端和內嵌/IoT 情節。  
  
 若要開始使用 .NET Core，請前往 [.NET Core 首頁](https://www.microsoft.com/net/core)。  
  
 .NET Core 的主要特性如下：  
  
-   **跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。 它目前支援三個主要作業系統 (OS)：Windows、Linux 和 macOS。 您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。 若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。
  
-   **開放原始碼︰**.NET Core 是 [.NET Foundation](http://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。  以 .NET Core 作為開放原始碼專案可促進更透明的開發程序，以及主動參與的社群。  
  
-   **彈性的部署︰**部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。 在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。  在獨立部署中，用來建置應用程式的 .NET Core 版本也會隨應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。    如需詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。

-   **模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。 不同於大型組件會包含大部分的核心功能，.NET Core 著眼於特定功能，會以較小型的套件提供。 這讓我們有更靈活的開發模型，並可讓您最佳化應用程式，只包含所需的 NuGet 套件。 應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。  
  
## <a name="the-net-core-platform"></a>.NET Core 平台  
 .NET Core 平台是由幾個元件所組成，其中包含 Managed 編譯器、執行階段、基底類別庫，以及許多應用程式模型 (例如 ASP.NET Core)。 您可以前往下列 [GitHub](https://github.com/) 存放庫，以深入了解並使用不同的元件：  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX - .NET Core 基本程式庫](https://github.com/dotnet/corefx)  
  
-   [CoreCLR - .NET Core 執行階段](https://github.com/dotnet/coreclr)  
  
-   [CLI - .NET Core 命令列工具](https://github.com/dotnet/cli)  
  
-   [Roslyn - .NET 編譯器平台](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>另請參閱  
 [.NET Core 首頁](https://www.microsoft.com/net/core)   
 [.NET Core 指南](../../core/index.md)   
 [ASP.NET Core 文件](/aspnet/core/)

