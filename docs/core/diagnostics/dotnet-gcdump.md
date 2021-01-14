---
title: dotnet-gcdump 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-gcdump CLI 工具，以使用 .NET EventPipe 收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: fe7772eed642daadbd1754627751f58d0ab57b8e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188565"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="83a6a-103">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="83a6a-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="83a6a-104">本文 **適用于：** ✔️ .net CORE 3.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="83a6a-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="83a6a-105">安裝</span><span class="sxs-lookup"><span data-stu-id="83a6a-105">Install</span></span>

<span data-ttu-id="83a6a-106">有兩種方式可以下載和安裝 `dotnet-gcdump` ：</span><span class="sxs-lookup"><span data-stu-id="83a6a-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="83a6a-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="83a6a-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="83a6a-108">若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="83a6a-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="83a6a-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="83a6a-109">**Direct download:**</span></span>

  <span data-ttu-id="83a6a-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="83a6a-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="83a6a-111">OS</span><span class="sxs-lookup"><span data-stu-id="83a6a-111">OS</span></span>  | <span data-ttu-id="83a6a-112">平台</span><span class="sxs-lookup"><span data-stu-id="83a6a-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="83a6a-113">Windows</span><span class="sxs-lookup"><span data-stu-id="83a6a-113">Windows</span></span> | <span data-ttu-id="83a6a-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \|[x64](https://aka.ms/dotnet-gcdump/win-x64) \|[arm](https://aka.ms/dotnet-gcdump/win-arm) \|[arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="83a6a-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="83a6a-115">macOS</span><span class="sxs-lookup"><span data-stu-id="83a6a-115">macOS</span></span>   | [<span data-ttu-id="83a6a-116">x64</span><span class="sxs-lookup"><span data-stu-id="83a6a-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="83a6a-117">Linux</span><span class="sxs-lookup"><span data-stu-id="83a6a-117">Linux</span></span>   | <span data-ttu-id="83a6a-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \|[arm](https://aka.ms/dotnet-gcdump/linux-arm) \|[arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="83a6a-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="83a6a-119">若要 `dotnet-gcdump` 在 x86 應用程式上使用，您需要工具的對應 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="83a6a-119">To use `dotnet-gcdump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83a6a-120">概要</span><span class="sxs-lookup"><span data-stu-id="83a6a-120">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="83a6a-121">Description</span><span class="sxs-lookup"><span data-stu-id="83a6a-121">Description</span></span>

<span data-ttu-id="83a6a-122">`dotnet-gcdump`全域工具會使用[EventPipe](./eventpipe.md)收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。</span><span class="sxs-lookup"><span data-stu-id="83a6a-122">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="83a6a-123">GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。</span><span class="sxs-lookup"><span data-stu-id="83a6a-123">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="83a6a-124">此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。</span><span class="sxs-lookup"><span data-stu-id="83a6a-124">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="83a6a-125">這些傾印適用于數種案例：</span><span class="sxs-lookup"><span data-stu-id="83a6a-125">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="83a6a-126">比較堆積上數個時間點的物件數目。</span><span class="sxs-lookup"><span data-stu-id="83a6a-126">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="83a6a-127">分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。</span><span class="sxs-lookup"><span data-stu-id="83a6a-127">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="83a6a-128">收集堆積上物件計數的一般統計資料。</span><span class="sxs-lookup"><span data-stu-id="83a6a-128">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="83a6a-129">查看從 dotnet 所捕獲的 GC 傾印-gcdump</span><span class="sxs-lookup"><span data-stu-id="83a6a-129">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="83a6a-130">在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="83a6a-130">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="83a6a-131">目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。</span><span class="sxs-lookup"><span data-stu-id="83a6a-131">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="83a6a-132">您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。</span><span class="sxs-lookup"><span data-stu-id="83a6a-132">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="83a6a-133">選項</span><span class="sxs-lookup"><span data-stu-id="83a6a-133">Options</span></span>

- **`--version`**

  <span data-ttu-id="83a6a-134">顯示公用程式的版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="83a6a-134">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="83a6a-135">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="83a6a-135">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="83a6a-136">從目前正在執行的進程收集 GC 傾印。</span><span class="sxs-lookup"><span data-stu-id="83a6a-136">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="83a6a-137">為了逐步進行 GC 堆積，此命令會觸發層代 2 (完整) 垃圾收集，這會長期暫停執行時間，特別是當 GC 堆積很大時。</span><span class="sxs-lookup"><span data-stu-id="83a6a-137">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="83a6a-138">當 GC 堆積很大時，請勿在效能敏感性環境中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="83a6a-138">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="83a6a-139">概要</span><span class="sxs-lookup"><span data-stu-id="83a6a-139">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="83a6a-140">選項</span><span class="sxs-lookup"><span data-stu-id="83a6a-140">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="83a6a-141">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="83a6a-141">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="83a6a-142">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="83a6a-142">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="83a6a-143">應寫入所收集 GC 傾印的路徑。</span><span class="sxs-lookup"><span data-stu-id="83a6a-143">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="83a6a-144">預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。</span><span class="sxs-lookup"><span data-stu-id="83a6a-144">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="83a6a-145">在收集 GC 傾印時輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="83a6a-145">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="83a6a-146">如果 GC 傾印花費的時間超過這段時間，請放棄收集。</span><span class="sxs-lookup"><span data-stu-id="83a6a-146">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="83a6a-147">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="83a6a-147">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="83a6a-148">要從中收集 GC 傾印的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="83a6a-148">The name of the process to collect the GC dump from.</span></span>

> [!NOTE]
> <span data-ttu-id="83a6a-149">在 Linux 和 macOS 上，此命令會預期目標應用程式，並 `dotnet-gcdump` 共用相同的 `TMPDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="83a6a-149">On Linux and macOS, this command expects the target application and `dotnet-gcdump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="83a6a-150">否則，此命令將會超時。</span><span class="sxs-lookup"><span data-stu-id="83a6a-150">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="83a6a-151">若要使用收集 GC 傾印 `dotnet-gcdump` ，必須以執行目標進程的使用者和根使用者的相同使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="83a6a-151">To collect a GC dump using `dotnet-gcdump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="83a6a-152">否則，此工具將無法建立與目標進程的連接。</span><span class="sxs-lookup"><span data-stu-id="83a6a-152">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="83a6a-153">列出可收集 GC 傾印的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="83a6a-153">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="83a6a-154">概要</span><span class="sxs-lookup"><span data-stu-id="83a6a-154">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="83a6a-155">從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。</span><span class="sxs-lookup"><span data-stu-id="83a6a-155">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="83a6a-156">概要</span><span class="sxs-lookup"><span data-stu-id="83a6a-156">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="83a6a-157">選項</span><span class="sxs-lookup"><span data-stu-id="83a6a-157">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="83a6a-158">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="83a6a-158">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="83a6a-159">從中收集 GC 傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="83a6a-159">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="83a6a-160">要產生的報表類型。</span><span class="sxs-lookup"><span data-stu-id="83a6a-160">The type of report to generate.</span></span> <span data-ttu-id="83a6a-161">可用的選項： heapstat (預設) 。</span><span class="sxs-lookup"><span data-stu-id="83a6a-161">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="83a6a-162">疑難排解</span><span class="sxs-lookup"><span data-stu-id="83a6a-162">Troubleshoot</span></span>

- <span data-ttu-id="83a6a-163">Gcdump 中沒有類型資訊。</span><span class="sxs-lookup"><span data-stu-id="83a6a-163">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="83a6a-164">在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。</span><span class="sxs-lookup"><span data-stu-id="83a6a-164">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="83a6a-165">這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。</span><span class="sxs-lookup"><span data-stu-id="83a6a-165">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="83a6a-166">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="83a6a-166">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="83a6a-167">COM 和靜態類型不在 GC 傾印中。</span><span class="sxs-lookup"><span data-stu-id="83a6a-167">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="83a6a-168">在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="83a6a-168">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="83a6a-169">這已在 .NET Core 3.1-preview2 中修正。</span><span class="sxs-lookup"><span data-stu-id="83a6a-169">This has been fixed in .NET Core 3.1-preview2.</span></span>
