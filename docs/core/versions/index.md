---
title: ".NET Core 版本設定 | Microsoft Docs"
description: ".NET Core 版本控制"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.translationtype: Human Translation
ms.sourcegitcommit: 9cd469dfd4f38605f1455c008388ad04c366e484
ms.openlocfilehash: 9ee687feebdd96022ca5a59443fb8118714e3fa4
ms.contentlocale: zh-tw
ms.lasthandoff: 06/20/2017

---

<a id="net-core-versioning" class="xliff"></a>

# .NET Core 版本控制

.NET Core 是 [NuGet 套件](../packages.md)的平台架構，並且是作為一個單位來散發。 這些平台層級可個別建立版本以獲得產品的靈活度，並正確地描述產品變更。 雖然有顯著的版本控制彈性，還是會渴望將平台當做一個單位來建立版本，讓產品更容易了解。

產品在某些方面是唯一的，透過封裝管理員 (NuGet) 以套件的方式來描述和傳遞。 雖然您通常會以獨立 SDK 形式取得 .NET Core，SDK 主要是 NuGet 套件的方便體驗，因此與套件並無不同。 因此，就套件而言，版本控制是最先且最重要的，其他版本控制體驗則為其後續。

<a id="semantic-versioning" class="xliff"></a>

## 語意版本控制

.NET Core 使用[語意版本控制 (SemVer)](http://semver.org/)，並採用 major.minor.patch 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。

下列版本控制範本通常會套用到 .NET Core。 在有些情況下，已經過調整以配合現有的版本控制。 本文件稍後會說明這些情況。 比方說，架構只用來代表平台和 API 功能，這與主要/次要版本控制一致。

<a id="versioning-form" class="xliff"></a>

### 版本控制格式

MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]

<a id="decision-tree" class="xliff"></a>

### 決策樹

MAJOR 的時機︰
  - 捨棄平台的支援
  - 採用現有相依性的較新的 MAJOR 版本 
  - 預設停用相容性實際關閉

MINOR 的時機︰
  - 新增公用 API 介面區 
  - 加入新行為
  - 採用現有相依性的較新的 MINOR 版本
  - 採用新的相依性 
  
PATCH 的時機︰
  - 進行 Bug 修正
  - 新增對較新平台的支援
  - 採用現有相依性的較新的 PATCH 版本
  - 任何其他變更 (它處未擷取)

在決定有多項變更時要遞增的項目時，請選擇最高的變更類型。

<a id="versioning-scheme" class="xliff"></a>

## 版本控制配置

.NET Core 可以下列方式定義，並且將如下進行版本控制︰

- 執行階段和架構實作，以套件進行散發。 每個套件會獨立建立版本，尤其是修補程式版本控制。
- 一組中繼套件，它們以建立版本的單位來參考細部的套件。 中繼套件與套件分開建立版本。
- 一組的架構 (例如，`netstandard`)，它們代表逐漸變大的 API 集，而這是以一組已建立版本的快照集來描述。

<a id="packages" class="xliff"></a>

### 封裝

程式庫套件會獨立演化及進行版本控制。 與 .NET Framework 系統重疊的套件。\* 組件通常使用 4.x 版本，並與 .NET Framework 4.x 版本控制 (一個歷史選項) 一致。 不與 .NET Framework 程式庫重疊的套件 (比方說，[System.Reflection.Metadata](https://www.nuget.org/packages/System.Reflection.Metadata)) 通常從 1.0 開始，並從該處遞增。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) 所描述的套件會被特別處理，因為它們是平台的基底。

- NETStandard.Library 套件通常會作為一個集合來進行版本控制，因為它們彼此之間有實作層級的相依性。
- API 將只會作為主要或次要 .NET Core 版本新增至 NETStandard.Library 套件，因為這樣做就必須新增新的 `netstandard` 版本。 這是 SemVer 需求之外額外增加。

<a id="metapackages" class="xliff"></a>

### 中繼套件

.NET Core 中繼套件的版本控制是根據它們所對應的架構。 中繼套件採用它在套件終止中對應到的架構最高版本號碼 (例如，netstandard1.6)。 

中繼套件的修補程式版本用來代表中繼套件的更新，以參考更新過的套件。 修補程式版本將永遠不會包含更新的架構版本。 因此，中繼套件並不與 SemVer 嚴格相容，因為其版本控制配置並不代表基礎套件中的變更程度，而是主要代表 API 層級。 

.NET Core 有兩個主要的中繼套件。

**NETStandard.Library**

- 截至 .NET Core 1.0 為 1.6 版 (這些版本通常不會相符，或是不會蓄意地相符)。
- 對應至 `netstandard` 架構。 
- 描述被視為現代化應用程式開發所需的套件，而且 .NET 平台必須實作這些套件才會被視為 [.NET Standard](../../standard/net-standard.md) 平台。

**Microsoft.NETCore.App**

- 截至 .NET Core 1.0 為 1.0 版 (這些版本將會相符)。
- 對應至 `netcoreapp` 架構。
- 描述 .NET Core 散發套件中的套件。

注意︰[`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) 是另一個 .NET Core 中繼套件。 它不會對應至特定的架構，因此其版本控制類似套件。

<a id="frameworks" class="xliff"></a>

### 架構

新增 API 時，會更新架構版本。 它們有沒有修補程式版本的概念，因為它們代表 API 圖形，而不是實作考量。 主要和次要版本控制會依照稍早指定的 SemVer 規則。

`netcoreapp` 架構會繫結至 .NET Core 散發套件。 它會遵循 .NET Core 所使用的版本號碼。 例如，.NET Core 2.0 發行時，它將以 `netcoreapp2.0` 為目標。 `netstandard` 架構不會符合任何 .NET 執行階段的版本控制配置，假設全部都同樣適用的話。

<a id="versioning-in-practice" class="xliff"></a>

## 版本控制實踐

GitHub 上的 .NET Core 儲存機制每天都有認可和 PR，進而產生許多程式庫的新組建。 為每一項變更建立新的公用版本 .NET Core 並不實際。 相反地，會針對一段定義寬鬆的時間 (例如，數週或數個月) 彙總變更，然後才製作新的公用穩定 .NET Core 版本。

新的 .NET Core 版本可能意謂著幾件事︰

- 新版本的套件和中繼套件。
- 新版本的各種架構，假設新增 API 版本的話。
- 新版本的 .NET Core 散發套件。

<a id="shipping-a-patch-release" class="xliff"></a>

### 修補程式版本出貨

.NET Core 1.0.0 版穩定版本出貨之後，會針對 .NET Core 程式庫進行修補程式層級的變更 (沒有新的 API)，以修正 Bug 並改善效能和可靠性。 各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 中繼套件的版本建立是作為修補程式的更新 (x.y.z)。 不會更新架構。 新的 .NET Core 散發套件發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件相符。

您可以在下列 project.json 範例中看到示範的修補程式更新。

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

<a id="shipping-a-minor-release" class="xliff"></a>

### 次要版本出貨

.NET Core v1.0.0 穩定版本出貨之後，新的 API 新增至 .NET Core 程式庫，以啟用新案例。 各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 中繼套件的版本建立為修補程式更新 (x.y) 以符合較高的架構版本。 各種架構已更新為說明新的 API。 新的 .NET Core 散發套件發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件相符。

您可以在下列專案檔中看到示範的次要更新：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<a id="shipping-a-major-release" class="xliff"></a>

### 主要版本出貨

對於 .NET Core v1.y.z 穩定版本，新的 API 已新增至 .NET Core 程式庫，以啟用主要的新案例。 或許，不再支援某個平台。 各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 `Microsoft.NETCore.App` 中繼套件和 `netcore` 架構的版本建立為主要更新 (x.)。 `NETStandard.Library` 中繼套件的版本可能建立為次要更新 (x.y)，因為它適用於多個 .NET 實作。 新的 .NET Core 散發套件發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件相符。

您可以在下列專案檔中看到示範的主要更新 (請注意，`netcoreapp2.0` 尚未發行)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

