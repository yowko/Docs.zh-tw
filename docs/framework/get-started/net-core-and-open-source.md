---
title: .NET 的核心和開放原始碼
description: 閱讀有關 .NET Core 的總覽，這是 .NET Standard 的一般用途、模組化、跨平臺和開放原始碼的執行。
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622753"
---
# <a name="net-core-and-open-source"></a>.NET Core 與開放原始碼

本文簡要介紹 .NET Core 的功能，並說明您可以如何尋找更多資訊。 若要尋找 .NET Core 檔的完整清單，請造訪[.Net core 指南](../../core/index.yml)。

## <a name="what-is-net-core"></a>什麼是 .NET Core？  

.NET Core 是 .NET Standard 的一般用途、模組化、跨平臺和開放原始碼的執行。 其中包含許多與 .NET Framework 相同的 Api （但 .NET Core 是較小的集合），並包含支援各種作業系統和晶片目標的執行時間、架構、編譯器和工具元件。 .NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。 它可用於裝置、雲端和內嵌/IoT 案例。  
  
若要開始使用 .NET Core，請[在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)流覽 .net 教學課程 Hello World。  
  
.NET Core 的主要特性如下：
  
- **跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。 它目前支援三個主要作業系統（OS）： Windows、Linux 和 macOS。 您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。 若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。
  
- **開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。 .NET Core 是開放原始碼專案，可提升更透明的開發流程，以及使用中和已參與的社區。  
  
- **彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。 在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。 透過獨立部署，用來建立應用程式的 .NET Core 版本也會隨您的應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。 如需詳細資訊，請參閱[.Net Core 應用程式部署](../../core/deploying/index.md)。

- **模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。 .NET Core 是以較小的功能中心套件提供，而不是一個包含大部分核心功能的大型元件。 此模組化可為我們提供更靈活的開發模型，並可讓您將應用程式優化，使其只包含所需的 NuGet 套件。 應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。  
  
## <a name="the-net-core-platform"></a>.NET Core 平臺
  
.NET Core 平臺是由數個元件所組成，包括 managed 編譯器、執行時間、基類庫，以及許多應用程式模型（例如 ASP.NET Core）。 您可以造訪下列[GitHub](https://github.com/)存放庫，以深入瞭解不同的元件並取得參與：  
  
- [.NET Core 首頁](https://github.com/dotnet/core)  
  
- [執行時間-.NET Core 平臺和執行時間](https://github.com/dotnet/runtime)  
  
- [CLI - .NET Core 命令列工具](https://github.com/dotnet/cli)  
  
- [Roslyn - .NET 編譯器平台](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>另請參閱

- [.NET 教學課程-10 分鐘內 Hello World](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [.NET Core 指南](../../core/index.yml)
- [ASP.NET Core 檔](/aspnet/core/)
