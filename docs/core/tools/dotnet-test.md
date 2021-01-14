---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 04/29/2020
ms.openlocfilehash: 4834da766bd052f44127a72635b65866eb7e3352
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189150"
---
# <a name="dotnet-test"></a>dotnet test

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Description

此 `dotnet test` 命令可用來在指定的解決方案中執行單元測試。 此 `dotnet test` 命令會建立方案，並針對方案中的每個測試專案執行測試主機應用程式。 測試主機會使用測試架構在指定的專案中執行測試，例如： MSTest、NUnit 或 xUnit，並報告每項測試的成功或失敗。 如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。

針對多目標專案，會針對每個目標架構執行測試。 測試主機和單元測試架構會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

測試 `Microsoft.NET.Test.Sdk` 主控制項 `xunit` 是測試架構。 和 `xunit.runner.visualstudio` 是測試介面卡，可讓 xUnit 架構搭配測試主機使用。

### <a name="implicit-restore"></a>隱含還原

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>引數

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - 測試專案的路徑。
  - 解決方案的路徑。
  - 包含專案或方案之目錄的路徑。
  - 測試專案 *.dll* 檔案的路徑。

  如果未指定，則會在目前的目錄中搜尋專案或方案。

## <a name="options"></a>選項

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  要在其中搜尋其他測試介面卡之目錄的路徑。 只會檢查具有尾碼的 *.dll* 檔案。 `.TestAdapter.dll` 如果未指定，則會搜尋 test *.dll* 的目錄。

- **`--blame`**

  在歸責模式下執行測試。 此選項有助於隔離導致測試主機損毀的有問題的測試。 當偵測到損毀時，它會在中建立一個序列檔案 `TestResults/<Guid>/<Guid>_Sequence.xml` ，該檔案會捕捉損毀之前執行的測試順序。

- **`--blame-crash`** 自 .NET 5.0 preview SDK 起可用 () 

  在有問題的模式下執行測試，並在測試主機非預期地結束時收集損毀傾印。 此選項取決於所使用的 .NET 版本、錯誤類型和作業系統。
  
  針對 managed 程式碼中的例外狀況，將會自動收集 .NET 5.0 和更新版本的傾印。 它會產生 testhost 的傾印或任何子進程（也會在 .NET 5.0 中執行並損毀）。 機器碼中的當機不會產生傾印。 此選項適用于 Windows、macOS 和 Linux。
  
  原生程式碼中的損毀傾印，或使用 .NET Core 3.1 或更早版本時，只能使用 Procdump 在 Windows 上收集。 包含 *procdump.exe* 和 *procdump64.exe* 的目錄必須在 PATH 或 PROCDUMP_PATH 環境變數中。 [下載工具](/sysinternals/downloads/procdump)。 意指 `--blame` 。
  
  若要從 .NET 5.0 或更新版本上執行的原生應用程式收集損毀傾印，可將環境變數設為，以強制使用 Procdump `VSTEST_DUMP_FORCEPROCDUMP` `1` 。

- **`--blame-crash-dump-type <DUMP_TYPE>`** 自 .NET 5.0 preview SDK 起可用 () 

  要收集的損毀傾印類型。 意指 `--blame-crash` 。

- **`--blame-crash-collect-always`** 自 .NET 5.0 preview SDK 起可用 () 

  收集預期的損毀傾印，以及未預期的測試主機結束。

- **`--blame-hang`** 自 .NET 5.0 preview SDK 起可用 () 

  在有阻礙的模式下執行測試，並在測試超過指定的超時時間時收集停止回應傾印。

- **`--blame-hang-dump-type <DUMP_TYPE>`** 自 .NET 5.0 preview SDK 起可用 () 

  要收集的損毀傾印類型。 它應該是 `full` 、 `mini` 或 `none` 。 當 `none` 指定時，會在超時時終止測試主機，但不會收集任何傾印。 意指 `--blame-hang` 。

- **`--blame-hang-timeout <TIMESPAN>`** 自 .NET 5.0 preview SDK 起可用 () 

  每個測試的超時時間，在這之後會觸發停止回應傾印，並傾印及終止測試主機進程及其所有子進程。 Timeout 值是以下列其中一種格式來指定：
  
  - 1.5 h，1.5 小時，1.5 小時
  - 90m, 90min, 90minute, 90minutes
  - 5400s, 5400sec, 5400second, 5400seconds
  - 5400000ms, 5400000mil, 5400000millisecond, 5400000milliseconds

  如果未使用任何單位 (例如 5400000) ，則會假設值為毫秒。 搭配資料驅動的測試使用時，超時行為取決於所使用的測試介面卡。 若為 xUnit 和 NUnit，則會在每個測試案例之後更新 timeout。 針對 MSTest，所有測試案例都會使用此超時時間。 使用 netcoreapp 2.1 和更新版本的 Windows、Linux 上的 netcoreapp 3.1 和更新版本，以及使用 net 5.0 或更新版本的 macOS 上，都支援此選項。 意指 `--blame` 和 `--blame-hang` 。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。

- **`--collect <DATA_COLLECTOR_NAME>`**

  測試回合啟用資料收集器。 如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。
  
  若要在 .NET Core 支援的任何平臺上收集程式碼涵蓋範圍，請安裝 [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) 並使用 `--collect:"XPlat Code Coverage"` 選項。

  在 Windows 上，您可以使用選項來收集程式碼涵蓋範圍 `--collect "Code Coverage"` 。 此選項會產生一個 *涵蓋範圍* 檔案，該檔案可在 Visual Studio 2019 Enterprise 中開啟。 如需詳細資訊，請參閱 [使用程式碼涵蓋範圍](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) 和 [自訂程式碼涵蓋範圍分析](/visualstudio/test/customizing-code-coverage-analysis)。

- **`-d|--diag <LOG_FILE>`**

  針對測試平臺啟用診斷模式，並將診斷訊息寫入至指定的檔案和其旁邊的檔案。 記錄訊息的程式會決定要建立哪些檔案，例如 `*.host_<date>.txt` 用於測試主機記錄檔，以及 `*.datacollector_<date>.txt` 資料收集器記錄檔。

- **`-f|--framework <FRAMEWORK>`**

  強制將 `dotnet` 或 .NET Framework 測試主機用於測試二進位檔。 此選項只會決定要使用的主機類型。 實際要使用的 framework 版本取決於測試專案的 *runtimeconfig.js* 。 如果未指定，則會使用 [TargetFramework 元件屬性](/dotnet/api/system.runtime.versioning.targetframeworkattribute) 來判斷主機的類型。 從 *.dll* 中移除該屬性時，會使用 .NET Framework 主機。

- **`--filter <EXPRESSION>`**

  使用指定的運算式篩選出目前專案中的測試。 如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。 如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

- **`-l|--logger <LOGGER>`**

  指定測試結果的記錄器。 與 MSBuild 不同的是，dotnet test 不接受縮寫：而不是 `-l "console;v=d"` 使用 `-l "console;verbosity=detailed"` 。 指定參數多次以啟用多個記錄器。

- **`--no-build`**

  不會在執行前建置測試專案。 它也會隱含地設定- `--no-restore` 旗標。

- **`--nologo`**

  執行測試而不顯示 Microsoft TestPlatform 橫幅。 自 .NET Core 3.0 SDK 起提供。

- **`--no-restore`**

  執行命令時，不會執行隱含還原。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  在其中尋找要執行的二進位檔的目錄。 如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。  針對具有多個目標 framework 的專案 (透過 `TargetFrameworks` 屬性) ，您也需要在 `--framework` 指定此選項時定義。 `dotnet test` 一律從輸出目錄執行測試。 您可以使用 <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> 來取用輸出目錄中的測試資產。

- **`-r|--results-directory <RESULTS_DIR>`**

  要放置測試結果的目錄。 如果指定的目錄不存在，則會建立該目錄。 預設值 `TestResults` 在包含專案檔的目錄中。

- **`--runtime <RUNTIME_IDENTIFIER>`**

  要測試的目標執行時間。

- **`-s|--settings <SETTINGS_FILE>`**

  用來執行測試的 `.runsettings` 檔案。 `TargetPlatform` (x86 | x64) 的元素沒有任何作用 `dotnet test` 。 若要執行以 x86 為目標的測試，請安裝 .NET Core 的 x86 版本。 路徑上的 *dotnet.exe* 位是將用來執行測試的。 如需詳細資訊，請參閱下列資源：

  - [使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。
  - [設定測試回合](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)

- **`-t|--list-tests`**

  列出探索到的測試，而不是執行測試。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設為 `minimal`。 如需詳細資訊，請參閱<xref:Microsoft.Build.Framework.LoggerVerbosity>。

- **`RunSettings`** 參數

 在 `RunSettings` "--" 之後，命令列上的最後一個引數會以內嵌的形式傳遞， (記下的空格--) 。 內嵌 `RunSettings` 是指定 `[name]=[value]` 成對的。 空格適用來分隔多個 `[name]=[value]` 組。

  範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  如需詳細資訊，請參閱 [透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。

## <a name="examples"></a>範例

- 執行目前目錄之專案中的測試：

  ```dotnetcli
  dotnet test
  ```

- 執行 `test1` 專案中的測試︰

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- 在目前目錄中的專案中執行測試，並以 .trx 格式產生測試結果檔案：

  ```dotnetcli
  dotnet test --logger trx
  ```

- 在目前目錄中的專案中執行測試，並在安裝 [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) 收集器整合) 之後產生程式碼涵蓋範圍檔案 (：

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- 在目前目錄中的專案中執行測試，並將程式碼涵蓋範圍檔案 (僅限 Windows) ：

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- 在目前目錄中的專案中執行測試，並以詳細的詳細資訊記錄到主控台：

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- 在目前目錄中的專案中執行測試，並在測試主機當機時進行報表測試：

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a>篩選選項詳細資料

`--filter <EXPRESSION>`

`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。

`<property>` 為 `Test Case` 的屬性。 以下為熱門單元測試架構所支援的屬性：

| 測試架構 | 支援的屬性                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>名稱</li><li>ClassName</li><li>優先順序</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>特性</li></ul>                                   |
| NUnit          | <ul><li>FullyQualifiedName</li><li>名稱</li><li>TestCategory</li><li>優先順序</li></ul>                                   |

`<operator>` 描述屬性和值之間的關聯性：

| 運算子 | 函式        |
| :------: | --------------- |
| `=`      | 完全相符     |
| `!=`     | 不完全相符 |
| `~`      | 包含        |
| `!~`     | Not contains    |

`<value>` 為字串。 所有的查閱皆不區分大小寫。

沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。

運算式可以使用條件運算子聯結：

| 運算子            | 函式 |
| ------------------- | -------- |
| <code>&#124;</code> | 或者       |
| `&`                 | AND      |

使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。

如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

## <a name="see-also"></a>另請參閱

- [架構與目標](../../standard/frameworks.md)
- [.NET 執行時間識別碼 (RID) 目錄](../rid-catalog.md)
- [透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
