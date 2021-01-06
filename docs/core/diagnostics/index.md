---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: d468ec5b9cc050cc54f6c53f8a4ea4531f8b58f5
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753610"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="ec1bc-103">.NET Core 中有哪些診斷工具可供使用？</span><span class="sxs-lookup"><span data-stu-id="ec1bc-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="ec1bc-104">軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="ec1bc-105">此文章會協助您找出所需的各種工具。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="ec1bc-106">受控偵錯工具</span><span class="sxs-lookup"><span data-stu-id="ec1bc-106">Managed debuggers</span></span>

<span data-ttu-id="ec1bc-107">[受管理的調試](managed-debuggers.md) 程式可讓您與程式互動。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="ec1bc-108">暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="ec1bc-109">偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="ec1bc-110">記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="ec1bc-110">Logging and tracing</span></span>

<span data-ttu-id="ec1bc-111">[記錄和追蹤](logging-tracing.md) 是相關的技術。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="ec1bc-112">它們會參考檢測程式碼以建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="ec1bc-113">那些檔案會記錄程式所執行之內容的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-113">The files record the details of what a program does.</span></span> <span data-ttu-id="ec1bc-114">這些詳細資料可用來診斷最為複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="ec1bc-115">透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="ec1bc-116">計量</span><span class="sxs-lookup"><span data-stu-id="ec1bc-116">Metrics</span></span>

<span data-ttu-id="ec1bc-117">[EventCounters](event-counters.md) 可讓您撰寫度量來識別和監視效能問題。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="ec1bc-118">相較于追蹤，計量會產生較低的效能負荷，因此更適合用於 always on 效能監視。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="ec1bc-119">.NET 執行時間和程式庫會發佈數個 [已知的 EventCounters](available-counters.md) ，您也可以進行監視。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="ec1bc-120">單元測試</span><span class="sxs-lookup"><span data-stu-id="ec1bc-120">Unit testing</span></span>

<span data-ttu-id="ec1bc-121">[單元測試](../testing/index.md) 是持續整合和部署高品質軟體的重要元件。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="ec1bc-122">單元測試的設計是要在您中斷某個項目時提前警告您。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="ec1bc-123">傾印</span><span class="sxs-lookup"><span data-stu-id="ec1bc-123">Dumps</span></span>

<span data-ttu-id="ec1bc-124">傾 [印是一種檔案](./dumps.md) ，其中包含建立時進程的快照集。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="ec1bc-125">這些可能有助於檢查應用程式的狀態，以進行偵測。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="symbols"></a><span data-ttu-id="ec1bc-126">符號</span><span class="sxs-lookup"><span data-stu-id="ec1bc-126">Symbols</span></span>

<span data-ttu-id="ec1bc-127">符號是偵錯工具和其他診斷工具的基本需求。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-127">Symbols are a fundamental requirement for debugging and other diagnostic tools.</span></span> <span data-ttu-id="ec1bc-128">符號檔的內容會因語言、編譯器和平臺而異。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-128">The contents of symbol files vary between languages, compilers, and platforms.</span></span> <span data-ttu-id="ec1bc-129">非常高層級的符號是原始程式碼和編譯器所產生的二進位檔之間的對應。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-129">At a very high level symbols are a mapping between the source code and the binary produced by the compiler.</span></span> <span data-ttu-id="ec1bc-130">這些對應是用來在診斷工具（例如 [Visual Studio](/visualstudio/debugger/what-is-debugging) 和 [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)）中提供一些像是行號資訊和區域變數名稱的專案。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-130">These mappings are used to provide things like line number information and names of your local variables in diagnostics tools such as [Visual Studio](/visualstudio/debugger/what-is-debugging) and [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  <span data-ttu-id="ec1bc-131">下列連結包含 Windows [符號](/windows/win32/dxtecharts/debugging-with-symbols) 的詳細說明，雖然許多概念也適用于其他平臺。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-131">The following link contains a detailed explanation of [symbols](/windows/win32/dxtecharts/debugging-with-symbols) for Windows, although many of the concepts apply to other platforms as well.</span></span> <span data-ttu-id="ec1bc-132">[.Net 可移植符號](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) 具有類似于 windows pdb 的「PDB」副檔名，但與 windows pdb 格式不相容。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-132">[.NET portable symbols](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) have a "PDB" file extension similar to Windows PDB, though are not compatible with the Windows PDB format.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="ec1bc-133">在容器中收集診斷</span><span class="sxs-lookup"><span data-stu-id="ec1bc-133">Collect diagnostics in containers</span></span>

<span data-ttu-id="ec1bc-134">在非容器化 Linux 環境中使用的診斷工具，也可以用來 [收集容器中的診斷](diagnostics-in-containers.md)資訊。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-134">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="ec1bc-135">為了確保工具在 Docker 容器中運作，只需要幾個使用方式變更。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-135">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="ec1bc-136">.NET Core 診斷通用工具</span><span class="sxs-lookup"><span data-stu-id="ec1bc-136">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="ec1bc-137">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ec1bc-137">dotnet-counters</span></span>

<span data-ttu-id="ec1bc-138">[dotnet-計數器](dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-138">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="ec1bc-139">它會觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-139">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="ec1bc-140">例如，您可以快速監視 CPU 使用量之類的專案，或在 .NET Core 應用程式中擲回例外狀況的速率。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-140">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="ec1bc-141">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="ec1bc-141">dotnet-dump</span></span>

<span data-ttu-id="ec1bc-142">[Dotnet](dotnet-dump.md)傾印工具可在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-142">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="ec1bc-143">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="ec1bc-143">dotnet-gcdump</span></span>

<span data-ttu-id="ec1bc-144">[Dotnet-gcdump](dotnet-gcdump.md)工具是一種方式，可 (垃圾收集行程收集即時 .net 處理常式) 傾印。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-144">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="ec1bc-145">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ec1bc-145">dotnet-trace</span></span>

<span data-ttu-id="ec1bc-146">.NET Core 包含 `EventPipe` 用來公開診斷資料的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-146">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="ec1bc-147">[Dotnet 追蹤](dotnet-trace.md)工具可讓您從應用程式取用有趣的分析資料，在需要根本原因的應用程式執行速度變慢的情況下，可能會有所説明。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-147">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="ec1bc-148">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="ec1bc-148">dotnet-symbol</span></span>

<span data-ttu-id="ec1bc-149">[dotnet-符號](dotnet-symbol.md) 會下載檔案 (符號、DAC/DBI、主機檔案等 ) 需要開啟核心傾印或小型傾印。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-149">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="ec1bc-150">如果您需要符號和模組，以針對在不同電腦上所捕捉的傾印檔案進行調試，請使用此工具。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-150">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="ec1bc-151">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="ec1bc-151">dotnet-sos</span></span>

<span data-ttu-id="ec1bc-152">[dotnet-sos](dotnet-sos.md) 會在 Linux 和 macOS (以及在 Windows 上安裝 [sos 調試延伸](sos-debugging-extension.md) 模組（如果您使用 [Windbg/cdb](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)) ）。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-152">[dotnet-sos](dotnet-sos.md) installs the [SOS debugging extension](sos-debugging-extension.md) on Linux and macOS (and on Windows if you're using [Windbg/cdb](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="ec1bc-153">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="ec1bc-153">PerfCollect</span></span>

<span data-ttu-id="ec1bc-154">[PerfCollect](trace-perfcollect-lttng.md) 是一種 bash 腳本，可讓您用來收集追蹤， `perf` 以及 `LTTng` 取得 Linux 發行版本上執行的 .net 應用程式更深入的效能分析。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-154">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="ec1bc-155">.NET Core 診斷教學課程</span><span class="sxs-lookup"><span data-stu-id="ec1bc-155">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="ec1bc-156">針對記憶體流失進行偵錯</span><span class="sxs-lookup"><span data-stu-id="ec1bc-156">Debug a memory leak</span></span>

<span data-ttu-id="ec1bc-157">[教學課程：偵測記憶體](debug-memory-leak.md) 流失會逐步引導您找出記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-157">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="ec1bc-158">[Dotnet 計數器](dotnet-counters.md)工具是用來確認流失，而[dotnet](dotnet-dump.md)傾印工具是用來診斷流失的問題。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-158">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="ec1bc-159">針對高 CPU 使用量進行偵錯</span><span class="sxs-lookup"><span data-stu-id="ec1bc-159">Debug high CPU usage</span></span>

<span data-ttu-id="ec1bc-160">[教學課程：「高 cpu 使用率](debug-highcpu.md) 」會逐步引導您調查高 cpu 使用率。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-160">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="ec1bc-161">它會使用 [dotnet 計數器](dotnet-counters.md) 工具來確認高 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-161">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="ec1bc-162">接著，它會逐步引導您使用 [追蹤效能分析公用程式 (`dotnet-trace`) ](dotnet-trace.md) 或 Linux `perf` 收集和查看 CPU 使用量設定檔。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-162">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="ec1bc-163">針對死結進行偵錯</span><span class="sxs-lookup"><span data-stu-id="ec1bc-163">Debug deadlock</span></span>

<span data-ttu-id="ec1bc-164">[教學課程： Debug 鎖死](debug-deadlock.md) 會示範如何使用 [dotnet](dotnet-dump.md) 傾印工具來調查執行緒和鎖定。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-164">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-a-stackoverflow"></a><span data-ttu-id="ec1bc-165">StackOverflow 的 Debug</span><span class="sxs-lookup"><span data-stu-id="ec1bc-165">Debug a StackOverflow</span></span>

<span data-ttu-id="ec1bc-166">[教學課程： StackOverflow 的 debug](debug-stackoverflow.md) 會示範如何 <xref:System.StackOverflowException> 在 Linux 上的進行 debug 錯。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-166">[Tutorial: Debug a StackOverflow](debug-stackoverflow.md) demonstrates how to debug a <xref:System.StackOverflowException> on Linux.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="ec1bc-167">對 Linux 傾印進行偵錯</span><span class="sxs-lookup"><span data-stu-id="ec1bc-167">Debug Linux dumps</span></span>

<span data-ttu-id="ec1bc-168">[Debug linux](debug-linux-dumps.md) 傾印說明如何收集和分析 linux 上的傾印。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-168">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="ec1bc-169">使用 EventCounters 測量效能</span><span class="sxs-lookup"><span data-stu-id="ec1bc-169">Measure performance using EventCounters</span></span>

<span data-ttu-id="ec1bc-170">[教學課程：在 .net 中使用 EventCounters 測量效能](event-counter-perf.md) 說明如何使用 <xref:System.Diagnostics.Tracing.EventCounter> API 來測量 .net 應用程式中的效能。</span><span class="sxs-lookup"><span data-stu-id="ec1bc-170">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
