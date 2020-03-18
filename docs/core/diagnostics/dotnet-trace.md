---
title: 點網跟蹤工具 - .NET 核心
description: 安裝和使用點網跟蹤命令列工具。
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737655"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>點網跟蹤性能分析實用程式

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

## <a name="install-dotnet-trace"></a>安裝點網跟蹤

使用`dotnet-trace` [dotnet 工具安裝](../tools/dotnet-tool-install.md)命令安裝[NuGet 包](https://www.nuget.org/packages/dotnet-trace)：

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>概要

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>描述

該工具`dotnet-trace`：

* 是一個跨平臺 .NET 核心工具。
* 支援在沒有本機探測器的情況下收集正在運行的進程的 .NET Core 跟蹤。
* 是圍繞 .NET Core`EventPipe`運行時的跨平臺技術構建的。
* 在 Windows、Linux 或 macOS 上提供相同的體驗。

## <a name="options"></a>選項。

- **`--version`**

  顯示點網計數器實用程式的版本。

- **`-h|--help`**

  顯示命令列説明。

## <a name="commands"></a>命令

| Command                                                     |
| ----------------------------------------------------------- |
| [點網跟蹤收集](#dotnet-trace-collect)               |
| [點網跟蹤轉換](#dotnet-trace-convert)               |
| [點內跟蹤 ps](#dotnet-trace-ps) |
| [點網跟蹤清單設定檔](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>點網跟蹤收集

從正在運行的進程收集診斷跟蹤。

### <a name="synopsis"></a>概要

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  從中收集跟蹤的過程。

- **`--buffersize <size>`**

  設置記憶體中圓形緩衝區的大小（以百萬位元組為單位）。 預設值 256 MB。

- **`-o|--output <trace-file-path>`**

  收集的跟蹤資料的輸出路徑。 如果未指定，則預設為`trace.nettrace`。

- **`--providers <list-of-comma-separated-providers>`**

  要啟用的提供程式的`EventPipe`逗號分隔清單。 這些供應商補充了 隱含的任何`--profile <profile-name>`提供程式。 如果特定提供程式有任何不一致，則此配置優先于設定檔中的隱式配置。

  提供程式清單的形式為：

  - `Provider[,Provider]`
  - `Provider`以以下形式： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`。
  - `KeyValueArgs`以以下形式： `[key1=value1][;key2=value2]`。

- **`--profile <profile-name>`**

  一組命名的預定義的提供程式配置，允許簡潔地指定常見跟蹤方案。

- **`--format {NetTrace|Speedscope}`**

  設置追蹤檔案轉換的輸出格式。 預設值為 `NetTrace`。

## <a name="dotnet-trace-convert"></a>點網跟蹤轉換

將`nettrace`跟蹤轉換為備用格式，以便與備用跟蹤分析工具一起使用。

### <a name="synopsis"></a>概要

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>引數

- **`<input-filename>`**

  要轉換的輸入追蹤檔案。 預設值為*跟蹤.net 跟蹤*。

### <a name="options"></a>選項。

- **`--format <NetTrace|Speedscope>`**

  設置追蹤檔案轉換的輸出格式。

- **`-o|--output <output-filename>`**

  輸出檔案名。 將添加目標格式的擴展。

## <a name="dotnet-trace-ps"></a>點內跟蹤 ps

列出可附加到的點網進程。

### <a name="synopsis"></a>概要

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>點網跟蹤清單設定檔

列出預構建的跟蹤設定檔，說明每個設定檔中有哪些提供程式和篩選器。

### <a name="synopsis"></a>概要

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>使用點網跟蹤收集跟蹤

使用 收集跟蹤： `dotnet-trace`

- 獲取 .NET Core 應用程式的流程識別碼 （PID）， 以便從中收集跟蹤。

  - 例如，在 Windows 上，可以使用任務`tasklist`管理器或命令。
  - 例如，在 Linux 上`ps`，命令。
  - [點內跟蹤 ps](#dotnet-trace-ps)

- 執行以下命令：

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  前面的命令生成類似于以下內容的輸出：

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- 按`<Enter>`鍵停止收集。 `dotnet-trace`將完成對*跟蹤.net 跟蹤*檔的日誌記錄事件。

## <a name="view-the-trace-captured-from-dotnet-trace"></a>查看從點網跟蹤捕獲的跟蹤

在 Windows 上，可以在[PerfView](https://github.com/microsoft/perfview)上查看 *.nettrace*檔進行分析：對於在其他平臺上收集的跟蹤，可以將追蹤檔案移動到在 PerfView 上查看的 Windows 電腦。

在 Linux 上，可以通過將 的`dotnet-trace`輸出格式更改為`speedscope`來查看跟蹤。 可以使用`-f|--format`選項更改輸出檔案格式 -`-f speedscope`將生成`dotnet-trace``speedscope`檔。 您可以在`nettrace`（預設選項） 和`speedscope`之間進行選擇。 `Speedscope`檔可以在 打開。 <https://www.speedscope.app>

> [!NOTE]
> .NET 核心運行時以`nettrace`格式生成跟蹤。 跟蹤完成後，跟蹤將轉換為速度範圍（如果指定）。 由於某些轉換可能會導致資料丟失，因此原始`nettrace`檔將保留在轉換後的檔旁邊。

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>使用點網跟蹤收集隨時間的計數器值

`dotnet-trace`可以：

* 用於`EventCounter`性能敏感環境中的基本運行狀況監視。 例如，在生產中。
* 收集跟蹤，以便不需要即時查看它們。

例如，要收集運行時效能計數器值，請使用以下命令：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

前面的命令告訴運行時計數器每秒報告一次以進行羽量級運行狀況監視。 替換為`EventCounterIntervalSec=1`較高的值（例如，60）允許在計數器資料中以較少的細微性收集較小的跟蹤。

以下命令比前面的命令減少開銷和跟蹤大小：

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

前面的命令禁用運行時事件和託管堆疊探測器。

## <a name="net-providers"></a>.NET 供應商

.NET 核心運行時支援以下 .NET 提供程式。 .NET Core 使用相同的關鍵字來啟用和`Event Tracing for Windows (ETW)``EventPipe`跟蹤。

| 提供者名稱                            | 資訊 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [執行階段提供者](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR 運行時關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [取消提供者](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR 運行關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | 啟用示例探測器。 |
