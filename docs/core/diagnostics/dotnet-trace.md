---
title: dotnet-追蹤診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet 追蹤 CLI 工具，以使用 .NET EventPipe 來收集執行中進程的 .NET 追蹤，而不使用原生 profiler。
ms.date: 11/17/2020
ms.openlocfilehash: a2925ac0a0815fe48ca9b36b643ff896aa3c0ff6
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593203"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet-追蹤效能分析公用程式

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="install"></a>安裝

有兩種方式可以下載和安裝 `dotnet-trace` ：

- **dotnet global tool：**

  若要安裝 `dotnet-trace` [NuGet 套件](https://www.nuget.org/packages/dotnet-trace)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- **直接下載：**

  下載符合您平臺的工具可執行檔：

  | OS  | 平台 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-trace/win-x86) \|[x64](https://aka.ms/dotnet-trace/win-x64) \|[arm](https://aka.ms/dotnet-trace/win-arm) \|[arm-x64](https://aka.ms/dotnet-trace/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-trace/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-trace/linux-x64) \|[arm](https://aka.ms/dotnet-trace/linux-arm) \|[arm64](https://aka.ms/dotnet-trace/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64) |

## <a name="synopsis"></a>概要

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-trace`工具：

* 是跨平臺 .NET Core 工具。
* 在不使用原生分析工具的情況下，啟用正在執行之進程的 .NET Core 追蹤收集。
* 是以 [`EventPipe`](./eventpipe.md) .Net Core 執行時間為基礎。
* 在 Windows、Linux 或 macOS 上提供相同的體驗。

## <a name="options"></a>選項

- **`-h|--help`**

  顯示命令列說明。

- **`--version`**

  顯示 dotnet 追蹤公用程式的版本。

## <a name="commands"></a>命令

| 命令                                                   |
|-----------------------------------------------------------|
| [dotnet-追蹤收集](#dotnet-trace-collect)             |
| [dotnet-追蹤轉換](#dotnet-trace-convert)             |
| [dotnet-追蹤 ps](#dotnet-trace-ps)                       |
| [dotnet-追蹤清單-設定檔](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-追蹤收集

從正在執行的進程收集診斷追蹤。

### <a name="synopsis"></a>概要

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a>選項

- **`--buffersize <size>`**

  設定記憶體中的圓形緩衝區大小（以 mb 為單位）。 預設值為 256 MB。

- **`--clreventlevel <clreventlevel>`**

  要發出之 CLR 事件的詳細資訊。

- **`--clrevents <clrevents>`**

  要發出之 CLR 運行時間事件的清單。

- **`--format {Chromium|NetTrace|Speedscope}`**

  設定追蹤檔案轉換的輸出格式。 預設值為 `NetTrace`。

- **`-n, --name <name>`**

  要從中收集追蹤的進程名稱。

- **`--diagnostic-port <path-to-port>`**

  要建立之診斷埠的名稱。 請參閱 [使用診斷埠從應用程式啟動收集追蹤](#use-diagnostic-port-to-collect-a-trace-from-app-startup) ，以瞭解如何使用此選項從應用程式啟動收集追蹤。

- **`-o|--output <trace-file-path>`**

  所收集之追蹤資料的輸出路徑。 如果未指定，則預設為 `trace.nettrace` 。

- **`-p|--process-id <PID>`**

  從中收集追蹤的處理序識別碼。

- **`--profile <profile-name>`**

  一組名為預先定義的提供者設定，可讓您簡潔地指定常見的追蹤案例。 可用設定檔如下：

 | 設定檔 | 說明 |
 |---------|-------------|
 |`cpu-sampling`|適用于追蹤 CPU 使用量和一般 .NET 執行時間資訊。 如果未指定任何設定檔或提供者，這是預設選項。|
 |`gc-verbose`|追蹤 GC 集合和範例物件配置。|
 |`gc-collect`|只會以極低的負荷追蹤 GC 集合。|

- **`--providers <list-of-comma-separated-providers>`**

  要啟用的提供者清單（以逗號分隔） `EventPipe` 。 這些提供者補充了所暗示的任何提供者 `--profile <profile-name>` 。 如果特定提供者有任何不一致的情況，此設定會優先于設定檔中的隱含設定。

  這份提供者清單的格式如下：

  - `Provider[,Provider]`
  - `Provider` 的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` 。
  - `KeyValueArgs` 的格式為： `[key1=value1][;key2=value2]` 。

- **`-- <command>` 僅執行 .NET 5.0 的目標應用程式 ()**

  在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。 這在診斷程式早期發生的問題（例如啟動效能問題或元件載入器和系結器錯誤）時，可能會很有説明。

  > [!NOTE]
  > 使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。 因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。

> [!NOTE]
> 針對大型應用程式，停止追蹤可能需要很長的時間 (最多幾分鐘的時間) 。 執行時間必須針對追蹤中所捕捉的所有 managed 程式碼，傳送類型快取。

## <a name="dotnet-trace-convert"></a>dotnet-追蹤轉換

將 `nettrace` 追蹤轉換成替代的格式，以搭配使用替代的追蹤分析工具。

### <a name="synopsis"></a>概要

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>引數

- **`<input-filename>`**

  要轉換的輸入追蹤檔案。 預設值為 *nettrace*。

### <a name="options"></a>選項

- **`--format <Chromium|NetTrace|Speedscope>`**

  設定追蹤檔案轉換的輸出格式。

- **`-o|--output <output-filename>`**

  輸出檔案名。 將會新增目標格式的擴充。

> [!NOTE]
> 將檔案轉換 `nettrace` 成或檔案無法 `chromium` `speedscope` 復原。 `speedscope` 和檔案 `chromium` 沒有重建檔案所需的所有資訊 `nettrace` 。 不過，此 `convert` 命令會保留原始檔案 `nettrace` ，因此，如果您打算在未來開啟此檔案，請勿刪除此檔案。

## <a name="dotnet-trace-ps"></a>dotnet-追蹤 ps

 列出可從中收集追蹤的 dotnet 進程。

### <a name="synopsis"></a>概要

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-追蹤清單-設定檔

列出預先建立的追蹤設定檔，其中包含每個設定檔中提供者和篩選器的描述。

### <a name="synopsis"></a>概要

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>使用 dotnet 收集追蹤

若要使用 `dotnet-trace` 下列內容收集追蹤：

- 取得 .NET Core 應用程式 (PID) 的處理序識別碼，以從中收集追蹤。

  - 例如，在 Windows 上，您可以使用工作管理員或 `tasklist` 命令。
  - 例如，在 Linux 上， `ps` 命令。
  - [dotnet-追蹤 ps](#dotnet-trace-ps)

- 執行下列命令：

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  上述命令會產生類似下列的輸出：

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- 按下按鍵以停止收集 `<Enter>` 。 `dotnet-trace` 將會完成 *nettrace* 檔案的記錄事件。

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a>啟動子應用程式，並使用 dotnet 從啟動中收集追蹤

> [!IMPORTANT]
> 這僅適用于執行 .NET 5.0 或更新版本的應用程式。

有時候，從啟動時收集處理常式的追蹤可能會很有用。 針對執行 .NET 5.0 或更新版本的應用程式，您可以使用 dotnet 來執行這項作業。

這會 `hello.exe` 以 `arg1` 和它的 `arg2` 命令列引數啟動，並從其執行時間啟動中收集追蹤：

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

上述命令會產生類似下列的輸出：

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

您可以按或鍵來停止收集 `<Enter>` 追蹤 `<Ctrl + C>` 。 這樣做也會結束 `hello.exe` 。

> [!NOTE]
> 透過 `hello.exe` dotnet 追蹤會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 互動。
> 透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。
> 如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a>使用診斷埠從應用程式啟動收集追蹤

  > [!IMPORTANT]
  > 這僅適用于執行 .NET 5.0 或更新版本的應用程式。

診斷埠是新增在 .NET 5 中的新執行時間功能，可讓您從應用程式啟動開始追蹤。 若要使用來執行此作業， `dotnet-trace` 您可以使用 `dotnet-trace collect -- <command>` 如上述範例中所述，或使用 `--diagnostic-port` 選項。

使用 `dotnet-trace <collect|monitor> -- <command>` 以子進程的形式啟動應用程式，是從啟動時快速追蹤它的最簡單方式。

但是，當您想要更精確地控制追蹤的應用程式存留期 (例如，只在前10分鐘內監視應用程式並繼續執行) 或者，如果您需要使用 CLI 與應用程式互動，使用 `--diagnostic-port` 選項可讓您控制受監視的目標應用程式和 `dotnet-trace` 。

1. 下列命令會建立 `dotnet-trace` 名為的診斷通訊端 `myport.sock` ，並等候連接。

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    輸出：

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. 在個別的主控台中，啟動目標應用程式，並將環境變數 `DOTNET_DiagnosticPorts` 設為輸出中的值 `dotnet-trace` 。

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    如此一 `dotnet-trace` 來，就可以開始追蹤 `my-dotnet-app` ：

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > 啟動您的應用程式可能 `dotnet run` 會造成問題，因為 DOTNET CLI 可能會產生許多不是您應用程式的子進程，而且它們可以在您的應用 `dotnet-trace` 程式之前連線，讓您的應用程式在執行時間暫停。 建議您直接使用應用程式的獨立版本，或用 `dotnet exec` 來啟動應用程式。

## <a name="view-the-trace-captured-from-dotnet-trace"></a>查看從 dotnet 捕捉的追蹤

在 Windows 中，可以在 [PerfView](https://github.com/microsoft/perfview)上查看 *nettrace* 檔案以供分析：對於在其他平臺上收集的追蹤，追蹤檔案可以移至要在 PerfView 上查看的 Windows 機器。

在 Linux 上，您可以藉由將的輸出格式變更 `dotnet-trace` 為來查看追蹤 `speedscope` 。 您可以使用選項來變更輸出檔案格式 `-f|--format` - `-f speedscope` 將會 `dotnet-trace` 產生檔案 `speedscope` 。 您可以選擇 `nettrace` (預設選項) 和 `speedscope` 。 `Speedscope` 您可以在中開啟檔案 <https://www.speedscope.app> 。

> [!NOTE]
> .NET Core 執行時間會以格式產生追蹤 `nettrace` 。 追蹤會轉換成 speedscope (如果在追蹤完成後指定) 。 因為某些轉換可能會導致資料遺失，所以 `nettrace` 已轉換的檔案旁邊會保留原始檔案。

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>使用 dotnet 來收集一段時間內的計數器值

`dotnet-trace` 可以：

* 用於 `EventCounter` 效能敏感性環境中的基本健康情況監視。 例如，在生產環境中。
* 收集追蹤，讓它們不需要即時觀看。

例如，若要收集執行時間效能計數器值，請使用下列命令：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

上述命令會告知執行時間計數器每秒回報一次，以進行輕量健康情況監視。 以 `EventCounterIntervalSec=1` 較高的值取代 (例如，60) 可讓您以較少的資料細微性收集計數器資料中較小的追蹤。

下列命令可減少額外負荷和追蹤大小，而不是前一個：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

上述命令會停用運行時間事件和 managed stack profiler。

## <a name="net-providers"></a>.NET 提供者

.NET Core 執行時間支援下列 .NET 提供者。 .NET Core 會使用相同的關鍵字來啟用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 追蹤。

| 提供者名稱                            | 資訊 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [執行階段提供者](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR 執行時間關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [取消提供者](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR 取消關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | 啟用範例 profiler。 |
