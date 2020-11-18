---
title: dotnet-gcdump 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-gcdump CLI 工具，以使用 .NET EventPipe 收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826036"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="349b9-103">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="349b9-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="349b9-104">本文 **適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="349b9-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="349b9-105">安裝</span><span class="sxs-lookup"><span data-stu-id="349b9-105">Install</span></span>

<span data-ttu-id="349b9-106">有兩種方式可以下載和安裝 `dotnet-gcdump` ：</span><span class="sxs-lookup"><span data-stu-id="349b9-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="349b9-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="349b9-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="349b9-108">若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="349b9-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="349b9-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="349b9-109">**Direct download:**</span></span>

  <span data-ttu-id="349b9-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="349b9-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="349b9-111">OS</span><span class="sxs-lookup"><span data-stu-id="349b9-111">OS</span></span>  | <span data-ttu-id="349b9-112">平台</span><span class="sxs-lookup"><span data-stu-id="349b9-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="349b9-113">Windows</span><span class="sxs-lookup"><span data-stu-id="349b9-113">Windows</span></span> | <span data-ttu-id="349b9-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \|[x64](https://aka.ms/dotnet-gcdump/win-x64) \|[arm](https://aka.ms/dotnet-gcdump/win-arm) \|[arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="349b9-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="349b9-115">macOS</span><span class="sxs-lookup"><span data-stu-id="349b9-115">macOS</span></span>   | [<span data-ttu-id="349b9-116">x64</span><span class="sxs-lookup"><span data-stu-id="349b9-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="349b9-117">Linux</span><span class="sxs-lookup"><span data-stu-id="349b9-117">Linux</span></span>   | <span data-ttu-id="349b9-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \|[arm](https://aka.ms/dotnet-gcdump/linux-arm) \|[arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="349b9-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="349b9-119">概要</span><span class="sxs-lookup"><span data-stu-id="349b9-119">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="349b9-120">說明</span><span class="sxs-lookup"><span data-stu-id="349b9-120">Description</span></span>

<span data-ttu-id="349b9-121">`dotnet-gcdump`全域工具會使用[EventPipe](./eventpipe.md)收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。</span><span class="sxs-lookup"><span data-stu-id="349b9-121">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="349b9-122">GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。</span><span class="sxs-lookup"><span data-stu-id="349b9-122">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="349b9-123">此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。</span><span class="sxs-lookup"><span data-stu-id="349b9-123">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="349b9-124">這些傾印適用于數種案例：</span><span class="sxs-lookup"><span data-stu-id="349b9-124">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="349b9-125">比較堆積上數個時間點的物件數目。</span><span class="sxs-lookup"><span data-stu-id="349b9-125">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="349b9-126">分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。</span><span class="sxs-lookup"><span data-stu-id="349b9-126">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="349b9-127">收集堆積上物件計數的一般統計資料。</span><span class="sxs-lookup"><span data-stu-id="349b9-127">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="349b9-128">查看從 dotnet 所捕獲的 GC 傾印-gcdump</span><span class="sxs-lookup"><span data-stu-id="349b9-128">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="349b9-129">在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="349b9-129">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="349b9-130">目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。</span><span class="sxs-lookup"><span data-stu-id="349b9-130">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="349b9-131">您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。</span><span class="sxs-lookup"><span data-stu-id="349b9-131">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="349b9-132">選項</span><span class="sxs-lookup"><span data-stu-id="349b9-132">Options</span></span>

- **`--version`**

  <span data-ttu-id="349b9-133">顯示公用程式的版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="349b9-133">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="349b9-134">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="349b9-134">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="349b9-135">從目前正在執行的進程收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="349b9-135">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="349b9-136">概要</span><span class="sxs-lookup"><span data-stu-id="349b9-136">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="349b9-137">選項</span><span class="sxs-lookup"><span data-stu-id="349b9-137">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="349b9-138">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="349b9-138">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="349b9-139">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="349b9-139">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="349b9-140">應寫入所收集 GC 傾印的路徑。</span><span class="sxs-lookup"><span data-stu-id="349b9-140">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="349b9-141">預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。</span><span class="sxs-lookup"><span data-stu-id="349b9-141">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="349b9-142">在收集 GC 傾印時輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="349b9-142">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="349b9-143">如果 GC 傾印花費的時間超過這段時間，請放棄收集。</span><span class="sxs-lookup"><span data-stu-id="349b9-143">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="349b9-144">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="349b9-144">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="349b9-145">要從中收集 GC 傾印的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="349b9-145">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="349b9-146">列出可收集 GC 傾印的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="349b9-146">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="349b9-147">概要</span><span class="sxs-lookup"><span data-stu-id="349b9-147">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="349b9-148">從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。</span><span class="sxs-lookup"><span data-stu-id="349b9-148">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="349b9-149">概要</span><span class="sxs-lookup"><span data-stu-id="349b9-149">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="349b9-150">選項</span><span class="sxs-lookup"><span data-stu-id="349b9-150">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="349b9-151">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="349b9-151">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="349b9-152">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="349b9-152">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="349b9-153">要產生的報表類型。</span><span class="sxs-lookup"><span data-stu-id="349b9-153">The type of report to generate.</span></span> <span data-ttu-id="349b9-154">可用的選項： heapstat (預設) 。</span><span class="sxs-lookup"><span data-stu-id="349b9-154">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="349b9-155">疑難排解</span><span class="sxs-lookup"><span data-stu-id="349b9-155">Troubleshoot</span></span>

- <span data-ttu-id="349b9-156">Gcdump 中沒有類型資訊。</span><span class="sxs-lookup"><span data-stu-id="349b9-156">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="349b9-157">在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。</span><span class="sxs-lookup"><span data-stu-id="349b9-157">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="349b9-158">這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。</span><span class="sxs-lookup"><span data-stu-id="349b9-158">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="349b9-159">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="349b9-159">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="349b9-160">COM 和靜態類型不在 GC 傾印中。</span><span class="sxs-lookup"><span data-stu-id="349b9-160">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="349b9-161">在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="349b9-161">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="349b9-162">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="349b9-162">This has been fixed in .NET Core 3.1-preview2.</span></span>
