---
title: dotnet-計數器-.NET Core
description: 瞭解如何安裝和使用 dotnet-counter 命令列工具。
ms.date: 10/14/2019
ms.openlocfilehash: 399d5908e8ac52bcd4a20c1a819fc6c99f4de2f4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737701"
---
# <a name="dotnet-counters"></a>dotnet-counters

**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="install-dotnet-counters"></a>安裝 dotnet-計數器

若要安裝 `dotnet-counters` [NuGet 套件](https://www.nuget.org/packages/dotnet-counters)的最新發行版本，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>概要

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-counters` 是一種效能監視工具，可用於臨機操作健全狀況監視和第一層效能調查。 它可以觀察透過 <xref:System.Diagnostics.Tracing.EventCounter> API 發佈的效能計數器值。 例如，您可以快速監視 CPU 使用量，或 .NET Core 應用程式中擲回之例外狀況的速率，以查看使用 `PerfView` 或 `dotnet-trace`進行更嚴重的效能調查之前是否有任何可疑的問題。

## <a name="options"></a>選項

- **`--version`**

  顯示 dotnet 計數器公用程式的版本。

- **`-h|--help`**

  顯示命令列說明。

## <a name="commands"></a>命令

| 命令                                             |
| --------------------------------------------------- |
| [dotnet-計數器清單](#dotnet-counters-list)       |
| [dotnet-計數器監視](#dotnet-counters-monitor) |

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
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>dotnet-計數器監視

顯示已選取計數器的定期重新整理值。

### <a name="synopsis"></a>概要

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>選項

- **`-p|--process-id <PID>`**

  要監視之進程的識別碼。

- **`--refresh-interval <SECONDS>`**

  更新所顯示計數器之間的延遲秒數

- **`counter_list <COUNTERS>`**

  以空格分隔的計數器清單。 `provider_name[:counter_name]`可以指定計數器。 如果在沒有符合資格的 `counter_name`的情況下使用 `provider_name`，則會顯示所有計數器。 若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。

### <a name="examples"></a>範例

- 以3秒的重新整理間隔監視 `System.Runtime` 的所有計數器：

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

- 僅監視 `System.Runtime`的 CPU 使用量和 GC 堆積大小：

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- 從使用者定義的 `EventSource`監視 `EventCounter` 值。 如需詳細資訊，請參閱[教學課程：如何使用 EventCounters 測量非常頻繁事件的效能](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
