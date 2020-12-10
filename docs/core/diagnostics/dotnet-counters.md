---
title: dotnet-計數器診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-counter CLI 工具，以進行臨機操作健全狀況監視和第一層效能調查。
ms.date: 11/17/2020
ms.openlocfilehash: 48e3b038ddb5c9421367612a592c5ba6b9459791
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009543"
---
# <a name="investigate-performance-counters-dotnet-counters"></a> (dotnet) 的計數器調查效能計數器

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

## <a name="install"></a>安裝

有兩種方式可以下載和安裝 `dotnet-counters` ：

- **dotnet global tool：**

  若要安裝 `dotnet-counters` [NuGet 套件](https://www.nuget.org/packages/dotnet-counters)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- **直接下載：**

  下載符合您平臺的工具可執行檔：

  | OS  | 平台 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-counters/win-x86) \|[x64](https://aka.ms/dotnet-counters/win-x64) \|[arm](https://aka.ms/dotnet-counters/win-arm) \|[arm-x64](https://aka.ms/dotnet-counters/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-counters/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-counters/linux-x64) \|[arm](https://aka.ms/dotnet-counters/linux-arm) \|[arm64](https://aka.ms/dotnet-counters/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64) |

## <a name="synopsis"></a>概要

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-counters` 是一種效能監視工具，適用于臨機操作健全狀況監視和第一層效能調查。 它可以觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。 例如，您可以在 .NET Core 應用程式中快速監視 CPU 使用量或擲回例外狀況率等專案，以查看是否有任何可疑的專案，然後再使用或進行更嚴重的效能調查 `PerfView` `dotnet-trace` 。

## <a name="options"></a>選項

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

定期收集選取的計數器值，並將其匯出為指定的檔案格式以進行後置處理。

### <a name="synopsis"></a>概要

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>選項

- **`-p|--process-id <PID>`**

  要從中收集計數器資料的進程識別碼。

- **`-n|--name <name>`**

  要從中收集計數器資料之進程的名稱。

- **`--diagnostic-port`**

  要建立之診斷埠的名稱。 請參閱 [使用診斷埠](#using-diagnostic-port) 來瞭解如何使用此選項，從應用程式啟動開始監視計數器。

- **`--refresh-interval <SECONDS>`**

  更新顯示的計數器之間的延遲秒數

- **`--counters <COUNTERS>`**

  以逗號分隔的計數器清單。 您可以指定計數器 `provider_name[:counter_name]` 。 如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。 若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。

- **`--format <csv|json>`**

  要匯出的格式。 目前可用： csv、json。

- **`-o|--output <output>`**

  輸出檔的名稱。

- **`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**

  在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。 `dotnet-counters` 將會使用所提供的命令啟動處理常式，並收集要求的度量。 這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。

  > [!NOTE]
  > 使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。 因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。

  > [!NOTE]
  > 透過 dotnet 啟動 .NET 可執行檔會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 進行互動。 透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。 如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。 如果您需要使用 stdin/stdout，可以使用 `--diagnostic-port` 選項。 如需詳細資訊，請參閱 [使用診斷埠](#using-diagnostic-port) 。

### <a name="examples"></a>範例

- 以3秒的重新整理間隔收集所有計數器，並產生 csv 作為輸出：

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- `dotnet mvc.dll`以子進程的形式啟動，並開始收集執行時間計數器，並從啟動 ASP.NET Core 裝載計數器，並將其儲存為 JSON 輸出：

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a>dotnet-計數器清單

顯示依提供者分組的計數器名稱和描述清單。

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
> `Microsoft.AspNetCore.Hosting`當有可支援這些計數器的進程時，就會顯示計數器，例如，當主機電腦上正在執行 ASP.NET Core 應用程式時。

## <a name="dotnet-counters-monitor"></a>dotnet-計數器監視

顯示定期重新整理所選計數器的值。

### <a name="synopsis"></a>概要

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a>選項

- **`-p|--process-id <PID>`**

  要監視之進程的識別碼。

- **`-n|--name <name>`**

  要監視之進程的名稱。

- **`--diagnostic-port`**

  要建立之診斷埠的名稱。 請參閱 [使用診斷埠](#using-diagnostic-port) 來瞭解如何使用此選項，從應用程式啟動開始監視計數器。

- **`--refresh-interval <SECONDS>`**

  更新顯示的計數器之間的延遲秒數

- **`--counters <COUNTERS>`**

  以逗號分隔的計數器清單。 您可以指定計數器 `provider_name[:counter_name]` 。 如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。 若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。

 **`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**

  在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。 `dotnet-counters` 將會使用所提供的命令啟動處理常式，並監視要求的計量。 這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。

  > [!NOTE]
  > 使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。 因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。

  > [!NOTE]
  > 透過 dotnet 啟動 .NET 可執行檔會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 進行互動。 透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。 如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。 如果您需要使用 stdin/stdout，可以使用 `--diagnostic-port` 選項。 如需詳細資訊，請參閱 [使用診斷埠](#using-diagnostic-port) 。

### <a name="examples"></a>範例

- 以3秒的重新整理間隔監視所有計數器 `System.Runtime` ：

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- 僅監視 CPU 使用量和 GC 堆積大小 `System.Runtime` ：

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- 監視 `EventCounter` 使用者自訂的值 `EventSource` 。 如需詳細資訊，請參閱 [教學課程：在 .Net Core 中使用 EventCounters 測量效能](event-counter-perf.md)。

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- 啟動 `my-aspnet-server.exe` 並監視從啟動 ( .net 5.0 或更新版本載入的元件 #) ：

  > [!IMPORTANT]
  > 這僅適用于執行 .NET 5.0 或更新版本的應用程式。

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- `my-aspnet-server.exe`以 `arg1` `arg2` 命令列引數啟動，並從啟動 ( .net 5.0 或更新版本監視其工作集和 GC 堆積大小，只) ：

  > [!IMPORTANT]
  > 這僅適用于執行 .NET 5.0 或更新版本的應用程式。

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
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
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a>使用診斷埠

  > [!IMPORTANT]
  > 這僅適用于執行 .NET 5.0 或更新版本的應用程式。

診斷埠是新增在 .NET 5 中的新執行時間功能，可讓您從應用程式啟動開始監視或收集計數器。 若要使用來執行此作業， `dotnet-counters` 您可以使用 `dotnet-counters <collect|monitor> -- <command>` 如上述範例中所述，或使用 `--diagnostic-port` 選項。

使用 `dotnet-counters <collect|monitor> -- <command>` 以子進程的形式啟動應用程式是從啟動時快速監視的最簡單方式。

但是，當您想要更精確地控制受監視的應用程式存留期 (例如，只在前10分鐘內監視應用程式並繼續執行) 或者，如果您需要使用 CLI 與應用程式互動，使用 `--diagnostic-port` 選項可讓您控制受監視的目標應用程式和 `dotnet-counters` 。

1. 下列命令會建立名為 dotnet 的診斷通訊端 `myport.sock` ，並等候連接。

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    輸出：

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. 在個別的主控台中，啟動目標應用程式，並將環境變數 `DOTNET_DiagnosticPorts` 設為輸出中的值 `dotnet-counters` 。

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    如此一來，就可以 `dotnet-counters` 開始收集計數器 `my-dotnet-app` ：

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > 啟動您的應用程式可能 `dotnet run` 會造成問題，因為 DOTNET CLI 可能會產生許多不是您應用程式的子進程，而且它們可以在您的應用 `dotnet-counters` 程式之前連線，讓您的應用程式在執行時間暫停。 建議您直接使用應用程式的獨立版本，或用 `dotnet exec` 來啟動應用程式。
