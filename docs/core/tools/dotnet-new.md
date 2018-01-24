---
title: "dotnet new 命令 - .NET Core CLI"
description: "dotnet new 命令會根據指定的範本建立新的 .NET Core 專案。"
keywords: "dotnet-new, CLI, CLI 命令, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet new` - 根據指定的範本建立新的專案、組態檔或方案。

## <a name="synopsis"></a>概要

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>描述

`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案。 

命令會呼叫[範本引擎](https://github.com/dotnet/templating)，以根據指定的範本和選項在磁碟上建立成品。

## <a name="arguments"></a>引數

`TEMPLATE`

要在叫用命令時具現化的範本。 每個範本可能會有您可以傳遞的特定選項。 如需詳細資訊，請參閱[範本選項](#template-options)。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

此命令包含預設的範本清單。 使用 `dotnet new -l` 以取得可用範本的清單。 下表顯示隨 .NET Core 2.0 SDK 預先安裝的範本。 範本的預設語言會顯示在方括號內。

|範本描述                          | 範本名稱 | 語言     |
|----------------------------------------------|---------------|---------------|
| 主控台應用程式                          | `console`     | [C#], F#, VB  |
| 類別庫                                | `classlib`    | [C#], F#, VB  |
| 單元測試專案                            | `mstest`      | [C#], F#, VB  |
| xUnit 測試專案                           | `xunit`       | [C#], F#, VB  |
| 空的 ASP.NET Core                           | `web`         | [C#]、F#      |
| ASP.NET Core Web 應用程式 (模型檢視控制器) | `mvc`         | [C#]、F#      |
| ASP.NET Core Web 應用程式                         | `razor`       | [C#]          |
| ASP.NET Core 與 Angular                    | `angular`     | [C#]          |
| ASP.NET Core 與 React.js                   | `react`       | [C#]          |
| ASP.NET Core 與 React.js 和 Redux         | `reactredux`  | [C#]          |
| ASP.NET Core Web API                         | `webapi`      | [C#]、F#      |
| global.json 檔案                             | `globaljson`  |               |
| Nuget 組態                                 | `nugetconfig` |               |
| Web 組態                                   | `webconfig`   |               |
| 方案檔                                | `sln`         |               |
| Razor 頁面                                   | `page`        |               |
| MVC/ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

此命令包含預設的範本清單。 使用 `dotnet new -all` 以取得可用範本的清單。 下表顯示隨 .NET Core 1.x SDK 預先安裝的範本。 範本的預設語言會顯示在方括號內。

|範本描述  | 範本名稱 | 語言 |
|----------------------|---------------|-----------|
| 主控台應用程式  | `console`     | [C#]、F#  |
| 類別庫        | `classlib`    | [C#]、F#  |
| 單元測試專案    | `mstest`      | [C#]、F#  |
| xUnit 測試專案   | `xunit`       | [C#]、F#  |
| 空的 ASP.NET Core   | `web`         | [C#]      |
| ASP.NET Core Web 應用程式 | `mvc`         | [C#]、F#  |
| ASP.NET Core Web API | `webapi`      | [C#]      |
| Nuget 組態         | `nugetconfig` |           |
| Web 組態           | `webconfig`   |           |
| 方案檔        | `sln`         |           |

---

## <a name="options"></a>選項

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--force`

強制產生內容，即使它會變更現有的檔案。 當輸出目錄中已包含專案時，這是必要選項。

`-h|--help`

印出命令的說明。 可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。

`-i|--install <PATH|NUGET_ID>`

安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。 如需建立自訂範本的資訊，請參閱 [dotnet new的自訂範本](custom-templates.md)。

`-l|--list`

列出包含指定名稱的範本。 如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。 例如，如果目錄中已包含專案，則不會列出所有專案範本。

`-lang|--language {C#|F#|VB}`

要建立的範本語言。 接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。 並非所有範本都適用。

`-n|--name <OUTPUT_NAME>`

所建立輸出的名稱。 如果未指定名稱，則會使用目前目錄的名稱。

`-o|--output <OUTPUT_DIRECTORY>`

放置所產生輸出的位置。 預設為目前的目錄。

`--type`

根據可用的類型篩選範本。 預先定義的值為「專案」、「項目」或「其他」。

`-u|--uninstall <PATH|NUGET_ID>`

解除安裝 `PATH` 或 `NUGET_ID` 提供的來源或範本套件。

> [!NOTE]
> 若要使用 `PATH` 將範本解除安裝，您需要使路徑成為完整路徑。 例如，*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。
> 此外，請勿在範本路徑中包含最終結尾目錄斜線。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

單獨在 `dotnet new` 命令的內容中執行時，顯示特定專案類型的所有範本。 在特定範本的內容中執行時 (例如 `dotnet new web -all`)，`-all` 會解譯為強制建立旗標。 當輸出目錄中已包含專案時，這是必要選項。

`-h|--help`

印出命令的說明。 可針對 `dotnet new` 命令本身或任何範本 (例如 `dotnet new mvc --help`) 叫用。

`-l|--list`

列出包含指定名稱的範本。 如果針對 `dotnet new` 命令叫用，則會列出指定目錄可能可用的範本。 例如，如果目錄中已包含專案，則不會列出所有專案範本。

`-lang|--language {C#|F#}`

要建立的範本語言。 接受的語言會因範本而有所不同 (請參閱[引數](#arguments)一節中的預設值)。 並非所有範本都適用。

`-n|--name <OUTPUT_NAME>`

所建立輸出的名稱。 如果未指定名稱，則會使用目前目錄的名稱。

`-o|--output <OUTPUT_DIRECTORY>`

放置所產生輸出的位置。 預設為目前的目錄。

---

## <a name="template-options"></a>範本選項

每個專案範本都可能會有其他可用的選項。 核心範本有下列額外選項：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**主控台, angular, react, reactredux**

`--no-restore` - 專案建立期間不執行隱含還原。

**classlib**

`-f|--framework <FRAMEWORK>` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp2.0` 建立 .NET Core 類別庫或 `netstandard2.0` 建立 .NET Standard 類別庫。 預設值是 `netstandard2.0`。

`--no-restore` - 專案建立期間不執行隱含還原。

**mstest, xunit**

`-p|--enable-pack` - 使用 [dotnet pack](dotnet-pack.md) 封裝專案。

`--no-restore` - 專案建立期間不執行隱含還原。

**globaljson**

`--sdk-version <VERSION_NUMBER>` - 指定要在 *global.json* 檔案中使用的 .NET Core SDK 版本。

**web**

`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。

`--no-restore` - 專案建立期間不執行隱含還原。

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。 可能值為：

- `None` - 無驗證 (預設值)。
- `IndividualB2C` - 使用 Azure AD B2C 的個別驗證。
- `SingleOrg` - 單一租用戶的組織驗證。
- `Windows` - Windows 驗證。

`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。 搭配 `IndividualB2C` 驗證使用。 預設值是 `https://login.microsoftonline.com/tfp/`。

`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。 搭配 `IndividualB2C` 驗證使用。

`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。 搭配 `SingleOrg` 驗證使用。 預設值是 `https://login.microsoftonline.com/`。

`--client-id <ID>` - 此專案的用戶端識別碼。 搭配 `IndividualB2C` 或 `SingleOrg` 驗證使用。 預設值是 `11111111-1111-1111-11111111111111111`。

`--domain <DOMAIN>` - 目錄租用戶的網域。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `qualified.domain.name`。

`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。 搭配 `SingleOrg` 驗證使用。 預設值是 `22222222-2222-2222-2222-222222222222`。

`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。 僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。

`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。

`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。 僅適用於 `Individual` 或 `IndividualB2C` 驗證。

`--no-restore` - 專案建立期間不執行隱含還原。

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` - 要使用的驗證類型。 可能值為：

- `None` - 無驗證 (預設值)。
- `Individual` - 個別驗證。
- `IndividualB2C` - 使用 Azure AD B2C 的個別驗證。
- `SingleOrg` - 單一租用戶的組織驗證。
- `MultiOrg` - 多個租用戶的組織驗證。
- `Windows` - Windows 驗證。

`--aad-b2c-instance <INSTANCE>` - 要連接的 Azure Active Directory B2C 執行個體。 搭配 `IndividualB2C` 驗證使用。 預設值是 `https://login.microsoftonline.com/tfp/`。

`-ssp|--susi-policy-id <ID>` - 此專案的登入及註冊原則識別碼。 搭配 `IndividualB2C` 驗證使用。

`-rp|--reset-password-policy-id <ID>` - 此專案的重設密碼原則識別碼。 搭配 `IndividualB2C` 驗證使用。

`-ep|--edit-profile-policy-id <ID>` - 此專案的編輯設定檔原則識別碼。 搭配 `IndividualB2C` 驗證使用。

`--aad-instance <INSTANCE>` - 要連接的 Azure Active Directory 執行個體。 搭配 `SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `https://login.microsoftonline.com/`。

`--client-id <ID>` - 此專案的用戶端識別碼。 搭配 `IndividualB2C`、`SingleOrg` 或 `MultiOrg` 驗證使用。 預設值是 `11111111-1111-1111-11111111111111111`。

`--domain <DOMAIN>` - 目錄租用戶的網域。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `qualified.domain.name`。

`--tenant-id <ID>` - 要連接的目錄 TenantId 識別碼。 搭配 `SingleOrg` 驗證使用。 預設值是 `22222222-2222-2222-2222-222222222222`。

`--callback-path <PATH>` - 重新導向 URI 的應用程式基底路徑內的要求路徑。 搭配 `SingleOrg` 或 `IndividualB2C` 驗證使用。 預設值是 `/signin-oidc`。

`-r|--org-read-access` - 允許此應用程式對目錄的讀取權限。 僅適用於 `SingleOrg` 或 `MultiOrg` 驗證。

`--use-launch-settings` - 在產生的範本輸出中包含 *launchSettings.json*。

`--use-browserlink` - 專案中包含 BrowserLink。

`-uld|--use-local-db` - 指定應該使用 LocalDB，不使用 SQLite。 僅適用於 `Individual` 或 `IndividualB2C` 驗證。

`--no-restore` - 專案建立期間不執行隱含還原。

**PAGE**

`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。 預設值是 `MyApp.Namespace`。

`-np|--no-pagemodel` - 不使用 PageModel 建立頁面。

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - 所產生程式碼的命名空間。 預設值是 `MyApp.Namespace`。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console、xunit、mstest、web、webapi**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0` 或 `netcoreapp1.1`。 預設值是 `netcoreapp1.0`。

**classlib**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0`、`netcoreapp1.1`，或 `netstandard1.0` 到 `netstandard1.6`。 預設值是 `netstandard1.4`。

**mvc**

`-f|--framework` - 指定要當成目標的[架構](../../standard/frameworks.md)。 值：`netcoreapp1.0` 或 `netcoreapp1.1`。 預設值是 `netcoreapp1.0`。

`-au|--auth` - 要使用的驗證類型。 值：`None` 或 `Individual`。 預設值是 `None`。

`-uld|--use-local-db` - 指定是否要使用 LocalDB，而不是 SQLite。 值：`true` 或 `false`。 預設值是 `false`。

---

## <a name="examples"></a>範例

在目前的目錄中建立 F# 主控台應用程式專案：

`dotnet new console -lang f#`

在指定的目錄中建立 .NET Standard 類別庫專案 (僅 .NET Core 2.0 SDK 或更新版本提供)：

`dotnet new classlib -lang VB -o MyLibrary`

未經驗證即在目前的目錄中，建立以 .NET Core 2.0 為目標的新 ASP.NET Core C# MVC 應用程式專案：

`dotnet new mvc -au None -f netcoreapp2.0`

建立以 .NET Core 2.0 為目標的新 xUnit 應用程式：

`dotnet new xunit --framework netcoreapp2.0`

列出 MVC 可用的所有範本：

`dotnet new mvc -l`

## <a name="see-also"></a>另請參閱

[dotnet new 的自訂範本](custom-templates.md)  
[建立適用於 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)  
[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)  
[dotnet new 的可用範本](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
