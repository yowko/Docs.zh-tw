---
title: dotnet-gcdump-.NET Core
description: 安裝和使用 dotnet-gcdump 命令列工具。
ms.date: 07/26/2020
ms.openlocfilehash: c73afae9ecdfa907e9655634a0ac355cab4ef558
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687612"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="f0916-103">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="f0916-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="f0916-104">本文 **適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f0916-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="f0916-105">安裝 dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="f0916-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="f0916-106">若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="f0916-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="f0916-107">概要</span><span class="sxs-lookup"><span data-stu-id="f0916-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="f0916-108">描述</span><span class="sxs-lookup"><span data-stu-id="f0916-108">Description</span></span>

<span data-ttu-id="f0916-109">`dotnet-gcdump`全域工具會使用[EventPipe](./eventpipe.md)收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。</span><span class="sxs-lookup"><span data-stu-id="f0916-109">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="f0916-110">GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。</span><span class="sxs-lookup"><span data-stu-id="f0916-110">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="f0916-111">此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。</span><span class="sxs-lookup"><span data-stu-id="f0916-111">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="f0916-112">這些傾印適用于數種案例：</span><span class="sxs-lookup"><span data-stu-id="f0916-112">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="f0916-113">比較堆積上數個時間點的物件數目。</span><span class="sxs-lookup"><span data-stu-id="f0916-113">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="f0916-114">分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。</span><span class="sxs-lookup"><span data-stu-id="f0916-114">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="f0916-115">收集堆積上物件計數的一般統計資料。</span><span class="sxs-lookup"><span data-stu-id="f0916-115">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="f0916-116">查看從 dotnet 所捕獲的 GC 傾印-gcdump</span><span class="sxs-lookup"><span data-stu-id="f0916-116">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="f0916-117">在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f0916-117">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="f0916-118">目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。</span><span class="sxs-lookup"><span data-stu-id="f0916-118">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="f0916-119">您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。</span><span class="sxs-lookup"><span data-stu-id="f0916-119">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="f0916-120">選項</span><span class="sxs-lookup"><span data-stu-id="f0916-120">Options</span></span>

- **`--version`**

  <span data-ttu-id="f0916-121">顯示公用程式的版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="f0916-121">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0916-122">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="f0916-122">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="f0916-123">從目前正在執行的進程收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="f0916-123">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f0916-124">概要</span><span class="sxs-lookup"><span data-stu-id="f0916-124">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="f0916-125">選項</span><span class="sxs-lookup"><span data-stu-id="f0916-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0916-126">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="f0916-126">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="f0916-127">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0916-127">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="f0916-128">應寫入所收集 GC 傾印的路徑。</span><span class="sxs-lookup"><span data-stu-id="f0916-128">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="f0916-129">預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。</span><span class="sxs-lookup"><span data-stu-id="f0916-129">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="f0916-130">在收集 GC 傾印時輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="f0916-130">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="f0916-131">如果 GC 傾印花費的時間超過這段時間，請放棄收集。</span><span class="sxs-lookup"><span data-stu-id="f0916-131">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="f0916-132">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="f0916-132">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="f0916-133">要從中收集 GC 傾印的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="f0916-133">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="f0916-134">列出可收集 GC 傾印的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="f0916-134">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f0916-135">概要</span><span class="sxs-lookup"><span data-stu-id="f0916-135">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="f0916-136">從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。</span><span class="sxs-lookup"><span data-stu-id="f0916-136">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f0916-137">概要</span><span class="sxs-lookup"><span data-stu-id="f0916-137">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="f0916-138">選項</span><span class="sxs-lookup"><span data-stu-id="f0916-138">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0916-139">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="f0916-139">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="f0916-140">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0916-140">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="f0916-141">要產生的報表類型。</span><span class="sxs-lookup"><span data-stu-id="f0916-141">The type of report to generate.</span></span> <span data-ttu-id="f0916-142">可用的選項： heapstat (預設) 。</span><span class="sxs-lookup"><span data-stu-id="f0916-142">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="f0916-143">疑難排解</span><span class="sxs-lookup"><span data-stu-id="f0916-143">Troubleshoot</span></span>

- <span data-ttu-id="f0916-144">Gcdump 中沒有類型資訊。</span><span class="sxs-lookup"><span data-stu-id="f0916-144">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="f0916-145">在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。</span><span class="sxs-lookup"><span data-stu-id="f0916-145">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="f0916-146">這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。</span><span class="sxs-lookup"><span data-stu-id="f0916-146">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="f0916-147">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="f0916-147">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="f0916-148">COM 和靜態類型不在 GC 傾印中。</span><span class="sxs-lookup"><span data-stu-id="f0916-148">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="f0916-149">在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="f0916-149">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="f0916-150">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="f0916-150">This has been fixed in .NET Core 3.1-preview2.</span></span>
