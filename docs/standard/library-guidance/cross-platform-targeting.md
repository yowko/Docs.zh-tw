---
title: .NET 程式庫的跨平台目標設定
description: 建立跨平台 .NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6bd310f2e4b7a9bd7bb550ed9c7da9ebabdf64ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129710"
---
# <a name="cross-platform-targeting"></a>跨平台目標設定

新式 .NET 支援多種作業系統與裝置。 .NET 開放原始碼程式庫要儘可能支援許多開發人員，無論是建置裝載於 Azure 的 ASP.NET 網站，還是 Unity 中的 .NET 遊戲，這一點非常重要。

## <a name="net-standard"></a>.NET Standard

.NET Standard 是為 .NET 程式庫新增跨平台支援的最佳方式。 [.NET Standard](../net-standard.md) 是在所有 .NET 實作都可以使用的 .NET API 規格。 將目標設為 .NET Standard，您可以產生限制為使用給定 .NET Standard 版本中之 API 的程式庫，這表示它可以被實作該 .NET 版本的所有平台使用。

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

將目標設為 .NET Standard 並成功地編譯您的專案，並不保證程式庫將可在所有平台上順利執行：

1. 平台特定 API 將會在其他平台上失敗。 例如，<xref:Microsoft.Win32.Registry?displayProperty=nameWithType> 會在 Windows 上成功，並在任何其他 OS 上使用時擲回 <xref:System.PlatformNotSupportedException>。
2. API 的行為會不一樣。 例如，當應用程式在 iOS 或 UWP 上使用預先編譯時，反映 API 具有不同的效能特性。

> [!TIP]
> .NET 小組[提供了一個 Roslyn 分析器](../analyzers/api-analyzer.md)，可協助您找出可能的問題。

**✔️ 請務必**開始包括 `netstandard2.0` 目標。

> 大部分的一般用途程式庫應該不需要 .NET Standard 2.0 以外的 API。 所有新式平台都支援 .NET Standard 2.0，而且是以一個目標支援多個平台的建議方法。

**❌ 避免**包含 `netstandard1.x` 目標。

> .NET standard 1.x 是以一組精細的 NuGet 套件形式發佈，它建立了一個大型的套件相依性圖形，並導致開發人員在建置時下載了大量的套件。 新式 .NET 平台，包括 .NET Framework 4.6.1、UWP 與 Xamarin，全都支援 .NET Standard 2.0。 如果您特別需要以較舊的平台為目標，則應僅將目標設為 .NET Standard 1.x。

**✔️ 請務必**包含 `netstandard2.0` 目標 (如果您需要 `netstandard1.x` 目標)。

> 所有支援 .NET Standard 2.0 的平台都將使用 `netstandard2.0` 目標，並從較小的套件圖形中受益，而較舊的平台仍會運作，並改為使用 `netstandard1.x` 目標。

**❌ 請勿**包含 .NET Standard 目標 (如果程式庫依賴平台特定應用程式模型)。

> 例如，UWP 控制項工具組程式庫相依於只有 UWP 上可用的應用程式模型。 .NET Standard 中將不提供應用程式模型特定 API。

## <a name="multi-targeting"></a>多目標

有時您需要從您的程式庫中存取架構特定 API。 呼叫架構特定 API 的最佳方法是使用多目標，它為許多 [.NET 目標 Framework](../frameworks.md) 建置專案，而不是僅為一個。

為了保護您的取用者不必為個別架構建置，您應該努力獲得 .NET Standard 輸出，加上一或多個架構特定輸出。 使用多目標時，所有組件都會封裝在單一 NuGet 套件中。 接著，取用者可以參考相同的套件，NuGet 將挑選適當的實作。 您的 .NET Standard 程式庫會作為在任何地方使用的後援程式庫，但您的 NuGet 套件提供架構特定實作的案例除外。 多目標可讓您在程式碼中使用條件式編譯，並呼叫架構特定 API。

![包含多個組件的 NuGet 套件](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "包含多個組件的 NuGet 套件")

**✔️ 考慮**將 .NET 實作設為目標 (除了 .NET Standard 之外)。

> 將 .NET 實作設為目標可讓您呼叫 .NET Standard 之外的平台特定 API。
>
> 執行此動作時，請不要捨棄 .NET Standard 的支援。 相反地，從實作擲回並提供功能API。 這樣，您的程式庫便能任何地方使用，並支援執行階段啟動功能。

**❌ 避免**使用多目標以及 .NET Standard 目標設定 (如果您的原始程式碼也適用於所有目標)。

> NuGet 將自動使用 .NET Standard 組件。 將單一 .NET 實作設為目標會增加 `*.nupkg` 大小，沒有任何好處。

**✔️ 考慮**針對 `net461` 新增目標 (當您提供 `netstandard2.0` 目標時)。 

> 使用 .NET Framework 中的 .NET Standard 2.0，會有一些在 .NET Framework 4.7.2 中已經解決的問題。 您可以透過為仍在 .NET Framework 4.6.1 - 4.7.1 上的開發人員提供針對 .NET Framework 4.6.1 建置的二進位檔，以改善其體驗。

**✔️ 優先**使用 NuGet 套件散發您的程式庫。

> NuGet 將為開發人員選取最佳目標，並讓他們不需要挑選適當的實作。

**✔️ 請務必**使用專案檔的 `TargetFrameworks` 屬性 (當使用多目標時)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**✔️ 考慮**使用 [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) (當針對 UWP 與 Xamarin 進行多目標時) 因為它可以大幅簡化您的專案檔。

## <a name="older-targets"></a>較舊的目標

.NET 支援長期不支援的 .NET Framework 的目標版本，以及不再常用的平台。 雖然使您的程式庫在儘可能多的目標上運作是有價值的，但是必須針對 API 遺漏問題找出因應措施會增加重大額外負荷。 考慮到其範圍與限制，我們認為特定架構已不再值得設為目標。

**❌ 請勿**包含可攜式類別庫 (PCL) 目標。 例如，`portable-net45+win8+wpa81+wp8`。

> .NET Standard 是支援跨平台 .NET 程式庫並取代 PCL 的新式方法。

**❌ 請勿**包含不再支援之 .NET 平台的目標。 例如，`SL4`、`WP`。

>[!div class="step-by-step"]
>[上一頁](get-started.md)
>[下一頁](strong-naming.md)
