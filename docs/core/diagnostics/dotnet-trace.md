---
title: dotnet-追蹤工具-.NET Core
description: 安裝和使用 dotnet 追蹤命令列工具。
ms.date: 11/21/2019
ms.openlocfilehash: 6dd968dc49522229dca02c0dc6f3de898026dd82
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924847"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet-追蹤效能分析公用程式

**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="install-dotnet-trace"></a>安裝 dotnet-追蹤

`dotnet-trace`使用[dotnet tool install](../tools/dotnet-tool-install.md)命令來安裝[NuGet 套件](https://www.nuget.org/packages/dotnet-trace)：

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>概要

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-trace`工具：

* 是跨平臺 .NET Core 工具。
* 可在不使用原生分析工具的情況下，收集執行中進程的 .NET Core 追蹤。
* 是圍繞 .NET Core 執行時間的跨平臺技術所建立 `EventPipe` 。
* 在 Windows、Linux 或 macOS 上提供相同的體驗。

## <a name="options"></a>選項。

- **`--version`**

  顯示 dotnet 追蹤公用程式的版本。

- **`-h|--help`**

  顯示命令列說明。

## <a name="commands"></a>命令

| Command                                                   |
|-----------------------------------------------------------|
| [dotnet-追蹤收集](#dotnet-trace-collect)             |
| [dotnet-追蹤轉換](#dotnet-trace-convert)             |
| [dotnet-追蹤 ps](#dotnet-trace-ps)                       |
| [dotnet-追蹤清單-設定檔](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-追蹤收集

從執行中的進程收集診斷追蹤。

### <a name="synopsis"></a>概要

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  要從中收集追蹤的進程。

- **`--buffersize <size>`**

  設定記憶體中迴圈緩衝區的大小（以 mb 為單位）。 預設值： 256 MB。

- **`-o|--output <trace-file-path>`**

  所收集追蹤資料的輸出路徑。 如果未指定，則預設為 `trace.nettrace` 。

- **`--providers <list-of-comma-separated-providers>`**

  要啟用的提供者清單（以逗號分隔） `EventPipe` 。 這些提供者會補充所隱含的任何提供者 `--profile <profile-name>` 。 如果特定提供者有任何不一致的情況，則此設定的優先順序會高於設定檔的隱含設定。

  這份提供者清單的格式如下：

  - `Provider[,Provider]`
  - `Provider`的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` 。
  - `KeyValueArgs`的格式為： `[key1=value1][;key2=value2]` 。

- **`--profile <profile-name>`**

  一組命名的預先定義提供者設定，可讓您簡潔地指定一般追蹤案例。

- **`--format {NetTrace|Speedscope}`**

  設定追蹤檔案轉換的輸出格式。 預設為 `NetTrace`。

## <a name="dotnet-trace-convert"></a>dotnet-追蹤轉換

將 `nettrace` 追蹤轉換為替代的格式，以搭配替代的追蹤分析工具使用。

### <a name="synopsis"></a>概要

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>引數

- **`<input-filename>`**

  要轉換的輸入追蹤檔案。 預設為*nettrace*。

### <a name="options"></a>選項。

- **`--format <NetTrace|Speedscope>`**

  設定追蹤檔案轉換的輸出格式。

- **`-o|--output <output-filename>`**

  輸出檔案名。 將會加入目標格式的副檔名。

## <a name="dotnet-trace-ps"></a>dotnet-追蹤 ps

列出可以附加至的 dotnet 進程。

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

## <a name="collect-a-trace-with-dotnet-trace"></a>使用 dotnet-trace 收集追蹤

若要使用來收集追蹤 `dotnet-trace` ：

- 取得要從中收集追蹤的 .NET Core 應用程式的處理序識別碼（PID）。

  - 例如，在 Windows 上，您可以使用 [工作管理員] 或 `tasklist` 命令。
  - 例如，在 Linux 上為 `ps` 命令。
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

- 按下鍵以停止收集 `<Enter>` 。 `dotnet-trace`將會完成記錄事件至*nettrace*檔案。

## <a name="view-the-trace-captured-from-dotnet-trace"></a>查看從 dotnet 所捕獲的追蹤

在 Windows 上，您可以在[PerfView](https://github.com/microsoft/perfview)上查看*nettrace*檔案以供分析：針對其他平臺上所收集的追蹤，追蹤檔案可以移至 Windows 機器，以在 PerfView 上查看。

在 Linux 上，您可以藉由將的輸出格式變更 `dotnet-trace` 為來查看追蹤 `speedscope` 。 您可以使用選項來變更輸出檔案格式 `-f|--format` - `-f speedscope` 將會 `dotnet-trace` 產生檔案 `speedscope` 。 您可以選擇 `nettrace` （預設選項）和 `speedscope` 。 `Speedscope`檔案可以在開啟 <https://www.speedscope.app> 。

> [!NOTE]
> .NET Core 執行時間會產生格式的追蹤 `nettrace` 。 追蹤完成後，追蹤會轉換成 speedscope （如果有指定的話）。 由於某些轉換可能會導致資料遺失，因此原始檔案 `nettrace` 會保留在轉換後的檔案旁邊。

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>使用 dotnet 追蹤來收集一段時間的計數器值

`dotnet-trace`可以

* 用於 `EventCounter` 效能相關環境中的基本健全狀況監視。 例如，在生產環境中。
* 收集追蹤，讓它們不需要即時查看。

例如，若要收集執行時間效能計數器值，請使用下列命令：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

上述命令會告訴執行時間計數器每秒報告一次，以進行輕量的健全狀況監視。 取代 `EventCounterIntervalSec=1` 為較高的值（例如，60），可讓您在計數器資料中收集較小的追蹤。

下列命令可減少額外負荷和追蹤大小，而不是上述其中一個：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

上述命令會停用運行時間事件和 managed 堆疊 profiler。

## <a name="net-providers"></a>.NET 提供者

.NET Core 執行時間支援下列 .NET 提供者。 .NET Core 會使用相同的關鍵字來同時啟用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 追蹤。

| 提供者名稱                            | 資訊 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [執行階段提供者](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR 執行時間關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [取消提供者](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR 取消關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | 啟用範例 profiler。 |
