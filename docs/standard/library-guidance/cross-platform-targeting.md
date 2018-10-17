---
title: 跨平台為目標
description: 建立跨平台.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374884"
---
# <a name="cross-platform-targeting"></a>跨平台為目標

新式的.NET 支援多個作業系統和裝置。 務必.NET 開放原始碼程式庫，才支援多個開發人員盡可能的情況下，不論它們要建置的 ASP.NET 網站裝載於 Azure 或在 Unity 中的進行.NET 遊戲。

## <a name="net-standard"></a>.NET Standard

.NET standard 是跨平台支援加入.NET 程式庫的最佳方式。 [.NET standard](../net-standard.md)是可在所有.NET 實作的.NET Api 的規格。 目標.NET Standard，可讓您產生限制為使用中指定版本的.NET Standard，這表示它是使用會實作.NET Standard 版本的所有平台 Api 的程式庫。

![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

目標.NET Standard，並成功地編譯您的專案，並不保證程式庫會在所有平台上順利執行：

1. 其他平台上，將會失敗的平台專屬的 Api。 例如，<xref:Microsoft.Win32.Registry?displayProperty=nameWithType>會在 Windows 上成功，則擲回<xref:System.PlatformNotSupportedException>使用任何其他作業系統上時。
2. Api 的行為。 例如，反映 Api 時，有不同的效能特性應用程式在 iOS 或 UWP 上使用預先 just-in-time 編譯。

> [!TIP]
> .NET 小組[提供一個 Roslyn 分析器](../analyzers/api-analyzer.md)可協助您找出可能的問題。

**請勿 ✔️**開頭包括`netstandard2.0`目標。

> 一般用途的文件庫應該不需要外部.NET Standard 2.0 的 Api。 .NET standard 2.0 支援所有新型平台，而且是建議用來支援多個目標平台。

**請避免 ❌**包括`netstandard1.x`目標。

> .NET standard 1.x 分散會建立大型的套件相依性圖形，並導致下載的封裝時建置的開發人員的 NuGet 套件的細微設定。 新式的.NET 平台，包括.NET Framework 4.6.1、 UWP 和 Xamarin，所有支援.NET Standard 2.0。 您只應該以目標為.NET Standard 1.x，如果您特別需要較舊的平台為目標。

**請勿 ✔️**包括`netstandard2.0`如果您需要為目標`netstandard1.x`目標。

> 將所有的平台支援.NET Standard 2.0`netstandard2.0`為目標，並受益於具有較小的套件圖形，而較舊的平台仍會運作，並改為使用`netstandard1.x`目標。

**不這麼做 ❌**包含.NET Standard 的目標，如果程式庫依賴平台專屬的應用程式模型。

> 例如，UWP 控制項工具組程式庫才可以使用 UWP 應用程式模型而定。 應用程式模型特定的 Api 不是在.NET Standard 中，您可以使用的狀態。

## <a name="multi-targeting"></a>多目標

有時候您需要存取特定架構的 Api，從您的程式庫。 呼叫架構特定 Api 的最佳方式使用多目標，建置您的專案提供了許多[目標的.NET frameworks](../frameworks.md)而不是其中一個。

若要防護您的取用者不必建立個別的架構，您應該盡量有.NET Standard 的輸出，再加上一個或多個架構特定輸出。 使用多目標會將所有組件封裝內單一 NuGet 套件中。 取用者可以參考相同的套件，NuGet 會挑選適當的實作。 後援文件庫會使用所有位置，其中您的 NuGet 套件提供的架構特定實作的案例除外，就會作為您的.NET Standard 程式庫。 多目標可讓您在程式碼中使用條件式編譯，並呼叫特定架構的 Api。

![具有多個組件的 NuGet 封裝](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "具有多個組件的 NuGet 封裝")

**請考慮 ✔️**目標除了.NET Standard 的.NET 實作。

> 目標為.NET 實作，可讓您呼叫外部.NET Standard 平台專屬 Api。
>
> 當您執行此動作不捨棄.NET Standard 的支援。 相反地，從實作擲回，並提供功能的 Api。 如此一來，您的程式庫可用於任何地方，並支援執行階段啟動的功能。

**請避免 ❌**使用多目標的.NET Standard 與您的程式碼是否適用於所有目標。

> NuGet 會自動使用.NET Standard 的組件。 目標為個別的.NET 實作會增加`*.nupkg`大小沒有任何好處。

**請考慮 ✔️**新增的目標`net461`當您提供`netstandard2.0`目標。 

> 使用.NET Standard 2.0，從.NET Framework 有一些.NET Framework 4.7.2 中已解決的問題。 您可以改善仍在使用.NET Framework 4.6.1-藉由提供他們建置適用於.NET Framework 4.6.1 的二進位檔 4.7.1 的開發人員的體驗。

**請勿 ✔️**散發您的程式庫使用 NuGet 套件。

> NuGet 會選取最佳的目標，開發人員，並避免它們需要挑選適當的實作。

**請勿 ✔️**使用專案檔的`TargetFrameworks`多目標時的屬性。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**請考慮 ✔️**使用[MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras)時多目標的 UWP 和 Xamarin，它可大幅簡化您的專案檔。

## <a name="older-targets"></a>較舊的目標

.NET 支援的.NET framework 是長時間不支援，以及不再常用的平台的目標版本。 雖然沒有在進行您的程式庫工作上需要解決遺失的 Api 越好，許多的目標可以新增重大額外負荷的值。 我們相信特定架構已不再值得目標，考量其觸達和限制。

**不這麼做 ❌**包含可攜式類別庫 (PCL) 目標。 例如，`portable-net45+win8+wpa81+wp8`。

> .NET standard 是現代化的方式，以支援跨平台.NET 程式庫，並取代 Pcl。

**不這麼做 ❌**包含不受支援的.NET 平台的目標。 例如，`SL4`、`WP`。

>[!div class="step-by-step"]
[上一頁](./get-started.md)
[下一頁](./strong-naming.md)
