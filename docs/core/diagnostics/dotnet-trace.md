---
title: dotnet-追蹤-.NET Core
description: 安裝和使用 dotnet 追蹤命令列工具。
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321579"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="7e15d-103">效能分析公用程式追蹤（`dotnet-trace`）</span><span class="sxs-lookup"><span data-stu-id="7e15d-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="7e15d-104">**本文適用于：** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="7e15d-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="7e15d-105">安裝 `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="7e15d-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="7e15d-106">若要安裝 `dotnet-trace` [NuGet 套件](https://www.nuget.org/packages/dotnet-trace)的最新發行版本，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="7e15d-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="7e15d-107">概要</span><span class="sxs-lookup"><span data-stu-id="7e15d-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="7e15d-108">描述</span><span class="sxs-lookup"><span data-stu-id="7e15d-108">Description</span></span>

<span data-ttu-id="7e15d-109">@No__t_0 工具是一種跨平臺 CLI 全域工具，可讓您收集執行中進程的 .NET Core 追蹤，而不需要任何原生分析工具。</span><span class="sxs-lookup"><span data-stu-id="7e15d-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="7e15d-110">它是圍繞 .NET Core 執行時間的跨平臺 `EventPipe` 技術所建立的。</span><span class="sxs-lookup"><span data-stu-id="7e15d-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="7e15d-111">`dotnet-trace` 在 Windows、Linux 或 macOS 上提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="7e15d-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="7e15d-112">選項</span><span class="sxs-lookup"><span data-stu-id="7e15d-112">Options</span></span>

- **`--version`**

<span data-ttu-id="7e15d-113">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="7e15d-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="7e15d-114">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="7e15d-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="7e15d-115">命令</span><span class="sxs-lookup"><span data-stu-id="7e15d-115">Commands</span></span>

| <span data-ttu-id="7e15d-116">命令</span><span class="sxs-lookup"><span data-stu-id="7e15d-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="7e15d-117">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="7e15d-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="7e15d-118">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="7e15d-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="7e15d-119">dotnet-追蹤清單-進程</span><span class="sxs-lookup"><span data-stu-id="7e15d-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="7e15d-120">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="7e15d-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="7e15d-121">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="7e15d-121">dotnet-trace collect</span></span>

<span data-ttu-id="7e15d-122">從執行中的進程收集診斷追蹤。</span><span class="sxs-lookup"><span data-stu-id="7e15d-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7e15d-123">概要</span><span class="sxs-lookup"><span data-stu-id="7e15d-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="7e15d-124">選項</span><span class="sxs-lookup"><span data-stu-id="7e15d-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7e15d-125">要從中收集追蹤的進程。</span><span class="sxs-lookup"><span data-stu-id="7e15d-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="7e15d-126">設定記憶體中的迴圈緩衝區大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="7e15d-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="7e15d-127">預設值： 256 MB。</span><span class="sxs-lookup"><span data-stu-id="7e15d-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="7e15d-128">所收集追蹤資料的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="7e15d-128">The output path for the collected trace data.</span></span> <span data-ttu-id="7e15d-129">如果未指定，則預設為 `trace.nettrace`。</span><span class="sxs-lookup"><span data-stu-id="7e15d-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="7e15d-130">要啟用的 `EventPipe` 提供者清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="7e15d-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="7e15d-131">這些提供者會補充 `--profile <profile-name>` 所隱含的任何提供者。</span><span class="sxs-lookup"><span data-stu-id="7e15d-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="7e15d-132">如果特定提供者有任何不一致的情況，此處的設定會優先于設定檔中的隱含設定。</span><span class="sxs-lookup"><span data-stu-id="7e15d-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="7e15d-133">這份提供者清單的格式如下：</span><span class="sxs-lookup"><span data-stu-id="7e15d-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="7e15d-134">`Provider` 的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`。</span><span class="sxs-lookup"><span data-stu-id="7e15d-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="7e15d-135">`KeyValueArgs` 的格式為： `[key1=value1][;key2=value2]`。</span><span class="sxs-lookup"><span data-stu-id="7e15d-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="7e15d-136">一組命名的預先定義提供者設定，可讓您簡潔地指定一般追蹤案例。</span><span class="sxs-lookup"><span data-stu-id="7e15d-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="7e15d-137">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="7e15d-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="7e15d-138">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="7e15d-138">dotnet-trace convert</span></span>

<span data-ttu-id="7e15d-139">將 `nettrace` 追蹤轉換為替代的格式，以搭配替代的追蹤分析工具使用。</span><span class="sxs-lookup"><span data-stu-id="7e15d-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7e15d-140">概要</span><span class="sxs-lookup"><span data-stu-id="7e15d-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="7e15d-141">引數</span><span class="sxs-lookup"><span data-stu-id="7e15d-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="7e15d-142">要轉換的輸入追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="7e15d-142">Input trace file to be converted.</span></span> <span data-ttu-id="7e15d-143">預設為*nettrace*。</span><span class="sxs-lookup"><span data-stu-id="7e15d-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="7e15d-144">選項</span><span class="sxs-lookup"><span data-stu-id="7e15d-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="7e15d-145">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="7e15d-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="7e15d-146">輸出檔案名。</span><span class="sxs-lookup"><span data-stu-id="7e15d-146">Output filename.</span></span> <span data-ttu-id="7e15d-147">將會加入目標格式的副檔名。</span><span class="sxs-lookup"><span data-stu-id="7e15d-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="7e15d-148">dotnet-追蹤清單-進程</span><span class="sxs-lookup"><span data-stu-id="7e15d-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="7e15d-149">列出可以追蹤的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="7e15d-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7e15d-150">概要</span><span class="sxs-lookup"><span data-stu-id="7e15d-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="7e15d-151">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="7e15d-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="7e15d-152">列出預先建立的追蹤設定檔，其中包含每個設定檔中提供者和篩選器的描述。</span><span class="sxs-lookup"><span data-stu-id="7e15d-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7e15d-153">概要</span><span class="sxs-lookup"><span data-stu-id="7e15d-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="7e15d-154">使用 `dotnet-trace` 收集追蹤</span><span class="sxs-lookup"><span data-stu-id="7e15d-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="7e15d-155">若要使用 `dotnet-trace` 收集追蹤，您必須先找出 .NET Core 應用程式的處理序識別碼（PID），以從中收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="7e15d-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="7e15d-156">在 Windows 上，有一些選項，例如使用工作管理員或 `tasklist` 命令。</span><span class="sxs-lookup"><span data-stu-id="7e15d-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="7e15d-157">在 Linux 上，[一般] 選項可能會使用 `ps` 命令。</span><span class="sxs-lookup"><span data-stu-id="7e15d-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="7e15d-158">您也可以使用[dotnet-追蹤清單-進程](#dotnet-trace-list-processes)命令，找出執行中的 .net Core 進程及其 pid。</span><span class="sxs-lookup"><span data-stu-id="7e15d-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="7e15d-159">然後，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7e15d-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="7e15d-160">最後，按下 `<Enter>` 鍵來停止收集，`dotnet-trace` 會完成記錄事件以 `trace.nettrace` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e15d-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="7e15d-161">查看從 `dotnet-trace` 所捕獲的追蹤</span><span class="sxs-lookup"><span data-stu-id="7e15d-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="7e15d-162">在 Windows 上，您可以在[PerfView](https://github.com/microsoft/perfview)上查看 `.nettrace` 檔案以進行分析，就像使用 ETW 或 LTTng 收集的追蹤一樣。</span><span class="sxs-lookup"><span data-stu-id="7e15d-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="7e15d-163">針對在 Linux 上收集的追蹤，您可以將追蹤移至要在 PerfView 上查看的 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="7e15d-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="7e15d-164">您也可以藉由將 `dotnet-trace` 的輸出格式變更為 `speedscope`，在 Linux 機器上觀看追蹤。</span><span class="sxs-lookup"><span data-stu-id="7e15d-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="7e15d-165">您可以使用 `-f|--format` 選項來變更輸出檔案格式，`-f speedscope` 會使 `dotnet-trace` 產生 `speedscope` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e15d-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="7e15d-166">您目前可以選擇 `nettrace` （預設選項）和 `speedscope`。</span><span class="sxs-lookup"><span data-stu-id="7e15d-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="7e15d-167">可以在 <https://www.speedscope.app> 開啟 `Speedscope` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7e15d-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="7e15d-168">.NET Core 執行時間會以 `nettrace` 格式產生追蹤，並在追蹤完成之後，轉換成 speedscope （如果有指定的話）。</span><span class="sxs-lookup"><span data-stu-id="7e15d-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="7e15d-169">由於某些轉換可能會導致資料遺失，因此原始 `nettrace` 檔案會保留在轉換後的檔案旁邊。</span><span class="sxs-lookup"><span data-stu-id="7e15d-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="7e15d-170">使用 `dotnet-trace` 來收集一段時間的計數器值</span><span class="sxs-lookup"><span data-stu-id="7e15d-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="7e15d-171">如果您嘗試在效能相關設定（例如生產環境）中使用基本健全狀況監視的 `EventCounter`，而您想要收集追蹤，而不是即時監看它們，您也可以透過 `dotnet-trace` 來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="7e15d-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="7e15d-172">例如，如果您想要收集執行時間效能計數器的值，您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="7e15d-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="7e15d-173">此命令會告訴執行時間計數器每秒報告一次，以進行輕量的健全狀況監視。</span><span class="sxs-lookup"><span data-stu-id="7e15d-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="7e15d-174">以較高的值取代 `EventCounterIntervalSec=1` （例如，60），可讓您以較少的計數器資料收集較小的追蹤。</span><span class="sxs-lookup"><span data-stu-id="7e15d-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="7e15d-175">如果您想要停用運行時間事件以減少額外負荷（和追蹤大小），您可以使用下列命令來停用運行時間事件和 managed 堆疊 profiler。</span><span class="sxs-lookup"><span data-stu-id="7e15d-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="7e15d-176">.NET 提供者</span><span class="sxs-lookup"><span data-stu-id="7e15d-176">.NET Providers</span></span>

<span data-ttu-id="7e15d-177">.NET Core 執行時間支援下列 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="7e15d-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="7e15d-178">.NET Core 會使用相同的關鍵字來啟用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 追蹤。</span><span class="sxs-lookup"><span data-stu-id="7e15d-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="7e15d-179">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="7e15d-179">Provider name</span></span>                            | <span data-ttu-id="7e15d-180">內容</span><span class="sxs-lookup"><span data-stu-id="7e15d-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="7e15d-181">執行時間提供者</span><span class="sxs-lookup"><span data-stu-id="7e15d-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="7e15d-182">CLR 執行時間關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e15d-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="7e15d-183">取消提供者</span><span class="sxs-lookup"><span data-stu-id="7e15d-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="7e15d-184">CLR 取消關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e15d-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="7e15d-185">啟用範例 profiler。</span><span class="sxs-lookup"><span data-stu-id="7e15d-185">Enables the sample profiler.</span></span> |
