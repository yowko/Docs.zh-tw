---
title: dotnet 命令
description: 瞭解 dotnet 命令 (.NET CLI 的一般驅動程式) 和其使用方式。
ms.date: 11/11/2020
ms.openlocfilehash: a2b4b026e7c89536a6a7eaf69b31e3f62bf5adfc
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556823"
---
# <a name="dotnet-command"></a>dotnet 命令

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet` -.NET CLI 的一般驅動程式。

## <a name="synopsis"></a>概要

若要取得可用命令和環境的相關資訊：

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

若要執行命令 (需要 SDK 安裝) ：

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

若要執行應用程式：

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` 自 .NET Core 3.x 起提供。 用於 `--roll-forward-on-no-candidate-fx` .Net Core 2.x。

## <a name="description"></a>描述

此 `dotnet` 命令有兩個功能：

- 它提供使用 .NET 專案的命令。

  例如， [`dotnet build`](dotnet-build.md) 建立專案。 每個命令都會定義自己的選項和引數。 所有命令都支援 `--help` 列印出有關如何使用命令的簡短檔的選項。

- 它會執行 .NET 應用程式。

  您可以指定應用程式檔的路徑 `.dll` 來執行應用程式。  若要執行應用程式，您可以尋找並執行進入點，在主控台應用程式的案例中，這是 `Main` 方法。 例如，會 `dotnet myapp.dll` 執行 `myapp` 應用程式。 若要瞭解部署選項，請參閱 [.net 應用程式部署](../deploying/index.md) 。

## <a name="options"></a>選項

您可以使用不同的選項來執行 `dotnet` 命令，以及執行應用程式。

### <a name="options-for-dotnet-by-itself"></a>Dotnet 本身的選項

以下是本身的選項 `dotnet` 。 例如，`dotnet --info`。 他們會列印環境的相關資訊。

- **`--info`**

  列印 .NET 安裝和電腦環境的詳細資訊，例如目前的作業系統，以及 .NET 版本的認可 SHA。

- **`--version`**

  列印出使用中的 .NET SDK 版本。

- **`--list-runtimes`**

  列印已安裝之 .NET 執行時間的清單。 X86 版本的 SDK 只會列出 x86 執行時間，而 x64 版本的 SDK 只會列出 x64 執行時間。

- **`--list-sdks`**

  列印已安裝的 .NET Sdk 清單。

- **`-h|--help`**

  列印出可用命令的清單。

### <a name="sdk-options-for-running-a-command"></a>用來執行命令的 SDK 選項

以下是 `dotnet` 使用命令的選項。 例如，`dotnet build --help`。

- **`-d|--diagnostics`**

  啟用診斷輸出。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 不支援每個命令。 請參閱特定的命令頁面，判斷此選項是否可用。

- **`-h|--help`**

  印出指定命令的文件，例如`dotnet build --help`。

- **`command options`**

  每個命令都會定義該命令特定的選項。 請參閱特定的命令頁面，以取得可用選項的清單。

### <a name="runtime-options"></a>執行時間選項

當您執行應用程式時，可以使用下列選項 `dotnet` 。 例如，`dotnet myapp.dll --roll-forward Major`。

- **`--additionalprobingpath <PATH>`**

  包含探查原則和要探查之組件的路徑。

- **`--additional-deps <PATH>`**

  其他 *.deps.json* 檔案的路徑。 檔案 *deps.js* 包含相依性、編譯相依性的清單，以及用來解決元件衝突的版本資訊。 如需詳細資訊，請參閱 GitHub 上的 [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)。

- **`--depsfile <PATH_TO_DEPSFILE>`**

  檔案 *deps.js* 的路徑。 檔案 *上的deps.js* 是一個設定檔，其中包含執行應用程式所需相依性的相關資訊。 這個檔案是由 .NET SDK 產生。

- **`--runtimeconfig`**

  *runtimeconfig.json* 檔案的路徑。 檔案 *上的runtimeconfig.js* 是包含執行時間設定的設定檔。 如需詳細資訊，請參閱 [.net 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。

- **`--roll-forward <SETTING>`****從 .NET Core SDK 3.0 開始提供。**

  控制如何將向前復原套用至應用程式。 `SETTING`可以是下列其中一個值。 如果未指定， `Minor` 則為預設值。

  - `LatestPatch` -向前復原到最高的修補程式版本。 這會停用次要版本向前復原。
  - `Minor` -如果遺漏要求的次要版本，則向前復原到最低的次要版本。 如果要求的次要版本存在，則會使用 LatestPatch 原則。
  - `Major` -如果缺少要求的主要版本，則向前復原到最低的最高主要版本，以及最低的次要版本。 如果要求的主要版本存在，則會使用 Minor 原則。
  - `LatestMinor` -向前復原到最高的次要版本，即使有要求的次要版本存在也一樣。 適用於裝載案例的元件。
  - `LatestMajor` -向前復原到最高的主要和最高次要版本，即使有要求的主要存在。 適用於裝載案例的元件。
  - `Disable` -不要向前復原。 只會繫結至指定的版本。 此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。 只有測試時才建議使用這個值。

  除了之外 `Disable` ，所有設定都會使用最高可用的修補程式版本。

  向前復原行為也可以在專案檔案屬性、執行時間配置檔案屬性和環境變數中設定。 如需詳細資訊，請參閱 [主要版本執行時間向前](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)復原。

- **`--roll-forward-on-no-candidate-fx <N>`****適用于 .Net Core 2.X SDK。**

  在必要的共用架構無法使用時定義行為。 `N` 可以是：

  - `0` - 對次要版本也停用向前復原。
  - `1` - 對次要版本向前復原，主要版本則不。 此為預設行為。
  - `2` - 對次要及主要版本向前復原。

  如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

  從 .NET Core 3.0 開始，此選項會被取代 `--roll-forward` ，而且應該改用該選項。

- **`--fx-version <VERSION>`**

  要用來執行應用程式的 .NET 執行階段版本。

  此選項會覆寫應用程式檔案中第一個架構參考的版本 `.runtimeconfig.json` 。 這表示如果只有一個架構參考，它只會如預期般運作。 如果應用程式有一個以上的架構參考，則使用這個選項可能會導致錯誤。

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>一般

| 命令                                       | 函式                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | 建立 .NET 應用程式。                                     |
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

命令 | 函式
--- | ---
[dotnet add reference](dotnet-add-reference.md) | 新增專案參考。
[dotnet list reference](dotnet-list-reference.md) | 列出專案參考。
[dotnet remove reference](dotnet-remove-reference.md) | 移除專案參考。

### <a name="nuget-packages"></a>NuGet 套件

命令 | 函式
--- | ---
[dotnet add package](dotnet-add-package.md) | 新增 NuGet 套件。
[dotnet remove package](dotnet-remove-package.md) | 移除 NuGet 套件。

### <a name="nuget-commands"></a>NuGet 命令

命令 | 函式
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | 從伺服器刪除或取消列出套件。
[dotnet nuget push](dotnet-nuget-push.md) | 將套件推送至伺服器並發行。
[dotnet nuget locals](dotnet-nuget-locals.md) | 清除或列出本機 NuGet 資源，例如 http-request 快取、暫時快取，或整部電腦的全域套件資料夾。
[dotnet nuget add source](dotnet-nuget-add-source.md) | 新增 NuGet 來源。
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | 停用 NuGet 來源。
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | 啟用 NuGet 來源。
[dotnet nuget list source](dotnet-nuget-list-source.md) | 列出所有已設定的 NuGet 來源。
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | 移除 NuGet 來源。
[dotnet nuget update source](dotnet-nuget-update-source.md) | 更新 NuGet 來源。

### <a name="global-tool-path-and-local-tools-commands"></a>全域、工具路徑和本機工具命令

工具是從 NuGet 套件安裝的主控台應用程式，會從命令提示字元叫用。 您可以自行撰寫工具或安裝協力廠商所撰寫的工具。 工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。 如需詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。 從 .NET Core SDK 2.1 開始，可以使用全域和工具路徑工具。 從 .NET Core SDK 3.0 開始，可以使用本機工具。

命令 | 函式
--- | ---
[dotnet tool install](dotnet-tool-install.md) | 在您的電腦上安裝工具。
[dotnet tool list](dotnet-tool-list.md) | 列出電腦上目前已安裝的所有全域、工具路徑或本機工具。
[dotnet 工具搜尋](dotnet-tool-list.md) | 搜尋 NuGet.org 是否有在其名稱或中繼資料中具有指定之搜尋詞彙的工具。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | 從您的電腦卸載工具。
[dotnet tool update](dotnet-tool-update.md) | 更新電腦上所安裝的工具。

### <a name="additional-tools"></a>其他工具

從 .NET Core SDK 2.1.300 開始，使用的一些工具現在僅適用于以專案為基礎的工具， `DotnetCliToolReference` 現在已可在 .NET SDK 中使用。 這些工具列於下列資料表中：

| 工具                                              | 函式                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 建立及管理開發憑證。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core 命令列工具。                    |
| sql-cache                                         | SQL Server 快取命令列工具。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 管理開發使用者祕密。                            |
| [看](/aspnet/core/tutorials/dotnet-watch)      | 啟動會在檔案變更時執行命令的檔案監看員。 |

如需每個工具的詳細資訊，請鍵入 `dotnet <tool-name> --help`。

## <a name="examples"></a>範例

建立新的 .NET Core 主控台應用程式：

```dotnetcli
dotnet new console
```

建置所指定目錄中的專案和其相依性：

```dotnetcli
dotnet build
```

執行應用程式：

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>環境變數

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  指定 .NET 執行時間的位置（如果未安裝在預設位置）。 Windows 上的預設位置為 `C:\Program Files\dotnet` 。 Linux 和 macOS 上的預設位置為 `/usr/share/dotnet` 。 此環境變數只會在透過產生的可執行檔（ (apphosts) ）執行應用程式時使用。 `DOTNET_ROOT(x86)` 當在64位作業系統上執行32位可執行檔時，會改用

- `NUGET_PACKAGES`

  全域套件資料夾。 如果未設定，預設為 `~/.nuget/packages` (Unix) 或 `%userprofile%\.nuget\packages` (Windows)。

- `DOTNET_SERVICING`

  指定載入執行階段時，共用主機所使用的服務索引位置。

- `DOTNET_NOLOGO`

  指定是否要在第一次執行時顯示 .NET 歡迎畫面和遙測訊息。 設定為可將 `true` 這些訊息靜音 (值 `true` 、 `1` 或 `yes` 接受) 或設定為， `false` 以允許 (值 `false` 、 `0` 或 `no` 接受) 。 如果未設定，預設值為， `false` 而訊息將會在第一次執行時顯示。 此旗標不會影響遙測 (請參閱退出傳送 `DOTNET_CLI_TELEMETRY_OPTOUT` 遙測) 。

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  指定是否收集 .NET 工具使用量的相關資料，並將其傳送給 Microsoft。 設為 `true` 以選擇加入遙測功能 (可接受的值為 `true`、`1` 或 `yes`)。 否則，請設為 `false` 以選擇退出遙測功能 (可接受的值為 `false`、`0` 或 `no`)。 如果未設定，預設值為 `false`，且遙測功能會處於作用狀態。

- `DOTNET_MULTILEVEL_LOOKUP`

  指定是否從全域位置解析 .NET 執行時間、共用架構或 SDK。 如果未設定，則預設為 1 (邏輯 `true`) 。 設定為 0 (邏輯 `false`) 不會從全域位置解析，並且具有隔離的 .net 安裝。 如需多層級查閱的詳細資訊，請參閱 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md) (多層級 SharedFX 查閱)。

- `DOTNET_ROLL_FORWARD`**從 .Net Core 3.x 開始提供。**

  判斷向前復原行為。 如需詳細資訊，請參閱本文稍 `--roll-forward` 早的選項。

- `DOTNET_ROLL_FORWARD_TO_PRERELEASE`**從 .Net Core 3.x 開始提供。**

  如果設定為 `1` (啟用) ，則可從發行版本向前復原至發行前版本。 依預設 (`0` -disabled) ，當要求 .net 執行時間的發行版本時，向前復原只會考慮已安裝的發行版本。

  如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)。

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**適用于 .Net Core 2.x。**

  如果設定為 `0`，將停用次要版本向前復原。 如需詳細資訊，請參閱[向前復原](../whats-new/dotnet-core-2-1.md#roll-forward)。

  這項設定已在 .NET Core 3.0 中取代 `DOTNET_ROLL_FORWARD` 。 您應改為使用新的設定。

- `DOTNET_CLI_UI_LANGUAGE`

  使用地區設定值（例如）設定 CLI UI 的語言 `en-us` 。 支援的值與 Visual Studio 的值相同。 如需詳細資訊，請參閱 [Visual Studio 安裝檔](/visualstudio/install/install-visual-studio)中的變更安裝程式語言一節。 適用 .NET resource manager 規則，因此您不需要挑選完全相符的結果， &mdash; 您也可以在樹狀目錄中挑選子系 `CultureInfo` 。 例如，如果您將它設定為 `fr-CA` ，CLI 會尋找並使用 `fr` 翻譯。 如果您將它設定為不支援的語言，CLI 會切換回英文。

- `DOTNET_DISABLE_GUI_ERRORS`

  啟用 GUI 的已產生可執行檔-停用對話方塊快顯視窗，通常會針對某些錯誤類別顯示。 它只會 `stderr` 在這些情況下寫入和結束。
  
- `DOTNET_ADDITIONAL_DEPS`

  相當於 CLI 選項 `--additional-deps` 。

- `DOTNET_RUNTIME_ID`

  覆寫偵測到的 RID。

- `DOTNET_SHARED_STORE`

  「共用存放區」的位置，在某些情況下，元件解析會回復為。

- `DOTNET_STARTUP_HOOKS`

  要載入和執行啟動攔截的元件清單。

- `DOTNET_BUNDLE_EXTRACT_BASE_DIR`**從 .Net Core 3.x 開始提供。**

  指定在執行單一檔案應用程式之前解壓縮的目錄。

  如需詳細資訊，請參閱 [單一檔案可執行](../whats-new/dotnet-core-3-0.md#single-file-executables)檔。

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  控制來自裝載元件的診斷追蹤，例如 `dotnet.exe` 、 `hostfxr` 和 `hostpolicy` 。

  * `COREHOST_TRACE=[0/1]` -預設為 `0` -追蹤已停用。 如果設定為 `1` ，則會啟用診斷追蹤。
  * `COREHOST_TRACEFILE=<file path>` -只有在啟用追蹤時，才會有作用 `COREHOST_TRACE=1` 。 設定時，追蹤資訊會寫入至指定的檔案，否則會將追蹤資訊寫入至 `stderr` 。 **從 .NET Core 3.x 開始提供。**
  * `COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -預設值為 `4` 。 只有透過啟用追蹤時，才會使用此設定 `COREHOST_TRACE=1` 。 **從 .NET Core 3.x 開始提供。**
    * `4` -寫入所有追蹤資訊
    * `3` -只寫入參考、警告和錯誤訊息
    * `2` -只寫入警告和錯誤訊息
    * `1` -只寫入錯誤訊息

  取得應用程式啟動詳細追蹤資訊的一般方式是設定，然後 `COREHOST_TRACE=1` `COREHOST_TRACEFILE=host_trace.txt` 執行應用程式。 `host_trace.txt`將會在目前目錄中建立含有詳細資訊的新檔案。

## <a name="see-also"></a>另請參閱

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) (執行階段組態檔)
- [.NET 執行時間設定](../run-time-config/index.md)
