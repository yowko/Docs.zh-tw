---
title: .NET 散發封裝
description: 瞭解如何封裝、命名和版本 .NET 以進行散發。
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 93d040064eb739b3bd045fdb16b356732353ddc8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216300"
---
# <a name="net-distribution-packaging"></a>.NET 散發封裝

由於 .NET 5 (和 .NET Core) 和更新版本會在更多平臺上提供使用，因此瞭解如何封裝、命名和使用它的應用程式和程式庫，是很有用的。 如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。 本文適用於符合下列項目的使用者：

- 正在嘗試從來源建立 .NET。
- 想要變更可能會影響所產生之配置或封裝的 .NET CLI。

## <a name="disk-layout"></a>磁碟配置

安裝時，.NET 會包含幾個配置檔案系統中的元件，如下所示：

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

-  (2) **host/fxr/ \<fxr version>** 包含主機所使用的架構解析邏輯。 主機會使用已安裝的最新 hostfxr。 Hostfxr 會負責在執行 .NET 應用程式時選取適當的執行時間。 例如，針對 .NET Core 2.0.0 建置的應用程式會在可用時使用 2.0.5 執行階段。 同樣地，hostfxr 會在開發期間選取適當的 SDK。

-  (3) **sdk/ \<sdk version>** sdk (也稱為「工具」 ) 是一組受管理的工具，可用來撰寫和建立 .net 程式庫和應用程式。 SDK 包含 .NET CLI、managed 語言編譯器、MSBuild，以及相關聯的組建工作與目標、NuGet、新專案範本等等。

- (4) **sdk/NuGetFallbackFolder** 包含 SDK 在還原作業期間使用的 NuGet 套件快取，例如在執行 `dotnet restore` 或 `dotnet build` 時。 此資料夾只會在 .NET Core 3.0 之前使用。 它無法從來源建立，因為它包含預建的二進位資產 `nuget.org` 。

**共用** 資料夾包含架構。 共用架構在集中位置提供一組程式庫，以供不同的應用程式使用。

-  (5) **shared/NETCore. App/ \<runtime version>** 此架構包含 .net 執行時間和支援的 managed 程式庫。

-  (6) **shared/AspNetCore. {App、All}/ \<aspnetcore version>** 包含 ASP.NET Core 程式庫。 下的程式庫 `Microsoft.AspNetCore.App` 是在 .net 專案中開發和支援的。 在 `Microsoft.AspNetCore.All` 下的程式庫是超集，其中也包含第三方程式庫。

-  (7) **共用/Microsoft. App/ \<desktop app version>** 包含 Windows 桌面程式庫。 這不包含在非 Windows 平臺上。

-  (8) **LICENSE.txt，ThirdPartyNotices.txt** 分別是 .net 中使用的 .net 授權和協力廠商程式庫的授權。

- (9、10) **dotnet.1.gz，dotnet** `dotnet.1.gz` 是 dotnet 手冊頁面。 `dotnet` 是 dotnet host(1) 的符號連結。 這些檔案會安裝在已知的位置以進行系統整合。

-  (11，12) **NETCore。 ref** 分別描述 .net 版本的 API 和 ASP.NET Core 的應用程式開發介面 `x.y` 。 針對這些目標版本進行編譯時，會使用這些套件。

-  (13) **NETCore \<rid>** 。 包含平臺的原生二進位檔 `rid` 。 將 .NET 應用程式編譯為該平臺的原生二進位檔時，此二進位檔是範本。

-  (14) **WindowsDesktop** 描述 `x.y` Windows 傳統型應用程式版本的 API。 針對該目標編譯時，會使用這些檔案。 非 Windows 平臺上不會提供此資訊。

-  (15) **NETStandard** 描述 NETStandard `x.y` API。 針對該目標編譯時，會使用這些檔案。

-  (16) **/etc/dotnet/install_location** 是包含完整路徑的檔案 `{dotnet_root}` 。 路徑結尾可以是分行符號。 當根目錄為時，並不需要加入這個檔案 `/usr/share/dotnet` 。

-  (17) **範本** 包含 SDK 所使用的範本。 例如， `dotnet new` 在這裡尋找專案範本。

標記為的資料夾 `(*)` 會由多個套件使用。 某些封裝格式 (例如， `rpm`) 需要這類資料夾的特殊處理。 封裝維護程式必須負責處理。

## <a name="recommended-packages"></a>建議的套件

.NET 版本控制是以執行時間元件的 `[major].[minor]` 版本號碼為基礎。
SDK 版本使用相同的 `[major].[minor]`，且具有獨立的 `[patch]`，其結合 SDK 的功能及修補程式語意。
例如： SDK 版本2.2.302 版是支援2.2 執行時間之 SDK 第三項功能版本的第二個修補程式版本。 如需版本控制運作方式的詳細資訊，請參閱 [.net 版本控制總覽](./versions/index.md)。

部分套件的名稱包含版本號碼部分。 這可讓您安裝特定版本。
其餘的版本不包含在版本名稱中。 這可讓 OS 套件管理員更新套件 (例如自動安裝安全性修正程式)。 支援的套件管理員特定於 Linux。

以下列出建議的封裝：

- `dotnet-sdk-[major].[minor]` -安裝適用于特定執行時間的最新 sdk
  - **版本：**\<sdk version>
  - **範例：** dotnet-sdk-2。1
  - **包含：** (3) 、 (4) 
  - 相依性 **：** `dotnet-runtime-[major].[minor]` 、 `aspnetcore-runtime-[major].[minor]` 、 `dotnet-targeting-pack-[major].[minor]` 、 `aspnetcore-targeting-pack-[major].[minor]` 、、 `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` `dotnet-apphost-pack-[major].[minor]` 、`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]` -安裝特定的 ASP.NET Core 執行時間
  - **版本：**\<aspnetcore runtime version>
  - **範例：** aspnetcore-runtime-2。1
  - **包含：** (6) 
  - 相依性 **：**`dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]`_(選擇性)_ -安裝執行獨立應用程式的相依性
  - **版本：**\<runtime version>
  - **範例：** dotnet-runtime-d-2。1
  - 相依性 **：** _散發特定_ 相依性

- `dotnet-runtime-[major].[minor]` -安裝特定執行時間
  - **版本：**\<runtime version>
  - **範例：** dotnet-runtime-2。1
  - **包含：** (5) 
  - 相依性 **：** `dotnet-hostfxr-[major].[minor]` 、`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr-[major].[minor]` -相依性
  - **版本：**\<runtime version>
  - **範例：** dotnet-hostfxr-3。0
  - **包含：** (2) 
  - 相依性 **：**`dotnet-host`

- `dotnet-host` -相依性
  - **版本：**\<runtime version>
  - **範例：** dotnet-主機
  - **包含：** (1) 、 (8) 、 (9) 、 (10) 、 (16) 

- `dotnet-apphost-pack-[major].[minor]` -相依性
  - **版本：**\<runtime version>
  - **包含：** (13) 

- `dotnet-targeting-pack-[major].[minor]` -允許以非最新執行時間為目標
  - **版本：**\<runtime version>
  - **包含：** (12) 

- `aspnetcore-targeting-pack-[major].[minor]` -允許以非最新執行時間為目標
  - **版本：**\<aspnetcore runtime version>
  - **包含：** (11) 

- `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` -允許以 netstandard 版本為目標
  - **版本：**\<sdk version>
  - **包含：** (15) 

- `dotnet-templates-[major].[minor]`
  - **版本：**\<sdk version>
  - **包含：** (15) 

`dotnet-runtime-deps-[major].[minor]`需要瞭解 _發行版本特有_ 的相依性。 因為發行版本組建系統可能會自動衍生此封裝，所以封裝是選擇性的，在這種情況下，這些相依性會直接加入 `dotnet-runtime-[major].[minor]` 封裝中。

當套件內容位於已建立版本的資料夾之下時，套件名稱會與已建立 `[major].[minor]` 版本的資料夾名稱相符。 除了以外的所有封裝之外 `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` ，這也會與 .net 版本相符。

套件之間的相依性應使用 _等於或大於_ 版本需求。 例如， `dotnet-sdk-2.2:2.2.401` 需要 `aspnetcore-runtime-2.2 >= 2.2.6` 。 如此一來，使用者就可以透過根封裝升級其安裝 (例如 `dnf update dotnet-sdk-2.2`) 。

大部分的發佈都需要從來源建置的所有成品。 這會對套件造成某個影響：

- `shared/Microsoft.AspNetCore.All` 下的第三方程式庫無法從來源輕鬆建置。 因此會從 `aspnetcore-runtime` 套件省略該資料夾。

- 使用 `nuget.org` 中的二進位成品填入 `NuGetFallbackFolder`。 它應該維持空白。

多個 `dotnet-sdk` 套件可能會提供相同的 `NuGetFallbackFolder` 檔案。 為了避免套件管理員問題，這些檔案都應該相同 (總和檢查碼、修改日期等)。

## <a name="building-packages"></a>建置套件

[Dotnet/來源組建](https://github.com/dotnet/source-build)存放庫提供如何建立 .net SDK 的來源 tarball 及其所有元件的指示。 source-build 存放庫的輸出會比對本文第一節中所述的配置。
