---
title: 點網追蹤工具 - .NET 核心
description: 安裝和使用點網跟蹤命令列工具。
ms.date: 11/21/2019
ms.openlocfilehash: 6880c3721e4cab12677bd02c82ca944cc9812670
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888081"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>點網追蹤效能分析實用程式

**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本

## <a name="install-dotnet-trace"></a>安裝點網追蹤

使用`dotnet-trace` [dotnet 工具安裝](../tools/dotnet-tool-install.md)指令安裝[NuGet 套件](https://www.nuget.org/packages/dotnet-trace):

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>概要

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>描述

該工具`dotnet-trace`:

* 是一個跨平臺 .NET 核心工具。
* 支援在沒有本機探查器的情況下收集正在運行的進程的 .NET Core 跟蹤。
* 是圍繞 .NET`EventPipe`Core 運行時的跨平臺技術構建的。
* 在 Windows、Linux 或 macOS 上提供相同的體驗。

## <a name="options"></a>選項。

- **`--version`**

  顯示點網跟蹤實用程式的版本。

- **`-h|--help`**

  顯示命令行説明。

## <a name="commands"></a>命令

| Command                                                     |
| ----------------------------------------------------------- |
| [點網追蹤收集](#dotnet-trace-collect)               |
| [點網追蹤轉換](#dotnet-trace-convert)               |
| [點內追蹤 ps](#dotnet-trace-ps) |
| [點網追蹤清單設定檔](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>點網追蹤收集

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

  設置記憶體中圓形緩衝區的大小(以兆位元組為單位)。 默認值 256 MB。

- **`-o|--output <trace-file-path>`**

  收集的跟蹤數據的輸出路徑。 沒有指定,則預設為`trace.nettrace`。

- **`--providers <list-of-comma-separated-providers>`**

  要啟用的提供程式的`EventPipe`逗號分隔清單。 這些提供商補充了 隱含的`--profile <profile-name>`任何 提供程式。 如果特定提供程式有任何不一致,則此配置優先於配置檔中的隱式配置。

  提供程式清單的形式為:

  - `Provider[,Provider]`
  - `Provider`以以下形式: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`。
  - `KeyValueArgs`以以下形式: `[key1=value1][;key2=value2]`。

- **`--profile <profile-name>`**

  一組命名的預定義的提供程式配置,允許簡潔地指定常見跟蹤方案。

- **`--format {NetTrace|Speedscope}`**

  設定追蹤檔轉換的輸出格式。 預設值為 `NetTrace`。

## <a name="dotnet-trace-convert"></a>點網追蹤轉換

將`nettrace`追蹤轉換為備用格式,以便與備用跟蹤分析工具一起使用。

### <a name="synopsis"></a>概要

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>引數

- **`<input-filename>`**

  要轉換的輸入跟蹤檔。 預設值為*追蹤.net 追蹤*。

### <a name="options"></a>選項。

- **`--format <NetTrace|Speedscope>`**

  設定追蹤檔轉換的輸出格式。

- **`-o|--output <output-filename>`**

  輸出檔名。 將添加目標格式的擴展。

## <a name="dotnet-trace-ps"></a>點內追蹤 ps

列出可附加到的點網進程。

### <a name="synopsis"></a>概要

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>點網追蹤清單設定檔

列出預建構的追蹤配置檔,說明每個設定檔中有哪些提供程式和篩選器。

### <a name="synopsis"></a>概要

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>使用點網追蹤收集追蹤

使用收集追蹤: `dotnet-trace`

- 取得 .NET Core 應用程式的流程識別碼 (PID), 以便從中收集追蹤。

  - 例如,在 Windows 上,可以`tasklist`使用任務 管理器或命令。
  - 例如,在 Linux`ps`上 ,命令。
  - [點內追蹤 ps](#dotnet-trace-ps)

- 執行以下命令：

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  前面的指令產生類似於以下內容的輸出:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- 按鍵`<Enter>`停止收集。 `dotnet-trace`將完成對*追蹤.net 追蹤*檔案的紀錄記錄事件。

## <a name="view-the-trace-captured-from-dotnet-trace"></a>檢視從點網追蹤擷取的追蹤

在 Windows 上,可以在[PerfView](https://github.com/microsoft/perfview)上查看 *.nettrace*檔進行分析:對於在其他平臺上收集的跟蹤,可以將追蹤檔移動到在 PerfView 上查看的 Windows 電腦。

在 Linux 上,可以`dotnet-trace`通過將的輸出`speedscope`格式更改為 來查看跟蹤。 可以使用`-f|--format`選項更改輸出檔案格式`-f speedscope`-`dotnet-trace``speedscope`將產生檔案。 您可以在`nettrace`(預設選項)`speedscope`和 之間進行選擇。 `Speedscope`文件可以在打開。 <https://www.speedscope.app>

> [!NOTE]
> .NET 核心運行時`nettrace`以 格式生成跟蹤。 跟蹤完成後,跟蹤將轉換為速度範圍(如果指定)。 由於某些轉換可能會導致資料丟失,因此`nettrace`原始 檔將保留在轉換後的文件旁邊。

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>使用點網追蹤收集隨時間的計數器值

`dotnet-trace`可以:

* 用於`EventCounter`性能敏感環境中的基本運行狀況監視。 例如,在生產中。
* 收集跟蹤,以便不需要即時查看它們。

例如,要收集運行時性能計數器值,請使用以下命令:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

前面的命令告訴運行時計數器每秒報告一次以進行羽量級運行狀況監視。 替換為`EventCounterIntervalSec=1`較高的值(例如,60)允許在計數器數據中以較少的粒度收集較小的跟蹤。

以下指令比前面的指令減少花費和追蹤大小:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

前面的命令禁用運行時事件和託管堆疊探查器。

## <a name="net-providers"></a>.NET 提供者

.NET 核心運行時支援以下 .NET 提供程式。 .NET Core 使用相同的關鍵字來`Event Tracing for Windows (ETW)``EventPipe`啟用和 跟蹤。

| 提供者名稱                            | 資訊 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [執行階段提供者](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR 執行時關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [取消提供者](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR 執行關鍵字](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | 啟用示例探查器。 |
