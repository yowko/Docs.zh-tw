---
title: ".NET Core 版本控制"
description: "了解 .NET Core 的版本控制運作方式。"
author: bleroy
ms.author: mairaw
ms.date: 08/10/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.translationtype: HT
ms.sourcegitcommit: 3a25c1c3b540bac8ef963a8bbf708b0700c3e9e2
ms.openlocfilehash: 94614e436734389df7bf3a6e2df2abe49593021a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/12/2017

---
# <a name="net-core-versioning"></a>.NET Core 版本控制

.NET Core 是由 [NuGet 套件](../packages.md)、工具及發佈為一個單位的架構所構成。 每一個平台層級都可以分別建立版本，以取得更好的靈活度。 雖然這樣有顯著的版本控制彈性，但還是希望能將平台當作一個單位來建立版本，讓產品更容易了解。

本文旨在釐清 .NET Core SDK 和執行階段如何建立版本。

.NET Core 中有許多活動的組件可獨立建立版本。 不過，從 .NET Core 2.0 開始，有一個大家都很容易明白的最上層版本號碼，就是 *".NET Core"*。 這份文件的其餘部分會深入說明所有這些組件的版本控制。 假如您是套件管理員，這些詳細資料就很重要。

## <a name="versioning-details"></a>版本控制的詳細資料

從 .NET Core 2.0 開始，下載在其檔案名稱中只顯示單一版本號碼。 統一下列版本號碼：

* 共用的架構和相關聯的執行階段。
* .NET Core SDK 和相關聯的 .NET Core CLI。
* `Microsoft.NETCore.App` 中繼套件。

使用單一版本號碼可讓使用者更容易了解在開發電腦上要安裝的 SDK 版本，以及佈建到生產環境時，應該使用的共用架構對應版本。 下載 SDK 或執行階段時，您看到的版本號碼就會是相同的。

### <a name="installers"></a>安裝程式

從 .NET Core 2.0 開始，[Daily Builds](https://github.com/dotnet/core-setup#daily-builds) (每日組建) 和[版本](https://www.microsoft.com/net/download/core)的下載會沿用容易了解的新命名配置。
這些下載的安裝程式 UI 也經過修改，以清楚呈現要安裝元件的名稱和版本。 特別是，標題現在在下載檔案名稱中會顯示相同的版本號碼。

#### <a name="file-name-format"></a>檔案名稱格式

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

以下是此格式的一些範例：

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

此格式易讀，並會清楚顯示您要下載的項目、版本和可以使用的位置。 執行階段套件名稱包含 `runtime`，SDK 則包含 `SDK`。

#### <a name="ui-string-format"></a>UI 字串格式

所有網站描述與安裝程式中的 UI 字串都保持一致、正確且簡單。 下表提供一些範例：

| Installer | 視窗標題                          | 安裝程式的其他內容 | 安裝的項目                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | .NET Core 2.0 SDK (x64) 安裝程式     | .NET Core 2.0.4 SDK        | .NET Core 2.0.4 工具 + .NET Core 2.0.4 執行階段 |
| 執行階段   | .NET Core 2.0 執行階段 (x64) 安裝程式 | .NET Core 2.0.4 執行階段    | .NET Core 2.0.4 執行階段                         |

Preview 版本略有不同：

| Installer | 視窗標題                                    | 安裝程式的其他內容        | 安裝的項目                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | .NET Core 2.0 Preview 1 SDK (x64) 安裝程式     | .NET Core 2.0.0 Preview 1 SDK     | .NET Core 2.0.0 Preview 1 工具 + .NET Core 2.0.0 Preview 1 執行階段 |
| 執行階段   | .NET Core 2.0 Preview 1 執行階段 (x64) 安裝程式 | .NET Core 2.0.0 Preview 1 執行階段 | .NET Core 2.0.0 Preview 1 執行階段                                   |

SDK 版本可能會包含多個執行階段版本。 當發生這種情況時，安裝程式 UX 看起來會像這樣 (只顯示 SDK 版本，已安裝的執行階段版本會顯示在 Windows 和 Mac 安裝程序結尾的摘要頁面上)：

| Installer | 視窗標題                      | 安裝程式的其他內容                                   | 安裝的項目                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | .NET Core 2.1 SDK (x64) 安裝程式 | .NET Core 2.1.1 SDK <br> .NET Core 2.1.1 執行階段 <br> .NET Core 2.0.6 執行階段 | .NET Core 2.1.1 工具 + .NET Core 2.1.1 執行階段 + .NET Core 2.0.6 執行階段 |

也可能是 .NET Core 工具需要更新，但執行階段不需要變更。 在此情況下，SDK 版本會增加 (例如，變成 2.1.2)，然後執行階段下次趕上 (例如，執行階段和 SDK 下次都變成 2.1.3)。

### <a name="package-managers"></a>套件管理員

Microsoft 以外的其他實體也可以散佈 .NET Core。 特別是，Linux 發行版本的擁有者和套件維護者，可將 .NET Core 套件新增至其套件管理員。 如需這些套件應如何命名和建立版本的建議，請參閱 [.NET Core 發佈封裝](../build/distribution-packaging.md)。

#### <a name="minimum-package-set"></a>最小封裝集合

* `dotnet-runtime-[major].[minor]`：指定版本的執行階段 (針對指定的主要 + 次要組合，套件管理員中僅可使用最新的更新程式版本)。 新的修補程式版本會更新套件，但新的次要版本或主要版本是個別的套件。
 
  **相依性**：`dotnet-host`

* `dotnet-sdk`：最新的 SDK。 `update` 會向前復原主要、次要和修補程式版本。

  **相依性**：最新的 `dotnet-sdk-[major].[minor]`。

* `dotnet-sdk-[major].[minor]`：指定版本的 SDK。 指定的版本是內含共用架構的最高內含版本，因此使用者可以輕鬆地將 SDK 與共用架構相關聯。 新的修補程式版本會更新套件，但新的次要版本或主要版本是個別的套件。

  **相依性**：`dotnet-host`，一或多個 `dotnet-runtime-[major].[minor]` (其中之一由 SDK 程式碼本身使用，其他執行階段則是供使用者作為目標建置和執行)。

* `dotnet-host`：最新的主機。

##### <a name="preview-versions"></a>預覽版本

套件維護人員可能會決定要包含執行階段和 SDK 的預覽版本。 不包含未建立版本的 `dotnet-sdk` 套件中的預覽版本，但可以作為已建立版本的套件發佈，且將其他預覽標記附加到名稱的主要版本和次要版本區段。 例如，可能會有 `dotnet-sdk-2.0-preview-1-final` 套件。

### <a name="docker"></a>Docker

一般的 Docker 標記命名慣例，是版本號碼在元件名稱之前。 這個慣例會繼續使用。 目前的標記只包含執行階段版本，如下所示。

* 1.0.8-runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-runtime
* 2.1.1-sdk

SDK 標記應該更新，以表示 SDK 版本，而不是表示執行階段。

我們可能也需要修復 .NET Core 工具，但重新附帶現有的執行階段。 在此情況下，SDK 版本會增加 (例如，變成 2.1.2)，然後執行階段下次趕上 (例如，執行階段和 SDK 下次都變成 2.1.3)。

## <a name="semantic-versioning"></a>語意版本控制

.NET Core 使用[語意版本控制 (SemVer)](http://semver.org/)，並採用 `MAJOR.MINOR.PATCH` 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件只存在於本機從來源目標建置的每日組建中，絕不會屬於支援的版本和不支援的預覽版本。

### <a name="how-version-numbers-are-incremented"></a>版本號碼如何遞增？

`MAJOR` 的遞增時機為：
  - 不再支援舊版本。
  - 採用現有相依性的較新 `MAJOR` 版本。
  - 相容性實際的預設設定變更為 [關閉]。

`MINOR` 的遞增時機為：
  - 新增公用 API 介面區。
  - 新增新的行為。
  - 採用現有相依性的較新 `MINOR` 版本。
  - 引入新的相依性。
  
`PATCH` 的遞增時機為：
  - 已修正 Bug。
  - 新增對較新平台的支援。
  - 採用現有相依性的較新 `PATCH` 版本。
  - 任何其他變更，不符合其中一個先前的案例。

當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。 例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。 當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。

### <a name="preview-versions"></a>預覽版本

預覽版本將 `-preview-[number]-([build]|"final")` 附加至版本。 例如，`2.0.0-preview-1-final`。

### <a name="lts-vs-current"></a>LTS 與目前的

有兩個 .NET Core 版本序列：長期支援 (LTS) 和目前。 讓使用者挑選他們想要且仍受支援的穩定性層級和新功能。

- LTS 表示取得新功能的頻率較低，但有較成熟的平台。 LTS 支援時間也較長。
- 「目前」表示取得新功能和 API 的頻率較高，但缺點是安裝更新的時段較短，以及這些更新發生地更頻繁。 「目前」也受到完全支援，但支援時間比 LTS 短。

「目前」的版本可升級為 LTS。

"LTS" 和「目前」應視為給特定版本的標籤，以表述相關聯的支援層級。

如需詳細資訊，請參閱 [.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support)。

## <a name="versioning-scheme-details"></a>版本控制配置詳細資料

.NET Core 由下列組件構成：

- 主機 (也稱為 muxer)：具有 `hostfxr` 原則庫的 `dotnet.exe`。
- SDK (開發人員電腦上必要的工具集，但不是生產環境中必要的)。
- 執行階段。
- 共用架構實作，以套件進行散發。 每個套件會獨立建立版本，尤其是修補程式版本控制。
- 或者，一組[中繼套件](../packages.md)，將細部套件當成已建立版本單位的參考。 中繼套件可與套件分開建立版本。

.NET Core 也包含一組目標 Framework (例如，`netstandard` 或 `netcoreapp`)，代表過大的 API 集，因為版本號碼遞增。

### <a name="net-standard"></a>.NET Standard

.NET Standard 一直使用 `MAJOR.MINOR` 版本設定配置。 `PATCH` 層級不適合 .NET Standard，因為它傳達的是不常反覆運算且不會呈現與實際實作相同之版本控制需求的合約集合。

.NET Standard 版本和 .NET Core 版本之間沒有實際結合：.NET Core 2.0 剛巧實作 .NET Standard 2.0，但不保證未來的 .NET Core 版本也會對應至相同的 .NET Standard 版本。 .NET Core 可以附帶不是 .NET Standard 定義的 API；如此，不需要新的 .NET Standard 也可以附帶新版本。 .NET Standard 也是適用其他目標的概念，例如 .NET Framework 或 Mono，即使它一開始與 .NET Core 一致。

### <a name="packages"></a>封裝

程式庫套件會獨立演化及進行版本控制。 與 .NET Framework 系統重疊的套件。\* 組件通常使用 4.x 版本，並與 .NET Framework 4.x 版本控制 (一個歷史選項) 一致。 不與 .NET Framework 程式庫重疊的套件 (例如，[`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) 通常從 1.0 開始，並從該處遞增。

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) 所描述的套件會被特別處理，因為它們是平台的基底。

`NETStandard.Library` 套件通常會作為一個集合來進行版本控制，因為它們彼此之間有實作層級的相依性。

### <a name="metapackages"></a>中繼套件

.NET Core 中繼套件的版本控制是以其所屬的 .NET Core 版本為基礎。

例如，.NET Core 2.1.3 中繼套件的 `MAJOR` 和 `MINOR` 版本號碼應該全都有 2.1。

每次更新參考的套件時，中繼套件的修補程式版本就會遞增。 修補程式版本不包含更新的架構版本。 因此，中繼套件並不與 SemVer 完相容，因為其版本控制配置並不代表基礎套件中的變更程度，而是主要代表 API 層級。 

.NET Core 目前有兩個主要中繼套件：

**Microsoft.NETCore.App**

- 截至 .NET Core 1.0 為 1.0 版 (這些版本會相符)。
- 對應至 `netcoreapp` 架構。
- 描述 .NET Core 散發套件中的套件。

注意：[`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) 是另一個 .NET Core 中繼套件，是為了與 .NET 的預先 .NET Standard 實作相容而存在。 它不會對應至特定的架構，因此其版本控制類似套件。

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) 描述 [.NET Standard](../../standard/library.md) 所包含的程式庫。 適用於所有支援 .NET Standard 的 .NET 實作，例如，.NET Framework、.NET Core 和 Mono。

### <a name="target-frameworks"></a>目標 Framework

新增新的 API 時，會更新目標架構版本。 它們有沒有修補程式版本的概念，因為它們代表 API 圖形，而不是實作考量。 主要和次要的版本控制會遵循之前指定的 SemVer 規則，符合實作它們之 .NET Core 發佈的 `MAJOR` 和 `MINOR` 號碼。

## <a name="versioning-in-practice"></a>版本控制實作

下載 .NET Core 時，您下載的檔案名稱攜有版本，例如 `dotnet-sdk-2.0.4-win10-x64.exe`。

GitHub 上的 .NET Core 存放庫每天都有認可和提取要求，進而產生許多程式庫的新組建。 為每一項變更建立新的公用版本 .NET Core 並不實際。 相反地，會針對一段不定時間 (例如，數週或數個月) 彙總變更，然後才製作新的公用穩定 .NET Core 版本。

新的 .NET Core 版本可能意謂著幾件事︰

- 新版本的套件和中繼套件。
- 新版本的各種架構，假設新增 API 版本的話。
- 新版本的 .NET Core 散發套件。

### <a name="shipping-a-patch-release"></a>修補程式版本出貨

.NET Core 主要版本出貨之後，例如 2.0.0 版，會針對 .NET Core 程式庫進行修補程式層級的變更，修正 Bug 並改善效能和可靠性。 這表示未引入新的 API。 各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 中繼套件是將版本建立為修補程式的更新 (`MAJOR.MINOR.PATCH`)。 目標 Framework 不會更新為更新版本的一部分。 新的 .NET Core 發佈發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件的版本號碼相符。

### <a name="shipping-a-minor-release"></a>次要版本出貨

有遞增 `MAJOR` 版本號碼的 .NET Core 版本出貨之後，新的 API 會新增至 .NET Core 程式庫，以啟用新案例。 各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 中繼套件建立的版本是修補程式更新加上符合新架構版本的 `MAJOR` 和 `MINOR` 版本號碼。 新增新的目標架構名稱和新的 `MAJOR.MINOR` 版本，以描述新的 API (例如，`netcoreapp2.1`)。 新的 .NET Core 散發套件發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件相符。

### <a name="shipping-a-major-release"></a>主要版本出貨

每次新的 .NET Core 主要版本出貨時，`MAJOR` 版本號碼就會遞增，而 `MINOR` 版本號碼則重設為零。 新的主要版本至少包含全部 API，它們是次要版本在前一個主要版本後新增的。 新的主要版本應該啟用重要的新案例，也可以中止對舊平台的支援。

各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。 [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) 中繼套件和 `netcore` 目標架構建立的版本是符合新版 `MAJOR` 版本號碼的重大更新。

## <a name="see-also"></a>請參閱
[目標 Framework](../../standard/frameworks.md)   
[.NET Core 發佈封裝](../build/distribution-packaging.md)   
[.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support)   
[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (.NET Core 2+ 版本繫結)   

