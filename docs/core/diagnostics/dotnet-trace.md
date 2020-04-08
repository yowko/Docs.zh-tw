---
title: 點網追蹤工具 - .NET 核心
description: 安裝和使用點網跟蹤命令列工具。
ms.date: 11/21/2019
ms.openlocfilehash: 6880c3721e4cab12677bd02c82ca944cc9812670
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888081"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="2c1fd-103">點網追蹤效能分析實用程式</span><span class="sxs-lookup"><span data-stu-id="2c1fd-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="2c1fd-104">**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="2c1fd-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="2c1fd-105">安裝點網追蹤</span><span class="sxs-lookup"><span data-stu-id="2c1fd-105">Install dotnet-trace</span></span>

<span data-ttu-id="2c1fd-106">使用`dotnet-trace` [dotnet 工具安裝](../tools/dotnet-tool-install.md)指令安裝[NuGet 套件](https://www.nuget.org/packages/dotnet-trace):</span><span class="sxs-lookup"><span data-stu-id="2c1fd-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="2c1fd-107">概要</span><span class="sxs-lookup"><span data-stu-id="2c1fd-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="2c1fd-108">描述</span><span class="sxs-lookup"><span data-stu-id="2c1fd-108">Description</span></span>

<span data-ttu-id="2c1fd-109">該工具`dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="2c1fd-110">是一個跨平臺 .NET 核心工具。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="2c1fd-111">支援在沒有本機探查器的情況下收集正在運行的進程的 .NET Core 跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="2c1fd-112">是圍繞 .NET`EventPipe`Core 運行時的跨平臺技術構建的。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="2c1fd-113">在 Windows、Linux 或 macOS 上提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="2c1fd-114">選項。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="2c1fd-115">顯示點網跟蹤實用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-115">Displays the version of the dotnet-trace utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2c1fd-116">顯示命令行説明。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="2c1fd-117">命令</span><span class="sxs-lookup"><span data-stu-id="2c1fd-117">Commands</span></span>

| <span data-ttu-id="2c1fd-118">Command</span><span class="sxs-lookup"><span data-stu-id="2c1fd-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="2c1fd-119">點網追蹤收集</span><span class="sxs-lookup"><span data-stu-id="2c1fd-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="2c1fd-120">點網追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="2c1fd-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="2c1fd-121">點內追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="2c1fd-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="2c1fd-122">點網追蹤清單設定檔</span><span class="sxs-lookup"><span data-stu-id="2c1fd-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="2c1fd-123">點網追蹤收集</span><span class="sxs-lookup"><span data-stu-id="2c1fd-123">dotnet-trace collect</span></span>

<span data-ttu-id="2c1fd-124">從正在運行的進程收集診斷跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2c1fd-125">概要</span><span class="sxs-lookup"><span data-stu-id="2c1fd-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="2c1fd-126">選項。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="2c1fd-127">從中收集跟蹤的過程。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="2c1fd-128">設置記憶體中圓形緩衝區的大小(以兆位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="2c1fd-129">默認值 256 MB。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="2c1fd-130">收集的跟蹤數據的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-130">The output path for the collected trace data.</span></span> <span data-ttu-id="2c1fd-131">沒有指定,則預設為`trace.nettrace`。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="2c1fd-132">要啟用的提供程式的`EventPipe`逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="2c1fd-133">這些提供商補充了 隱含的`--profile <profile-name>`任何 提供程式。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="2c1fd-134">如果特定提供程式有任何不一致,則此配置優先於配置檔中的隱式配置。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="2c1fd-135">提供程式清單的形式為:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="2c1fd-136">`Provider`以以下形式: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="2c1fd-137">`KeyValueArgs`以以下形式: `[key1=value1][;key2=value2]`。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="2c1fd-138">一組命名的預定義的提供程式配置,允許簡潔地指定常見跟蹤方案。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="2c1fd-139">設定追蹤檔轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="2c1fd-140">預設值為 `NetTrace`。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="2c1fd-141">點網追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="2c1fd-141">dotnet-trace convert</span></span>

<span data-ttu-id="2c1fd-142">將`nettrace`追蹤轉換為備用格式,以便與備用跟蹤分析工具一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2c1fd-143">概要</span><span class="sxs-lookup"><span data-stu-id="2c1fd-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="2c1fd-144">引數</span><span class="sxs-lookup"><span data-stu-id="2c1fd-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="2c1fd-145">要轉換的輸入跟蹤檔。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-145">Input trace file to be converted.</span></span> <span data-ttu-id="2c1fd-146">預設值為*追蹤.net 追蹤*。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="2c1fd-147">選項。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="2c1fd-148">設定追蹤檔轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="2c1fd-149">輸出檔名。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-149">Output filename.</span></span> <span data-ttu-id="2c1fd-150">將添加目標格式的擴展。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="2c1fd-151">點內追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="2c1fd-151">dotnet-trace ps</span></span>

<span data-ttu-id="2c1fd-152">列出可附加到的點網進程。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2c1fd-153">概要</span><span class="sxs-lookup"><span data-stu-id="2c1fd-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="2c1fd-154">點網追蹤清單設定檔</span><span class="sxs-lookup"><span data-stu-id="2c1fd-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="2c1fd-155">列出預建構的追蹤配置檔,說明每個設定檔中有哪些提供程式和篩選器。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2c1fd-156">概要</span><span class="sxs-lookup"><span data-stu-id="2c1fd-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="2c1fd-157">使用點網追蹤收集追蹤</span><span class="sxs-lookup"><span data-stu-id="2c1fd-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="2c1fd-158">使用收集追蹤: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="2c1fd-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="2c1fd-159">取得 .NET Core 應用程式的流程識別碼 (PID), 以便從中收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="2c1fd-160">例如,在 Windows 上,可以`tasklist`使用任務 管理器或命令。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="2c1fd-161">例如,在 Linux`ps`上 ,命令。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="2c1fd-162">點內追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="2c1fd-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="2c1fd-163">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2c1fd-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="2c1fd-164">前面的指令產生類似於以下內容的輸出:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="2c1fd-165">按鍵`<Enter>`停止收集。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="2c1fd-166">`dotnet-trace`將完成對*追蹤.net 追蹤*檔案的紀錄記錄事件。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="2c1fd-167">檢視從點網追蹤擷取的追蹤</span><span class="sxs-lookup"><span data-stu-id="2c1fd-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="2c1fd-168">在 Windows 上,可以在[PerfView](https://github.com/microsoft/perfview)上查看 *.nettrace*檔進行分析:對於在其他平臺上收集的跟蹤,可以將追蹤檔移動到在 PerfView 上查看的 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="2c1fd-169">在 Linux 上,可以`dotnet-trace`通過將的輸出`speedscope`格式更改為 來查看跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="2c1fd-170">可以使用`-f|--format`選項更改輸出檔案格式`-f speedscope`-`dotnet-trace``speedscope`將產生檔案。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="2c1fd-171">您可以在`nettrace`(預設選項)`speedscope`和 之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="2c1fd-172">`Speedscope`文件可以在打開。 <https://www.speedscope.app></span><span class="sxs-lookup"><span data-stu-id="2c1fd-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="2c1fd-173">.NET 核心運行時`nettrace`以 格式生成跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="2c1fd-174">跟蹤完成後,跟蹤將轉換為速度範圍(如果指定)。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="2c1fd-175">由於某些轉換可能會導致資料丟失,因此`nettrace`原始 檔將保留在轉換後的文件旁邊。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="2c1fd-176">使用點網追蹤收集隨時間的計數器值</span><span class="sxs-lookup"><span data-stu-id="2c1fd-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="2c1fd-177">`dotnet-trace`可以:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="2c1fd-178">用於`EventCounter`性能敏感環境中的基本運行狀況監視。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="2c1fd-179">例如,在生產中。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-179">For example, in production.</span></span>
* <span data-ttu-id="2c1fd-180">收集跟蹤,以便不需要即時查看它們。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="2c1fd-181">例如,要收集運行時性能計數器值,請使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="2c1fd-182">前面的命令告訴運行時計數器每秒報告一次以進行羽量級運行狀況監視。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="2c1fd-183">替換為`EventCounterIntervalSec=1`較高的值(例如,60)允許在計數器數據中以較少的粒度收集較小的跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="2c1fd-184">以下指令比前面的指令減少花費和追蹤大小:</span><span class="sxs-lookup"><span data-stu-id="2c1fd-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="2c1fd-185">前面的命令禁用運行時事件和託管堆疊探查器。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="2c1fd-186">.NET 提供者</span><span class="sxs-lookup"><span data-stu-id="2c1fd-186">.NET Providers</span></span>

<span data-ttu-id="2c1fd-187">.NET 核心運行時支援以下 .NET 提供程式。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="2c1fd-188">.NET Core 使用相同的關鍵字來`Event Tracing for Windows (ETW)``EventPipe`啟用和 跟蹤。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="2c1fd-189">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="2c1fd-189">Provider name</span></span>                            | <span data-ttu-id="2c1fd-190">資訊</span><span class="sxs-lookup"><span data-stu-id="2c1fd-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="2c1fd-191">執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="2c1fd-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="2c1fd-192">CLR 執行時關鍵字</span><span class="sxs-lookup"><span data-stu-id="2c1fd-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="2c1fd-193">取消提供者</span><span class="sxs-lookup"><span data-stu-id="2c1fd-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="2c1fd-194">CLR 執行關鍵字</span><span class="sxs-lookup"><span data-stu-id="2c1fd-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="2c1fd-195">啟用示例探查器。</span><span class="sxs-lookup"><span data-stu-id="2c1fd-195">Enables the sample profiler.</span></span> |
