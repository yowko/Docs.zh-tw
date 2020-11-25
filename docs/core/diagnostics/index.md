---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: c43e661ad8c9f665151e0240bf6b54e61b9acfef
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031913"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="7d9f3-103">.NET Core 中有哪些診斷工具可供使用？</span><span class="sxs-lookup"><span data-stu-id="7d9f3-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="7d9f3-104">軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="7d9f3-105">此文章會協助您找出所需的各種工具。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="7d9f3-106">受控偵錯工具</span><span class="sxs-lookup"><span data-stu-id="7d9f3-106">Managed debuggers</span></span>

<span data-ttu-id="7d9f3-107">[受管理的調試](managed-debuggers.md) 程式可讓您與程式互動。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="7d9f3-108">暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="7d9f3-109">偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="7d9f3-110">記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="7d9f3-110">Logging and tracing</span></span>

<span data-ttu-id="7d9f3-111">[記錄和追蹤](logging-tracing.md) 是相關的技術。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="7d9f3-112">它們會參考檢測程式碼以建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="7d9f3-113">那些檔案會記錄程式所執行之內容的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-113">The files record the details of what a program does.</span></span> <span data-ttu-id="7d9f3-114">這些詳細資料可用來診斷最為複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="7d9f3-115">透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="7d9f3-116">單元測試</span><span class="sxs-lookup"><span data-stu-id="7d9f3-116">Unit testing</span></span>

<span data-ttu-id="7d9f3-117">[單元測試](../testing/index.md) 是持續整合和部署高品質軟體的重要元件。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="7d9f3-118">單元測試的設計是要在您中斷某個項目時提前警告您。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="7d9f3-119">傾印</span><span class="sxs-lookup"><span data-stu-id="7d9f3-119">Dumps</span></span>

<span data-ttu-id="7d9f3-120">傾 [印是一種檔案](./dumps.md) ，其中包含建立時進程的快照集。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-120">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="7d9f3-121">這些可能有助於檢查應用程式的狀態，以進行偵測。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-121">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="7d9f3-122">在容器中收集診斷</span><span class="sxs-lookup"><span data-stu-id="7d9f3-122">Collect diagnostics in containers</span></span>

<span data-ttu-id="7d9f3-123">在非容器化 Linux 環境中使用的診斷工具，也可以用來 [收集容器中的診斷](diagnostics-in-containers.md)資訊。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-123">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="7d9f3-124">為了確保工具在 Docker 容器中運作，只需要幾個使用方式變更。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-124">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="7d9f3-125">對 Linux 傾印進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7d9f3-125">Debug Linux dumps</span></span>

<span data-ttu-id="7d9f3-126">[Debug linux](debug-linux-dumps.md) 傾印說明如何收集和分析 linux 上的傾印。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-126">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="7d9f3-127">.NET Core 診斷通用工具</span><span class="sxs-lookup"><span data-stu-id="7d9f3-127">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="7d9f3-128">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="7d9f3-128">dotnet-counters</span></span>

<span data-ttu-id="7d9f3-129">[dotnet-計數器](dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-129">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="7d9f3-130">它會觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-130">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="7d9f3-131">例如，您可以快速監視 CPU 使用量之類的專案，或在 .NET Core 應用程式中擲回例外狀況的速率。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-131">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="7d9f3-132">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="7d9f3-132">dotnet-dump</span></span>

<span data-ttu-id="7d9f3-133">[Dotnet](dotnet-dump.md)傾印工具可在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-133">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="7d9f3-134">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="7d9f3-134">dotnet-gcdump</span></span>

<span data-ttu-id="7d9f3-135">[Dotnet-gcdump](dotnet-gcdump.md)工具是一種方式，可 (垃圾收集行程收集即時 .net 處理常式) 傾印。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-135">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="7d9f3-136">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="7d9f3-136">dotnet-trace</span></span>

<span data-ttu-id="7d9f3-137">.NET Core 包含 `EventPipe` 用來公開診斷資料的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-137">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="7d9f3-138">[Dotnet 追蹤](dotnet-trace.md)工具可讓您從應用程式取用有趣的分析資料，在需要根本原因的應用程式執行速度變慢的情況下，可能會有所説明。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-138">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="7d9f3-139">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="7d9f3-139">dotnet-symbol</span></span>

<span data-ttu-id="7d9f3-140">[dotnet-符號](dotnet-symbol.md) 會下載檔案 (符號、DAC/DBI、主機檔案等 ) 需要開啟核心傾印或小型傾印。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-140">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="7d9f3-141">如果您需要符號和模組，以針對在不同電腦上所捕捉的傾印檔案進行調試，請使用此工具。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-141">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="7d9f3-142">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="7d9f3-142">dotnet-sos</span></span>

<span data-ttu-id="7d9f3-143">[dotnet-sos](dotnet-sos.md) 可用來將 [sos 偵錯工具擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能安裝在 Linux 或 MacOS (或 Windows 上（如果使用舊版偵錯工具) ）。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-143">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="7d9f3-144">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="7d9f3-144">PerfCollect</span></span>

<span data-ttu-id="7d9f3-145">[PerfCollect](trace-perfcollect-lttng.md) 是一種 bash 腳本，可讓您用來收集追蹤， `perf` 以及 `LTTng` 取得 Linux 發行版本上執行的 .net 應用程式更深入的效能分析。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-145">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="7d9f3-146">.NET Core 診斷教學課程</span><span class="sxs-lookup"><span data-stu-id="7d9f3-146">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="7d9f3-147">針對記憶體流失進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7d9f3-147">Debug a memory leak</span></span>

<span data-ttu-id="7d9f3-148">[教學課程：偵測記憶體](debug-memory-leak.md) 流失會逐步引導您找出記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-148">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="7d9f3-149">[Dotnet 計數器](dotnet-counters.md)工具是用來確認流失，而[dotnet](dotnet-dump.md)傾印工具是用來診斷流失的問題。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-149">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="7d9f3-150">針對高 CPU 使用量進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7d9f3-150">Debug high CPU usage</span></span>

<span data-ttu-id="7d9f3-151">[教學課程：「高 cpu 使用率](debug-highcpu.md) 」會逐步引導您調查高 cpu 使用率。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-151">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="7d9f3-152">它會使用 [dotnet 計數器](dotnet-counters.md) 工具來確認高 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-152">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="7d9f3-153">接著，它會逐步引導您使用 [追蹤效能分析公用程式 (`dotnet-trace`) ](dotnet-trace.md) 或 Linux `perf` 收集和查看 CPU 使用量設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-153">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="7d9f3-154">針對死結進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7d9f3-154">Debug deadlock</span></span>

<span data-ttu-id="7d9f3-155">[教學課程： Debug 鎖死](debug-deadlock.md) 會示範如何使用 [dotnet](dotnet-dump.md) 傾印工具來調查執行緒和鎖定。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-155">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="7d9f3-156">使用 EventCounters 測量效能</span><span class="sxs-lookup"><span data-stu-id="7d9f3-156">Measure performance using EventCounters</span></span>

<span data-ttu-id="7d9f3-157">[教學課程：在 .net 中使用 EventCounters 測量效能](event-counter-perf.md) 說明如何使用 <xref:System.Diagnostics.Tracing.EventCounter> API 來測量 .net 應用程式中的效能。</span><span class="sxs-lookup"><span data-stu-id="7d9f3-157">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
