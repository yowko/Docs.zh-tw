---
title: dotnet 命令
description: 瞭解 dotnet 命令(.NET Core CLI 的通用驅動程式)及其用法。
ms.date: 02/13/2020
ms.openlocfilehash: d700f35f3c977524ff3857da99519882eb0136e9
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463277"
---
# <a name="dotnet-command"></a>dotnet 命令

**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet`- .NET 核心 CLI 的通用驅動程式。

## <a name="synopsis"></a>概要

要取得有關可用命令和環境的資訊,請造訪:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

要執行指令(需要 SDK 安裝):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

要執行應用程式:

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`可用自 .NET 核心 3.x。 用於`--roll-forward-on-no-candidate-fx`.NET 核心 2.x。

## <a name="description"></a>描述

該`dotnet`指令具有兩個函數:

- 它提供了用於處理 .NET Core 專案的命令。

  例如,[`dotnet build`](dotnet-build.md)生成專案。 每個命令定義自己的選項和參數。 所有命令都支援列印`--help`有關如何使用該命令的簡短文檔的選項。

- 它運行 .NET 核心應用程式。

  指定應用程式`.dll`檔案的路徑以執行應用程式。  執行應用程式意味著查找和執行入口點,在主控台應用的情況下`Main`, 這是方法。 例如,`dotnet myapp.dll``myapp`執行 應用程式。 請參閱[.NET 核心應用程式部署](../deploying/index.md)以瞭解部署選項。

## <a name="options"></a>選項。

不同的選項本身可用於`dotnet`運行命令和運行應用程式。

### <a name="options-for-dotnet-by-itself"></a>點網本身的選項

以下選項`dotnet`本身。 例如： `dotnet --info` 。 他們列印出有關環境的資訊。

- **`--info`**

  會印出關於 .NET Core 安裝和電腦環境的詳細資訊，例如目前作業系統和 .NET Core 版本的認可 SHA。

- **`--version`**

  印出使用中的 .NET Core SDK 版本。

- **`--list-runtimes`**

  列印已安裝的 .NET 核心執行時的清單。 x86 版本的 SDK 僅列出 x86 執行時,x64 版本的 SDK 僅列出 x64 執行時。

- **`--list-sdks`**

  列印已安裝的 .NET 核心 SDK 的清單。

- **`-h|--help`**

  列印出可用命令的清單。

### <a name="sdk-options-for-running-a-command"></a>執行指令的 SDK 選項

以下選項適用於`dotnet`命令。 例如： `dotnet build --help` 。

- **`-d|--diagnostics`**

  啟用診斷輸出。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 每個命令都不支援。 請參閱特定命令頁以確定此選項是否可用。

- **`-h|--help`**

  印出指定命令的文件，例如`dotnet build --help`。

- **`command options`**

  每個命令定義特定於該命令的選項。 有關可用選項的清單,請參閱特定命令頁。

### <a name="runtime-options"></a>執行時選項

執行應用程式時`dotnet`,以下選項可用。 例如： `dotnet myapp.dll --fx-version 3.1.1` 。

- **`--additionalprobingpath <PATH>`**

  包含探查原則和要探查之組件的路徑。

- **`--additional-deps <PATH>`**

  其他 *.deps.json* 檔案的路徑。 *deps.json*檔包含用於解決程式集衝突的依賴項、編譯依賴項和版本資訊的清單。 如需詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。

- **`--fx-version <VERSION>`**

  用來執行應用程式的 .NET Core 執行階段版本。

- **`--runtimeconfig`**

  *runtimeconfig.json* 檔案的路徑。 *運行時 config.json*檔是包含執行時設定的設定檔。 有關詳細資訊,請參閱[.NET Core 執行時設定設定](../run-time-config/index.md#runtimeconfigjson)。

- **`--roll-forward-on-no-candidate-fx <N>`****在 .NET 核心 2.x SDK 中提供。**

  在必要的共用架構無法使用時定義行為。 `N` 可以是：

  - `0` - 對次要版本也停用向前復原。
  - `1` - 對次要版本向前復原，主要版本則不。 此為預設行為。
  - `2` - 對次要及主要版本向前復原。

   如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

- **`--roll-forward <SETTING>`****可從 .NET 核心 SDK 3.0 開始。**

  控制如何向前滾動應用於應用。 `SETTING`可以是以下值之一。 如果未指定,`Minor`則為預設值。

  - `LatestPatch`- 向前滾動到最高補丁版本。 這會停用次要版本向前復原。
  - `Minor`- 如果缺少請求的次要版本,請向前滾動到最低較高的次要版本。 如果要求的次要版本存在，則會使用 LatestPatch 原則。
  - `Major`- 如果缺少請求的主要版本,則向前滾動到最低較高主版本和最低次要版本。 如果要求的主要版本存在，則會使用 Minor 原則。
  - `LatestMinor`- 向前滾動到最高次要版本,即使存在請求的次要版本。 適用於裝載案例的元件。
  - `LatestMajor`- 向前滾動到最高主要和最高的次要版本,即使請求的主要存在。 適用於裝載案例的元件。
  - `Disable`-別向前滾 只會繫結至指定的版本。 此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。 只有測試時才建議使用這個值。

除`Disable`之外 ,所有設置都將使用最高可用的修補程式版本。

前滾行為也可以在專案檔屬性、運行時設定檔屬性和環境變數中配置。 有關詳細資訊,請參閱[主版本執行時向前捲動](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)。

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>一般

| Command                                       | 函式                                                            |
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

### <a name="project-references"></a>專案參考

Command | 函式
--- | ---
[dotnet add reference](dotnet-add-reference.md) | 新增專案參考。
[dotnet list reference](dotnet-list-reference.md) | 列出專案參考。
[dotnet remove reference](dotnet-remove-reference.md) | 移除專案參考。

### <a name="nuget-packages"></a>NuGet 套件

Command | 函式
--- | ---
[dotnet add package](dotnet-add-package.md) | 新增 NuGet 套件。
[dotnet remove package](dotnet-remove-package.md) | 移除 NuGet 套件。

### <a name="nuget-commands"></a>NuGet 命令

Command | 函式
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | 從伺服器刪除或取消列出套件。
[dotnet nuget push](dotnet-nuget-push.md) | 將套件推送至伺服器並發行。
[dotnet nuget locals](dotnet-nuget-locals.md) | 清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。
[dotnet nuget add source](dotnet-nuget-add-source.md) | 添加 NuGet 源。
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | 禁用 NuGet 源。
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | 啟用 NuGet 源。
[dotnet nuget list source](dotnet-nuget-list-source.md) | 列出所有配置的 NuGet 源。
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | 刪除 NuGet 源。
[dotnet nuget update source](dotnet-nuget-update-source.md) | 更新 NuGet 源。

### <a name="global-tool-path-and-local-tools-commands"></a>全域、工具路徑與本地端工具指令

工具是從 NuGet 套件安裝並從命令提示符呼叫的主控台應用程式。 您可以自己編寫工具或安裝由第三方編寫的工具。 工具也稱為全域工具、刀具路徑工具和本地工具。 有關詳細資訊,請參閱[.NET 核心工具概述](global-tools.md)。 全域和工具路徑工具可從 .NET 核心 SDK 2.1 開始。 本地工具可從 .NET 核心 SDK 3.0 開始。

Command | 函式
--- | ---
[dotnet tool install](dotnet-tool-install.md) | 在電腦上安裝工具。
[dotnet tool list](dotnet-tool-list.md) | 列出電腦上目前安裝的所有全域、工具路徑或本地工具。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | 從電腦卸載工具。
[dotnet tool update](dotnet-tool-update.md) | 更新安裝在電腦上的工具。

### <a name="additional-tools"></a>其他工具

從 .NET Core SDK 2.1.300 開始，先前僅能透過 `DotnetCliToolReference` 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。 這些工具列於下列資料表中：

| 工具                                              | 函式                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 建立及管理開發憑證。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core 命令列工具。                    |
| sql-cache                                         | SQL Server 快取命令列工具。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 管理開發使用者祕密。                            |
| [看](/aspnet/core/tutorials/dotnet-watch)      | 啟動會在檔案變更時執行命令的檔案監看員。 |

如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。

## <a name="examples"></a>範例

建立新的 .NET 核心主控台應用程式:

```dotnetcli
dotnet new console
```

建置所指定目錄中的專案和其相依性：

```dotnetcli
dotnet build
```

執行應用程式:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>環境變數

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  指定 .NET Core 執行時的位置(如果它們未安裝在預設位置)。 Windows 上的預設位置`C:\Program Files\dotnet`為 。 Linux 與 macOS`/usr/share/dotnet`上的預設位置為 。 僅當通過生成的可執行檔(應用程式主機)運行應用時,才會使用此環境變數。 `DOTNET_ROOT(x86)`在 64 位元作業系統上運行 32 位元可執行檔時,將改為使用。

- `DOTNET_PACKAGES`

  全域套件資料夾。 如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。

- `DOTNET_SERVICING`

  指定載入執行階段時，共用主機所使用的服務索引位置。

- `DOTNET_NOLOGO`

  指定第一次執行時是否顯示 .NET Core 歡迎消息和遙測消息。 `true`設置為將這些消息靜音(值`true`、`1`或`yes`已接受)或設置為`false`允許(值`false`、`0`或`no`已接受)。 如果未設置,則預設值為`false`,並且消息將在首次運行時顯示。 請注意,此標誌對遙測沒有影響(請參閱`DOTNET_CLI_TELEMETRY_OPTOUT`選擇不發送遙測)。

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  指定是否收集 .NET Core 工作使用資料，並將其傳送給 Microsoft。 設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。 否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。

- `DOTNET_MULTILEVEL_LOOKUP`

  指定是否從全域位置解析 .NET Core 執行階段、共用架構或 SDK。 如果未設置,則預設為 1(`true`邏輯 )。 設置為 0(`false`邏輯 ),以不從全域位置解析,並且具有隔離的 .NET Core 安裝。 如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。

- `DOTNET_ROLL_FORWARD`**可從 .NET 核心 3.x SDK 開始。**

  確定向前滾行行為。 有關詳細資訊,請參閱本文前面`--roll-forward`的選項。

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**在 .NET 核心 2.x SDK 中提供。**

  如果設定為 `0`，將停用次要版本向前復原。 如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

- `DOTNET_CLI_UI_LANGUAGE`

  使用區域設置值(如`en-us`)設置 CLI UI 的語言。 支援的值與 Visual Studio 的值相同。 有關詳細資訊,請參閱[Visual Studio 安裝文檔中](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)有關更改安裝程式語言的部分。 .NET 資源管理員規則適用,因此您不必選擇完全匹配&mdash;項 ,您也可以在樹`CultureInfo`中選擇 後代。 例如,如果將其設置為`fr-CA`,CLI 將查找`fr`並使用 翻譯。 如果將其設置為不支援的語言,則 CLI 將回退為英語。

- `DOTNET_DISABLE_GUI_ERRORS`

  對於啟用 GUI 生成的可執行檔 - 禁用對話框彈出視窗,該對話框通常顯示某些類別的錯誤。 在這種情況下,它只寫入`stderr`和退出。
  
- `DOTNET_ADDITIONAL_DEPS`

  等效於 CLI`--additional-deps`選項。

- `DOTNET_RUNTIME_ID`

  覆蓋檢測到的 RID。

- `DOTNET_SHARED_STORE`

  "共用存儲"的位置,在某些情況下,程式集解析度會回退於該存儲。

- `DOTNET_STARTUP_HOOKS`

  要載入和執行啟動掛鉤的程式集的清單。

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  控制從宿主元件(如`dotnet.exe`)`hostfxr``hostpolicy`和的診斷跟蹤。

## <a name="see-also"></a>另請參閱

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)
- [.NET 核心執行時設定設定](../run-time-config/index.md)
