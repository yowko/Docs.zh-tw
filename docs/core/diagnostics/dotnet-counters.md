---
title: dotnet-計數器診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-counter CLI 工具，以進行臨機操作健全狀況監視和第一層效能調查。
ms.date: 11/17/2020
ms.openlocfilehash: 1842b1fb9cde0e0b7a570456766cbfdeb64c5896
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188578"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="740eb-103"> (dotnet) 的計數器調查效能計數器</span><span class="sxs-lookup"><span data-stu-id="740eb-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="740eb-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="740eb-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="740eb-105">安裝</span><span class="sxs-lookup"><span data-stu-id="740eb-105">Install</span></span>

<span data-ttu-id="740eb-106">有兩種方式可以下載和安裝 `dotnet-counters` ：</span><span class="sxs-lookup"><span data-stu-id="740eb-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="740eb-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="740eb-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="740eb-108">若要安裝 `dotnet-counters` [NuGet 套件](https://www.nuget.org/packages/dotnet-counters)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="740eb-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="740eb-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="740eb-109">**Direct download:**</span></span>

  <span data-ttu-id="740eb-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="740eb-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="740eb-111">OS</span><span class="sxs-lookup"><span data-stu-id="740eb-111">OS</span></span>  | <span data-ttu-id="740eb-112">平台</span><span class="sxs-lookup"><span data-stu-id="740eb-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="740eb-113">Windows</span><span class="sxs-lookup"><span data-stu-id="740eb-113">Windows</span></span> | <span data-ttu-id="740eb-114">[x86](https://aka.ms/dotnet-counters/win-x86) \|[x64](https://aka.ms/dotnet-counters/win-x64) \|[arm](https://aka.ms/dotnet-counters/win-arm) \|[arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="740eb-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="740eb-115">macOS</span><span class="sxs-lookup"><span data-stu-id="740eb-115">macOS</span></span>   | [<span data-ttu-id="740eb-116">x64</span><span class="sxs-lookup"><span data-stu-id="740eb-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="740eb-117">Linux</span><span class="sxs-lookup"><span data-stu-id="740eb-117">Linux</span></span>   | <span data-ttu-id="740eb-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \|[arm](https://aka.ms/dotnet-counters/linux-arm) \|[arm64](https://aka.ms/dotnet-counters/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="740eb-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="740eb-119">若要 `dotnet-counters` 在 x86 應用程式上使用，您需要工具的對應 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="740eb-119">To use `dotnet-counters` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="740eb-120">概要</span><span class="sxs-lookup"><span data-stu-id="740eb-120">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="740eb-121">Description</span><span class="sxs-lookup"><span data-stu-id="740eb-121">Description</span></span>

<span data-ttu-id="740eb-122">`dotnet-counters` 是一種效能監視工具，適用于臨機操作健全狀況監視和第一層效能調查。</span><span class="sxs-lookup"><span data-stu-id="740eb-122">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="740eb-123">它可以觀察經由 API 發佈的效能計數器值 <xref:System.Diagnostics.Tracing.EventCounter> 。</span><span class="sxs-lookup"><span data-stu-id="740eb-123">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="740eb-124">例如，您可以在 .NET Core 應用程式中快速監視 CPU 使用量或擲回例外狀況率等專案，以查看是否有任何可疑的專案，然後再使用或進行更嚴重的效能調查 `PerfView` `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-124">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="740eb-125">選項</span><span class="sxs-lookup"><span data-stu-id="740eb-125">Options</span></span>

- **`--version`**

  <span data-ttu-id="740eb-126">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="740eb-126">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="740eb-127">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="740eb-127">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="740eb-128">命令</span><span class="sxs-lookup"><span data-stu-id="740eb-128">Commands</span></span>

| <span data-ttu-id="740eb-129">命令</span><span class="sxs-lookup"><span data-stu-id="740eb-129">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="740eb-130">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="740eb-130">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="740eb-131">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="740eb-131">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="740eb-132">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="740eb-132">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="740eb-133">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="740eb-133">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="740eb-134">dotnet-計數器收集</span><span class="sxs-lookup"><span data-stu-id="740eb-134">dotnet-counters collect</span></span>

<span data-ttu-id="740eb-135">定期收集選取的計數器值，並將其匯出為指定的檔案格式以進行後置處理。</span><span class="sxs-lookup"><span data-stu-id="740eb-135">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="740eb-136">概要</span><span class="sxs-lookup"><span data-stu-id="740eb-136">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="740eb-137">選項</span><span class="sxs-lookup"><span data-stu-id="740eb-137">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="740eb-138">要從中收集計數器資料的進程識別碼。</span><span class="sxs-lookup"><span data-stu-id="740eb-138">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="740eb-139">要從中收集計數器資料之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="740eb-139">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="740eb-140">要建立之診斷埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="740eb-140">The name of the diagnostic port to create.</span></span> <span data-ttu-id="740eb-141">請參閱 [使用診斷埠](#using-diagnostic-port) 來瞭解如何使用此選項，從應用程式啟動開始監視計數器。</span><span class="sxs-lookup"><span data-stu-id="740eb-141">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="740eb-142">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="740eb-142">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="740eb-143">以逗號分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="740eb-143">A comma-separated list of counters.</span></span> <span data-ttu-id="740eb-144">您可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-144">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="740eb-145">如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。</span><span class="sxs-lookup"><span data-stu-id="740eb-145">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="740eb-146">若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="740eb-146">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="740eb-147">要匯出的格式。</span><span class="sxs-lookup"><span data-stu-id="740eb-147">The format to be exported.</span></span> <span data-ttu-id="740eb-148">目前可用： csv、json。</span><span class="sxs-lookup"><span data-stu-id="740eb-148">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="740eb-149">輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="740eb-149">The name of the output file.</span></span>

- <span data-ttu-id="740eb-150">**`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="740eb-150">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="740eb-151">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-151">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="740eb-152">`dotnet-counters` 將會使用所提供的命令啟動處理常式，並收集要求的度量。</span><span class="sxs-lookup"><span data-stu-id="740eb-152">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="740eb-153">這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。</span><span class="sxs-lookup"><span data-stu-id="740eb-153">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="740eb-154">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-154">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="740eb-155">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="740eb-155">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="740eb-156">透過 dotnet 啟動 .NET 可執行檔會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 進行互動。</span><span class="sxs-lookup"><span data-stu-id="740eb-156">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="740eb-157">透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。</span><span class="sxs-lookup"><span data-stu-id="740eb-157">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="740eb-158">如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。</span><span class="sxs-lookup"><span data-stu-id="740eb-158">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="740eb-159">如果您需要使用 stdin/stdout，可以使用 `--diagnostic-port` 選項。</span><span class="sxs-lookup"><span data-stu-id="740eb-159">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="740eb-160">如需詳細資訊，請參閱 [使用診斷埠](#using-diagnostic-port) 。</span><span class="sxs-lookup"><span data-stu-id="740eb-160">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="740eb-161">在 Linux 和 macOS 上，此命令會預期目標應用程式，並 `dotnet-counters` 共用相同的 `TMPDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="740eb-161">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="740eb-162">否則，此命令將會超時。</span><span class="sxs-lookup"><span data-stu-id="740eb-162">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="740eb-163">若要使用收集計量 `dotnet-counters` ，則必須以執行目標進程的使用者或做為根使用者的相同使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="740eb-163">To collect metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="740eb-164">否則，此工具將無法建立與目標進程的連接。</span><span class="sxs-lookup"><span data-stu-id="740eb-164">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

### <a name="examples"></a><span data-ttu-id="740eb-165">範例</span><span class="sxs-lookup"><span data-stu-id="740eb-165">Examples</span></span>

- <span data-ttu-id="740eb-166">以3秒的重新整理間隔收集所有計數器，並產生 csv 作為輸出：</span><span class="sxs-lookup"><span data-stu-id="740eb-166">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="740eb-167">`dotnet mvc.dll`以子進程的形式啟動，並開始收集執行時間計數器，並從啟動 ASP.NET Core 裝載計數器，並將其儲存為 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="740eb-167">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="740eb-168">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="740eb-168">dotnet-counters list</span></span>

<span data-ttu-id="740eb-169">顯示依提供者分組的計數器名稱和描述清單。</span><span class="sxs-lookup"><span data-stu-id="740eb-169">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="740eb-170">概要</span><span class="sxs-lookup"><span data-stu-id="740eb-170">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="740eb-171">範例</span><span class="sxs-lookup"><span data-stu-id="740eb-171">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="740eb-172">`Microsoft.AspNetCore.Hosting`當有可支援這些計數器的進程時，就會顯示計數器，例如，當主機電腦上正在執行 ASP.NET Core 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="740eb-172">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="740eb-173">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="740eb-173">dotnet-counters monitor</span></span>

<span data-ttu-id="740eb-174">顯示定期重新整理所選計數器的值。</span><span class="sxs-lookup"><span data-stu-id="740eb-174">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="740eb-175">概要</span><span class="sxs-lookup"><span data-stu-id="740eb-175">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="740eb-176">選項</span><span class="sxs-lookup"><span data-stu-id="740eb-176">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="740eb-177">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="740eb-177">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="740eb-178">要監視之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="740eb-178">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="740eb-179">要建立之診斷埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="740eb-179">The name of the diagnostic port to create.</span></span> <span data-ttu-id="740eb-180">請參閱 [使用診斷埠](#using-diagnostic-port) 來瞭解如何使用此選項，從應用程式啟動開始監視計數器。</span><span class="sxs-lookup"><span data-stu-id="740eb-180">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="740eb-181">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="740eb-181">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="740eb-182">以逗號分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="740eb-182">A comma-separated list of counters.</span></span> <span data-ttu-id="740eb-183">您可以指定計數器 `provider_name[:counter_name]` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-183">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="740eb-184">如果在 `provider_name` 沒有符合合格計數器清單的情況下使用，則會顯示來自提供者的所有計數器。</span><span class="sxs-lookup"><span data-stu-id="740eb-184">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="740eb-185">若要探索提供者和計數器名稱，請使用 [dotnet 計數器 list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="740eb-185">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="740eb-186">**`-- <command>` 僅限執行 .NET 5.0 或更新版本的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="740eb-186">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="740eb-187">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-187">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="740eb-188">`dotnet-counters` 將會使用所提供的命令啟動處理常式，並監視要求的計量。</span><span class="sxs-lookup"><span data-stu-id="740eb-188">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="740eb-189">這通常很適合用來收集應用程式啟動路徑的計量，也可以用來診斷或監視主要進入點之前或不久之後發生的問題。</span><span class="sxs-lookup"><span data-stu-id="740eb-189">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="740eb-190">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-190">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="740eb-191">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="740eb-191">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="740eb-192">透過 dotnet 啟動 .NET 可執行檔會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 進行互動。</span><span class="sxs-lookup"><span data-stu-id="740eb-192">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="740eb-193">透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。</span><span class="sxs-lookup"><span data-stu-id="740eb-193">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="740eb-194">如果子進程在工具之前結束，則工具也會結束。</span><span class="sxs-lookup"><span data-stu-id="740eb-194">If the child process exits before the tool, the tool will exit as well.</span></span> <span data-ttu-id="740eb-195">如果您需要使用 stdin/stdout，可以使用 `--diagnostic-port` 選項。</span><span class="sxs-lookup"><span data-stu-id="740eb-195">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="740eb-196">如需詳細資訊，請參閱 [使用診斷埠](#using-diagnostic-port) 。</span><span class="sxs-lookup"><span data-stu-id="740eb-196">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="740eb-197">在 Linux 和 macOS 上，此命令會預期目標應用程式，並 `dotnet-counters` 共用相同的 `TMPDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="740eb-197">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span>

> [!NOTE]
> <span data-ttu-id="740eb-198">若要使用監視計量 `dotnet-counters` ，則必須以執行目標進程的使用者或做為根使用者的相同使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="740eb-198">To monitor metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span>

### <a name="examples"></a><span data-ttu-id="740eb-199">範例</span><span class="sxs-lookup"><span data-stu-id="740eb-199">Examples</span></span>

- <span data-ttu-id="740eb-200">以3秒的重新整理間隔監視所有計數器 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="740eb-200">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="740eb-201">僅監視 CPU 使用量和 GC 堆積大小 `System.Runtime` ：</span><span class="sxs-lookup"><span data-stu-id="740eb-201">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="740eb-202">監視 `EventCounter` 使用者自訂的值 `EventSource` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-202">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="740eb-203">如需詳細資訊，請參閱 [教學課程：在 .Net Core 中使用 EventCounters 測量效能](event-counter-perf.md)。</span><span class="sxs-lookup"><span data-stu-id="740eb-203">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="740eb-204">查看中所有可用的已知計數器 `dotnet-counters` ：</span><span class="sxs-lookup"><span data-stu-id="740eb-204">View all well-known counters that are available in `dotnet-counters`:</span></span>

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- <span data-ttu-id="740eb-205">查看 `dotnet-counters` 適用于 .net 5 應用程式的所有知名計數器：</span><span class="sxs-lookup"><span data-stu-id="740eb-205">View all well-known counters that are available in `dotnet-counters` for .NET 5 apps:</span></span>

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- <span data-ttu-id="740eb-206">啟動 `my-aspnet-server.exe` 並監視從啟動 ( .net 5.0 或更新版本載入的元件 #) ：</span><span class="sxs-lookup"><span data-stu-id="740eb-206">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="740eb-207">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-207">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="740eb-208">`my-aspnet-server.exe`以 `arg1` `arg2` 命令列引數啟動，並從啟動 ( .net 5.0 或更新版本監視其工作集和 GC 堆積大小，只) ：</span><span class="sxs-lookup"><span data-stu-id="740eb-208">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="740eb-209">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-209">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="740eb-210">dotnet-計數器 ps</span><span class="sxs-lookup"><span data-stu-id="740eb-210">dotnet-counters ps</span></span>

<span data-ttu-id="740eb-211">顯示可以監視的 dotnet 進程清單。</span><span class="sxs-lookup"><span data-stu-id="740eb-211">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="740eb-212">概要</span><span class="sxs-lookup"><span data-stu-id="740eb-212">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="740eb-213">範例</span><span class="sxs-lookup"><span data-stu-id="740eb-213">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="740eb-214">使用診斷埠</span><span class="sxs-lookup"><span data-stu-id="740eb-214">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="740eb-215">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-215">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="740eb-216">診斷埠是新增在 .NET 5 中的新執行時間功能，可讓您從應用程式啟動開始監視或收集計數器。</span><span class="sxs-lookup"><span data-stu-id="740eb-216">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="740eb-217">若要使用來執行此作業， `dotnet-counters` 您可以使用 `dotnet-counters <collect|monitor> -- <command>` 如上述範例中所述，或使用 `--diagnostic-port` 選項。</span><span class="sxs-lookup"><span data-stu-id="740eb-217">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="740eb-218">使用 `dotnet-counters <collect|monitor> -- <command>` 以子進程的形式啟動應用程式是從啟動時快速監視的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="740eb-218">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="740eb-219">但是，當您想要更精確地控制受監視的應用程式存留期 (例如，只在前10分鐘內監視應用程式並繼續執行) 或者，如果您需要使用 CLI 與應用程式互動，使用 `--diagnostic-port` 選項可讓您控制受監視的目標應用程式和 `dotnet-counters` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-219">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="740eb-220">下列命令會建立名為 dotnet 的診斷通訊端 `myport.sock` ，並等候連接。</span><span class="sxs-lookup"><span data-stu-id="740eb-220">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="740eb-221">輸出：</span><span class="sxs-lookup"><span data-stu-id="740eb-221">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="740eb-222">在個別的主控台中，啟動目標應用程式，並將環境變數 `DOTNET_DiagnosticPorts` 設為輸出中的值 `dotnet-counters` 。</span><span class="sxs-lookup"><span data-stu-id="740eb-222">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="740eb-223">如此一來，就可以 `dotnet-counters` 開始收集計數器 `my-dotnet-app` ：</span><span class="sxs-lookup"><span data-stu-id="740eb-223">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="740eb-224">啟動您的應用程式可能 `dotnet run` 會造成問題，因為 DOTNET CLI 可能會產生許多不是您應用程式的子進程，而且它們可以在您的應用 `dotnet-counters` 程式之前連線，讓您的應用程式在執行時間暫停。</span><span class="sxs-lookup"><span data-stu-id="740eb-224">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="740eb-225">建議您直接使用應用程式的獨立版本，或用 `dotnet exec` 來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="740eb-225">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
