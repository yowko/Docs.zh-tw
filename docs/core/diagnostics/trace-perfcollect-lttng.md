---
title: 使用 PerfCollect 追蹤 .NET 應用程式。
description: 本教學課程會逐步引導您使用 .NET 中的 perfcollect 收集追蹤。
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 53e4584953d2af4e766daadfa757cca752ae7329
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593216"
---
# <a name="trace-net-applications-with-perfcollect"></a><span data-ttu-id="a09b1-103">使用 PerfCollect 追蹤 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="a09b1-103">Trace .NET applications with PerfCollect</span></span>

<span data-ttu-id="a09b1-104">本文 **適用于：✔️** .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a09b1-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="a09b1-105">當 Linux 上發生效能問題時，使用收集追蹤 `perfcollect` 可用來收集有關效能問題時電腦上發生之狀況的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a09b1-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="a09b1-106">`perfcollect` 是一種 bash 腳本，它會利用 [Linux 追蹤 Tookit-Next 產生 (LTTng) ](https://lttng.org) 收集從執行時間或任何 [EventSource](xref:System.Diagnostics.Tracing.EventListener)撰寫的事件， [以及使用](https://perf.wiki.kernel.org/) 效能收集目標進程的 CPU 範例。</span><span class="sxs-lookup"><span data-stu-id="a09b1-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="prepare-your-machine"></a><span data-ttu-id="a09b1-107">準備您的電腦</span><span class="sxs-lookup"><span data-stu-id="a09b1-107">Prepare your machine</span></span>

<span data-ttu-id="a09b1-108">遵循下列步驟來準備您的機器，以收集效能追蹤 `perfcollect` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="a09b1-109">如果您是在容器環境中，您的容器必須有 `SYS_ADMIN` 功能。</span><span class="sxs-lookup"><span data-stu-id="a09b1-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="a09b1-110">如需使用 PerfCollect 在容器內追蹤應用程式的詳細資訊，請參閱 [在容器中收集診斷](./diagnostics-in-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="a09b1-110">For more information on tracing applications inside containers using PerfCollect, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

1. <span data-ttu-id="a09b1-111">下載 `perfcollect` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="a09b1-112">讓腳本成為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a09b1-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="a09b1-113">安裝追蹤必要條件-這些是實際的追蹤程式庫。</span><span class="sxs-lookup"><span data-stu-id="a09b1-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="a09b1-114">這會在您的電腦上安裝下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="a09b1-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="a09b1-115">`perf`： Linux 效能事件子系統和隨附的使用者模式集合/檢視器應用程式。</span><span class="sxs-lookup"><span data-stu-id="a09b1-115">`perf`: the Linux Performance Events subsystem and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="a09b1-116">`perf` 是 Linux 核心來源的一部分，但通常不會預設安裝。</span><span class="sxs-lookup"><span data-stu-id="a09b1-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="a09b1-117">`LTTng`：用來捕捉 CoreCLR 在執行時間發出的事件資料。</span><span class="sxs-lookup"><span data-stu-id="a09b1-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="a09b1-118">這項資料接著會用來分析各種執行時間元件的行為，例如 GC、JIT 和執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="a09b1-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT, and thread pool.</span></span>

<span data-ttu-id="a09b1-119">最新版本的 .NET Core 和 Linux 效能工具支援自動解析架構程式碼的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="a09b1-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="a09b1-120">如果您使用的是 .NET Core 3.1 版或更低版本，則需要額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="a09b1-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="a09b1-121">請參閱 [解析架構符號](#resolve-framework-symbols) 以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a09b1-121">See [Resolving Framework Symbols](#resolve-framework-symbols) for details.</span></span>

<span data-ttu-id="a09b1-122">若要解析原生執行時間 Dll 的方法名稱 (例如 libcoreclr.so) ， `perfcollect` 將會在轉換資料時解析它們的符號，但只有在這些二進位檔的符號存在時才會解析這些符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="a09b1-123">如需詳細資料，請參閱 [取得原生運行](#get-symbols-for-the-native-runtime) 時間的符號一節。</span><span class="sxs-lookup"><span data-stu-id="a09b1-123">See [Getting Symbols for the Native Runtime](#get-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collect-a-trace"></a><span data-ttu-id="a09b1-124">收集追蹤</span><span class="sxs-lookup"><span data-stu-id="a09b1-124">Collect a trace</span></span>

1. <span data-ttu-id="a09b1-125">有兩個可用的 shell-一個用來控制追蹤，稱為 **[Trace]**，另一個用來執行應用程式，稱為 **[App]**。</span><span class="sxs-lookup"><span data-stu-id="a09b1-125">Have two shells available - one for controlling tracing, referred to as **[Trace]**, and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="a09b1-126">**[追蹤]** 開始收集。</span><span class="sxs-lookup"><span data-stu-id="a09b1-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="a09b1-127">預期的輸出：</span><span class="sxs-lookup"><span data-stu-id="a09b1-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="a09b1-128">**[應用程式]** 使用下列環境變數來設定應用程式 shell-這會啟用 CoreCLR 的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="a09b1-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="a09b1-129">**[應用程式]** 執行應用程式-讓它在您需要的時間內執行，以便捕捉效能問題。</span><span class="sxs-lookup"><span data-stu-id="a09b1-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="a09b1-130">確切的長度可以是您所需的最短時間，只要它足以捕捉您要調查的效能問題發生的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="a09b1-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="a09b1-131">**[追蹤]** 停止收集-按 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="a09b1-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    <span data-ttu-id="a09b1-132">壓縮的追蹤檔案現在會儲存在目前的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="a09b1-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="a09b1-133">查看追蹤</span><span class="sxs-lookup"><span data-stu-id="a09b1-133">View a trace</span></span>

<span data-ttu-id="a09b1-134">有許多選項可供您用來查看已收集的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a09b1-134">There are a number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="a09b1-135">追蹤最適合使用 Windows 上的 [PerfView](https://aka.ms/perfview) ，但可以直接在 Linux 上使用 `PerfCollect` 本身或來查看 `TraceCompass` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-135">Traces are best viewed using [PerfView](https://aka.ms/perfview) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="use-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="a09b1-136">使用 PerfCollect 來查看追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="a09b1-136">Use PerfCollect to view the trace file</span></span>

<span data-ttu-id="a09b1-137">您可以使用 perfcollect 本身來查看您所收集的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a09b1-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="a09b1-138">若要這樣做，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a09b1-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="a09b1-139">根據預設，這會使用來顯示應用程式的 CPU 追蹤 `perf` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="a09b1-140">若要查看透過所收集的事件 `LTTng` ，您可以傳入旗標 `-viewer lttng` 以查看個別事件：</span><span class="sxs-lookup"><span data-stu-id="a09b1-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="a09b1-141">這會使用 `babeltrace` 檢視器來列印事件承載：</span><span class="sxs-lookup"><span data-stu-id="a09b1-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a><span data-ttu-id="a09b1-142">使用 PerfView 開啟追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="a09b1-142">Use PerfView to open the trace file</span></span>

<span data-ttu-id="a09b1-143">若要查看 CPU 範例和事件的匯總視圖，您可以 `PerfView` 在 Windows 電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="a09b1-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="a09b1-144">將 trace.zip 檔案從 Linux 複製到 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="a09b1-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="a09b1-145">從下載 PerfView <https://aka.ms/perfview> 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-145">Download PerfView from <https://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="a09b1-146">執行 PerfView.exe</span><span class="sxs-lookup"><span data-stu-id="a09b1-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="a09b1-147">PerfView 會根據追蹤檔中包含的資料，顯示支援的視圖清單。</span><span class="sxs-lookup"><span data-stu-id="a09b1-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="a09b1-148">針對 CPU 調查，請選擇 [ **cpu 堆疊**]。</span><span class="sxs-lookup"><span data-stu-id="a09b1-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="a09b1-149">如需詳細的 GC 資訊，請選擇 [ **GCStats**]。</span><span class="sxs-lookup"><span data-stu-id="a09b1-149">For detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="a09b1-150">針對每個進程/模組/方法的 JIT 資訊，請選擇 [ **JITStats**]。</span><span class="sxs-lookup"><span data-stu-id="a09b1-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="a09b1-151">如果沒有您需要的資訊，您可以嘗試在「原始事件」視圖中尋找事件。</span><span class="sxs-lookup"><span data-stu-id="a09b1-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="a09b1-152">選擇 [ **事件**]。</span><span class="sxs-lookup"><span data-stu-id="a09b1-152">Choose **Events**.</span></span>

<span data-ttu-id="a09b1-153">如需有關如何在 PerfView 中解讀視圖的詳細資訊，請參閱 view 本身的說明連結，或從 PerfView 的主視窗中，選擇 [說明 **->使用者指南**]。</span><span class="sxs-lookup"><span data-stu-id="a09b1-153">For more information on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView, choose **Help->Users Guide**.</span></span>

### <a name="use-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="a09b1-154">使用 TraceCompass 開啟追蹤檔案</span><span class="sxs-lookup"><span data-stu-id="a09b1-154">Use TraceCompass to open the trace file</span></span>

<span data-ttu-id="a09b1-155">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) 是另一個可供您用來查看追蹤的選項。</span><span class="sxs-lookup"><span data-stu-id="a09b1-155">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you can use to view the traces.</span></span> <span data-ttu-id="a09b1-156">`TraceCompass` 也可在 Linux 機器上運作，因此您不需要將追蹤移至 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="a09b1-156">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="a09b1-157">若要使用 `TraceCompass` 開啟您的追蹤檔案，您將需要解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="a09b1-157">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="a09b1-158">`perfcollect` 會將收集到的 LTTng 追蹤儲存到中子目錄的 CTF 檔案格式 `lttngTrace` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-158">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="a09b1-159">具體來說，CTF 檔會位於看起來像這樣的目錄中 `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-159">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="a09b1-160">您可以 `TraceCompass` 選取並選取檔案，以開啟中的 CTF 追蹤檔案 `File -> Open Trace` `metadata` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-160">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="a09b1-161">如需詳細資訊，請參閱[ `TraceCompass` 檔](https://www.eclipse.org/tracecompass/)。</span><span class="sxs-lookup"><span data-stu-id="a09b1-161">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolve-framework-symbols"></a><span data-ttu-id="a09b1-162">解析架構符號</span><span class="sxs-lookup"><span data-stu-id="a09b1-162">Resolve framework symbols</span></span>

<span data-ttu-id="a09b1-163">在收集追蹤時，需要手動產生 Framework 符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-163">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="a09b1-164">它們與應用層級符號不同，因為架構是預先編譯的，而應用程式程式碼則是在編譯時進行。</span><span class="sxs-lookup"><span data-stu-id="a09b1-164">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="a09b1-165">針對已先行編譯成機器碼的架構程式碼，您必須呼叫 `crossgen` ，知道如何從機器碼產生對應到方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="a09b1-165">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="a09b1-166">`perfcollect` 可以為您處理大部分的詳細資料，但它必須可以 `crossgen` 使用。</span><span class="sxs-lookup"><span data-stu-id="a09b1-166">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="a09b1-167">依預設，它不會隨 .NET 發行版本一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a09b1-167">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="a09b1-168">如果 `crossgen` 不存在， `perfcollect` 則會警告您，並參考這些指示。</span><span class="sxs-lookup"><span data-stu-id="a09b1-168">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="a09b1-169">若要修正此問題，您必須針對所使用的執行時間，提取正確的 crossgen 版本。</span><span class="sxs-lookup"><span data-stu-id="a09b1-169">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="a09b1-170">如果您將 crossgen 工具放在與 .NET 執行時間 Dll 相同的目錄中 (例如 libcoreclr.so) ，則 `perfcollect` 可以找到它，並為您將架構符號新增至追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="a09b1-170">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (for example, libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="a09b1-171">一般來說，當您建立 .NET 應用程式時，它只會為您撰寫的程式碼產生 DLL，並使用其餘的執行時間共用複本。</span><span class="sxs-lookup"><span data-stu-id="a09b1-171">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="a09b1-172">不過，您也可以產生所謂的「獨立」版本的應用程式，其中包含所有執行時間 Dll。</span><span class="sxs-lookup"><span data-stu-id="a09b1-172">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="a09b1-173">`crossgen` 是 NuGet 套件的一部分，用來建立獨立式應用程式，因此取得正確版本的其中一種方式 `crossgen` 就是建立應用程式的獨立套件。</span><span class="sxs-lookup"><span data-stu-id="a09b1-173">`crossgen` is part of the NuGet package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="a09b1-174">例如：</span><span class="sxs-lookup"><span data-stu-id="a09b1-174">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="a09b1-175">這會建立新的 Hello World 應用程式，並將其建立為獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="a09b1-175">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="a09b1-176">作為建立獨立式應用程式的副作用，dotnet 工具會下載名為 linux-x64 的 NuGet 套件，並將它放在目錄 ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION 中，其中 VERSION 是 .NET Core 執行時間的版本號碼 (例如 2.1.0) 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-176">As a side effect of creating the self-contained application the dotnet tool will download a NuGet package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (for example, 2.1.0).</span></span> <span data-ttu-id="a09b1-177">這是一個工具目錄，裡面有您需要的 crossgen 工具。</span><span class="sxs-lookup"><span data-stu-id="a09b1-177">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="a09b1-178">從 .NET Core 3.0 開始，套件位置是 ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION。</span><span class="sxs-lookup"><span data-stu-id="a09b1-178">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="a09b1-179">此 `crossgen` 工具必須放在應用程式實際使用的執行時間旁。</span><span class="sxs-lookup"><span data-stu-id="a09b1-179">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="a09b1-180">一般來說，您的應用程式會使用安裝在/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION 的 .NET Core 共用版本，其中版本是 .NET 執行時間的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a09b1-180">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="a09b1-181">這是共用的位置，因此您必須是超級使用者才能修改它。</span><span class="sxs-lookup"><span data-stu-id="a09b1-181">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="a09b1-182">如果版本是2.1.0，則要更新的命令將 `crossgen` 會是：</span><span class="sxs-lookup"><span data-stu-id="a09b1-182">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="a09b1-183">完成此步驟之後， `perfcollect` 將會使用 crossgen 來包含架構符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-183">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="a09b1-184">`perfcollect`用來發出問題的警告應該會消失。</span><span class="sxs-lookup"><span data-stu-id="a09b1-184">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="a09b1-185">在您更新執行時間) 之前，每一部電腦只能有一次 (。</span><span class="sxs-lookup"><span data-stu-id="a09b1-185">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="a09b1-186">替代方法：關閉先行編譯器代碼的使用</span><span class="sxs-lookup"><span data-stu-id="a09b1-186">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="a09b1-187">如果您無法更新 .NET 執行時間 (以新增 `crossgen`) ，或上述程式因某些原因而無法運作，則可以使用另一種方法來取得架構符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-187">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="a09b1-188">您可以告訴執行時間單純不使用先行編譯的架構程式碼。</span><span class="sxs-lookup"><span data-stu-id="a09b1-188">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="a09b1-189">這段程式碼將會及時編譯，而且 `crossgen` 不需要。</span><span class="sxs-lookup"><span data-stu-id="a09b1-189">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="a09b1-190">選擇此方法可能會增加應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="a09b1-190">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="a09b1-191">若要這樣做，您可以新增下列環境變數：</span><span class="sxs-lookup"><span data-stu-id="a09b1-191">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="a09b1-192">透過這種變更，您應該會取得所有 .NET 程式碼的符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-192">With this change, you should get the symbols for all .NET code.</span></span>

## <a name="get-symbols-for-the-native-runtime"></a><span data-ttu-id="a09b1-193">取得原生執行時間的符號</span><span class="sxs-lookup"><span data-stu-id="a09b1-193">Get symbols for the native runtime</span></span>

<span data-ttu-id="a09b1-194">大部分情況下，您對自己的程式碼有興趣， `perfcollect` 預設會解決此情況。</span><span class="sxs-lookup"><span data-stu-id="a09b1-194">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="a09b1-195">有時候，查看 .NET Dll 內的內容會很有用 (這是最後一節) 的部分，但有時在原生執行時間 dll 中的情況下， (通常會 libcoreclr.so) ，這是很有趣的事。</span><span class="sxs-lookup"><span data-stu-id="a09b1-195">Sometimes it is useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="a09b1-196">`perfcollect` 會在轉換其資料時解析這些符號，但只有在這些原生 Dll 的符號存在 (，而且位於) 的程式庫旁時，才會解析這些符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-196">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="a09b1-197">有一個稱為 dotnet 的全域命令，它會執行這 [項](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) 工作。</span><span class="sxs-lookup"><span data-stu-id="a09b1-197">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) that does this.</span></span> <span data-ttu-id="a09b1-198">若要使用 dotnet-符號來取得原生執行時間符號：</span><span class="sxs-lookup"><span data-stu-id="a09b1-198">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="a09b1-199">安裝 `dotnet-symbol`：</span><span class="sxs-lookup"><span data-stu-id="a09b1-199">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="a09b1-200">下載符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-200">Download the symbols.</span></span> <span data-ttu-id="a09b1-201">如果您已安裝 .NET Core 執行時間的版本2.1.0，則執行此動作的命令為：</span><span class="sxs-lookup"><span data-stu-id="a09b1-201">If your installed version of the .NET Core runtime is 2.1.0, the command to do this is:</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="a09b1-202">將符號複製到正確的位置。</span><span class="sxs-lookup"><span data-stu-id="a09b1-202">Copy the symbols to the correct place.</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="a09b1-203">如果因為您沒有適當目錄的寫入權限而無法完成，您可以使用 `perf buildid-cache` 新增符號。</span><span class="sxs-lookup"><span data-stu-id="a09b1-203">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="a09b1-204">之後，當您執行時，應該會取得原生 dll 的符號名稱 `perfcollect` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-204">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collect-in-a-docker-container"></a><span data-ttu-id="a09b1-205">在 Docker 容器中收集</span><span class="sxs-lookup"><span data-stu-id="a09b1-205">Collect in a Docker container</span></span>

<span data-ttu-id="a09b1-206">如需有關如何 `perfcollect` 在容器環境中使用的詳細資訊，請參閱在 [容器中收集診斷](./diagnostics-in-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="a09b1-206">For more information on how to use `perfcollect` in container environments, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

## <a name="learn-more-about-collection-options"></a><span data-ttu-id="a09b1-207">深入瞭解收集選項</span><span class="sxs-lookup"><span data-stu-id="a09b1-207">Learn more about collection options</span></span>

<span data-ttu-id="a09b1-208">您可以指定下列選擇性旗標， `perfcollect` 使其更符合您的診斷需求。</span><span class="sxs-lookup"><span data-stu-id="a09b1-208">You can specify the following optional flags with `perfcollect` to better suit your diagnostic needs.</span></span>

### <a name="collect-for-a-specific-duration"></a><span data-ttu-id="a09b1-209">針對特定持續時間進行收集</span><span class="sxs-lookup"><span data-stu-id="a09b1-209">Collect for a specific duration</span></span>

<span data-ttu-id="a09b1-210">當您想要收集特定期間的追蹤時，您可以使用 `-collectsec` 選項，後面接著一個數位，以指定收集追蹤的總秒數。</span><span class="sxs-lookup"><span data-stu-id="a09b1-210">When you want to collect a trace for a specific duration, you can use `-collectsec` option followed by a number specifying the total seconds to collect a trace for.</span></span>

### <a name="collect-threadtime-traces"></a><span data-ttu-id="a09b1-211">收集 threadtime 追蹤</span><span class="sxs-lookup"><span data-stu-id="a09b1-211">Collect threadtime traces</span></span>

<span data-ttu-id="a09b1-212">指定 `-threadtime` with 可 `perfcollect` 讓您收集每個執行緒的 CPU 使用量資料。</span><span class="sxs-lookup"><span data-stu-id="a09b1-212">Specifying `-threadtime` with `perfcollect` lets you collect per-thread CPU usage data.</span></span> <span data-ttu-id="a09b1-213">這可讓您分析每個執行緒花費其 CPU 時間的位置。</span><span class="sxs-lookup"><span data-stu-id="a09b1-213">This lets you analyze where every thread was spending its CPU time.</span></span>

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a><span data-ttu-id="a09b1-214">收集 managed 記憶體和垃圾收集行程效能的追蹤</span><span class="sxs-lookup"><span data-stu-id="a09b1-214">Collect traces for managed memory and garbage collector performance</span></span>

<span data-ttu-id="a09b1-215">下列選項可讓您明確地從執行時間收集 GC 事件。</span><span class="sxs-lookup"><span data-stu-id="a09b1-215">The following options let you specifically collect the GC events from the runtime.</span></span>

* `perfcollect collect -gccollectonly`

<span data-ttu-id="a09b1-216">只收集一組基本的 GC 收集事件。</span><span class="sxs-lookup"><span data-stu-id="a09b1-216">Collect only a minimal set of GC Collection events.</span></span> <span data-ttu-id="a09b1-217">這是最不詳細的 GC 事件集合設定檔，對目標應用程式效能的影響最低。</span><span class="sxs-lookup"><span data-stu-id="a09b1-217">This is the least verbose GC eventing collection profile with the lowest impact on the target app's performance.</span></span> <span data-ttu-id="a09b1-218">此命令類似于 `PerfView.exe /GCCollectOnly collect` PerfView 中的命令。</span><span class="sxs-lookup"><span data-stu-id="a09b1-218">This command is analogous to `PerfView.exe /GCCollectOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gconly`

<span data-ttu-id="a09b1-219">使用 JIT、載入器和例外狀況事件收集更詳細的 GC 收集事件。</span><span class="sxs-lookup"><span data-stu-id="a09b1-219">Collect more verbose GC collection events with JIT, Loader, and Exception events.</span></span> <span data-ttu-id="a09b1-220">這會要求更詳細的事件 (例如配置資訊和 GC 聯結資訊) ，而且對目標應用程式效能的影響會比選項更多 `-gccollectonly` 。</span><span class="sxs-lookup"><span data-stu-id="a09b1-220">This requests more verbose events (such as the allocation information and GC join information) and will have more impact to the target app's performance than `-gccollectonly` option.</span></span> <span data-ttu-id="a09b1-221">此命令類似于 `PerfView.exe /GCOnly collect` PerfView 中的命令。</span><span class="sxs-lookup"><span data-stu-id="a09b1-221">This command is analogous to `PerfView.exe /GCOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gcwithheap`

<span data-ttu-id="a09b1-222">收集最詳細的 GC 收集事件，這些事件也會追蹤堆積的存活和移動。</span><span class="sxs-lookup"><span data-stu-id="a09b1-222">Collect the most verbose GC collection events which tracks the heap survival and movements as well.</span></span> <span data-ttu-id="a09b1-223">這可提供 GC 行為的深入分析，但會產生高效能的成本，因為每個 GC 可能需要兩倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="a09b1-223">This gives in-depth analysis of the GC behavior but will incur high performance cost as each GC can take more than two times longer.</span></span> <span data-ttu-id="a09b1-224">建議您瞭解在生產環境中進行追蹤時，使用此追蹤選項的效能含意。</span><span class="sxs-lookup"><span data-stu-id="a09b1-224">It is recommended you understand the performance implication of using this trace option when tracing in production environments.</span></span>
