---
title: .NET 的核心和開放原始碼
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: b5aa42d0460d743bffe8f17a2603773c03c09ce0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181615"
---
# <a name="net-core-and-open-source"></a>.NET 核心和開源

本文簡要概述了什麼是 .NET Core，並展示了如何找到更多資訊。 要查找 .NET Core 的完整文檔清單，請訪問[.NET 核心指南](../../core/index.md)。

## <a name="what-is-net-core"></a>什麼是 .NET Core？  

.NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作。 它包含與 .NET Framework 相同的許多 API (但 .NET Core 是較小的集合)，並包含支援各種作業系統和晶片目標的執行階段、架構、編譯器和工具元件。 .NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。 它可用於裝置、雲端和內嵌/IoT 情節。  
  
要開始與 .NET Core， 訪問 .NET 教程[Hello World 在 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
.NET 核心的主要特點是：
  
- **跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。 它目前支援三個主要作業系統 (OS)：Windows、Linux 和 macOS。 您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。 若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。
  
- **開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。  以 .NET Core 作為開放原始碼專案可促進更透明的開發程序，以及主動參與的社群。  
  
- **彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。 在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。  在獨立部署中，用來建置應用程式的 .NET Core 版本也會隨應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。    有關詳細資訊，請參閱[.NET 核心應用程式部署](../../core/deploying/index.md)。

- **模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。 不同於大型組件會包含大部分的核心功能，.NET Core 著眼於特定功能，會以較小型的套件提供。 這讓我們有更靈活的開發模型，並可讓您最佳化應用程式，只包含所需的 NuGet 套件。 應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。  
  
## <a name="the-net-core-platform"></a>.NET 核心平臺
  
.NET Core 平臺由多個元件組成，包括託管編譯器、運行時、基類庫和大量應用程式模型，如ASP.NET Core。 您可以瞭解有關不同元件的更多內容，並通過訪問以下[GitHub](https://github.com/)存儲庫進行參與：  
  
- [.NET 核心主頁](https://github.com/dotnet/core)  
  
- [運行時 - .NET 核心平臺和運行時](https://github.com/dotnet/runtime)  
  
- [CLI - .NET Core 命令列工具](https://github.com/dotnet/cli)  
  
- [Roslyn - .NET 編譯器平台](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>另請參閱

- [.NET 教程 - 10 分鐘內的"你好世界"](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [.NET 核心指南](../../core/index.md)
- [ASP.NET核心文檔](/aspnet/core/)
