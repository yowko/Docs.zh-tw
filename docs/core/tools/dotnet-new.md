---
title: dotnet new 命令
description: dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463604"
---
# <a name="dotnet-new"></a>dotnet new

**本文適用於:✔️** .NET Core 2.0 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>描述

該`dotnet new`指令基於範本創建 .NET Core 專案或其他專案。

命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。

## <a name="arguments"></a>引數

- **`TEMPLATE`**

  要在叫用命令時具現化的範本。 每個範本可能會有您可以傳遞的特定選項。 如需詳細資訊，請參閱[範本選項](#template-options)。

  您可以執行`dotnet new --list`以查看所有已安裝範本的清單。 如果`TEMPLATE`該值與返回表中的 **「樣本**」或 **「短名稱」** 欄中的文字不匹配,則對這兩列執行子字串匹配。

  從 .NET Core 3.0 SDK 開始,當您`dotnet new`在以下條件下調用 指令時,CLI 會搜索NuGet.org中的樣本:

  - 如果 CLI 在`dotnet new`調用 時找不到範本匹配,甚至不是部分範本。
  - 如果有較新版本的範本可用。 在這種情況下,將創建專案或專案,但 CLI 會警告您有關範本的更新版本。

  此命令包含預設的範本清單。 使用 `dotnet new -l` 以取得可用範本的清單。 下表顯示了預安裝的 .NET Core SDK 的範本。 範本的預設語言會顯示在方括號內。 按下短名稱連結以查看特定的範本選項。

| 範本                                    | 簡短名稱                      | Language     | Tags                                  | 介紹 |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| 主控台應用程式                          | [安慰](#console)             | [C#], F#, VB | 通用/主控台                        | 1.0        |
| 類別庫                                | [classlib](#classlib)           | [C#], F#, VB | 通用/程式庫                        | 1.0        |
| WPF 應用程式                              | [Wpf](#wpf)                     | [C#]         | 公開/WPF                            | 3.0        |
| WPF 類庫                            | [wpflib](#wpf)                  | [C#]         | 公開/WPF                            | 3.0        |
| WPF 自訂控制項程式庫                   | [wpf自訂控制lib](#wpf)     | [C#]         | 公開/WPF                            | 3.0        |
| WPF 使用者控制項程式庫                     | [wpfuser 控制lib](#wpf)       | [C#]         | 公開/WPF                            | 3.0        |
| 視窗表單(贏表單)應用程式         | [溫窗體](#winforms)           | [C#]         | 通用/雙贏                       | 3.0        |
| 視窗表單(獲勝表單)類別庫       | [溫多利布](#winforms)        | [C#]         | 通用/雙贏                       | 3.0        |
| 工人服務                               | [工人](#web-others)           | [C#]         | 公用/工人/網路                     | 3.0        |
| 單元測試專案                            | [mstest](#test)                 | [C#], F#, VB | 測試/MSTest                           | 1.0        |
| NUnit 3 測試專案                         | [Nunit](#nunit)                  | [C#], F#, VB | 測試/NUnit                            | 2.1.400    |
| NUnit 3 測試項目                            | `nunit-test`                    | [C#], F#, VB | 測試/NUnit                            | 2.2        |
| xUnit 測試專案                           | [森特](#test)                  | [C#], F#, VB | 測試/XUnit                            | 1.0        |
| 剃刀元件                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3.0        |
| Razor 頁面                                   | [網頁](#page)                   | [C#]         | Web/ASP.NET                           | 2.0        |
| MVC ViewImports                              | [viewimports](#namespace)       | [C#]         | Web/ASP.NET                           | 2.0        |
| MVC ViewStart                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2.0        |
| 布拉佐伺服器應用程式                            | [布拉佐伺服器](#blazorserver)   | [C#]         | 網路/布拉佐爾                            | 3.0        |
| 空的 ASP.NET Core                           | [Web](#web)                     | [C#]、F#     | Web/空白                             | 1.0        |
| ASP.NET Core Web 應用程式 (模型檢視控制器) | [Mvc](#web-options)             | [C#]、F#     | Web/MVC                               | 1.0        |
| ASP.NET Core Web 應用程式                         | [網路應用程式, 剃鬚刀](#web-options)   | [C#]         | Web/MVC/Razor 頁面                   | 2.2, 2.0   |
| ASP.NET Core 與 Angular                    | [角](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core 與 React.js                   | [反應](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core 與 React.js 和 Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Razor 類別庫                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/程式庫/Razor 類別庫 | 2.1        |
| ASP.NET Core Web API                         | [韋薩皮](#webapi)               | [C#]、F#     | Web/WebAPI                            | 1.0        |
| ASP.NET核心 gRPC 服務                    | [grpc](#web-others)             | [C#]         | 網路/gRPC                              | 3.0        |
| 協定緩衝區檔案                         | [原](#namespace)             |              | 網路/gRPC                              | 3.0        |
| 點網 gitignore 檔案                        | `gitignore`                     |              | Config                                | 3.0        |
| global.json 檔案                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| NuGet 組態                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| 點網本地工具清單檔案              | `tool-manifest`                 |              | Config                                | 3.0        |
| Web 組態                                   | `webconfig`                     |              | Config                                | 1.0        |
| 方案檔                                | `sln`                           |              | 解決方法                              | 1.0        |

## <a name="options"></a>選項。

- **`--dry-run`**

  顯示運行給定命令時將會發生什麼情況的摘要。 自 .NET 核心 2.2 SDK 以來可用。

- **`--force`**

  強制產生內容，即使它會變更現有的檔案。 當選擇的範本將覆蓋輸出目錄中的現有檔時,這是必需的。

- **`-h|--help`**

  印出命令的說明。 可以為`dotnet new`命令本身或任何範本調用它。 例如： `dotnet new mvc --help` 。

- **`-i|--install <PATH|NUGET_ID>`**

  從`PATH``NUGET_ID`或安裝 提供的範本包。 若您想要安裝預先發行版本的範本套件，就必須以 `<package-name>::<package-version>` 的格式指定版本。 默認情況下,`dotnet new`將\*傳遞 版本,該版本表示最新的穩定包版本。 請參閱[「示例](#examples)」部分中的範例。
  
  如果在運行此命令時已安裝範本的版本,則範本將更新為指定版本,如果沒有指定版本,則該範本將更新到最新的穩定版本。

  如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。

- **`-l|--list`**

  列出包含指定名稱的範本。 如果未指定名稱,則列出所有範本。

- **`-lang|--language {C#|F#|VB}`**

  要建立的範本語言。 接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。 並非所有範本都適用。

  > [!NOTE]
  > 某些 Shell 會將 `#` 解譯為特殊字元。 在這些情況下,將語言參數值括在引號中。 例如： `dotnet new console -lang "F#"` 。

- **`-n|--name <OUTPUT_NAME>`**

  所建立輸出的名稱。 如果未指定名稱，則會使用目前目錄的名稱。

- **`--nuget-source <SOURCE>`**

  請指定安裝期間所要使用的 NuGet 來源。 自 .NET 核心 2.1 SDK 以來可用。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  放置所產生輸出的位置。 預設值是目前的目錄。

- **`--type <TYPE>`**

  根據可用的類型篩選範本。 預先定義值`project``item`為`other`或 。

- **`-u|--uninstall [PATH|NUGET_ID]`**

  在`PATH``NUGET_ID`或 上卸載範本包。 未指定`<PATH|NUGET_ID>`該值時,將顯示所有當前安裝的範本包及其關聯的範本。 指定`NUGET_ID`時,不包括版本號。

  如果不為此選項指定參數,該命令將列出已安裝的範本及其詳細資訊。

  > [!NOTE]
  > 若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。 例如 *,C:/使用者\</ 使用者>/文檔/範本/加西亞軟體.ConsoleTemplate.CSharp*將工作,但 *./GarciaSoftware.ConsoleTemplate.CSharp*從包含的資料夾中不會。
  > 不要在範本路徑上包含最終終止目錄斜杠。

- **`--update-apply`**

  檢查目前安裝的範本包是否有可用的更新並安裝它們。 自 .NET Core 3.0 SDK 起提供。

- **`--update-check`**

  檢查當前安裝的範本包是否有可用的更新。 自 .NET Core 3.0 SDK 起提供。

## <a name="template-options"></a>範本選項

每個專案範本都可能會有其他可用的選項。 核心範本有下列額外選項：

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 自 .NET Core 3.0 SDK 起提供。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  在`LangVersion`建立的項目檔中設定屬性。 例如，使用 `--langVersion 7.3` 可使用 C# 7.3。 不支援 F#。 自 .NET 核心 2.2 SDK 以來可用。

  有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。

- **`--no-restore`**

  如果指定,則不會在項目創建期間執行隱式還原。 自 .NET 核心 2.2 SDK 以來可用。

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 值：`netcoreapp<version>` 建立 .NET Core 類別庫或 `netstandard<version>` 建立 .NET Standard 類別庫。 預設值是 `netstandard2.0`。

- **`--langVersion <VERSION_NUMBER>`**

  在`LangVersion`建立的項目檔中設定屬性。 例如，使用 `--langVersion 7.3` 可使用 C# 7.3。 不支援 F#。 自 .NET 核心 2.2 SDK 以來可用。

  有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>wpf, wpflib, wpf自定義控制lib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 預設值是 `netcoreapp3.1`。 自 .NET 核心 3.1 SDK 以來可用。

- **`--langVersion <VERSION_NUMBER>`**

  在`LangVersion`建立的項目檔中設定屬性。 例如，使用 `--langVersion 7.3` 可使用 C# 7.3。

  有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>勝利,溫多利布

- **`--langVersion <VERSION_NUMBER>`**

  在`LangVersion`建立的項目檔中設定屬性。 例如，使用 `--langVersion 7.3` 可使用 C# 7.3。

  有關預設 C# 版本的清單,請參閱[預設值](../../csharp/language-reference/configure-language-version.md#defaults)。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="worker-grpc"></a><a name="web-others"></a>工人, grpc

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 預設值是 `netcoreapp3.1`。 自 .NET 核心 3.1 SDK 以來可用。

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="mstest-xunit"></a><a name="test"></a>斯泰斯特, 迅達

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項可用,因為 .NET 核心 3.0 SDK。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="nunit"></a>Nunit

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  使用[dotnet 套件](dotnet-pack.md)為專案啟用打包。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="page"></a>頁面

- **`-na|--namespace <NAMESPACE_NAME>`**

  生成的代碼的命名空間。 預設值是 `MyApp.Namespace`。

- **`-np|--no-pagemodel`**

  創建沒有頁面模型的頁面。

***

### <a name="viewimports-proto"></a><a name="namespace"></a>檢視導入, 原型

- **`-na|--namespace <NAMESPACE_NAME>`**

  生成的代碼的命名空間。 預設值是 `MyApp.Namespace`。

***

### <a name="blazorserver"></a>布拉佐伺服器

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  要使用的驗證類型。 可能的值包括：

  - `None` - 無驗證 (預設值)。
  - `Individual` - 個別驗證。
  - `IndividualB2C` - 使用 Azure AD B2C 的個別驗證。
  - `SingleOrg` - 單一租用戶的組織驗證。
  - `MultiOrg` - 多個租用戶的組織驗證。
  - `Windows` - Windows 驗證。

- **`--aad-b2c-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄 B2C 實體。 搭配 `IndividualB2C` 驗證使用。 預設值是 `https://login.microsoftonline.com/tfp/`。

- **`-ssp|--susi-policy-id <ID>`**

  此項目的登錄和註冊策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`-rp|--reset-password-policy-id <ID>`**

  此專案的重置密碼策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`-ep|--edit-profile-policy-id <ID>`**

  此項目的編輯設定檔策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`--aad-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄實例。 搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `https://login.microsoftonline.com/`。

- **`--client-id <ID>`**

  此專案的用戶端 ID。 搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `11111111-1111-1111-11111111111111111`。

- **`--domain <DOMAIN>`**

  目錄租戶的域。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `qualified.domain.name`。

- **`--tenant-id <ID>`**

  要連接到的目錄的租戶 ID ID。 搭配 `SingleOrg` 驗證使用。 預設值是 `22222222-2222-2222-2222-222222222222`。

- **`--callback-path <PATH>`**

  重定向URI的應用程式基本路徑中的請求路徑。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `/signin-oidc`。

- **`-r|--org-read-access`**

  允許此應用程式讀取訪問目錄。 僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`--no-https`**

  關閉 HTTPS。 僅當 、`Individual`或`IndividualB2C`未`SingleOrg``--auth`用於`MultiOrg`時 ,此選項才適用。

- **`-uld|--use-local-db`**

  指定本地資料庫應使用而不是 SQLite。 僅適用於 `Individual` 或 `IndividualB2C` 驗證。

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="web"></a>Web

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項在 .NET 核心 2.2 SDK 中不可用。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

- **`--no-https`**

  關閉 HTTPS。

***

### <a name="mvc-webapp"></a><a name="web-options"></a>mvc, 網路應用

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  要使用的驗證類型。 可能的值包括：

  - `None` - 無驗證 (預設值)。
  - `Individual` - 個別驗證。
  - `IndividualB2C` - 使用 Azure AD B2C 的個別驗證。
  - `SingleOrg` - 單一租用戶的組織驗證。
  - `MultiOrg` - 多個租用戶的組織驗證。
  - `Windows` - Windows 驗證。

- **`--aad-b2c-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄 B2C 實體。 搭配 `IndividualB2C` 驗證使用。 預設值是 `https://login.microsoftonline.com/tfp/`。

- **`-ssp|--susi-policy-id <ID>`**

  此項目的登錄和註冊策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`-rp|--reset-password-policy-id <ID>`**

  此專案的重置密碼策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`-ep|--edit-profile-policy-id <ID>`**

  此項目的編輯設定檔策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`--aad-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄實例。 搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `https://login.microsoftonline.com/`。

- **`--client-id <ID>`**

  此專案的用戶端 ID。 搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `11111111-1111-1111-11111111111111111`。

- **`--domain <DOMAIN>`**

  目錄租戶的域。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `qualified.domain.name`。

- **`--tenant-id <ID>`**

  要連接到的目錄的租戶 ID ID。 搭配 `SingleOrg` 驗證使用。 預設值是 `22222222-2222-2222-2222-222222222222`。

- **`--callback-path <PATH>`**

  重定向URI的應用程式基本路徑中的請求路徑。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `/signin-oidc`。

- **`-r|--org-read-access`**

  允許此應用程式讀取訪問目錄。 僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`--no-https`**

  關閉 HTTPS。 此選項僅適用於未使用 `Individual`、`IndividualB2C`、`SingleOrg` 或 `MultiOrg` 時。

- **`-uld|--use-local-db`**

  指定本地資料庫應使用而不是 SQLite。 僅適用於 `Individual` 或 `IndividualB2C` 驗證。

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項可用,因為 .NET 核心 3.0 SDK。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

- **`--use-browserlink`**

  在專案中包括瀏覽器連結。 選項在 .NET Core 2.2 和 3.1 SDK 中不可用。

- **`-rrc|--razor-runtime-compilation`**

  決定項目是否設定為除錯產生中使用[Razor 執行時編譯](/aspnet/core/mvc/views/view-compilation#runtime-compilation)。 選項可用,因為 .NET 核心 3.1 SDK。

***

### <a name="angular-react"></a><a name="spa"></a>角,反應

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  要使用的驗證類型。 自 .NET Core 3.0 SDK 起提供。
  
  可能的值包括：

  - `None` - 無驗證 (預設值)。
  - `Individual` - 個別驗證。

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

- **`--no-https`**

  關閉 HTTPS。 僅當身份驗證為`None`時,此選項才適用。

- **`-uld|--use-local-db`**

  指定本地資料庫應使用而不是 SQLite。 僅適用於 `Individual` 或 `IndividualB2C` 驗證。 自 .NET Core 3.0 SDK 起提供。

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項在 .NET 核心 2.2 SDK 中不可用。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項在 .NET 核心 2.2 SDK 中不可用。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

- **`--no-https`**

  關閉 HTTPS。

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

- **`-s|--support-pages-and-views`**

  除了元件添加到此庫之外,還支援添加傳統的 Razor 頁面和檢視。 自 .NET Core 3.0 SDK 起提供。

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  要使用的驗證類型。 可能的值包括：

  - `None` - 無驗證 (預設值)。
  - `IndividualB2C` - 使用 Azure AD B2C 的個別驗證。
  - `SingleOrg` - 單一租用戶的組織驗證。
  - `Windows` - Windows 驗證。

- **`--aad-b2c-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄 B2C 實體。 搭配 `IndividualB2C` 驗證使用。 預設值是 `https://login.microsoftonline.com/tfp/`。

- **`-ssp|--susi-policy-id <ID>`**

  此項目的登錄和註冊策略 ID。 搭配 `IndividualB2C` 驗證使用。

- **`--aad-instance <INSTANCE>`**

  要連接到的 Azure 活動目錄實例。 搭配 `SingleOrg` 驗證使用。 預設值是 `https://login.microsoftonline.com/`。

- **`--client-id <ID>`**

  此專案的用戶端 ID。 搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。 預設值是 `11111111-1111-1111-11111111111111111`。

- **`--domain <DOMAIN>`**

  目錄租戶的域。 搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。 預設值是 `qualified.domain.name`。

- **`--tenant-id <ID>`**

  要連接到的目錄的租戶 ID ID。 搭配 `SingleOrg` 驗證使用。 預設值是 `22222222-2222-2222-2222-222222222222`。

- **`-r|--org-read-access`**

  允許此應用程式讀取訪問目錄。 僅適用於`SingleOrg`身份驗證。

- **`--exclude-launch-settings`**

  從生成的範本中排除*啟動設置.json。*

- **`--no-https`**

  關閉 HTTPS。 `app.UseHsts` 和 `app.UseHttpsRedirection` 並未新增至 `Startup.Configure`。 此選項僅適用於或不`SingleOrg`用於身份`IndividualB2C`驗證 時。

- **`-uld|--use-local-db`**

  指定本地資料庫應使用而不是 SQLite。 僅適用於`IndividualB2C`身份驗證。

- **`-f|--framework <FRAMEWORK>`**

  指定要定位[的框架](../../standard/frameworks.md)。 選項在 .NET 核心 2.2 SDK 中不可用。

  下表根據您使用的 SDK 版本號列出預設值:

  | SDK 版本 | 預設值   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  在項目創建期間不執行隱式還原。

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  指定要在*global.json*檔中使用的 .NET Core SDK 的版本。

***

## <a name="examples"></a>範例

- 藉由指定範本名稱，建立 C# 主控台應用程式專案：

  ```dotnetcli
  dotnet new "Console Application"
  ```

- 在目前的目錄中建立 F# 主控台應用程式專案：

  ```dotnetcli
  dotnet new console -lang F#
  ```

- 在指定的目錄中建立 .NET 標準類別庫專案:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- 未經驗證即在目前目錄中建立新的 ASP.NET Core C# MVC 專案：

  ```dotnetcli
  dotnet new mvc -au None
  ```

- 建立新的 xUnit 專案：

  ```dotnetcli
  dotnet new xunit
  ```

- 列出可用於單頁應用程式 (SPA) 樣本的所有樣本:

  ```dotnetcli
  dotnet new spa -l
  ```

- 列出所有符合 *we* 子字串的範本。 找不到完全相符的項目，因此會對 [簡短名稱] 和 [名稱] 兩欄執行子字串比對作業。

  ```dotnetcli
  dotnet new we -l
  ```

- 嘗試叫用符合 *ng* 的範本。 如果無法判別單一相符項目，則列出部分相符的範本。

  ```dotnetcli
  dotnet new ng
  ```

- 安裝 ASP.NET核心的 SPA 樣本版本 2.0:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- 列出已安裝的範本及其詳細資訊,包括如何卸載它們:

  ```dotnetcli
  dotnet new -u
  ```

- 在目前的目錄中建立*全域.json*將 SDK 版本設定為 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>另請參閱

- [dotnet new 的自訂範本](custom-templates.md)
- [建立適用於 dotnet new 的自訂範本](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)
- [dotnet new 的可用範本](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
