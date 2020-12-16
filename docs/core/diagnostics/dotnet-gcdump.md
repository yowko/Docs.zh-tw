---
title: dotnet-gcdump 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-gcdump CLI 工具，以使用 .NET EventPipe 收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: 02e1a7c5d86b582289672a027464aefd67a6f490
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593366"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="34d7a-103">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="34d7a-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="34d7a-104">本文 **適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="34d7a-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="34d7a-105">安裝</span><span class="sxs-lookup"><span data-stu-id="34d7a-105">Install</span></span>

<span data-ttu-id="34d7a-106">有兩種方式可以下載和安裝 `dotnet-gcdump` ：</span><span class="sxs-lookup"><span data-stu-id="34d7a-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="34d7a-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="34d7a-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="34d7a-108">若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="34d7a-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="34d7a-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="34d7a-109">**Direct download:**</span></span>

  <span data-ttu-id="34d7a-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="34d7a-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="34d7a-111">OS</span><span class="sxs-lookup"><span data-stu-id="34d7a-111">OS</span></span>  | <span data-ttu-id="34d7a-112">平台</span><span class="sxs-lookup"><span data-stu-id="34d7a-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="34d7a-113">Windows</span><span class="sxs-lookup"><span data-stu-id="34d7a-113">Windows</span></span> | <span data-ttu-id="34d7a-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \|[x64](https://aka.ms/dotnet-gcdump/win-x64) \|[arm](https://aka.ms/dotnet-gcdump/win-arm) \|[arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="34d7a-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="34d7a-115">macOS</span><span class="sxs-lookup"><span data-stu-id="34d7a-115">macOS</span></span>   | [<span data-ttu-id="34d7a-116">x64</span><span class="sxs-lookup"><span data-stu-id="34d7a-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="34d7a-117">Linux</span><span class="sxs-lookup"><span data-stu-id="34d7a-117">Linux</span></span>   | <span data-ttu-id="34d7a-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \|[arm](https://aka.ms/dotnet-gcdump/linux-arm) \|[arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="34d7a-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="34d7a-119">概要</span><span class="sxs-lookup"><span data-stu-id="34d7a-119">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="34d7a-120">描述</span><span class="sxs-lookup"><span data-stu-id="34d7a-120">Description</span></span>

<span data-ttu-id="34d7a-121">`dotnet-gcdump`全域工具會使用[EventPipe](./eventpipe.md)收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。</span><span class="sxs-lookup"><span data-stu-id="34d7a-121">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="34d7a-122">GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。</span><span class="sxs-lookup"><span data-stu-id="34d7a-122">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="34d7a-123">此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。</span><span class="sxs-lookup"><span data-stu-id="34d7a-123">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="34d7a-124">這些傾印適用于數種案例：</span><span class="sxs-lookup"><span data-stu-id="34d7a-124">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="34d7a-125">比較堆積上數個時間點的物件數目。</span><span class="sxs-lookup"><span data-stu-id="34d7a-125">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="34d7a-126">分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。</span><span class="sxs-lookup"><span data-stu-id="34d7a-126">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="34d7a-127">收集堆積上物件計數的一般統計資料。</span><span class="sxs-lookup"><span data-stu-id="34d7a-127">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="34d7a-128">查看從 dotnet 所捕獲的 GC 傾印-gcdump</span><span class="sxs-lookup"><span data-stu-id="34d7a-128">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="34d7a-129">在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="34d7a-129">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="34d7a-130">目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。</span><span class="sxs-lookup"><span data-stu-id="34d7a-130">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="34d7a-131">您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。</span><span class="sxs-lookup"><span data-stu-id="34d7a-131">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="34d7a-132">選項</span><span class="sxs-lookup"><span data-stu-id="34d7a-132">Options</span></span>

- **`--version`**

  <span data-ttu-id="34d7a-133">顯示公用程式的版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="34d7a-133">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="34d7a-134">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="34d7a-134">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="34d7a-135">從目前正在執行的進程收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="34d7a-135">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="34d7a-136">為了逐步進行 GC 堆積，此命令會觸發層代 2 (完整) 垃圾收集，這會長期暫停執行時間，特別是當 GC 堆積很大時。</span><span class="sxs-lookup"><span data-stu-id="34d7a-136">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="34d7a-137">當 GC 堆積很大時，請勿在效能敏感性環境中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="34d7a-137">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="34d7a-138">概要</span><span class="sxs-lookup"><span data-stu-id="34d7a-138">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="34d7a-139">選項</span><span class="sxs-lookup"><span data-stu-id="34d7a-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="34d7a-140">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="34d7a-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="34d7a-141">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="34d7a-141">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="34d7a-142">應寫入所收集 GC 傾印的路徑。</span><span class="sxs-lookup"><span data-stu-id="34d7a-142">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="34d7a-143">預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。</span><span class="sxs-lookup"><span data-stu-id="34d7a-143">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="34d7a-144">在收集 GC 傾印時輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="34d7a-144">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="34d7a-145">如果 GC 傾印花費的時間超過這段時間，請放棄收集。</span><span class="sxs-lookup"><span data-stu-id="34d7a-145">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="34d7a-146">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="34d7a-146">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="34d7a-147">要從中收集 GC 傾印的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="34d7a-147">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="34d7a-148">列出可收集 GC 傾印的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="34d7a-148">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="34d7a-149">概要</span><span class="sxs-lookup"><span data-stu-id="34d7a-149">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="34d7a-150">從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。</span><span class="sxs-lookup"><span data-stu-id="34d7a-150">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="34d7a-151">概要</span><span class="sxs-lookup"><span data-stu-id="34d7a-151">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="34d7a-152">選項</span><span class="sxs-lookup"><span data-stu-id="34d7a-152">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="34d7a-153">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="34d7a-153">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="34d7a-154">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="34d7a-154">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="34d7a-155">要產生的報表類型。</span><span class="sxs-lookup"><span data-stu-id="34d7a-155">The type of report to generate.</span></span> <span data-ttu-id="34d7a-156">可用的選項： heapstat (預設) 。</span><span class="sxs-lookup"><span data-stu-id="34d7a-156">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="34d7a-157">疑難排解</span><span class="sxs-lookup"><span data-stu-id="34d7a-157">Troubleshoot</span></span>

- <span data-ttu-id="34d7a-158">Gcdump 中沒有類型資訊。</span><span class="sxs-lookup"><span data-stu-id="34d7a-158">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="34d7a-159">在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。</span><span class="sxs-lookup"><span data-stu-id="34d7a-159">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="34d7a-160">這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。</span><span class="sxs-lookup"><span data-stu-id="34d7a-160">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="34d7a-161">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="34d7a-161">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="34d7a-162">COM 和靜態類型不在 GC 傾印中。</span><span class="sxs-lookup"><span data-stu-id="34d7a-162">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="34d7a-163">在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="34d7a-163">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="34d7a-164">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="34d7a-164">This has been fixed in .NET Core 3.1-preview2.</span></span>
