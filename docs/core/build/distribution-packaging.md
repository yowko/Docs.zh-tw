---
title: .NET Core 發佈封裝
description: 了解如何封裝、命名以及建立 .NET Core 版本以進行發佈。
author: tmds
ms.date: 10/09/2019
ms.custom: seodec18
ms.openlocfilehash: 3c41ce8a4a9ac1a914de2535a9b2423a7ddfa2cf
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250133"
---
# <a name="net-core-distribution-packaging"></a>.NET Core 發佈封裝

隨著 .NET Core 可在越來越多的平台上使用，了解如何封裝、命名和建立 .NET Core 版本是有用的。 如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。 本文適用於符合下列項目的使用者：

- 嘗試從來源建置 .NET Core。
- 希望對可能影響產生之配置或套件的 .NET Core CLI 進行變更。

## <a name="disk-layout"></a>磁碟配置

安裝後，.NET Core 包含幾個元件，這些元件在檔案系統中以下列所示進行配置：

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** 主機 (也稱為"muxer") 有兩個不同的角色：啟用執行階段以啟動應用程式，以及啟用 SDK 將命令分派給它。 主機是原生可執行檔 (`dotnet.exe`)。

雖然是單一主機，但大部分其他元件都會位於已建立版本的目錄中 (2、3、5、6)。 這表示多個版本可能會存在於系統上，因為為並排安裝。

- (2) **host/fxr/\<fxr 版本>** 包含主機所使用的架構解析邏輯。 主機會使用已安裝的最新 hostfxr。 hostfxr 負責在執行 .NET Core 應用程式時選取適當的執行階段。 例如，針對 .NET Core 2.0.0 建置的應用程式會在可用時使用 2.0.5 執行階段。 同樣地，hostfxr 會在開發期間選取適當的 SDK。

- (3) **sdk/\< 版本>** SDK (也稱為「工具」) 是一組受控工具，用於撰寫和建置 .NET Core 程式庫和應用程式。 SDK 包含 .NET Core 命令列介面 (CLI)、受控語言編譯器、MSBuild 以及相關聯的建置工作和目標、NuGet、新專案範本等。

- (4) **sdk/NuGetFallbackFolder** 包含 SDK 在還原作業期間使用的 NuGet 套件快取，例如在執行 `dotnet restore` 或 `dotnet build /t:Restore` 時。 此資料夾只會在 .NET Core 3.0 之前使用。 它無法從來源建立，因為它包含從 `nuget.org` 的預建二進位資產。

**共用**資料夾包含架構。 共用架構在集中位置提供一組程式庫，以供不同的應用程式使用。

- (5) **shared/Microsoft.NETCore.App/\<執行階段版本>** 此架構包含 .NET Core 執行階段和支援受控程式庫。

- （6） **shared/AspNetCore。 {App、All}/@no__t 1aspnetcore 版本 >** 包含 ASP.NET Core 程式庫。 在 .NET Core 專案期間，開發並支援 `Microsoft.AspNetCore.App` 下的程式庫。 在 `Microsoft.AspNetCore.All` 下的程式庫是超集，其中也包含第三方程式庫。

- （7）**共用 @no__t/1desktop 應用程式版本 >** 包含 Windows 桌面程式庫。 這不包含在非 Windows 平臺上。

- (8) **LICENSE.txt、ThirdPartyNotices.txt** 分別是在 .NET Core 中使用的 .NET Core 授權和第三方程式庫授權。

- (9、10) **dotnet.1.gz，dotnet** `dotnet.1.gz` 是 dotnet 手冊頁面。 `dotnet` 是 dotnet host(1) 的符號連結。 這些檔案會安裝在已知位置，以進行系統整合。

- （11，12） NETCore 會分別描述 .NET Core @no__t 1 版的 API，以及 ASP.NET Core 的**應用程式**開發介面。 這些套件會在針對那些目標版本進行編譯時使用。

- （13） **@no__t NETCore >** 包含平臺 `rid` 的原生二進位檔。 將 .NET Core 應用程式編譯成該平臺的原生二進位檔時，此二進位檔是範本。

- （14） **WindowsDesktop**說明 Windows 桌面應用程式 @no__t 1 版本的 API。 針對該目標編譯時，會使用這些檔案。 這不是在非 Windows 平臺上提供。

- （15） **NETStandard**描述 NETStandard `x.y` API。 針對該目標編譯時，會使用這些檔案。

- （16） **/etc/dotnet/install_location**是一個檔案，其中包含 `{dotnet_root}` 的完整路徑。 路徑的結尾可能是新行。 當根 `/usr/share/dotnet` 時，不需要新增此檔案。

- （17）**範本**包含 SDK 所使用的範本。 例如，`dotnet new` 會在這裡找到專案範本。

標記為 `(*)` 的資料夾會由多個封裝使用。 某些套件格式（例如，`rpm`）需要對這類資料夾進行特殊處理。 封裝維護員必須負責處理。

## <a name="recommended-packages"></a>建議的套件

.NET Core 版本設定是以執行階段元件 `[major].[minor]` 版本號碼為基礎。
SDK 版本使用相同的 `[major].[minor]`，且具有獨立的 `[patch]`，其結合 SDK 的功能及修補程式語意。
例如: SDK 2.2.302 版是 SDK 第三個功能版本的第二個修補程式版本，其支援 2.2 執行階段。 如需版本設定運作方式的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。

部分套件的名稱包含版本號碼部分。 這可讓您安裝特定版本。
其餘的版本不包含在版本名稱中。 這可讓 OS 套件管理員更新套件 (例如自動安裝安全性修正程式)。 支援的套件管理員特定於 Linux。

下列列出建議的套件：

- `dotnet-sdk-[major].[minor]`-安裝特定執行時間的最新 sdk
  - **版本：** @no__t 1runtime 版本 >
  - **範例：** dotnet-sdk-2。1
  - **包含**(3),(4)
  - 相依性 **：** `dotnet-runtime-[major].[minor]`，`aspnetcore-runtime-[major].[minor]`，`dotnet-targeting-pack-[major].[minor]`，`aspnetcore-targeting-pack-[major].[minor]`，`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`，`dotnet-apphost-pack-[major].[minor]`，`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-安裝特定的 ASP.NET Core 執行時間
  - **版本：** @no__t 1aspnetcore 執行階段版本 >
  - **範例：** aspnetcore-runtime-2。1
  - **包含**(6)
  - 相依性 **：** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _（選擇性）_ -安裝執行獨立應用程式的相依性
  - **版本：** @no__t 1runtime 版本 >
  - **範例：** dotnet-runtime-.deps.json-2。1
  - 相依性 **：** _散發版本特定_的相依性

- `dotnet-runtime-[major].[minor]`-安裝特定執行時間
  - **版本：** @no__t 1runtime 版本 >
  - **範例：** dotnet-runtime-2。1
  - **包含**(5)
  - 相依性 **：** `dotnet-hostfxr-[major].[minor]`，`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr-[major].[minor]`-相依性
  - **版本：** @no__t 1runtime 版本 >
  - **範例：** dotnet-用 hostfxr-3。0
  - **包含**(2)
  - 相依性 **：** `dotnet-host`

- `dotnet-host`-相依性
  - **版本：** @no__t 1runtime 版本 >
  - **範例：** dotnet-host
  - **包含**（1）、（8）、（9）、（10）、（16）

- `dotnet-apphost-pack-[major].[minor]`-相依性
  - **版本：** @no__t 1runtime 版本 >
  - **包含**十三

- `dotnet-targeting-pack-[major].[minor]`-允許以非最新的執行時間為目標
  - **版本：** @no__t 1runtime 版本 >
  - **包含**12

- `aspnetcore-targeting-pack-[major].[minor]`-允許以非最新的執行時間為目標
  - **版本：** @no__t 1aspnetcore 執行階段版本 >
  - **包含**英寸

- `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-允許以 netstandard 版本為目標
  - **版本：** @no__t 1sdk 版本 >
  - **包含**次

- `dotnet-templates-[major].[minor]`
  - **版本：** @no__t 1sdk 版本 >
  - **包含**次

@No__t-0 需要瞭解_散發版本特有_的相依性。 由於散發版本組建系統可能能夠自動衍生此專案，因此封裝是選擇性的，在此情況下，這些相依性會直接新增至 `dotnet-runtime-[major].[minor]` 套件。

當套件內容在已建立版本的資料夾下時，套件名稱 `[major].[minor]` 會符合已建立版本的資料夾名稱。 除了 `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` 以外的所有套件，這也符合 .NET Core 版本。

封裝之間的相依性應使用_等於或大於_版本需求。 例如，`dotnet-sdk-2.2:2.2.401` 需要 `aspnetcore-runtime-2.2 >= 2.2.6`。 如此一來，使用者就可以透過根封裝（例如 `dnf update dotnet-sdk-2.2`）升級其安裝。

大部分的發佈都需要從來源建置的所有成品。 這會對套件造成某個影響：

- `shared/Microsoft.AspNetCore.All` 下的第三方程式庫無法從來源輕鬆建置。 因此會從 `aspnetcore-runtime` 套件省略該資料夾。

- 使用 `nuget.org` 中的二進位成品填入 `NuGetFallbackFolder`。 它應該維持空白。

多個 `dotnet-sdk` 套件可能會提供相同的 `NuGetFallbackFolder` 檔案。 為了避免套件管理員問題，這些檔案都應該相同 (總和檢查碼、修改日期等)。

## <a name="building-packages"></a>建置套件

[dotnet/source-build](https://github.com/dotnet/source-build) \(英文\) 存放庫提供有關如何建置 .NET Core SDK 與其所有元件之來源 tarball 的指示。 source-build 存放庫的輸出會比對本文第一節中所述的配置。
