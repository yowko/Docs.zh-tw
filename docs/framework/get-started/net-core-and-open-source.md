---
title: .NET 的核心和開放原始碼
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 4d9d42304c58c631020d8b12bec5c038bc0c07ab
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888237"
---
# <a name="net-core-and-open-source"></a>.NET Core 與開放原始碼

本文簡要概述了什麼是 .NET Core,並展示了如何找到更多資訊。 要尋找 .NET Core 的完整文件清單,請造[訪 .NET 核心指南](../../core/index.yml)。

## <a name="what-is-net-core"></a>什麼是 .NET Core？  

.NET Core 是 .NET 標準的通用、模組化、跨平臺和開源實現。 它包含許多與 .NET 框架相同的 API(但 .NET Core 是一個較小的集),並且包括支援各種作業系統和晶片目標的運行時、框架、編譯器和工具元件。 .NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。 它可用於設備、雲和嵌入式/IoT 方案。  
  
要開始與 .NET Core, 訪問 .NET 教程[Hello World 在 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
.NET 核心的主要特點是:
  
- **跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。 它目前支援三個主要作業系統 (OS):Windows、Linux 和 macOS。 您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。 若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。
  
- **開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。 作為一個開源專案,.NET Core 促進更加透明的開發過程和積極和參與的社區。  
  
- **彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。 在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。 使用自包含部署時,用於構建應用程式的.NET Core版本也會與應用和第三方依賴項一起部署,並可以與其他版本並行運行。 有關詳細資訊,請參閱[.NET 核心應用程式部署](../../core/deploying/index.md)。

- **模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。 .NET Core 不是包含大多數核心功能的大型程式集,而是作為更小、以功能為中心的包提供。 這種模組化為我們提供了一個更靈活的開發模式,並允許您優化你的應用,只包括您需要的 NuGet 包。 應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。  
  
## <a name="the-net-core-platform"></a>.NET 核心平臺
  
.NET Core 平臺由多個元件組成,包括託管編譯器、運行時、基類庫和大量應用程式模型,如ASP.NET Core。 您可以瞭解有關不同元件的更多內容,並透過存取以下[GitHub](https://github.com/)儲存函式庫進行參與:  
  
- [.NET 核心首頁](https://github.com/dotnet/core)  
  
- [執行時 - .NET 核心平台與執行時](https://github.com/dotnet/runtime)  
  
- [CLI - .NET Core 命令列工具](https://github.com/dotnet/cli)  
  
- [Roslyn - .NET 編譯器平台](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>另請參閱

- [.NET 教程 - 10 分鐘內的"你好世界"](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [.NET Core 指南](../../core/index.yml)
- [ASP.NET核心文件](/aspnet/core/)
