---
title: dotnet-追蹤工具-.NET Core
description: 安裝和使用 dotnet 追蹤命令列工具。
ms.date: 11/21/2019
ms.openlocfilehash: 4a3694f6ed748779809ee4c4bfd941bb6f1ac490
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687625"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="e6423-103">dotnet-追蹤效能分析公用程式</span><span class="sxs-lookup"><span data-stu-id="e6423-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="e6423-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e6423-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="e6423-105">安裝 dotnet-追蹤</span><span class="sxs-lookup"><span data-stu-id="e6423-105">Install dotnet-trace</span></span>

<span data-ttu-id="e6423-106">`dotnet-trace`使用[dotnet 工具安裝](../tools/dotnet-tool-install.md)命令安裝[NuGet 套件](https://www.nuget.org/packages/dotnet-trace)：</span><span class="sxs-lookup"><span data-stu-id="e6423-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="e6423-107">概要</span><span class="sxs-lookup"><span data-stu-id="e6423-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e6423-108">描述</span><span class="sxs-lookup"><span data-stu-id="e6423-108">Description</span></span>

<span data-ttu-id="e6423-109">`dotnet-trace`工具：</span><span class="sxs-lookup"><span data-stu-id="e6423-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="e6423-110">是跨平臺 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="e6423-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="e6423-111">在不使用原生分析工具的情況下，啟用正在執行之進程的 .NET Core 追蹤收集。</span><span class="sxs-lookup"><span data-stu-id="e6423-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="e6423-112">是以 [`EventPipe`](./eventpipe.md) .Net Core 執行時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="e6423-112">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="e6423-113">在 Windows、Linux 或 macOS 上提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="e6423-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="e6423-114">選項</span><span class="sxs-lookup"><span data-stu-id="e6423-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e6423-115">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="e6423-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="e6423-116">顯示 dotnet 追蹤公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="e6423-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="e6423-117">命令</span><span class="sxs-lookup"><span data-stu-id="e6423-117">Commands</span></span>

| <span data-ttu-id="e6423-118">命令</span><span class="sxs-lookup"><span data-stu-id="e6423-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="e6423-119">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="e6423-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="e6423-120">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="e6423-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="e6423-121">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e6423-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="e6423-122">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="e6423-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="e6423-123">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="e6423-123">dotnet-trace collect</span></span>

<span data-ttu-id="e6423-124">從正在執行的進程收集診斷追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6423-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6423-125">概要</span><span class="sxs-lookup"><span data-stu-id="e6423-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="e6423-126">選項</span><span class="sxs-lookup"><span data-stu-id="e6423-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="e6423-127">設定記憶體中的圓形緩衝區大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="e6423-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="e6423-128">預設值為 256 MB。</span><span class="sxs-lookup"><span data-stu-id="e6423-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="e6423-129">要發出之 CLR 事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e6423-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="e6423-130">要發出之 CLR 運行時間事件的清單。</span><span class="sxs-lookup"><span data-stu-id="e6423-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="e6423-131">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="e6423-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="e6423-132">預設為 `NetTrace`。</span><span class="sxs-lookup"><span data-stu-id="e6423-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="e6423-133">要從中收集追蹤的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="e6423-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="e6423-134">所收集之追蹤資料的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="e6423-134">The output path for the collected trace data.</span></span> <span data-ttu-id="e6423-135">如果未指定，則預設為 `trace.nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e6423-136">從中收集追蹤的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6423-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="e6423-137">一組名為預先定義的提供者設定，可讓您簡潔地指定常見的追蹤案例。</span><span class="sxs-lookup"><span data-stu-id="e6423-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="e6423-138">要啟用的提供者清單（以逗號分隔） `EventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="e6423-139">這些提供者補充了所暗示的任何提供者 `--profile <profile-name>` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="e6423-140">如果特定提供者有任何不一致的情況，此設定會優先于設定檔中的隱含設定。</span><span class="sxs-lookup"><span data-stu-id="e6423-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="e6423-141">這份提供者清單的格式如下：</span><span class="sxs-lookup"><span data-stu-id="e6423-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="e6423-142">`Provider` 的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="e6423-143">`KeyValueArgs` 的格式為： `[key1=value1][;key2=value2]` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="e6423-144">**`-- <command>` 僅執行 .NET 5.0 的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="e6423-144">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="e6423-145">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6423-145">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="e6423-146">這在診斷程式早期發生的問題（例如啟動效能問題或元件載入器和系結器錯誤）時，可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="e6423-146">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e6423-147">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6423-147">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="e6423-148">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="e6423-148">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="e6423-149">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="e6423-149">dotnet-trace convert</span></span>

<span data-ttu-id="e6423-150">將 `nettrace` 追蹤轉換成替代的格式，以搭配使用替代的追蹤分析工具。</span><span class="sxs-lookup"><span data-stu-id="e6423-150">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6423-151">概要</span><span class="sxs-lookup"><span data-stu-id="e6423-151">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="e6423-152">引數</span><span class="sxs-lookup"><span data-stu-id="e6423-152">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="e6423-153">要轉換的輸入追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="e6423-153">Input trace file to be converted.</span></span> <span data-ttu-id="e6423-154">預設值為 *nettrace*。</span><span class="sxs-lookup"><span data-stu-id="e6423-154">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="e6423-155">選項</span><span class="sxs-lookup"><span data-stu-id="e6423-155">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="e6423-156">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="e6423-156">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="e6423-157">輸出檔案名。</span><span class="sxs-lookup"><span data-stu-id="e6423-157">Output filename.</span></span> <span data-ttu-id="e6423-158">將會新增目標格式的擴充。</span><span class="sxs-lookup"><span data-stu-id="e6423-158">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="e6423-159">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e6423-159">dotnet-trace ps</span></span>

 <span data-ttu-id="e6423-160">列出可從中收集追蹤的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="e6423-160">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6423-161">概要</span><span class="sxs-lookup"><span data-stu-id="e6423-161">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="e6423-162">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="e6423-162">dotnet-trace list-profiles</span></span>

<span data-ttu-id="e6423-163">列出預先建立的追蹤設定檔，其中包含每個設定檔中提供者和篩選器的描述。</span><span class="sxs-lookup"><span data-stu-id="e6423-163">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6423-164">概要</span><span class="sxs-lookup"><span data-stu-id="e6423-164">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="e6423-165">使用 dotnet 收集追蹤</span><span class="sxs-lookup"><span data-stu-id="e6423-165">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="e6423-166">若要使用 `dotnet-trace` 下列內容收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="e6423-166">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="e6423-167">取得 .NET Core 應用程式 (PID) 的處理序識別碼，以從中收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6423-167">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="e6423-168">例如，在 Windows 上，您可以使用工作管理員或 `tasklist` 命令。</span><span class="sxs-lookup"><span data-stu-id="e6423-168">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="e6423-169">例如，在 Linux 上， `ps` 命令。</span><span class="sxs-lookup"><span data-stu-id="e6423-169">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="e6423-170">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e6423-170">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="e6423-171">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e6423-171">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="e6423-172">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="e6423-172">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="e6423-173">按下按鍵以停止收集 `<Enter>` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-173">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="e6423-174">`dotnet-trace` 將會完成 *nettrace* 檔案的記錄事件。</span><span class="sxs-lookup"><span data-stu-id="e6423-174">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="e6423-175">啟動子應用程式，並使用 dotnet 從啟動中收集追蹤</span><span class="sxs-lookup"><span data-stu-id="e6423-175">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

<span data-ttu-id="e6423-176">注意：這只適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6423-176">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="e6423-177">有時候，從啟動時收集處理常式的追蹤可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="e6423-177">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="e6423-178">針對執行 .NET 5.0 或更新版本的應用程式，您可以使用 dotnet 來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="e6423-178">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="e6423-179">這會 `hello.exe` 以 `arg1` 和它的 `arg2` 命令列引數啟動，並從其執行時間啟動中收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="e6423-179">This will launch `hello.exe` with `arg1` and `arg2` as its command line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="e6423-180">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="e6423-180">The preceding command generates output similar to the following:</span></span>

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

<span data-ttu-id="e6423-181">您可以按或鍵來停止收集 `<Enter>` 追蹤 `<Ctrl + C>` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-181">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="e6423-182">這樣做也會結束 `hello.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-182">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="e6423-183">透過 `hello.exe` dotnet 追蹤會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 互動。</span><span class="sxs-lookup"><span data-stu-id="e6423-183">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="e6423-184">透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。</span><span class="sxs-lookup"><span data-stu-id="e6423-184">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="e6423-185">如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6423-185">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="e6423-186">查看從 dotnet 捕捉的追蹤</span><span class="sxs-lookup"><span data-stu-id="e6423-186">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="e6423-187">在 Windows 中，可以在 [PerfView](https://github.com/microsoft/perfview)上查看 *nettrace* 檔案以供分析：對於在其他平臺上收集的追蹤，追蹤檔案可以移至要在 PerfView 上查看的 Windows 機器。</span><span class="sxs-lookup"><span data-stu-id="e6423-187">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="e6423-188">在 Linux 上，您可以藉由將的輸出格式變更 `dotnet-trace` 為來查看追蹤 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-188">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="e6423-189">您可以使用選項來變更輸出檔案格式 `-f|--format` - `-f speedscope` 將會 `dotnet-trace` 產生檔案 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-189">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="e6423-190">您可以選擇 `nettrace` (預設選項) 和 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-190">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="e6423-191">`Speedscope` 您可以在中開啟檔案 <https://www.speedscope.app> 。</span><span class="sxs-lookup"><span data-stu-id="e6423-191">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="e6423-192">.NET Core 執行時間會以格式產生追蹤 `nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="e6423-192">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="e6423-193">追蹤會轉換成 speedscope (如果在追蹤完成後指定) 。</span><span class="sxs-lookup"><span data-stu-id="e6423-193">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="e6423-194">因為某些轉換可能會導致資料遺失，所以 `nettrace` 已轉換的檔案旁邊會保留原始檔案。</span><span class="sxs-lookup"><span data-stu-id="e6423-194">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="e6423-195">使用 dotnet 來收集一段時間內的計數器值</span><span class="sxs-lookup"><span data-stu-id="e6423-195">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="e6423-196">`dotnet-trace` 可以：</span><span class="sxs-lookup"><span data-stu-id="e6423-196">`dotnet-trace` can:</span></span>

* <span data-ttu-id="e6423-197">用於 `EventCounter` 效能敏感性環境中的基本健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="e6423-197">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="e6423-198">例如，在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="e6423-198">For example, in production.</span></span>
* <span data-ttu-id="e6423-199">收集追蹤，讓它們不需要即時觀看。</span><span class="sxs-lookup"><span data-stu-id="e6423-199">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="e6423-200">例如，若要收集執行時間效能計數器值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="e6423-200">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="e6423-201">上述命令會告知執行時間計數器每秒回報一次，以進行輕量健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="e6423-201">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="e6423-202">以 `EventCounterIntervalSec=1` 較高的值取代 (例如，60) 可讓您以較少的資料細微性收集計數器資料中較小的追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6423-202">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="e6423-203">下列命令可減少額外負荷和追蹤大小，而不是前一個：</span><span class="sxs-lookup"><span data-stu-id="e6423-203">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="e6423-204">上述命令會停用運行時間事件和 managed stack profiler。</span><span class="sxs-lookup"><span data-stu-id="e6423-204">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="e6423-205">.NET 提供者</span><span class="sxs-lookup"><span data-stu-id="e6423-205">.NET Providers</span></span>

<span data-ttu-id="e6423-206">.NET Core 執行時間支援下列 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="e6423-206">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="e6423-207">.NET Core 會使用相同的關鍵字來啟用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6423-207">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="e6423-208">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="e6423-208">Provider name</span></span>                            | <span data-ttu-id="e6423-209">資訊</span><span class="sxs-lookup"><span data-stu-id="e6423-209">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="e6423-210">執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="e6423-210">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="e6423-211">CLR 執行時間關鍵字</span><span class="sxs-lookup"><span data-stu-id="e6423-211">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="e6423-212">取消提供者</span><span class="sxs-lookup"><span data-stu-id="e6423-212">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="e6423-213">CLR 取消關鍵字</span><span class="sxs-lookup"><span data-stu-id="e6423-213">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="e6423-214">啟用範例 profiler。</span><span class="sxs-lookup"><span data-stu-id="e6423-214">Enables the sample profiler.</span></span> |
