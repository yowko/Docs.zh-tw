---
title: 偵測記憶體流失教學課程
description: 瞭解如何在 .NET Core 中偵測記憶體流失。
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 7fa87a411606e81ffe91348c3cbce5f258a6e4e2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538588"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="377aa-103">在 .NET Core 中偵測記憶體流失</span><span class="sxs-lookup"><span data-stu-id="377aa-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="377aa-104">本文**適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="377aa-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="377aa-105">本教學課程示範用來分析 .NET Core 記憶體流失的工具。</span><span class="sxs-lookup"><span data-stu-id="377aa-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="377aa-106">本教學課程使用範例應用程式，其設計目的是刻意洩漏記憶體。</span><span class="sxs-lookup"><span data-stu-id="377aa-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="377aa-107">範例是以練習的形式提供。</span><span class="sxs-lookup"><span data-stu-id="377aa-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="377aa-108">您也可以分析意外流失記憶體的應用程式。</span><span class="sxs-lookup"><span data-stu-id="377aa-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="377aa-109">在本教學課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="377aa-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="377aa-110">檢查 [dotnet 計數器](dotnet-counters.md)的 managed 記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="377aa-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="377aa-111">產生傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="377aa-111">Generate a dump file.</span></span>
> - <span data-ttu-id="377aa-112">使用傾印檔案分析記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="377aa-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="377aa-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="377aa-113">Prerequisites</span></span>

<span data-ttu-id="377aa-114">教學課程會使用：</span><span class="sxs-lookup"><span data-stu-id="377aa-114">The tutorial uses:</span></span>

- <span data-ttu-id="377aa-115">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="377aa-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="377aa-116">[dotnet-追蹤](dotnet-trace.md) 以列出進程。</span><span class="sxs-lookup"><span data-stu-id="377aa-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="377aa-117">[dotnet-](dotnet-counters.md) 用來檢查 managed 記憶體使用量的計數器。</span><span class="sxs-lookup"><span data-stu-id="377aa-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="377aa-118">[dotnet-](dotnet-dump.md) 傾印可收集和分析傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="377aa-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="377aa-119">要診斷的 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios/) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="377aa-119">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="377aa-120">本教學課程假設範例和工具已安裝且可供使用。</span><span class="sxs-lookup"><span data-stu-id="377aa-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="377aa-121">檢查受控記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="377aa-121">Examine managed memory usage</span></span>

<span data-ttu-id="377aa-122">在您開始收集診斷資料以協助我們根本原因的情況下，您必須確定您實際上看到記憶體流失 (記憶體成長) 。</span><span class="sxs-lookup"><span data-stu-id="377aa-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="377aa-123">您可以使用 [dotnet 計數器](dotnet-counters.md) 工具來確認。</span><span class="sxs-lookup"><span data-stu-id="377aa-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="377aa-124">開啟主控台視窗，並流覽至您下載並解壓縮 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios/)的目錄。</span><span class="sxs-lookup"><span data-stu-id="377aa-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="377aa-125">執行目標：</span><span class="sxs-lookup"><span data-stu-id="377aa-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="377aa-126">從個別的主控台中，使用 [dotnet 追蹤](dotnet-trace.md) 工具尋找處理序識別碼：</span><span class="sxs-lookup"><span data-stu-id="377aa-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="377aa-127">輸出應該會類似：</span><span class="sxs-lookup"><span data-stu-id="377aa-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="377aa-128">現在，請使用 [dotnet 計數器](dotnet-counters.md) 工具檢查 managed 記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="377aa-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="377aa-129">指定重新整理 `--refresh-interval` 之間的秒數：</span><span class="sxs-lookup"><span data-stu-id="377aa-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="377aa-130">即時輸出應如下所示：</span><span class="sxs-lookup"><span data-stu-id="377aa-130">The live output should be similar to:</span></span>

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

<span data-ttu-id="377aa-131">將焦點放在這一行：</span><span class="sxs-lookup"><span data-stu-id="377aa-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="377aa-132">您可以在啟動後看到 managed 堆積記憶體是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="377aa-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="377aa-133">現在，按下 URL `https://localhost:5001/api/diagscenario/memleak/20000` 。</span><span class="sxs-lookup"><span data-stu-id="377aa-133">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="377aa-134">觀察記憶體使用量已成長至 30 MB。</span><span class="sxs-lookup"><span data-stu-id="377aa-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="377aa-135">藉由監看記憶體使用量，您可以放心地指出記憶體正在成長或流失。</span><span class="sxs-lookup"><span data-stu-id="377aa-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="377aa-136">下一步是收集正確的記憶體分析資料。</span><span class="sxs-lookup"><span data-stu-id="377aa-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="377aa-137">產生記憶體傾印</span><span class="sxs-lookup"><span data-stu-id="377aa-137">Generate memory dump</span></span>

<span data-ttu-id="377aa-138">在分析可能的記憶體流失時，您需要存取應用程式的記憶體堆積。</span><span class="sxs-lookup"><span data-stu-id="377aa-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="377aa-139">然後您就可以分析記憶體內容。</span><span class="sxs-lookup"><span data-stu-id="377aa-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="377aa-140">查看物件之間的關聯性，您可以建立理論，以瞭解為何無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="377aa-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="377aa-141">常見的診斷資料來源是 Windows 上的記憶體傾印或 Linux 上對等的核心轉儲。</span><span class="sxs-lookup"><span data-stu-id="377aa-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="377aa-142">若要產生 .NET Core 應用程式的傾印，您可以使用 [dotnet) ](dotnet-dump.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="377aa-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="377aa-143">使用先前啟動的 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios/) ，執行下列命令以產生 Linux core 傾印：</span><span class="sxs-lookup"><span data-stu-id="377aa-143">Using the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="377aa-144">結果是位於相同資料夾的核心傾印。</span><span class="sxs-lookup"><span data-stu-id="377aa-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="377aa-145">重新開機失敗的進程</span><span class="sxs-lookup"><span data-stu-id="377aa-145">Restart the failed process</span></span>

<span data-ttu-id="377aa-146">收集傾印之後，您應該有足夠的資訊來診斷失敗的進程。</span><span class="sxs-lookup"><span data-stu-id="377aa-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="377aa-147">如果在實際執行伺服器上執行失敗的程式，現在是重新開機處理常式的短期補救的理想時間。</span><span class="sxs-lookup"><span data-stu-id="377aa-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="377aa-148">在本教學課程中，您現在已完成 [範例 debug 目標](/samples/dotnet/samples/diagnostic-scenarios/) ，而且您可以將它關閉。</span><span class="sxs-lookup"><span data-stu-id="377aa-148">In this tutorial, you're now done with the [Sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="377aa-149">流覽至啟動伺服器的終端機，然後按下 <kbd>Ctrl + C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="377aa-149">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="377aa-150">分析核心傾印</span><span class="sxs-lookup"><span data-stu-id="377aa-150">Analyze the core dump</span></span>

<span data-ttu-id="377aa-151">現在您已產生核心傾印，請使用 [dotnet](dotnet-dump.md) 傾印工具來分析傾印：</span><span class="sxs-lookup"><span data-stu-id="377aa-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="377aa-152">其中 `core_20190430_185145` 是您想要分析的核心轉儲的名稱。</span><span class="sxs-lookup"><span data-stu-id="377aa-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="377aa-153">如果您發現抱怨找不到 *libdl.so* 的錯誤，您可能必須安裝 *libc6 開發* 套件。</span><span class="sxs-lookup"><span data-stu-id="377aa-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="377aa-154">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../install/linux.md)。</span><span class="sxs-lookup"><span data-stu-id="377aa-154">For more information, see [Prerequisites for .NET Core on Linux](../install/linux.md).</span></span>

<span data-ttu-id="377aa-155">您將會看到可輸入 SOS 命令的提示。</span><span class="sxs-lookup"><span data-stu-id="377aa-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="377aa-156">通常，您想要查看的第一件事是 managed 堆積的整體狀態：</span><span class="sxs-lookup"><span data-stu-id="377aa-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="377aa-157">在這裡，您可以看到大部分的物件都是 `String` 或 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="377aa-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="377aa-158">您可以使用命令，搭配 `dumpheap` 方法資料表 (MT) 來取得所有實例的清單 `String` ：</span><span class="sxs-lookup"><span data-stu-id="377aa-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="377aa-159">您現在可以 `gcroot` 在實例上使用命令， `System.String` 以查看物件的根目錄和原因。</span><span class="sxs-lookup"><span data-stu-id="377aa-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="377aa-160">請耐心等候，因為此命令需要幾分鐘的時間，且具有 30 MB 的堆積：</span><span class="sxs-lookup"><span data-stu-id="377aa-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="377aa-161">您可以看到， `String` 直接由物件保留， `Customer` 且由物件間接保留 `CustomerCache` 。</span><span class="sxs-lookup"><span data-stu-id="377aa-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="377aa-162">您可以繼續傾印物件，以查看大部分的 `String` 物件都遵循類似的模式。</span><span class="sxs-lookup"><span data-stu-id="377aa-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="377aa-163">此時，調查已提供足夠的資訊來識別程式碼中的根本原因。</span><span class="sxs-lookup"><span data-stu-id="377aa-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="377aa-164">此一般程式可讓您識別主要記憶體流失的來源。</span><span class="sxs-lookup"><span data-stu-id="377aa-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="377aa-165">清除資源</span><span class="sxs-lookup"><span data-stu-id="377aa-165">Clean up resources</span></span>

<span data-ttu-id="377aa-166">在本教學課程中，您已啟動範例 web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="377aa-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="377aa-167">此伺服器應該已關閉，如「 [重新開機失敗的](#restart-the-failed-process) 程式」一節所述。</span><span class="sxs-lookup"><span data-stu-id="377aa-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="377aa-168">您也可以刪除已建立的傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="377aa-168">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="377aa-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="377aa-169">See also</span></span>

- <span data-ttu-id="377aa-170">[dotnet-列出進程的追蹤](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="377aa-170">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="377aa-171">[dotnet-](dotnet-counters.md) 檢查 managed 記憶體使用量的計數器</span><span class="sxs-lookup"><span data-stu-id="377aa-171">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="377aa-172">[dotnet-](dotnet-dump.md) 傾印以收集及分析傾印檔案</span><span class="sxs-lookup"><span data-stu-id="377aa-172">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="377aa-173">dotnet/診斷</span><span class="sxs-lookup"><span data-stu-id="377aa-173">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="377aa-174">後續步驟</span><span class="sxs-lookup"><span data-stu-id="377aa-174">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="377aa-175">在 .NET Core 中調試高 CPU</span><span class="sxs-lookup"><span data-stu-id="377aa-175">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
