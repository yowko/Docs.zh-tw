---
title: 高 CPU 使用率的調試層-.NET Core
description: 本教學課程會逐步引導您在 .NET Core 中偵測高 CPU 使用量。
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: e69585d0eb6f04bf37d0c023a1956be62c2a1cf3
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86926394"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="52883-103">在 .NET Core 中進行高 CPU 使用率的調試</span><span class="sxs-lookup"><span data-stu-id="52883-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="52883-104">**本文適用于：✔️** .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="52883-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="52883-105">在本教學課程中，您將瞭解如何針對過多的 CPU 使用量案例進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="52883-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="52883-106">使用提供的範例[ASP.NET Core web 應用程式](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)原始程式碼存放庫，您可能會刻意造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="52883-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="52883-107">端點會遇到停止回應和執行緒累積的情況。</span><span class="sxs-lookup"><span data-stu-id="52883-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="52883-108">您將瞭解如何使用各種工具，以診斷資料的幾個重要部分來診斷此案例。</span><span class="sxs-lookup"><span data-stu-id="52883-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="52883-109">在本教學課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="52883-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="52883-110">調查高 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="52883-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="52883-111">使用[dotnet](dotnet-counters.md)來判斷 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="52883-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="52883-112">使用[dotnet](dotnet-trace.md)追蹤產生的追蹤</span><span class="sxs-lookup"><span data-stu-id="52883-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="52883-113">PerfView 中的設定檔效能</span><span class="sxs-lookup"><span data-stu-id="52883-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="52883-114">診斷並解決過多的 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="52883-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52883-115">先決條件</span><span class="sxs-lookup"><span data-stu-id="52883-115">Prerequisites</span></span>

<span data-ttu-id="52883-116">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="52883-116">The tutorial uses:</span></span>

- <span data-ttu-id="52883-117">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更新版本。</span><span class="sxs-lookup"><span data-stu-id="52883-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="52883-118">觸發案例的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)。</span><span class="sxs-lookup"><span data-stu-id="52883-118">[Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="52883-119">[dotnet-追蹤](dotnet-trace.md)以列出進程並產生設定檔。</span><span class="sxs-lookup"><span data-stu-id="52883-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="52883-120">[dotnet-](dotnet-counters.md)用來監視 cpu 使用量的計數器。</span><span class="sxs-lookup"><span data-stu-id="52883-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="52883-121">CPU 計數器</span><span class="sxs-lookup"><span data-stu-id="52883-121">CPU counters</span></span>

<span data-ttu-id="52883-122">在嘗試收集診斷資料之前，您必須先觀察到高 CPU 的狀況。</span><span class="sxs-lookup"><span data-stu-id="52883-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="52883-123">使用下列命令，從專案根目錄執行[範例應用程式](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)。</span><span class="sxs-lookup"><span data-stu-id="52883-123">Run the [sample application](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="52883-124">若要尋找處理序識別碼，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="52883-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="52883-125">請記下命令輸出中的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="52883-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="52883-126">我們的處理序識別碼是 `22884` ，但您的程式識別碼不同。</span><span class="sxs-lookup"><span data-stu-id="52883-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="52883-127">若要檢查目前的 CPU 使用量，請使用[dotnet 計數器](dotnet-counters.md)工具命令：</span><span class="sxs-lookup"><span data-stu-id="52883-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="52883-128">`refresh-interval`是計數器輪詢 CPU 值之間的秒數。</span><span class="sxs-lookup"><span data-stu-id="52883-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="52883-129">輸出應如下所示：</span><span class="sxs-lookup"><span data-stu-id="52883-129">The output should be similar to the following:</span></span>

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

<span data-ttu-id="52883-130">當 web 應用程式執行時，在啟動後立即不會耗用 CPU，且會在回報 `0%` 。</span><span class="sxs-lookup"><span data-stu-id="52883-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="52883-131">以 `api/diagscenario/highcpu` `60000` 作為路由參數的形式導覽至路由：</span><span class="sxs-lookup"><span data-stu-id="52883-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

[https://localhost:5001/api/diagscenario/highcpu/60000](https://localhost:5001/api/diagscenario/highcpu/60000)

<span data-ttu-id="52883-132">現在，請重新執行[dotnet 計數器](dotnet-counters.md)命令。</span><span class="sxs-lookup"><span data-stu-id="52883-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="52883-133">若只要監視 `cpu-usage` ，請指定 `System.Runtime[cpu-usage]` 做為命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="52883-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="52883-134">您應該會看到 CPU 使用量增加，如下所示：</span><span class="sxs-lookup"><span data-stu-id="52883-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="52883-135">在要求的持續期間內，CPU 使用率將會停留在25% 的附近。</span><span class="sxs-lookup"><span data-stu-id="52883-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="52883-136">視主機電腦而定，預期會有不同的 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="52883-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="52883-137">若要將更高的 CPU 使用率視覺化，您可以同時在多個瀏覽器索引標籤中執行此端點。</span><span class="sxs-lookup"><span data-stu-id="52883-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="52883-138">此時，您可以放心地說，CPU 的執行高於您預期的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="52883-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="52883-139">追蹤產生</span><span class="sxs-lookup"><span data-stu-id="52883-139">Trace generation</span></span>

<span data-ttu-id="52883-140">分析緩慢的要求時，您需要可讓您深入瞭解程式碼所執行作業的診斷工具。</span><span class="sxs-lookup"><span data-stu-id="52883-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="52883-141">一般的選擇是分析工具，而且有不同的 profiler 選項可供選擇。</span><span class="sxs-lookup"><span data-stu-id="52883-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="52883-142">Linux</span><span class="sxs-lookup"><span data-stu-id="52883-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="52883-143">此 `perf` 工具可以用來產生 .Net Core 應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="52883-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="52883-144">結束[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)的先前實例。</span><span class="sxs-lookup"><span data-stu-id="52883-144">Exit the previous instance of the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="52883-145">設定 `COMPlus_PerfMapEnabled` 環境變數，使 .Net Core 應用程式 `map` 在目錄中建立檔案 `/tmp` 。</span><span class="sxs-lookup"><span data-stu-id="52883-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="52883-146">這個檔案 `map` 是由用 `perf` 來依名稱將 CPU 位址對應至 JIT 產生的函式。</span><span class="sxs-lookup"><span data-stu-id="52883-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="52883-147">如需詳細資訊，請參閱[Write perf map](../run-time-config/debugging-profiling.md#write-perf-map)。</span><span class="sxs-lookup"><span data-stu-id="52883-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="52883-148">在相同的終端機會話中執行[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)。</span><span class="sxs-lookup"><span data-stu-id="52883-148">Run the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="52883-149">再次練習高 CPU API （ <https://localhost:5001/api/diagscenario/highcpu/60000> ）端點。</span><span class="sxs-lookup"><span data-stu-id="52883-149">Exercise the high CPU API (<https://localhost:5001/api/diagscenario/highcpu/60000>) endpoint again.</span></span> <span data-ttu-id="52883-150">當它在1分鐘的要求內執行時，請 `perf` 使用您的進程 ID 來執行命令：</span><span class="sxs-lookup"><span data-stu-id="52883-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="52883-151">`perf`命令會啟動效能集合進程。</span><span class="sxs-lookup"><span data-stu-id="52883-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="52883-152">讓它執行約20-30 秒，然後按<kbd>Ctrl + C</kbd>結束收集程式。</span><span class="sxs-lookup"><span data-stu-id="52883-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="52883-153">您可以使用相同的 `perf` 命令來查看追蹤的輸出。</span><span class="sxs-lookup"><span data-stu-id="52883-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="52883-154">您也可以使用下列命令來產生_火焰圖形_：</span><span class="sxs-lookup"><span data-stu-id="52883-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="52883-155">此命令會產生 `flamegraph.svg` 您可以在瀏覽器中查看的，以調查效能問題：</span><span class="sxs-lookup"><span data-stu-id="52883-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="52883-156">[![火焰圖形 SVG 影像](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="52883-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="52883-157">Windows</span><span class="sxs-lookup"><span data-stu-id="52883-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="52883-158">在 Windows 上，您可以使用[dotnet 追蹤](dotnet-trace.md)工具做為 profiler。</span><span class="sxs-lookup"><span data-stu-id="52883-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="52883-159">使用先前的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)，再次練習高 CPU （ <https://localhost:5001/api/diagscenario/highcpu/60000> ）端點。</span><span class="sxs-lookup"><span data-stu-id="52883-159">Using the previous [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU (<https://localhost:5001/api/diagscenario/highcpu/60000>) endpoint again.</span></span> <span data-ttu-id="52883-160">當它在1分鐘的要求內執行時，請使用 `collect` 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="52883-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="52883-161">讓[dotnet 追蹤](dotnet-trace.md)執行大約20-30 秒，然後按下<kbd>enter</kbd>鍵結束集合。</span><span class="sxs-lookup"><span data-stu-id="52883-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="52883-162">結果是 `nettrace` 位於相同資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="52883-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="52883-163">這些檔案 `nettrace` 是在 Windows 上使用現有分析工具的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="52883-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="52883-164">使用開啟 `nettrace` ， [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) 如下所示。</span><span class="sxs-lookup"><span data-stu-id="52883-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="52883-165">[![PerfView 影像](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="52883-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="52883-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52883-166">See also</span></span>

- <span data-ttu-id="52883-167">[dotnet-列出進程的追蹤](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="52883-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="52883-168">[dotnet-](dotnet-counters.md)檢查 managed 記憶體使用量的計數器</span><span class="sxs-lookup"><span data-stu-id="52883-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="52883-169">[dotnet-](dotnet-dump.md)用來收集和分析傾印檔案的傾印</span><span class="sxs-lookup"><span data-stu-id="52883-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="52883-170">dotnet/診斷</span><span class="sxs-lookup"><span data-stu-id="52883-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="52883-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="52883-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="52883-172">在 .NET Core 中調試鎖死</span><span class="sxs-lookup"><span data-stu-id="52883-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
