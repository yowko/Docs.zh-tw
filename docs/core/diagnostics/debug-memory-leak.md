---
title: 調試記憶體流失教學課程
description: 瞭解如何在 .NET Core 中偵測記憶體流失。
author: sdmaclea
ms.author: stmaclea
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: def848b5fe6f08cf32067b833bbf6a97a56edda1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443509"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="f32b6-103">教學課程：在 .NET Core 中偵測記憶體流失</span><span class="sxs-lookup"><span data-stu-id="f32b6-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="f32b6-104">**本文適用于：✓** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f32b6-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="f32b6-105">本教學課程示範用來分析 .NET Core 記憶體流失的工具。</span><span class="sxs-lookup"><span data-stu-id="f32b6-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="f32b6-106">本教學課程使用範例應用程式，其設計目的是刻意流失記憶體。</span><span class="sxs-lookup"><span data-stu-id="f32b6-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="f32b6-107">範例是以練習的形式提供。</span><span class="sxs-lookup"><span data-stu-id="f32b6-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="f32b6-108">您也可以分析意外流失記憶體的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f32b6-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="f32b6-109">在本教學課程中，您將進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f32b6-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f32b6-110">使用[dotnet-計數器](dotnet-counters.md)檢查 managed 記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="f32b6-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="f32b6-111">產生傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="f32b6-111">Generate a dump file.</span></span>
> - <span data-ttu-id="f32b6-112">使用傾印檔案來分析記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="f32b6-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f32b6-113">必要條件：</span><span class="sxs-lookup"><span data-stu-id="f32b6-113">Prerequisites</span></span>

<span data-ttu-id="f32b6-114">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="f32b6-114">The tutorial uses:</span></span>

- <span data-ttu-id="f32b6-115">[.Net Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f32b6-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="f32b6-116">[dotnet-](dotnet-trace.md)用來列出進程的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f32b6-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="f32b6-117">[dotnet-](dotnet-counters.md)用來檢查 managed 記憶體使用量的計數器。</span><span class="sxs-lookup"><span data-stu-id="f32b6-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="f32b6-118">[dotnet-](dotnet-dump.md)傾印以收集和分析傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="f32b6-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="f32b6-119">要診斷的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)應用程式。</span><span class="sxs-lookup"><span data-stu-id="f32b6-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="f32b6-120">本教學課程假設已安裝範例和工具，並可供使用。</span><span class="sxs-lookup"><span data-stu-id="f32b6-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="f32b6-121">檢查 managed 記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="f32b6-121">Examine managed memory usage</span></span>

<span data-ttu-id="f32b6-122">在您開始收集診斷資料以協助我們根本造成這種情況時，您必須確定您確實看到記憶體流失（記憶體成長）。</span><span class="sxs-lookup"><span data-stu-id="f32b6-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="f32b6-123">您可以使用[dotnet 計數器](dotnet-counters.md)工具來確認。</span><span class="sxs-lookup"><span data-stu-id="f32b6-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="f32b6-124">開啟主控台視窗，並流覽至您下載並解壓縮[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)的目錄。</span><span class="sxs-lookup"><span data-stu-id="f32b6-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="f32b6-125">執行目標：</span><span class="sxs-lookup"><span data-stu-id="f32b6-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="f32b6-126">從個別的主控台，使用[dotnet 追蹤](dotnet-trace.md)工具來尋找處理序識別碼：</span><span class="sxs-lookup"><span data-stu-id="f32b6-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="f32b6-127">輸出應該會類似：</span><span class="sxs-lookup"><span data-stu-id="f32b6-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="f32b6-128">現在，使用[dotnet 計數器](dotnet-counters.md)工具來檢查 managed 記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="f32b6-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="f32b6-129">`--refresh-interval` 指定重新整理之間的秒數：</span><span class="sxs-lookup"><span data-stu-id="f32b6-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="f32b6-130">即時輸出應該類似：</span><span class="sxs-lookup"><span data-stu-id="f32b6-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="f32b6-131">重點放在這一行：</span><span class="sxs-lookup"><span data-stu-id="f32b6-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="f32b6-132">在啟動之後，您可以看到受控堆積記憶體是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="f32b6-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="f32b6-133">現在，請按 `http://localhost:5000/api/diagscenario/memleak/20000`的 URL。</span><span class="sxs-lookup"><span data-stu-id="f32b6-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="f32b6-134">請注意，記憶體使用量已增加至 30 MB。</span><span class="sxs-lookup"><span data-stu-id="f32b6-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="f32b6-135">藉由監看記憶體使用量，您可以放心地指出記憶體正在增加或流失。</span><span class="sxs-lookup"><span data-stu-id="f32b6-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="f32b6-136">下一個步驟是收集正確的記憶體分析資料。</span><span class="sxs-lookup"><span data-stu-id="f32b6-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="f32b6-137">產生記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="f32b6-137">Generate memory dump</span></span>

<span data-ttu-id="f32b6-138">分析可能的記憶體流失時，您需要存取應用程式的記憶體堆積。</span><span class="sxs-lookup"><span data-stu-id="f32b6-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="f32b6-139">然後您就可以分析記憶體內容。</span><span class="sxs-lookup"><span data-stu-id="f32b6-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="f32b6-140">查看物件之間的關聯性時，您會建立理論，說明為何無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="f32b6-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="f32b6-141">常見的診斷資料來源是 Windows 上的記憶體傾印或 Linux 上的對等核心傾印。</span><span class="sxs-lookup"><span data-stu-id="f32b6-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="f32b6-142">若要產生 .NET Core 應用程式的傾印，您可以使用[dotnet-dump）](dotnet-dump.md)工具。</span><span class="sxs-lookup"><span data-stu-id="f32b6-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="f32b6-143">使用先前啟動的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，執行下列命令以產生 Linux 核心傾印：</span><span class="sxs-lookup"><span data-stu-id="f32b6-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="f32b6-144">結果是位於相同資料夾中的核心傾印。</span><span class="sxs-lookup"><span data-stu-id="f32b6-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="f32b6-145">重新開機失敗的進程</span><span class="sxs-lookup"><span data-stu-id="f32b6-145">Restart the failed process</span></span>

<span data-ttu-id="f32b6-146">收集到傾印之後，您應該會有足夠的資訊來診斷失敗的進程。</span><span class="sxs-lookup"><span data-stu-id="f32b6-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="f32b6-147">如果失敗的進程是在實際執行伺服器上執行，現在是重新開機程式，這是短期補救的理想時機。</span><span class="sxs-lookup"><span data-stu-id="f32b6-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="f32b6-148">在本教學課程中，您現在已完成[範例的 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，而且您可以將它關閉。</span><span class="sxs-lookup"><span data-stu-id="f32b6-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="f32b6-149">流覽至啟動伺服器的終端機，然後按 `Control-C`。</span><span class="sxs-lookup"><span data-stu-id="f32b6-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="f32b6-150">分析核心傾印</span><span class="sxs-lookup"><span data-stu-id="f32b6-150">Analyze the core dump</span></span>

<span data-ttu-id="f32b6-151">現在您已產生核心傾印，請使用[dotnet-](dotnet-dump.md)傾印）工具來分析傾印：</span><span class="sxs-lookup"><span data-stu-id="f32b6-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="f32b6-152">其中 `core_20190430_185145` 是您想要分析的核心傾印名稱。</span><span class="sxs-lookup"><span data-stu-id="f32b6-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="f32b6-153">如果您看到錯誤，指出找不到*libdl.so* ，您可能必須安裝*libc6 開發人員*套件。</span><span class="sxs-lookup"><span data-stu-id="f32b6-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="f32b6-154">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../linux-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="f32b6-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="f32b6-155">您會看到提示，您可以在其中輸入 SOS 命令。</span><span class="sxs-lookup"><span data-stu-id="f32b6-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="f32b6-156">通常，您想要查看的第一件事是受控堆積的整體狀態：</span><span class="sxs-lookup"><span data-stu-id="f32b6-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="f32b6-157">在這裡，您可以看到大部分的物件都是 `String` 或 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="f32b6-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="f32b6-158">您可以使用 [`dumpheap`] 命令，搭配方法表（MT）來取得所有 `String` 實例的清單：</span><span class="sxs-lookup"><span data-stu-id="f32b6-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="f32b6-159">您現在可以在 `System.String` 實例上使用 `gcroot` 命令，以查看物件的根目錄和原因。</span><span class="sxs-lookup"><span data-stu-id="f32b6-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="f32b6-160">請耐心等候，因為此命令需要幾分鐘的時間，其中包含 30 MB 的堆積：</span><span class="sxs-lookup"><span data-stu-id="f32b6-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="f32b6-161">您可以看到 `String` 直接由 `Customer` 物件持有，並由 `CustomerCache` 物件間接持有。</span><span class="sxs-lookup"><span data-stu-id="f32b6-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="f32b6-162">您可以繼續傾印物件，以查看大部分的 `String` 物件遵循類似的模式。</span><span class="sxs-lookup"><span data-stu-id="f32b6-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="f32b6-163">此時，調查已提供足夠的資訊來識別程式碼中的根本原因。</span><span class="sxs-lookup"><span data-stu-id="f32b6-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="f32b6-164">這個一般程式可讓您識別主要記憶體流失的來源。</span><span class="sxs-lookup"><span data-stu-id="f32b6-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="f32b6-165">清除資源</span><span class="sxs-lookup"><span data-stu-id="f32b6-165">Clean up resources</span></span>

<span data-ttu-id="f32b6-166">在本教學課程中，您已啟動範例 web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f32b6-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="f32b6-167">此伺服器應已關閉，如[重新開機失敗的進程](#restart-the-failed-process)一節中所述。</span><span class="sxs-lookup"><span data-stu-id="f32b6-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="f32b6-168">您也可以刪除已建立的傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="f32b6-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f32b6-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f32b6-169">Next steps</span></span>

<span data-ttu-id="f32b6-170">恭喜您完成本教學課程。</span><span class="sxs-lookup"><span data-stu-id="f32b6-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="f32b6-171">我們仍在發行更多診斷教學課程。</span><span class="sxs-lookup"><span data-stu-id="f32b6-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="f32b6-172">您可以閱讀[dotnet/診斷](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)存放庫中的草稿版本。</span><span class="sxs-lookup"><span data-stu-id="f32b6-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="f32b6-173">本教學課程涵蓋重要 .NET 診斷工具的基本概念。</span><span class="sxs-lookup"><span data-stu-id="f32b6-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="f32b6-174">如需先進的使用方式，請參閱下列參考檔：</span><span class="sxs-lookup"><span data-stu-id="f32b6-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="f32b6-175">[dotnet-](dotnet-trace.md)用來列出進程的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f32b6-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="f32b6-176">[dotnet-](dotnet-counters.md)用來檢查 managed 記憶體使用量的計數器。</span><span class="sxs-lookup"><span data-stu-id="f32b6-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="f32b6-177">[dotnet-](dotnet-dump.md)傾印以收集和分析傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="f32b6-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
