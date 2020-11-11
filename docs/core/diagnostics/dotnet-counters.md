---
title: dotnet-計數器-.NET Core
description: 瞭解如何安裝和使用 dotnet 計數器命令列工具。
ms.date: 02/26/2020
ms.openlocfilehash: 7ff29ad91ad271afd35e3d38a4d748bc79ad6c03
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507250"
---
# <a name="dotnet-counters"></a><span data-ttu-id="8113d-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="8113d-103">dotnet-counters</span></span>

<span data-ttu-id="8113d-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="8113d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="8113d-105">安裝 dotnet-計數器</span><span class="sxs-lookup"><span data-stu-id="8113d-105">Install dotnet-counters</span></span>

<span data-ttu-id="8113d-106">若要安裝 `dotnet-counters` [NuGet 套件](https://www.nuget.org/packages/dotnet-counters)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="8113d-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="8113d-107">概要</span><span class="sxs-lookup"><span data-stu-id="8113d-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="8113d-108">描述</span><span class="sxs-lookup"><span data-stu-id="8113d-108">Description</span></span>

<span data-ttu-id="8113d-109">`dotnet-counters` 是一種效能監視工具，適用于臨機操作健全狀況監視和第一層效能調查。</span><span class="sxs-lookup"><span data-stu-id="8113d-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="8113d-110">它可以觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="8113d-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="8113d-111">例如，您可以在 .NET Core 應用程式中快速監視 CPU 使用量或擲回例外狀況率等專案，以查看是否有任何可疑的專案，然後再使用或進行更嚴重的效能調查 `PerfView` `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="8113d-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="8113d-112">選項</span><span class="sxs-lookup"><span data-stu-id="8113d-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="8113d-113">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="8113d-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8113d-114">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="8113d-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="8113d-115">命令</span><span class="sxs-lookup"><span data-stu-id="8113d-115">Commands</span></span>

| <span data-ttu-id="8113d-116">命令</span><span class="sxs-lookup"><span data-stu-id="8113d-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="8113d-117">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="8113d-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="8113d-118">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="8113d-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="8113d-119">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="8113d-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="8113d-120">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="8113d-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="8113d-121">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="8113d-121">dotnet-counters collect</span></span>

<span data-ttu-id="8113d-122">定期收集選取的計數器值，並將其匯出為指定的檔案格式以進行後置處理。</span><span class="sxs-lookup"><span data-stu-id="8113d-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8113d-123">概要</span><span class="sxs-lookup"><span data-stu-id="8113d-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="8113d-124">選項</span><span class="sxs-lookup"><span data-stu-id="8113d-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8113d-125">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8113d-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="8113d-126">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="8113d-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="8113d-127">以逗號分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="8113d-127">A comma-separated list of counters.</span></span> <span data-ttu-id="8113d-128">您可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="8113d-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="8113d-129">如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。</span><span class="sxs-lookup"><span data-stu-id="8113d-129">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="8113d-130">若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="8113d-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="8113d-131">要匯出的格式。</span><span class="sxs-lookup"><span data-stu-id="8113d-131">The format to be exported.</span></span> <span data-ttu-id="8113d-132">目前可用： csv、json。</span><span class="sxs-lookup"><span data-stu-id="8113d-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="8113d-133">輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8113d-133">The name of the output file.</span></span>

- <span data-ttu-id="8113d-134">**`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="8113d-134">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="8113d-135">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-135">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="8113d-136">`dotnet-counters` 將會使用所提供的命令啟動處理常式，並收集要求的度量。</span><span class="sxs-lookup"><span data-stu-id="8113d-136">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="8113d-137">這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。</span><span class="sxs-lookup"><span data-stu-id="8113d-137">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

> [!NOTE]
> <span data-ttu-id="8113d-138">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-138">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="8113d-139">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="8113d-139">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="8113d-140">範例</span><span class="sxs-lookup"><span data-stu-id="8113d-140">Examples</span></span>

- <span data-ttu-id="8113d-141">以3秒的重新整理間隔收集所有計數器，並產生 csv 作為輸出：</span><span class="sxs-lookup"><span data-stu-id="8113d-141">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="8113d-142">`dotnet mvc.dll`以子進程的形式啟動，並開始收集執行時間計數器，並從啟動 ASP.NET Core 裝載計數器，並將其儲存為 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8113d-142">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="8113d-143">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="8113d-143">dotnet-counters list</span></span>

<span data-ttu-id="8113d-144">顯示依提供者分組的計數器名稱和描述清單。</span><span class="sxs-lookup"><span data-stu-id="8113d-144">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8113d-145">概要</span><span class="sxs-lookup"><span data-stu-id="8113d-145">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="8113d-146">範例</span><span class="sxs-lookup"><span data-stu-id="8113d-146">Example</span></span>

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
> <span data-ttu-id="8113d-147">`Microsoft.AspNetCore.Hosting`當有可支援這些計數器的進程時，就會顯示計數器，例如，當主機電腦上正在執行 ASP.NET Core 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="8113d-147">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="8113d-148">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="8113d-148">dotnet-counters monitor</span></span>

<span data-ttu-id="8113d-149">顯示定期重新整理所選計數器的值。</span><span class="sxs-lookup"><span data-stu-id="8113d-149">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8113d-150">概要</span><span class="sxs-lookup"><span data-stu-id="8113d-150">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="8113d-151">選項</span><span class="sxs-lookup"><span data-stu-id="8113d-151">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8113d-152">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8113d-152">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="8113d-153">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="8113d-153">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="8113d-154">以逗號分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="8113d-154">A comma-separated list of counters.</span></span> <span data-ttu-id="8113d-155">您可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="8113d-155">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="8113d-156">如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。</span><span class="sxs-lookup"><span data-stu-id="8113d-156">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="8113d-157">若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="8113d-157">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="8113d-158">**`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="8113d-158">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="8113d-159">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-159">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="8113d-160">`dotnet-counters` 將會使用所提供的命令啟動處理常式，並監視要求的計量。</span><span class="sxs-lookup"><span data-stu-id="8113d-160">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="8113d-161">這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。</span><span class="sxs-lookup"><span data-stu-id="8113d-161">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8113d-162">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-162">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="8113d-163">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="8113d-163">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="8113d-164">範例</span><span class="sxs-lookup"><span data-stu-id="8113d-164">Examples</span></span>

- <span data-ttu-id="8113d-165">以3秒的重新整理間隔監視所有計數器 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="8113d-165">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="8113d-166">僅監視 CPU 使用量和 GC 堆積大小 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="8113d-166">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="8113d-167">監視 `EventCounter` 使用者自訂的值 `EventSource` 。</span><span class="sxs-lookup"><span data-stu-id="8113d-167">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="8113d-168">如需詳細資訊，請參閱 [教學課程：在 .Net Core 中使用 EventCounters 測量效能](event-counter-perf.md)。</span><span class="sxs-lookup"><span data-stu-id="8113d-168">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="8113d-169">啟動 `my-aspnet-server.exe` 並監視從啟動 ( .net 5.0 或更新版本載入的元件 #) ：</span><span class="sxs-lookup"><span data-stu-id="8113d-169">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="8113d-170">注意：這只適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-170">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="8113d-171">`my-aspnet-server.exe`以 `arg1` `arg2` 命令列引數啟動，並從啟動 ( .net 5.0 或更新版本監視其工作集和 GC 堆積大小，只) ：</span><span class="sxs-lookup"><span data-stu-id="8113d-171">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="8113d-172">注意：這只適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8113d-172">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="8113d-173">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="8113d-173">dotnet-counters ps</span></span>

<span data-ttu-id="8113d-174">顯示可以監視的 dotnet 進程清單。</span><span class="sxs-lookup"><span data-stu-id="8113d-174">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8113d-175">概要</span><span class="sxs-lookup"><span data-stu-id="8113d-175">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="8113d-176">範例</span><span class="sxs-lookup"><span data-stu-id="8113d-176">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
