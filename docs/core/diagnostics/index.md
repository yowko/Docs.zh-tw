---
title: 診斷工具概觀 - .NET Core
description: 可用來診斷 .NET Core 應用程式之工具與技術的概觀。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 568f237e131cde18dad7c87ddff2fdd3d4bc5b8b
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89597973"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="87323-103">.NET Core 中有哪些診斷工具可供使用？</span><span class="sxs-lookup"><span data-stu-id="87323-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="87323-104">軟體不一定會如您預期般地運作，但是 .NET Core 具有可協助您迅速且有效地診斷這些問題的工具與 API。</span><span class="sxs-lookup"><span data-stu-id="87323-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="87323-105">此文章會協助您找出所需的各種工具。</span><span class="sxs-lookup"><span data-stu-id="87323-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="87323-106">受控偵錯工具</span><span class="sxs-lookup"><span data-stu-id="87323-106">Managed debuggers</span></span>

<span data-ttu-id="87323-107">[受管理的調試](managed-debuggers.md) 程式可讓您與程式互動。</span><span class="sxs-lookup"><span data-stu-id="87323-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="87323-108">暫停、以累加方式執行、檢查及繼續等功能，可讓您取得您程式碼行為的見解。</span><span class="sxs-lookup"><span data-stu-id="87323-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="87323-109">偵錯工具是診斷可輕易重現之功能性問題的第一個選擇。</span><span class="sxs-lookup"><span data-stu-id="87323-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="87323-110">記錄和追蹤</span><span class="sxs-lookup"><span data-stu-id="87323-110">Logging and tracing</span></span>

<span data-ttu-id="87323-111">[記錄和追蹤](logging-tracing.md) 是相關的技術。</span><span class="sxs-lookup"><span data-stu-id="87323-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="87323-112">它們會參考檢測程式碼以建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87323-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="87323-113">那些檔案會記錄程式所執行之內容的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="87323-113">The files record the details of what a program does.</span></span> <span data-ttu-id="87323-114">這些詳細資料可用來診斷最為複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="87323-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="87323-115">透過與時間戳記結合，這些技術在調查效能方面的問題上也非常有用。</span><span class="sxs-lookup"><span data-stu-id="87323-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="87323-116">單元測試</span><span class="sxs-lookup"><span data-stu-id="87323-116">Unit testing</span></span>

<span data-ttu-id="87323-117">[單元測試](../testing/index.md) 是持續整合和部署高品質軟體的重要元件。</span><span class="sxs-lookup"><span data-stu-id="87323-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="87323-118">單元測試的設計是要在您中斷某個項目時提前警告您。</span><span class="sxs-lookup"><span data-stu-id="87323-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="87323-119">Debug Linux 傾印</span><span class="sxs-lookup"><span data-stu-id="87323-119">Debug Linux dumps</span></span>

<span data-ttu-id="87323-120">[Debug linux](debug-linux-dumps.md) 傾印說明如何收集和分析 linux 上的傾印。</span><span class="sxs-lookup"><span data-stu-id="87323-120">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="87323-121">.NET Core 診斷通用工具</span><span class="sxs-lookup"><span data-stu-id="87323-121">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="87323-122">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="87323-122">dotnet-counters</span></span>

<span data-ttu-id="87323-123">[dotnet-計數器](dotnet-counters.md) 是效能監視工具，適用于第一層健康情況監視和效能調查。</span><span class="sxs-lookup"><span data-stu-id="87323-123">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="87323-124">它會觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="87323-124">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="87323-125">例如，您可以快速監視 CPU 使用量之類的專案，或在 .NET Core 應用程式中擲回例外狀況的速率。</span><span class="sxs-lookup"><span data-stu-id="87323-125">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="87323-126">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="87323-126">dotnet-dump</span></span>

<span data-ttu-id="87323-127">[Dotnet](dotnet-dump.md)傾印工具可在不使用原生偵錯工具的情況下，收集和分析 Windows 和 Linux 核心傾印。</span><span class="sxs-lookup"><span data-stu-id="87323-127">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="87323-128">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="87323-128">dotnet-gcdump</span></span>

<span data-ttu-id="87323-129">[Dotnet-gcdump](dotnet-gcdump.md)工具是一種方式，可 (垃圾收集行程收集即時 .net 處理常式) 傾印。</span><span class="sxs-lookup"><span data-stu-id="87323-129">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="87323-130">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="87323-130">dotnet-trace</span></span>

<span data-ttu-id="87323-131">.NET Core 包含 `EventPipe` 用來公開診斷資料的呼叫。</span><span class="sxs-lookup"><span data-stu-id="87323-131">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="87323-132">[Dotnet 追蹤](dotnet-trace.md)工具可讓您從應用程式取用有趣的分析資料，在需要根本原因的應用程式執行速度變慢的情況下，可能會有所説明。</span><span class="sxs-lookup"><span data-stu-id="87323-132">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="87323-133">dotnet-符號</span><span class="sxs-lookup"><span data-stu-id="87323-133">dotnet-symbol</span></span>

<span data-ttu-id="87323-134">[dotnet-符號](dotnet-symbol.md) 會下載檔案 (符號、DAC/DBI、主機檔案等 ) 需要開啟核心傾印或小型傾印。</span><span class="sxs-lookup"><span data-stu-id="87323-134">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="87323-135">如果您需要符號和模組，以針對在不同電腦上所捕捉的傾印檔案進行調試，請使用此工具。</span><span class="sxs-lookup"><span data-stu-id="87323-135">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="87323-136">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="87323-136">dotnet-sos</span></span>

<span data-ttu-id="87323-137">[dotnet-sos](dotnet-sos.md) 可用來將 [sos 偵錯工具擴充](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) 功能安裝在 Linux 或 MacOS (或 Windows 上（如果使用舊版偵錯工具) ）。</span><span class="sxs-lookup"><span data-stu-id="87323-137">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="87323-138">.NET Core 診斷教學課程</span><span class="sxs-lookup"><span data-stu-id="87323-138">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="87323-139">針對記憶體流失進行偵錯</span><span class="sxs-lookup"><span data-stu-id="87323-139">Debug a memory leak</span></span>

<span data-ttu-id="87323-140">[教學課程：偵測記憶體](debug-memory-leak.md) 流失會逐步引導您找出記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="87323-140">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="87323-141">[Dotnet 計數器](dotnet-counters.md)工具是用來確認流失，而[dotnet](dotnet-dump.md)傾印工具是用來診斷流失的問題。</span><span class="sxs-lookup"><span data-stu-id="87323-141">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="87323-142">針對高 CPU 使用量進行偵錯</span><span class="sxs-lookup"><span data-stu-id="87323-142">Debug high CPU usage</span></span>

<span data-ttu-id="87323-143">[教學課程：「高 cpu 使用率](debug-highcpu.md) 」會逐步引導您調查高 cpu 使用率。</span><span class="sxs-lookup"><span data-stu-id="87323-143">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="87323-144">它會使用 [dotnet 計數器](dotnet-counters.md) 工具來確認高 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="87323-144">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="87323-145">接著，它會逐步引導您使用 [追蹤效能分析公用程式 (`dotnet-trace`) ](dotnet-trace.md) 或 Linux `perf` 收集和查看 CPU 使用量設定檔。</span><span class="sxs-lookup"><span data-stu-id="87323-145">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="87323-146">針對死結進行偵錯</span><span class="sxs-lookup"><span data-stu-id="87323-146">Debug deadlock</span></span>

<span data-ttu-id="87323-147">[教學課程： Debug 鎖死](debug-deadlock.md) 會示範如何使用 [dotnet](dotnet-dump.md) 傾印工具來調查執行緒和鎖定。</span><span class="sxs-lookup"><span data-stu-id="87323-147">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
