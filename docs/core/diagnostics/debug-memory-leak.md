---
title: 除錯記憶體洩漏教程
description: 瞭解如何在 .NET Core 中調試記憶體洩漏。
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: d47992bab9dab64cf7f88ff679eef407dd891b5a
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021354"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="68297-103">教程:在 .NET 核心中調試記憶體洩漏</span><span class="sxs-lookup"><span data-stu-id="68297-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="68297-104">**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="68297-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="68297-105">本教程演示了分析 .NET 核心記憶體洩漏的工具。</span><span class="sxs-lookup"><span data-stu-id="68297-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="68297-106">本教程使用示例應用,該應用旨在有意洩漏記憶體。</span><span class="sxs-lookup"><span data-stu-id="68297-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="68297-107">示例作為練習提供。</span><span class="sxs-lookup"><span data-stu-id="68297-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="68297-108">您可以分析無意中洩漏記憶體的應用。</span><span class="sxs-lookup"><span data-stu-id="68297-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="68297-109">在本教學課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="68297-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="68297-110">使用[點網計數器](dotnet-counters.md)檢查託管記憶體使用方式。</span><span class="sxs-lookup"><span data-stu-id="68297-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="68297-111">生成轉儲檔。</span><span class="sxs-lookup"><span data-stu-id="68297-111">Generate a dump file.</span></span>
> - <span data-ttu-id="68297-112">使用轉儲檔分析記憶體使用方式。</span><span class="sxs-lookup"><span data-stu-id="68297-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68297-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="68297-113">Prerequisites</span></span>

<span data-ttu-id="68297-114">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="68297-114">The tutorial uses:</span></span>

- <span data-ttu-id="68297-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="68297-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="68297-116">[點網跟蹤](dotnet-trace.md)到清單進程。</span><span class="sxs-lookup"><span data-stu-id="68297-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="68297-117">[點網計數器](dotnet-counters.md),用於檢查託管記憶體使用方式。</span><span class="sxs-lookup"><span data-stu-id="68297-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="68297-118">[點網轉儲](dotnet-dump.md)以收集和分析轉儲檔。</span><span class="sxs-lookup"><span data-stu-id="68297-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="68297-119">要診斷[的示例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)應用。</span><span class="sxs-lookup"><span data-stu-id="68297-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="68297-120">本教程假定示例和工具已安裝並可供使用。</span><span class="sxs-lookup"><span data-stu-id="68297-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="68297-121">檢查託管記憶體使用方式</span><span class="sxs-lookup"><span data-stu-id="68297-121">Examine managed memory usage</span></span>

<span data-ttu-id="68297-122">在開始收集診斷數據以幫助我們根本原因此方案之前,您需要確保實際看到記憶體洩漏(記憶體增長)。</span><span class="sxs-lookup"><span data-stu-id="68297-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="68297-123">您可以使用[點網計數器](dotnet-counters.md)工具來確認這一點。</span><span class="sxs-lookup"><span data-stu-id="68297-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="68297-124">開啟主控台視窗並瀏覽到下載的目錄並解壓縮[範例除錯目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)。</span><span class="sxs-lookup"><span data-stu-id="68297-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="68297-125">執行目標:</span><span class="sxs-lookup"><span data-stu-id="68297-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="68297-126">從單獨的主控台,使用[點網追蹤](dotnet-trace.md)工具搜尋行程 ID:</span><span class="sxs-lookup"><span data-stu-id="68297-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="68297-127">輸出應該會類似：</span><span class="sxs-lookup"><span data-stu-id="68297-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="68297-128">現在,使用[點網計數器](dotnet-counters.md)工具檢查託管記憶體使用方式。</span><span class="sxs-lookup"><span data-stu-id="68297-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="68297-129">指定`--refresh-interval`刷新之間的秒數:</span><span class="sxs-lookup"><span data-stu-id="68297-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="68297-130">即時輸出應類似於:</span><span class="sxs-lookup"><span data-stu-id="68297-130">The live output should be similar to:</span></span>

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

<span data-ttu-id="68297-131">專注於這條線:</span><span class="sxs-lookup"><span data-stu-id="68297-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="68297-132">您可以看到託管堆內存在啟動后立即為 4 MB。</span><span class="sxs-lookup"><span data-stu-id="68297-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="68297-133">現在,點擊`http://localhost:5000/api/diagscenario/memleak/20000`URL 。</span><span class="sxs-lookup"><span data-stu-id="68297-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="68297-134">觀察記憶體使用量已增長到 30 MB。</span><span class="sxs-lookup"><span data-stu-id="68297-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="68297-135">通過觀察記憶體使用方式,您可以安全地說記憶體在增長或洩漏。</span><span class="sxs-lookup"><span data-stu-id="68297-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="68297-136">下一步是收集正確的記憶體分析數據。</span><span class="sxs-lookup"><span data-stu-id="68297-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="68297-137">產生記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="68297-137">Generate memory dump</span></span>

<span data-ttu-id="68297-138">分析可能的記憶體洩漏時,您需要存取應用的記憶體堆。</span><span class="sxs-lookup"><span data-stu-id="68297-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="68297-139">然後,您可以分析記憶體內容。</span><span class="sxs-lookup"><span data-stu-id="68297-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="68297-140">觀察對象之間的關係,您創建關於為什麼記憶沒有被釋放的理論。</span><span class="sxs-lookup"><span data-stu-id="68297-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="68297-141">常見的診斷資料來源是 Windows 上的記憶體轉儲或 Linux 上的等效核心轉儲。</span><span class="sxs-lookup"><span data-stu-id="68297-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="68297-142">要生成 .NET Core 應用程式的轉印,可以使用[dotnet 轉印存)](dotnet-dump.md)工具。</span><span class="sxs-lookup"><span data-stu-id="68297-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="68297-143">使用以前啟動[的範例除錯目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/),執行以下指令以產生 Linux 核心轉印:</span><span class="sxs-lookup"><span data-stu-id="68297-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="68297-144">結果是位於同一資料夾中的核心轉儲。</span><span class="sxs-lookup"><span data-stu-id="68297-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="68297-145">重新啟動失敗的行程</span><span class="sxs-lookup"><span data-stu-id="68297-145">Restart the failed process</span></span>

<span data-ttu-id="68297-146">收集轉儲后,您應該有足夠的資訊來診斷失敗的進程。</span><span class="sxs-lookup"><span data-stu-id="68297-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="68297-147">如果失敗的進程在生產伺服器上運行,現在正是通過重新啟動流程進行短期補救的理想時間。</span><span class="sxs-lookup"><span data-stu-id="68297-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="68297-148">在本教學中,您現在已完成[範例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/),您可以關閉它。</span><span class="sxs-lookup"><span data-stu-id="68297-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="68297-149">導覽到啟動伺服器的終端機,`Control-C`然後按 。</span><span class="sxs-lookup"><span data-stu-id="68297-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="68297-150">分析核心傾儲</span><span class="sxs-lookup"><span data-stu-id="68297-150">Analyze the core dump</span></span>

<span data-ttu-id="68297-151">現在生成了核心轉儲,請使用[dotnet 轉儲](dotnet-dump.md)工具分析轉儲:</span><span class="sxs-lookup"><span data-stu-id="68297-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="68297-152">要`core_20190430_185145`分析的核心轉儲的名稱在哪裡。</span><span class="sxs-lookup"><span data-stu-id="68297-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="68297-153">如果您發現錯誤,抱怨找不到*libdl.so,* 您可能需要安裝*libc6-dev*套件。</span><span class="sxs-lookup"><span data-stu-id="68297-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="68297-154">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../install/dependencies.md?pivots=os-linux)。</span><span class="sxs-lookup"><span data-stu-id="68297-154">For more information, see [Prerequisites for .NET Core on Linux](../install/dependencies.md?pivots=os-linux).</span></span>

<span data-ttu-id="68297-155">您將看到一個提示,您可以在其中輸入 SOS 命令。</span><span class="sxs-lookup"><span data-stu-id="68297-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="68297-156">通常,您要查看的第一件事是託管堆的總體狀態:</span><span class="sxs-lookup"><span data-stu-id="68297-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="68297-157">在這裡,您可以看到大多數對像是或`String``Customer`物件。</span><span class="sxs-lookup"><span data-stu-id="68297-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="68297-158">可以將`dumpheap`這個指令與方法表 (MT) 再使用,`String`以取得所有實體的清單:</span><span class="sxs-lookup"><span data-stu-id="68297-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="68297-159">現在,可以使用`System.String`實例`gcroot`上的命令來查看物件如何以及為什麼紮根。</span><span class="sxs-lookup"><span data-stu-id="68297-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="68297-160">耐心等待,因為此命令需要幾分鐘時間使用 30 MB 堆:</span><span class="sxs-lookup"><span data-stu-id="68297-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="68297-161">您可以看到,`String``Customer`由 物件直接持有,並`CustomerCache`間接由 物件持有。</span><span class="sxs-lookup"><span data-stu-id="68297-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="68297-162">您可以繼續轉儲物件,以查看大多數`String`物件遵循類似的模式。</span><span class="sxs-lookup"><span data-stu-id="68297-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="68297-163">此時,調查提供了足夠的信息來識別代碼中的根本原因。</span><span class="sxs-lookup"><span data-stu-id="68297-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="68297-164">此常規過程允許您識別主要記憶體洩漏的來源。</span><span class="sxs-lookup"><span data-stu-id="68297-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="68297-165">清除資源</span><span class="sxs-lookup"><span data-stu-id="68297-165">Clean up resources</span></span>

<span data-ttu-id="68297-166">在本教學中,您啟動了一個範例 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="68297-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="68297-167">如[「重新啟動失敗的進程](#restart-the-failed-process)」部分所述,此伺服器應該已關閉。</span><span class="sxs-lookup"><span data-stu-id="68297-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="68297-168">您還可以刪除建立的轉儲檔。</span><span class="sxs-lookup"><span data-stu-id="68297-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68297-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="68297-169">Next steps</span></span>

<span data-ttu-id="68297-170">祝賀您完成本教程。</span><span class="sxs-lookup"><span data-stu-id="68297-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="68297-171">我們仍在發佈更多診斷教程。</span><span class="sxs-lookup"><span data-stu-id="68297-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="68297-172">您可以在[dotnet/診斷](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)儲存庫上讀取草稿版本。</span><span class="sxs-lookup"><span data-stu-id="68297-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="68297-173">本教程介紹了關鍵 .NET 診斷工具的基礎知識。</span><span class="sxs-lookup"><span data-stu-id="68297-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="68297-174">有關高級用法,請參閱以下參考文檔:</span><span class="sxs-lookup"><span data-stu-id="68297-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="68297-175">[點網跟蹤](dotnet-trace.md)到清單進程。</span><span class="sxs-lookup"><span data-stu-id="68297-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="68297-176">[點網計數器](dotnet-counters.md),用於檢查託管記憶體使用方式。</span><span class="sxs-lookup"><span data-stu-id="68297-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="68297-177">[點網轉儲](dotnet-dump.md)以收集和分析轉儲檔。</span><span class="sxs-lookup"><span data-stu-id="68297-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
