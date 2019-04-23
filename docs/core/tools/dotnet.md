---
title: dotnet 命令
description: 了解 dotnet 命令 (.NET Core CLI 工具的通用驅動器) 和其用法。
ms.date: 06/04/2018
ms.openlocfilehash: 5278adf44d12e428cdeacf1d475377ce9155c314
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613001"
---
# <a name="dotnet-command"></a>dotnet 命令

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet` - 管理 .NET 原始程式碼和二進位檔的工具。

## <a name="synopsis"></a>概要

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>說明

`dotnet` 是管理 .NET 原始程式碼和二進位檔的工具。 會公開執行特定工作的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。 每個命令會定義自己的引數。 每個命令後方鍵入 `--help` 以存取簡短說明文件。

可藉由指定應用程式 DLL (例如 `dotnet myapp.dll`)，使用 `dotnet` 來執行應用程式。 請參閱 [.NET Core 應用程式部署](../deploying/index.md) 來了解部署選項。

## <a name="options"></a>選項

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

其他 *deps.json* 檔案的路徑。

`--additionalprobingpath <PATH>`

包含探查原則和要探查之組件的路徑。

`-d|--diagnostics`

啟用診斷輸出。

`--fx-version <VERSION>`

用來執行應用程式的 .NET Core 執行階段版本。

`-h|--help`

印出指定命令的文件，例如`dotnet build --help`。 `dotnet --help` 會印出可用命令的清單。

`--info`

會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。

`--list-runtimes`

顯示已安裝的 .NET Core 執行階段。

`--list-sdks`

顯示已安裝的 .NET Core SDK。

`--roll-forward-on-no-candidate-fx <N>`

在必要的共用架構無法使用時定義行為。 `N` 可以是：
* `0` - 對次要版本也停用向前復原。
* `1` - 對次要版本向前復原，主要版本則不。 這是預設行為。
* `2` - 對次要及主要版本向前復原。

 如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。

`--version`

印出使用中的 .NET Core SDK 版本。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

其他 *deps.json* 檔案的路徑。

`--additionalprobingpath <PATH>`

包含探查原則和要探查之組件的路徑。

`-d|--diagnostics`

啟用診斷輸出。

`--fx-version <VERSION>`

用來執行應用程式的 .NET Core 執行階段版本。

`-h|--help`

印出指定命令的文件，例如`dotnet build --help`。 `dotnet --help` 會印出可用命令的清單。

`--info`

會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。

`--roll-forward-on-no-candidate-fx`

 如果設定為 `0`，將停用次要版本向前復原。 如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。

`--version`

印出使用中的 .NET Core SDK 版本。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

包含探查原則和要探查之組件的路徑。

`-d|--diagnostics`

啟用診斷輸出。

`--fx-version <VERSION>`

用來執行應用程式的 .NET Core 執行階段版本。

`-h|--help`

印出指定命令的文件，例如`dotnet build --help`。 `dotnet --help` 會印出可用命令的清單。

`--info`

會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 不在每項命令中支援，請參考特定命令的頁面來判斷此選項是否可用。

`--version`

印出使用中的 .NET Core SDK 版本。

---

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>一般

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| 命令                                       | 功能                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | 建置 .NET Core 應用程式。                                     |
| [dotnet build-server](dotnet-build-server.md) | 與組建所啟動的伺服器互動。                          |
| [dotnet clean](dotnet-clean.md)               | 清除組建輸出。                                                |
| [dotnet help](dotnet-help.md)                 | 顯示命令更詳細的線上文件。           |
| [dotnet migrate](dotnet-migrate.md)           | 將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。  |
| [dotnet msbuild](dotnet-msbuild.md)           | 提供對 MSBuild 命令列的存取。                        |
| [dotnet new](dotnet-new.md)                   | 初始化指定範本的 C# 或 F# 專案。                |
| [dotnet pack](dotnet-pack.md)                 | 建立您程式碼的 NuGet 套件。                               |
| [dotnet publish](dotnet-publish.md)           | 發行 .NET 與 Framework 相依的應用程式或獨立應用程式。 |
| [dotnet restore](dotnet-restore.md)           | 還原所指定應用程式的相依性。                  |
| [dotnet run](dotnet-run.md)                   | 從原始檔執行應用程式。                                   |
| [dotnet sln](dotnet-sln.md)                   | 要在方案檔中新增、移除及列出專案的選項。       |
| [dotnet store](dotnet-store.md)               | 在執行階段套件存放區中儲存組件。                     |
| [dotnet test](dotnet-test.md)                 | 使用測試執行器執行測試。                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| 命令                             | 功能                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | 建置 .NET Core 應用程式。                                     |
| [dotnet clean](dotnet-clean.md)     | 清除組建輸出。                                              |
| [dotnet help](dotnet-help.md)       | 顯示命令更詳細的線上文件。           |
| [dotnet migrate](dotnet-migrate.md) | 將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。  |
| [dotnet msbuild](dotnet-msbuild.md) | 提供對 MSBuild 命令列的存取。                        |
| [dotnet new](dotnet-new.md)         | 初始化指定範本的 C# 或 F# 專案。                |
| [dotnet pack](dotnet-pack.md)       | 建立您程式碼的 NuGet 套件。                               |
| [dotnet publish](dotnet-publish.md) | 發行 .NET 與 Framework 相依的應用程式或獨立應用程式。 |
| [dotnet restore](dotnet-restore.md) | 還原所指定應用程式的相依性。                  |
| [dotnet run](dotnet-run.md)         | 從原始檔執行應用程式。                                   |
| [dotnet sln](dotnet-sln.md)         | 要在方案檔中新增、移除及列出專案的選項。       |
| [dotnet store](dotnet-store.md)     | 在執行階段套件存放區中儲存組件。                     |
| [dotnet test](dotnet-test.md)       | 使用測試執行器執行測試。                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| 命令                             | 功能                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | 建置 .NET Core 應用程式。                                     |
| [dotnet clean](dotnet-clean.md)     | 清除組建輸出。                                              |
| [dotnet migrate](dotnet-migrate.md) | 將有效的 Preview 2 專案移轉至 .NET Core SDK 1.0 專案。  |
| [dotnet msbuild](dotnet-msbuild.md) | 提供對 MSBuild 命令列的存取。                        |
| [dotnet new](dotnet-new.md)         | 初始化指定範本的 C# 或 F# 專案。                |
| [dotnet pack](dotnet-pack.md)       | 建立您程式碼的 NuGet 套件。                               |
| [dotnet publish](dotnet-publish.md) | 發行 .NET 與 Framework 相依的應用程式或獨立應用程式。 |
| [dotnet restore](dotnet-restore.md) | 還原所指定應用程式的相依性。                  |
| [dotnet run](dotnet-run.md)         | 從原始檔執行應用程式。                                   |
| [dotnet sln](dotnet-sln.md)         | 要在方案檔中新增、移除及列出專案的選項。       |
| [dotnet test](dotnet-test.md)       | 使用測試執行器執行測試。                                     |

---

### <a name="project-references"></a>專案參考

命令 | 功能
--- | ---
[dotnet add reference](dotnet-add-reference.md) | 新增專案參考。
[dotnet list reference](dotnet-list-reference.md) | 列出專案參考。
[dotnet remove reference](dotnet-remove-reference.md) | 移除專案參考。

### <a name="nuget-packages"></a>NuGet 套件

命令 | 功能
--- | ---
[dotnet add package](dotnet-add-package.md) | 新增 NuGet 套件。
[dotnet remove package](dotnet-remove-package.md) | 移除 NuGet 套件。

### <a name="nuget-commands"></a>NuGet 命令

命令 | 功能
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | 從伺服器刪除或取消列出套件。
[dotnet nuget locals](dotnet-nuget-locals.md) | 清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。
[dotnet nuget push](dotnet-nuget-push.md) | 將套件推送至伺服器並發行。

### <a name="global-tools-commands"></a>通用工具命令

[.NET Core 通用工具](global-tools.md)將從 .NET Core SDK 2.1.300 開始提供使用：

命令 | 功能
--- | ---
[dotnet tool install](dotnet-tool-install.md) | 在您的電腦上安裝通用工具。
[dotnet tool list](dotnet-tool-list.md) | 列出在您電腦上的預設目錄或在指定路徑中目前已安裝的所有通用工具。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | 將通用工具從您的電腦解除安裝。
[dotnet tool update](dotnet-tool-update.md) | 更新您電腦上的通用工具。

### <a name="additional-tools"></a>其他工具

從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。 這些工具列於下列資料表中：

| 工具                                              | 功能                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 建立及管理開發憑證。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core 命令列工具。                    |
| sql-cache                                         | SQL Server 快取命令列工具。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 管理開發使用者祕密。                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | 啟動會在檔案變更時執行命令的檔案監看員。 |

如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。

## <a name="examples"></a>範例

建立新的 .NET Core 主控台應用程式：

`dotnet new console`

還原所指定應用程式的相依性：

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

建置所指定目錄中的專案和其相依性：

`dotnet build`

執行應用程式 DLL，例如 `myapp.dll`：

`dotnet myapp.dll`

## <a name="environment-variables"></a>環境變數

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

主要套件快取。 如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。

`DOTNET_SERVICING`

指定載入執行階段時，共用主機所使用的服務索引位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。 否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。

`DOTNET_MULTILEVEL_LOOKUP`

指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。 如果未設定，則預設為 `true`。 設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。 如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

如果設定為 `0`，將停用次要版本向前復原。 如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

主要套件快取。 如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。

`DOTNET_SERVICING`

指定載入執行階段時，共用主機所使用的服務索引位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。 否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。

`DOTNET_MULTILEVEL_LOOKUP`

指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。 如果未設定，則預設為 `true`。 設定為 `false` 則不會從全域位置解析，而且會有獨立模式的 .NET Core 安裝 (接受 `0` 或 `false` 值)。 如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

主要套件快取。 如果未設定，預設為 `$HOME/.nuget/packages` (Unix) 或 `%HOME%\NuGet\Packages` (Windows)。

`DOTNET_SERVICING`

指定載入執行階段時，共用主機所使用的服務索引位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。 否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。

---
