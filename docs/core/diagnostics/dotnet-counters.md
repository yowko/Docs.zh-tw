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
# <a name="dotnet-counters"></a><span data-ttu-id="b0da3-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b0da3-103">dotnet-counters</span></span>

<span data-ttu-id="b0da3-104">**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b0da3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="b0da3-105">安裝 dotnet-計數器</span><span class="sxs-lookup"><span data-stu-id="b0da3-105">Install dotnet-counters</span></span>

<span data-ttu-id="b0da3-106">若要安裝 NuGet 套件的最新發行版本 `dotnet-counters` [ ](https://www.nuget.org/packages/dotnet-counters)，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="b0da3-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="b0da3-107">概要</span><span class="sxs-lookup"><span data-stu-id="b0da3-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="b0da3-108">描述</span><span class="sxs-lookup"><span data-stu-id="b0da3-108">Description</span></span>

<span data-ttu-id="b0da3-109">`dotnet-counters`是一種效能監視工具，可用於臨機操作健全狀況監視和第一層效能調查。</span><span class="sxs-lookup"><span data-stu-id="b0da3-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="b0da3-110">它可以觀察透過 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="b0da3-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="b0da3-111">例如，您可以快速監視 CPU 使用量，或 .NET Core 應用程式中擲回之例外狀況的速率，以在使用或進行更嚴重的效能調查之前，查看是否有任何可疑的專案 `PerfView` `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="b0da3-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="b0da3-112">選項。</span><span class="sxs-lookup"><span data-stu-id="b0da3-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="b0da3-113">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="b0da3-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b0da3-114">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="b0da3-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="b0da3-115">命令</span><span class="sxs-lookup"><span data-stu-id="b0da3-115">Commands</span></span>

| <span data-ttu-id="b0da3-116">命令</span><span class="sxs-lookup"><span data-stu-id="b0da3-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="b0da3-117">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="b0da3-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="b0da3-118">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="b0da3-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="b0da3-119">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="b0da3-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="b0da3-120">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="b0da3-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="b0da3-121">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="b0da3-121">dotnet-counters collect</span></span>

<span data-ttu-id="b0da3-122">定期收集選取的計數器值，並將它們匯出為指定的檔案格式，以進行後續處理。</span><span class="sxs-lookup"><span data-stu-id="b0da3-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b0da3-123">概要</span><span class="sxs-lookup"><span data-stu-id="b0da3-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="b0da3-124">選項。</span><span class="sxs-lookup"><span data-stu-id="b0da3-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="b0da3-125">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0da3-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="b0da3-126">更新所顯示計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="b0da3-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="b0da3-127">以空格分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="b0da3-127">A space separated list of counters.</span></span> <span data-ttu-id="b0da3-128">可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="b0da3-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="b0da3-129">如果在 `provider_name` 沒有符合資格的情況下使用 `counter_name` ，則會顯示所有計數器。</span><span class="sxs-lookup"><span data-stu-id="b0da3-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="b0da3-130">若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。</span><span class="sxs-lookup"><span data-stu-id="b0da3-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="b0da3-131">要匯出的格式。</span><span class="sxs-lookup"><span data-stu-id="b0da3-131">TThe format to be exported.</span></span> <span data-ttu-id="b0da3-132">目前可用： csv、json。</span><span class="sxs-lookup"><span data-stu-id="b0da3-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="b0da3-133">輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0da3-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="b0da3-134">範例</span><span class="sxs-lookup"><span data-stu-id="b0da3-134">Examples</span></span>

- <span data-ttu-id="b0da3-135">以3秒的重新整理間隔收集所有計數器，並產生 csv 作為輸出：</span><span class="sxs-lookup"><span data-stu-id="b0da3-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="b0da3-136">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="b0da3-136">dotnet-counters list</span></span>

<span data-ttu-id="b0da3-137">顯示計數器名稱和描述的清單，依提供者分組。</span><span class="sxs-lookup"><span data-stu-id="b0da3-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b0da3-138">概要</span><span class="sxs-lookup"><span data-stu-id="b0da3-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="b0da3-139">範例</span><span class="sxs-lookup"><span data-stu-id="b0da3-139">Example</span></span>

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
> <span data-ttu-id="b0da3-140">`Microsoft.AspNetCore.Hosting`當有識別支援這些計數器的進程（例如，在主機電腦上執行 ASP.NET Core 應用程式）時，就會顯示計數器。</span><span class="sxs-lookup"><span data-stu-id="b0da3-140">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="b0da3-141">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="b0da3-141">dotnet-counters monitor</span></span>

<span data-ttu-id="b0da3-142">顯示已選取計數器的定期重新整理值。</span><span class="sxs-lookup"><span data-stu-id="b0da3-142">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b0da3-143">概要</span><span class="sxs-lookup"><span data-stu-id="b0da3-143">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="b0da3-144">選項。</span><span class="sxs-lookup"><span data-stu-id="b0da3-144">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="b0da3-145">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0da3-145">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="b0da3-146">更新所顯示計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="b0da3-146">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="b0da3-147">以空格分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="b0da3-147">A space separated list of counters.</span></span> <span data-ttu-id="b0da3-148">可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="b0da3-148">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="b0da3-149">如果在 `provider_name` 沒有符合資格的情況下使用 `counter_name` ，則會顯示所有計數器。</span><span class="sxs-lookup"><span data-stu-id="b0da3-149">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="b0da3-150">若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。</span><span class="sxs-lookup"><span data-stu-id="b0da3-150">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="b0da3-151">範例</span><span class="sxs-lookup"><span data-stu-id="b0da3-151">Examples</span></span>

- <span data-ttu-id="b0da3-152">以3秒的重新整理間隔監視所有計數器 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="b0da3-152">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="b0da3-153">僅監視 CPU 使用量和 GC 堆積大小來源 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="b0da3-153">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="b0da3-154">監視 `EventCounter` 使用者定義的值 `EventSource` 。</span><span class="sxs-lookup"><span data-stu-id="b0da3-154">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="b0da3-155">如需詳細資訊，請參閱[教學課程：在 .Net Core 中使用 EventCounters 測量效能](event-counter-perf.md)。</span><span class="sxs-lookup"><span data-stu-id="b0da3-155">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="b0da3-156">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="b0da3-156">dotnet-counters ps</span></span>

<span data-ttu-id="b0da3-157">顯示可以監視的 dotnet 進程清單。</span><span class="sxs-lookup"><span data-stu-id="b0da3-157">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b0da3-158">概要</span><span class="sxs-lookup"><span data-stu-id="b0da3-158">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="b0da3-159">範例</span><span class="sxs-lookup"><span data-stu-id="b0da3-159">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
