---
title: Debug high CPU 使用量-.NET Core
description: 本教學課程會逐步引導您在 .NET Core 中進行高 CPU 使用率的偵錯工具。
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 71e0b98f7ad38836c6a20c3e0e75a878fb6525c7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538705"
---
# <a name="debug-high-cpu-usage-in-net-core"></a>在 .NET Core 中進行高 CPU 使用率的調試

本文**適用于：✔️** .net CORE 3.1 SDK 和更新版本

在本教學課程中，您將瞭解如何對過多的 CPU 使用量案例進行調試。 使用提供的範例 [ASP.NET Core web 應用程式](/samples/dotnet/samples/diagnostic-scenarios) 原始程式碼存放庫，您可以刻意造成鎖死。 端點將會遇到停止回應和執行緒累積。 您將瞭解如何使用各種工具來診斷此案例，其中包含幾個重要的診斷資料片段。

在本教學課程中，您將：

> [!div class="checklist"]
>
> - 調查高 CPU 使用率
> - 使用[dotnet](dotnet-counters.md)來判斷 CPU 使用量
> - 使用 [dotnet](dotnet-trace.md) 追蹤產生追蹤
> - PerfView 中的設定檔效能
> - 診斷和解決過度的 CPU 使用率

## <a name="prerequisites"></a>Prerequisites

教學課程會使用：

- [.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。
- 觸發案例的[範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios)。
- [dotnet-追蹤](dotnet-trace.md) 以列出進程並產生設定檔。
- [dotnet-](dotnet-counters.md) 監視 cpu 使用量的計數器。

## <a name="cpu-counters"></a>CPU 計數器

在嘗試收集診斷資料之前，您必須先觀察到高 CPU 的狀況。 從專案根目錄中，使用下列命令來執行 [範例應用程式](/samples/dotnet/samples/diagnostic-scenarios) 。

```dotnetcli
dotnet run
```

若要尋找處理序識別碼，請使用下列命令：

```dotnetcli
dotnet-trace ps
```

記下命令輸出中的處理序識別碼。 我們的處理序識別碼為 `22884` ，但您的進程識別碼不同。 若要檢查目前的 CPU 使用量，請使用 [dotnet 計數器](dotnet-counters.md) 工具命令：

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

`refresh-interval`是計數器輪詢 CPU 值之間的秒數。 輸出應如下所示：

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

當 web 應用程式執行時，在啟動後立即無法耗用 CPU，並且在中報告 `0%` 。 使用路由參數流覽至 `api/diagscenario/highcpu` 路由 `60000` ：

`https://localhost:5001/api/diagscenario/highcpu/60000`

現在，請重新執行 [dotnet 計數器](dotnet-counters.md) 命令。 若只要監視 `cpu-usage` ，請指定 `System.Runtime[cpu-usage]` 做為命令的一部分。

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

您應該會看到 CPU 使用率增加，如下所示：

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

在要求的整個持續期間，CPU 使用率將會停留在25%。 根據主機電腦，預期會有不同的 CPU 使用率。

> [!TIP]
> 若要將更高的 CPU 使用量視覺化，您可以同時在多個瀏覽器索引標籤中執行此端點。

此時，您可以放心地指出 CPU 的執行高於預期。

## <a name="trace-generation"></a>產生追蹤

分析緩慢的要求時，您需要可讓您深入瞭解程式碼所執行之工作的診斷工具。 一般選擇是分析工具，而且有不同的 profiler 選項可供選擇。

### <a name="linux"></a>[Linux](#tab/linux)

此 `perf` 工具可用來產生 .Net Core 應用程式佈建檔。 結束 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios)的先前實例。

設定 `COMPlus_PerfMapEnabled` 環境變數，讓 .Net Core 應用程式 `map` 在目錄中建立檔案 `/tmp` 。 `map`會使用這個檔案， `perf` 依名稱將 CPU 位址對應到 JIT 產生的函式。 如需詳細資訊，請參閱 [寫入效能對應](../run-time-config/debugging-profiling.md#write-perf-map)。

在相同的終端機會話中執行 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios) 。

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

請 () 重新執行高 CPU API 端點 `https://localhost:5001/api/diagscenario/highcpu/60000` 。 當它在1分鐘的要求中執行時，請 `perf` 使用您的處理序識別碼來執行命令：

```bash
sudo perf record -p 2266 -g
```

此 `perf` 命令會啟動效能收集程式。 讓它執行大約20-30 秒，然後按下 <kbd>Ctrl + C</kbd> 以結束收集程式。 您可以使用相同的 `perf` 命令來查看追蹤的輸出。

```bash
sudo perf report -f
```

您也可以使用下列命令來產生 _火焰圖_ ：

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

此命令會產生 `flamegraph.svg` ，您可以在瀏覽器中查看以調查效能問題：

[![火焰圖形 SVG 影像](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

在 Windows 上，您可以使用 [dotnet 追蹤](dotnet-trace.md) 工具作為 profiler。 使用先前的 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios)， () 重新執行高 CPU 端點 `https://localhost:5001/api/diagscenario/highcpu/60000` 。 當它在1分鐘的要求中執行時，請使用 `collect` 命令，如下所示：

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

讓 [dotnet 追蹤](dotnet-trace.md) 執行大約20-30 秒，然後按下 <kbd>enter</kbd> 鍵結束收集。 結果就是 `nettrace` 位於相同資料夾中的檔案。 這些檔案 `nettrace` 是在 Windows 上使用現有分析工具的絕佳方式。

開啟， `nettrace` [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) 如下所示。

[![PerfView 影像](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>另請參閱

- [dotnet-列出進程的追蹤](dotnet-trace.md)
- [dotnet-](dotnet-counters.md) 檢查 managed 記憶體使用量的計數器
- [dotnet-](dotnet-dump.md) 傾印以收集及分析傾印檔案
- [dotnet/診斷](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 .NET Core 中偵測鎖死](debug-deadlock.md)
