---
title: dotnet-gcdump-.NET Core
description: 安裝和使用 dotnet-gcdump 命令列工具。
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656647"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="ff7ad-103">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="ff7ad-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="ff7ad-104">本文**適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ff7ad-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="ff7ad-105">安裝 dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="ff7ad-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="ff7ad-106">若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="ff7ad-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="ff7ad-107">概要</span><span class="sxs-lookup"><span data-stu-id="ff7ad-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="ff7ad-108">說明</span><span class="sxs-lookup"><span data-stu-id="ff7ad-108">Description</span></span>

<span data-ttu-id="ff7ad-109">`dotnet-gcdump`全域工具是一種方式，可收集 GC (垃圾收集行程，) 即時 .net 進程的傾印。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="ff7ad-110">它會使用 EventPipe 技術，這是 Windows 上的 ETW 的跨平臺替代方案。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="ff7ad-111">GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="ff7ad-112">此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-112">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="ff7ad-113">這些傾印適用于數種案例：</span><span class="sxs-lookup"><span data-stu-id="ff7ad-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="ff7ad-114">比較堆積上數個時間點的物件數目。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="ff7ad-115">分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="ff7ad-116">收集堆積上物件計數的一般統計資料。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="ff7ad-117">查看從 dotnet 所捕獲的 GC 傾印-gcdump</span><span class="sxs-lookup"><span data-stu-id="ff7ad-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="ff7ad-118">在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="ff7ad-119">目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="ff7ad-120">您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="ff7ad-121">選項</span><span class="sxs-lookup"><span data-stu-id="ff7ad-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="ff7ad-122">顯示公用程式的版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ff7ad-123">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="ff7ad-124">從目前正在執行的進程收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ff7ad-125">概要</span><span class="sxs-lookup"><span data-stu-id="ff7ad-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="ff7ad-126">選項</span><span class="sxs-lookup"><span data-stu-id="ff7ad-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="ff7ad-127">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="ff7ad-128">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-128">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="ff7ad-129">應寫入所收集 GC 傾印的路徑。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="ff7ad-130">預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="ff7ad-131">在收集 GC 傾印時輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="ff7ad-132">如果 GC 傾印花費的時間超過這段時間，請放棄收集。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="ff7ad-133">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="ff7ad-134">要從中收集 GC 傾印的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="ff7ad-135">列出可收集 GC 傾印的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ff7ad-136">概要</span><span class="sxs-lookup"><span data-stu-id="ff7ad-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="ff7ad-137">從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ff7ad-138">概要</span><span class="sxs-lookup"><span data-stu-id="ff7ad-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="ff7ad-139">選項</span><span class="sxs-lookup"><span data-stu-id="ff7ad-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="ff7ad-140">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="ff7ad-141">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-141">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="ff7ad-142">要產生的報表類型。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-142">The type of report to generate.</span></span> <span data-ttu-id="ff7ad-143">可用的選項： heapstat (預設) 。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="ff7ad-144">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ff7ad-144">Troubleshoot</span></span>

- <span data-ttu-id="ff7ad-145">Gcdump 中沒有類型資訊。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="ff7ad-146">在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="ff7ad-147">這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="ff7ad-148">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="ff7ad-149">COM 和靜態類型不在 GC 傾印中。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="ff7ad-150">在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="ff7ad-151">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="ff7ad-151">This has been fixed in .NET Core 3.1-preview2.</span></span>
