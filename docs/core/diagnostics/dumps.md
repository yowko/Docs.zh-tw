---
title: 傾印-.NET
description: .NET 中傾印的簡介。
ms.date: 10/12/2020
ms.openlocfilehash: 56cf4085d10658c828bac39be93eed3f774e00d5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242769"
---
# <a name="dumps"></a><span data-ttu-id="bd63d-103">傾印</span><span class="sxs-lookup"><span data-stu-id="bd63d-103">Dumps</span></span>

<span data-ttu-id="bd63d-104">傾印是一個檔案，其中包含建立進程的快照集，而且在檢查應用程式的狀態時很有用。</span><span class="sxs-lookup"><span data-stu-id="bd63d-104">A dump is a file that contains a snapshot of the process at the time it was created and can be useful for examining the state of your application.</span></span> <span data-ttu-id="bd63d-105">當您很難將偵錯工具附加至應用程式，例如生產或 CI 環境時，可使用傾印來對 .NET 應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bd63d-105">Dumps can be used to debug your .NET application when it is difficult to attach a debugger to it such as production or CI environments.</span></span> <span data-ttu-id="bd63d-106">使用傾印可讓您捕捉有問題的程式狀態，並檢查它，而不需要停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd63d-106">Using dumps allows you to capture the state of the problematic process and examine it without having to stop the application.</span></span>

## <a name="collect-dumps"></a><span data-ttu-id="bd63d-107">收集傾印</span><span class="sxs-lookup"><span data-stu-id="bd63d-107">Collect dumps</span></span>

<span data-ttu-id="bd63d-108">您可以透過各種方式收集傾印，視您執行應用程式的平臺而定。</span><span class="sxs-lookup"><span data-stu-id="bd63d-108">Dumps can be collected in a variety of ways depending on which platform you are running your app on.</span></span>

> [!NOTE]
> <span data-ttu-id="bd63d-109">在容器內收集傾印需要 PTRACE 功能，可透過 `--cap-add=SYS_PTRACE` 或新增 `--privileged` 。</span><span class="sxs-lookup"><span data-stu-id="bd63d-109">Collecting a dump inside a container requires PTRACE capability, which can be added via `--cap-add=SYS_PTRACE` or `--privileged`.</span></span>

> [!NOTE]
> <span data-ttu-id="bd63d-110">傾印可能包含機密資訊，因為它們可以包含執行中進程的完整記憶體。</span><span class="sxs-lookup"><span data-stu-id="bd63d-110">Dumps may contain sensitive information because they can contain the full memory of the running process.</span></span> <span data-ttu-id="bd63d-111">請注意任何安全性限制和 guidances 的處理方式。</span><span class="sxs-lookup"><span data-stu-id="bd63d-111">Handle them with any security restrictions and guidances in mind.</span></span>

### <a name="collecting-dumps-on-crash"></a><span data-ttu-id="bd63d-112">在損毀時收集傾印</span><span class="sxs-lookup"><span data-stu-id="bd63d-112">Collecting dumps on crash</span></span>

<span data-ttu-id="bd63d-113">您可以使用環境變數來設定應用程式，以在損毀時收集傾印。</span><span class="sxs-lookup"><span data-stu-id="bd63d-113">You can use environment variables to configure your application to collect a dump upon a crash.</span></span> <span data-ttu-id="bd63d-114">當您想要瞭解發生損毀的原因時，這會很有説明。</span><span class="sxs-lookup"><span data-stu-id="bd63d-114">This is helpful when you want to get an understanding of why a crash happened.</span></span> <span data-ttu-id="bd63d-115">例如，當擲回例外狀況時，捕捉傾印可協助您在應用程式損毀時檢查應用程式的狀態，以找出問題。</span><span class="sxs-lookup"><span data-stu-id="bd63d-115">For example, capturing a dump when an exception is thrown helps you identify an issue by examining the state of the app when it crashed.</span></span>

<span data-ttu-id="bd63d-116">下表顯示您可以設定的環境變數，以便在損毀時收集傾印。</span><span class="sxs-lookup"><span data-stu-id="bd63d-116">The following table shows the environment variables you can configure for collecting dumps on a crash.</span></span>

|<span data-ttu-id="bd63d-117">環境變數</span><span class="sxs-lookup"><span data-stu-id="bd63d-117">Environment variable</span></span>|<span data-ttu-id="bd63d-118">描述</span><span class="sxs-lookup"><span data-stu-id="bd63d-118">Description</span></span>|<span data-ttu-id="bd63d-119">預設值</span><span class="sxs-lookup"><span data-stu-id="bd63d-119">Default value</span></span>|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|<span data-ttu-id="bd63d-120">如果設定為1，則啟用核心傾印產生。</span><span class="sxs-lookup"><span data-stu-id="bd63d-120">If set to 1, enable core dump generation.</span></span>|<span data-ttu-id="bd63d-121">0</span><span class="sxs-lookup"><span data-stu-id="bd63d-121">0</span></span>|
|`COMPlus_DbgMiniDumpType`|<span data-ttu-id="bd63d-122">要收集的傾印類型。</span><span class="sxs-lookup"><span data-stu-id="bd63d-122">Type of dump to be collected.</span></span> <span data-ttu-id="bd63d-123">如需詳細資訊，請參閱下表</span><span class="sxs-lookup"><span data-stu-id="bd63d-123">For more information, see the table below</span></span>|<span data-ttu-id="bd63d-124">2 (`MiniDumpWithPrivateReadWriteMemory`) </span><span class="sxs-lookup"><span data-stu-id="bd63d-124">2 (`MiniDumpWithPrivateReadWriteMemory`)</span></span>|
|`COMPlus_DbgMiniDumpName`|<span data-ttu-id="bd63d-125">寫入傾印之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="bd63d-125">Path to a file to write the dump to.</span></span>|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|<span data-ttu-id="bd63d-126">如果設定為1，則啟用傾印處理的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="bd63d-126">If set to 1, enable diagnostic logging of dump process.</span></span>|<span data-ttu-id="bd63d-127">0</span><span class="sxs-lookup"><span data-stu-id="bd63d-127">0</span></span>|

<span data-ttu-id="bd63d-128">下表顯示您可以用來指定做為值的所有選項 `COMPlus_DbgMiniDumpType` 。</span><span class="sxs-lookup"><span data-stu-id="bd63d-128">The table below shows all the options you may use for `COMPlus_DbgMiniDumpType` which can be specified as a value.</span></span> <span data-ttu-id="bd63d-129">例如，將設定 `COMPlus_DbgMiniDumpType` 為1，表示 `MiniDumpNormal` 會在損毀時收集型別傾印。</span><span class="sxs-lookup"><span data-stu-id="bd63d-129">For example, setting `COMPlus_DbgMiniDumpType` to 1 means `MiniDumpNormal` type dump will be collected on a crash.</span></span>

|<span data-ttu-id="bd63d-130">值</span><span class="sxs-lookup"><span data-stu-id="bd63d-130">Value</span></span>|<span data-ttu-id="bd63d-131">名稱</span><span class="sxs-lookup"><span data-stu-id="bd63d-131">Name</span></span>|<span data-ttu-id="bd63d-132">描述</span><span class="sxs-lookup"><span data-stu-id="bd63d-132">Description</span></span>|
|-----|----|-----------|
|<span data-ttu-id="bd63d-133">1</span><span class="sxs-lookup"><span data-stu-id="bd63d-133">1</span></span>|`MiniDumpNormal`|<span data-ttu-id="bd63d-134">只包含為進程中所有現有線程捕捉堆疊追蹤所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-134">Include just the information necessary to capture stack traces for all existing threads in a process.</span></span> <span data-ttu-id="bd63d-135">有限的 GC 堆積記憶體和資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-135">Limited GC heap memory and information.</span></span>|
|<span data-ttu-id="bd63d-136">2</span><span class="sxs-lookup"><span data-stu-id="bd63d-136">2</span></span>|`MiniDumpWithPrivateReadWriteMemory`|<span data-ttu-id="bd63d-137">包含 GC 堆積以及在進程中為所有現有線程捕捉堆疊追蹤所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-137">Includes the GC heaps and information necessary to capture stack traces for all existing threads in a process.</span></span>|
|<span data-ttu-id="bd63d-138">3</span><span class="sxs-lookup"><span data-stu-id="bd63d-138">3</span></span>|`MiniDumpFilterTriage`|<span data-ttu-id="bd63d-139">只包含為進程中所有現有線程捕捉堆疊追蹤所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-139">Include just the information necessary to capture stack traces for all existing threads in a process.</span></span> <span data-ttu-id="bd63d-140">有限的 GC 堆積記憶體和資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-140">Limited GC heap memory and information.</span></span>|
|<span data-ttu-id="bd63d-141">4</span><span class="sxs-lookup"><span data-stu-id="bd63d-141">4</span></span>|`MiniDumpWithFullMemory`|<span data-ttu-id="bd63d-142">在進程中包含所有可存取的記憶體。</span><span class="sxs-lookup"><span data-stu-id="bd63d-142">Include all accessible memory in the process.</span></span> <span data-ttu-id="bd63d-143">原始記憶體資料會包含在結尾，因此可以直接對應初始結構，而不需要原始記憶體資訊。</span><span class="sxs-lookup"><span data-stu-id="bd63d-143">The raw memory data is included at the end, so that the initial structures can be mapped directly without the raw memory information.</span></span> <span data-ttu-id="bd63d-144">此選項可能會產生非常大的檔案。</span><span class="sxs-lookup"><span data-stu-id="bd63d-144">This option can result in a very large file.</span></span>|

### <a name="collecting-dumps-at-specific-point-in-time"></a><span data-ttu-id="bd63d-145">在特定時間點收集傾印</span><span class="sxs-lookup"><span data-stu-id="bd63d-145">Collecting dumps at specific point in time</span></span>

<span data-ttu-id="bd63d-146">當應用程式尚未損毀時，您可能會想要收集傾印。</span><span class="sxs-lookup"><span data-stu-id="bd63d-146">You may want to collect a dump when the app hasn't crashed yet.</span></span> <span data-ttu-id="bd63d-147">例如，如果您想要檢查看似處於鎖死的應用程式狀態，則設定環境變數以收集損毀傾印時，將不會有説明，因為應用程式仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="bd63d-147">For example, if you want to examine the state of an application that seems to be in a deadlock, configuring the environment variables to collect dumps on crash will not be helpful because the app is still running.</span></span>

<span data-ttu-id="bd63d-148">若要在您自己的要求中收集傾印，您可以使用 `dotnet-dump` ，這是用來收集和分析傾印的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="bd63d-148">To collect dump at your own request, you can use `dotnet-dump`, which is a CLI tool for collecting and analyzing dumps.</span></span> <span data-ttu-id="bd63d-149">如需如何使用它來收集傾印的詳細資訊 `dotnet-dump` ，請參閱傾印 [收集和分析公用程式](dotnet-dump.md)。</span><span class="sxs-lookup"><span data-stu-id="bd63d-149">For more information on how to use it to collect dumps with `dotnet-dump`, see [Dump collection and analysis utility](dotnet-dump.md).</span></span>

## <a name="analyze-dumps"></a><span data-ttu-id="bd63d-150">分析傾印</span><span class="sxs-lookup"><span data-stu-id="bd63d-150">Analyze dumps</span></span>

<span data-ttu-id="bd63d-151">傾印可使用進行分析 [`dotnet-dump`](dotnet-dump.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd63d-151">Dumps can be analyzed using [`dotnet-dump`](dotnet-dump.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd63d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd63d-152">See also</span></span>

<span data-ttu-id="bd63d-153">深入瞭解您可以如何運用傾印來協助診斷 .NET 應用程式中的問題。</span><span class="sxs-lookup"><span data-stu-id="bd63d-153">Learn more about how you can leverage dumps to help diagnosing problems in your .NET application.</span></span>

* <span data-ttu-id="bd63d-154">[Debug linux](debug-linux-dumps.md) 傾印教學課程會逐步解說如何對在 Linux 中收集的傾印進行 debug 錯。</span><span class="sxs-lookup"><span data-stu-id="bd63d-154">[Debug Linux dumps](debug-linux-dumps.md) tutorial walks you through how to debug a dump that was collected in Linux.</span></span>

* <span data-ttu-id="bd63d-155">[Debug 鎖死](debug-deadlock.md) 教學課程會逐步引導您使用傾印，在 .net 應用程式中進行鎖死的偵測。</span><span class="sxs-lookup"><span data-stu-id="bd63d-155">[Debug deadlock](debug-deadlock.md) tutorial walks you through how to debug a deadlock in your .NET application using dumps.</span></span>
