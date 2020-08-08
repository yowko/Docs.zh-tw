---
title: dotnet-計數器-.NET Core
description: 瞭解如何安裝和使用 dotnet-counter 命令列工具。
ms.date: 02/26/2020
ms.openlocfilehash: 71e3c4f0a60960c4e672b95000bc0d67bd427514
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024624"
---
# <a name="dotnet-counters"></a>dotnet-counters

**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="install-dotnet-counters"></a>安裝 dotnet-計數器

若要安裝 NuGet 套件的最新發行版本 `dotnet-counters` [ ](https://www.nuget.org/packages/dotnet-counters)，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>概要

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-counters`是一種效能監視工具，可用於臨機操作健全狀況監視和第一層效能調查。 它可以觀察透過 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。 例如，您可以快速監視 CPU 使用量，或 .NET Core 應用程式中擲回之例外狀況的速率，以在使用或進行更嚴重的效能調查之前，查看是否有任何可疑的專案 `PerfView` `dotnet-trace` 。

## <a name="options"></a>選項。

- **`--version`**

  顯示 dotnet 計數器公用程式的版本。

- **`-h|--help`**

  顯示命令列說明。

## <a name="commands"></a>命令

| 命令                                             |
|-----------------------------------------------------|
| [dotnet-計數器收集](#dotnet-counters-collect) |
| [dotnet-計數器清單](#dotnet-counters-list)       |
| [dotnet-計數器監視](#dotnet-counters-monitor) |
| [dotnet-計數器 ps](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet-計數器收集

定期收集選取的計數器值，並將它們匯出為指定的檔案格式，以進行後續處理。

### <a name="synopsis"></a>概要

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  要監視之進程的識別碼。

- **`--refresh-interval <SECONDS>`**

  更新所顯示計數器之間的延遲秒數

- **`counter_list <COUNTERS>`**

  以空格分隔的計數器清單。 可以指定計數器 `provider_name[:counter_name]` 。 如果在 `provider_name` 沒有符合資格的情況下使用 `counter_name` ，則會顯示所有計數器。 若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。

- **`--format <csv|json>`**

  要匯出的格式。 目前可用： csv、json。

- **`-o|--output <output>`**

  輸出檔案的名稱。

### <a name="examples"></a>範例

- 以3秒的重新整理間隔收集所有計數器，並產生 csv 作為輸出：

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>dotnet-計數器清單

顯示計數器名稱和描述的清單，依提供者分組。

### <a name="synopsis"></a>概要

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>範例

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> `Microsoft.AspNetCore.Hosting`當有識別支援這些計數器的進程（例如，在主機電腦上執行 ASP.NET Core 應用程式）時，就會顯示計數器。

## <a name="dotnet-counters-monitor"></a>dotnet-計數器監視

顯示已選取計數器的定期重新整理值。

### <a name="synopsis"></a>概要

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  要監視之進程的識別碼。

- **`--refresh-interval <SECONDS>`**

  更新所顯示計數器之間的延遲秒數

- **`counter_list <COUNTERS>`**

  以空格分隔的計數器清單。 可以指定計數器 `provider_name[:counter_name]` 。 如果在 `provider_name` 沒有符合資格的情況下使用 `counter_name` ，則會顯示所有計數器。 若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。

### <a name="examples"></a>範例

- 以3秒的重新整理間隔監視所有計數器 `System.Runtime` ：

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- 僅監視 CPU 使用量和 GC 堆積大小來源 `System.Runtime` ：

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- 監視 `EventCounter` 使用者定義的值 `EventSource` 。 如需詳細資訊，請參閱[教學課程：在 .Net Core 中使用 EventCounters 測量效能](event-counter-perf.md)。

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-計數器 ps

顯示可以監視的 dotnet 進程清單。

### <a name="synopsis"></a>概要

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>範例

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
