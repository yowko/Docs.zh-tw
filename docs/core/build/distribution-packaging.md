---
title: .NET Core 發佈封裝
description: 了解如何封裝、命名以及建立 .NET Core 版本以進行發佈。
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: df1ba6a93106cd6b3ceafa93b7c548287878c3fe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840484"
---
# <a name="net-core-distribution-packaging"></a>.NET Core 發佈封裝

隨著 .NET Core 可在越來越多的平台上使用，了解如何封裝、命名及建立 .NET Core 版本是有用的。 如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。

## <a name="disk-layout"></a>磁碟配置

安裝時，.NET Core 包含在檔案系統中進行如下配置的數個元件：

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** 主機 (也稱為"muxer") 有兩個不同的角色：啟用執行階段以啟動應用程式，以及啟用 SDK 將命令分派給它。 主機是原生可執行檔 (`dotnet.exe`)。

有單一主機時，大部分的其他元件都會位在已建立版本的目錄 (2,3,5,6) 中。 這些表示系統上可以有多個版本，因為它們是並排安裝。

- (2) **host/fxr/\<fxr 版本>** 包含主機所使用的架構解析邏輯。 主機會使用已安裝的最新 hostfxr。 hostfxr 負責在執行 .NET Core 應用程式時選取適當的執行階段。 例如，針對 .NET Core 2.0.0 所建置的應用程式將會使用可用的 2.0.5 執行階段。 同樣地，hostfxr 會在開發期間選取適當的 SDK。

- (3) **sdk/\<SDK 版本>** SDK (也稱為「工具」) 是一組受控工具，可用來撰寫與建置 .NET Core 程式庫和應用程式。 SDK 包含 CLI、Roslyn 編譯器、MSBuild，以及相關聯的建置工作與目標、NuGet 及新的專案範本等。

- (4) **sdk/NuGetFallbackFolder** 包含 SDK 在 `dotnet restore` 步驟期間所使用的 NuGet 套件快取。

**共用**資料夾包含架構。 共用架構在集中位置提供一組程式庫，以供不同的應用程式使用。

- (5) **shared/Microsoft.NETCore.App/\<執行階段版本>** 此架構包含 .NET Core 執行階段和支援受控程式庫。

- (6,7) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore 版本>** 包含 ASP.NET Core 程式庫。 在 .NET Core 專案期間，開發並支援 `Microsoft.AspNetCore.App` 下的程式庫。 `Microsoft.AspNetCore.All` 下的程式庫是也包含協力廠商程式庫的超集。

- (8) **LICENSE.txt,ThirdPartyNotices.txt** 是 .NET Core 授權以及 .NET Core 中所使用協力廠商程式庫的授權。

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` 是 dotnet 手冊頁。 `dotnet` 是 dotnet host(1) 的符號連結。 這些檔案會安裝在已知位置，以進行系統整合。

## <a name="recommended-packages"></a>建議的套件

.NET Core 版本設定是以執行階段元件 `[major].[minor]` 版本號碼為基礎。
SDK 版本會使用相同的 `[major].[minor]`，並且具有合併 SDK 功能及修補程式語意的獨立 `[patch]`。
例如：SDK 2.2.302 版是支援 2.2 執行階段的 SDK 之第 3 個功能版本的第 2 個修補程式版本。

部分套件的名稱包含版本號碼部分。 這可讓使用者安裝特定版本。
版本的其餘部分不會納入版本名稱中。 這可讓 OS 套件管理員更新套件 (例如自動安裝安全性修正)。

下列各表顯示建議的套件。

| 名稱                                    | 範例                | 使用案例：安裝...           | 包含           | 相依性                                   | 版本            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | 執行階段主要的最新 SDK    |                    | dotnet-sdk-[major].[latestminor]               | \<SDK 版本>     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | 特定執行階段的最新 SDK |                    | dotnet-sdk-[major].[minor].[latest sdk feat]xx | \<SDK 版本>     |
| dotnet-sdk-[major].[minor].[sdk feat]xx | dotnet-sdk-2.1.3xx     | 特定 SDK 功能版本    | (3),(4)            | aspnetcore-runtime-[major].[minor]             | \<SDK 版本>     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | 特定 ASP.NET Core 執行階段   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<執行階段版本> |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | 特定執行階段                | (5)                | host-fxr:\<執行階段版本>+                   | \<執行階段版本> |
| dotnet-host-fxr                         | dotnet-host-fxr        | _dependency_                    | (2)                | host:\<執行階段版本>+                       | \<執行階段版本> |
| dotnet-host                             | dotnet-host            | _dependency_                    | (1),(8),(9),(10)   |                                                | \<執行階段版本> |

大部分的發佈都需要從來源建置的所有成品。 這會對套件造成某個影響：

- 無法從來源輕鬆地建置 `shared/Microsoft.AspNetCore.All` 下的協力廠商程式庫。 因此會從 `aspnetcore-runtime` 套件省略該資料夾。

- 使用 `nuget.org` 中的二進位成品填入 `NuGetFallbackFolder`。 它應該維持空白。

多個 `dotnet-sdk` 套件可能會提供相同的 `NuGetFallbackFolder` 檔案。 若要避免套件管理員問題，這些檔案應該相同 (總和檢查碼、修改日期...)。

#### <a name="preview-versions"></a>預覽版本

套件維護人員可能會決定要提供共用架構和 SDK 的預覽版本。 可能會使用 `dotnet-sdk-[major].[minor].[sdk feat]xx`、`aspnetcore-runtime-[major].[minor]`、`dotnet-runtime-[major].[minor]` 套件提供 Preview 版本。 針對 Preview 版本，套件版本主要必須設為零。 因此，最終版本將會安裝為套件的升級。

#### <a name="patch-packages"></a>修補程式套件

因為套件的修補程式版本可能會導致重大變更，所以套件維護人員可能想要提供「修補程式套件」。 這些套件允許安裝不會自動升級的特定修補程式版本。 只有在極少數的情況下才應該使用修補程式套件，因為它們不會與 (安全性) 修正程式一起自動升級。

下表顯示建議的套件和**修補程式套件**。

| 名稱                                           | 範例                  | 包含         | 相依性                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | dotnet-sdk-[major].[latest sdk minor]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | dotnet-sdk-[major].[minor].[latest sdk feat]xx            |
| dotnet-sdk-[major].[minor].[sdk feat]xx        | dotnet-sdk-2.1.3xx       |                  | dotnet-sdk-[major].[minor].[latest sdk patch]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore-runtime-[major].[minor].[sdk runtime patch]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore-runtime-[major].[minor].[latest runtime patch] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | dotnet-runtime-[major].[minor].[latest runtime patch]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr:\<執行階段版本>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | host:\<執行階段版本>+                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

使用修補程式套件的替代方法，是使用套件管理員將套件「釘選」到特定版本。 若要避免影響其他應用程式/使用者，可以在容器中建置和部署這類應用程式。

## <a name="building-packages"></a>建置套件

[dotnet/source-build](https://github.com/dotnet/source-build) \(英文\) 存放庫提供有關如何建置 .NET Core SDK 與其所有元件之來源 tarball 的指示。 source-build 存放庫的輸出會比對本文第一節中所述的配置。