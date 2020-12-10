---
title: dotnet-追蹤診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet 追蹤 CLI 工具，以使用 .NET EventPipe 來收集執行中進程的 .NET 追蹤，而不使用原生 profiler。
ms.date: 11/17/2020
ms.openlocfilehash: 868ce7828eee6bd7f2101d5d6a65c7f7bf87fe24
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009530"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="e5058-103">dotnet-追蹤效能分析公用程式</span><span class="sxs-lookup"><span data-stu-id="e5058-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="e5058-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e5058-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="e5058-105">安裝</span><span class="sxs-lookup"><span data-stu-id="e5058-105">Install</span></span>

<span data-ttu-id="e5058-106">有兩種方式可以下載和安裝 `dotnet-trace` ：</span><span class="sxs-lookup"><span data-stu-id="e5058-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="e5058-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="e5058-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="e5058-108">若要安裝 `dotnet-trace` [NuGet 套件](https://www.nuget.org/packages/dotnet-trace)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="e5058-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="e5058-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="e5058-109">**Direct download:**</span></span>

  <span data-ttu-id="e5058-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="e5058-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="e5058-111">OS</span><span class="sxs-lookup"><span data-stu-id="e5058-111">OS</span></span>  | <span data-ttu-id="e5058-112">平台</span><span class="sxs-lookup"><span data-stu-id="e5058-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="e5058-113">Windows</span><span class="sxs-lookup"><span data-stu-id="e5058-113">Windows</span></span> | <span data-ttu-id="e5058-114">[x86](https://aka.ms/dotnet-trace/win-x86) \|[x64](https://aka.ms/dotnet-trace/win-x64) \|[arm](https://aka.ms/dotnet-trace/win-arm) \|[arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="e5058-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="e5058-115">macOS</span><span class="sxs-lookup"><span data-stu-id="e5058-115">macOS</span></span>   | [<span data-ttu-id="e5058-116">x64</span><span class="sxs-lookup"><span data-stu-id="e5058-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="e5058-117">Linux</span><span class="sxs-lookup"><span data-stu-id="e5058-117">Linux</span></span>   | <span data-ttu-id="e5058-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \|[arm](https://aka.ms/dotnet-trace/linux-arm) \|[arm64](https://aka.ms/dotnet-trace/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="e5058-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="e5058-119">概要</span><span class="sxs-lookup"><span data-stu-id="e5058-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e5058-120">描述</span><span class="sxs-lookup"><span data-stu-id="e5058-120">Description</span></span>

<span data-ttu-id="e5058-121">`dotnet-trace`工具：</span><span class="sxs-lookup"><span data-stu-id="e5058-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="e5058-122">是跨平臺 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="e5058-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="e5058-123">在不使用原生分析工具的情況下，啟用正在執行之進程的 .NET Core 追蹤收集。</span><span class="sxs-lookup"><span data-stu-id="e5058-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="e5058-124">是以 [`EventPipe`](./eventpipe.md) .Net Core 執行時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="e5058-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="e5058-125">在 Windows、Linux 或 macOS 上提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="e5058-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="e5058-126">選項</span><span class="sxs-lookup"><span data-stu-id="e5058-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e5058-127">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="e5058-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="e5058-128">顯示 dotnet 追蹤公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="e5058-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="e5058-129">命令</span><span class="sxs-lookup"><span data-stu-id="e5058-129">Commands</span></span>

| <span data-ttu-id="e5058-130">命令</span><span class="sxs-lookup"><span data-stu-id="e5058-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="e5058-131">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="e5058-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="e5058-132">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="e5058-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="e5058-133">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e5058-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="e5058-134">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="e5058-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="e5058-135">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="e5058-135">dotnet-trace collect</span></span>

<span data-ttu-id="e5058-136">從正在執行的進程收集診斷追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5058-137">概要</span><span class="sxs-lookup"><span data-stu-id="e5058-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="e5058-138">選項</span><span class="sxs-lookup"><span data-stu-id="e5058-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="e5058-139">設定記憶體中的圓形緩衝區大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="e5058-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="e5058-140">預設值為 256 MB。</span><span class="sxs-lookup"><span data-stu-id="e5058-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="e5058-141">要發出之 CLR 事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e5058-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="e5058-142">要發出之 CLR 運行時間事件的清單。</span><span class="sxs-lookup"><span data-stu-id="e5058-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="e5058-143">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="e5058-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="e5058-144">預設值為 `NetTrace`。</span><span class="sxs-lookup"><span data-stu-id="e5058-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="e5058-145">要從中收集追蹤的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="e5058-145">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="e5058-146">要建立之診斷埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5058-146">The name of the diagnostic port to create.</span></span> <span data-ttu-id="e5058-147">請參閱 [使用診斷埠從應用程式啟動收集追蹤](#use-diagnostic-port-to-collect-a-trace-from-app-startup) ，以瞭解如何使用此選項從應用程式啟動收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-147">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="e5058-148">所收集之追蹤資料的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="e5058-148">The output path for the collected trace data.</span></span> <span data-ttu-id="e5058-149">如果未指定，則預設為 `trace.nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-149">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e5058-150">從中收集追蹤的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="e5058-150">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="e5058-151">一組名為預先定義的提供者設定，可讓您簡潔地指定常見的追蹤案例。</span><span class="sxs-lookup"><span data-stu-id="e5058-151">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="e5058-152">可用設定檔如下：</span><span class="sxs-lookup"><span data-stu-id="e5058-152">The following profiles are available:</span></span>

 | <span data-ttu-id="e5058-153">設定檔</span><span class="sxs-lookup"><span data-stu-id="e5058-153">Profile</span></span> | <span data-ttu-id="e5058-154">說明</span><span class="sxs-lookup"><span data-stu-id="e5058-154">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="e5058-155">適用于追蹤 CPU 使用量和一般 .NET 執行時間資訊。</span><span class="sxs-lookup"><span data-stu-id="e5058-155">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="e5058-156">如果未指定任何設定檔或提供者，這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="e5058-156">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="e5058-157">追蹤 GC 集合和範例物件配置。</span><span class="sxs-lookup"><span data-stu-id="e5058-157">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="e5058-158">只會以極低的負荷追蹤 GC 集合。</span><span class="sxs-lookup"><span data-stu-id="e5058-158">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="e5058-159">要啟用的提供者清單（以逗號分隔） `EventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-159">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="e5058-160">這些提供者補充了所暗示的任何提供者 `--profile <profile-name>` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-160">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="e5058-161">如果特定提供者有任何不一致的情況，此設定會優先于設定檔中的隱含設定。</span><span class="sxs-lookup"><span data-stu-id="e5058-161">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="e5058-162">這份提供者清單的格式如下：</span><span class="sxs-lookup"><span data-stu-id="e5058-162">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="e5058-163">`Provider` 的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-163">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="e5058-164">`KeyValueArgs` 的格式為： `[key1=value1][;key2=value2]` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-164">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="e5058-165">**`-- <command>` 僅執行 .NET 5.0 的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="e5058-165">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="e5058-166">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5058-166">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="e5058-167">這在診斷程式早期發生的問題（例如啟動效能問題或元件載入器和系結器錯誤）時，可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="e5058-167">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e5058-168">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5058-168">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="e5058-169">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="e5058-169">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="e5058-170">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="e5058-170">dotnet-trace convert</span></span>

<span data-ttu-id="e5058-171">將 `nettrace` 追蹤轉換成替代的格式，以搭配使用替代的追蹤分析工具。</span><span class="sxs-lookup"><span data-stu-id="e5058-171">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5058-172">概要</span><span class="sxs-lookup"><span data-stu-id="e5058-172">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="e5058-173">引數</span><span class="sxs-lookup"><span data-stu-id="e5058-173">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="e5058-174">要轉換的輸入追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="e5058-174">Input trace file to be converted.</span></span> <span data-ttu-id="e5058-175">預設值為 *nettrace*。</span><span class="sxs-lookup"><span data-stu-id="e5058-175">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="e5058-176">選項</span><span class="sxs-lookup"><span data-stu-id="e5058-176">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="e5058-177">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="e5058-177">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="e5058-178">輸出檔案名。</span><span class="sxs-lookup"><span data-stu-id="e5058-178">Output filename.</span></span> <span data-ttu-id="e5058-179">將會新增目標格式的擴充。</span><span class="sxs-lookup"><span data-stu-id="e5058-179">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="e5058-180">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e5058-180">dotnet-trace ps</span></span>

 <span data-ttu-id="e5058-181">列出可從中收集追蹤的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="e5058-181">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5058-182">概要</span><span class="sxs-lookup"><span data-stu-id="e5058-182">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="e5058-183">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="e5058-183">dotnet-trace list-profiles</span></span>

<span data-ttu-id="e5058-184">列出預先建立的追蹤設定檔，其中包含每個設定檔中提供者和篩選器的描述。</span><span class="sxs-lookup"><span data-stu-id="e5058-184">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5058-185">概要</span><span class="sxs-lookup"><span data-stu-id="e5058-185">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="e5058-186">使用 dotnet 收集追蹤</span><span class="sxs-lookup"><span data-stu-id="e5058-186">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="e5058-187">若要使用 `dotnet-trace` 下列內容收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="e5058-187">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="e5058-188">取得 .NET Core 應用程式 (PID) 的處理序識別碼，以從中收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-188">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="e5058-189">例如，在 Windows 上，您可以使用工作管理員或 `tasklist` 命令。</span><span class="sxs-lookup"><span data-stu-id="e5058-189">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="e5058-190">例如，在 Linux 上， `ps` 命令。</span><span class="sxs-lookup"><span data-stu-id="e5058-190">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="e5058-191">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="e5058-191">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="e5058-192">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e5058-192">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="e5058-193">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="e5058-193">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="e5058-194">按下按鍵以停止收集 `<Enter>` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-194">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="e5058-195">`dotnet-trace` 將會完成 *nettrace* 檔案的記錄事件。</span><span class="sxs-lookup"><span data-stu-id="e5058-195">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="e5058-196">啟動子應用程式，並使用 dotnet 從啟動中收集追蹤</span><span class="sxs-lookup"><span data-stu-id="e5058-196">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5058-197">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5058-197">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="e5058-198">有時候，從啟動時收集處理常式的追蹤可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="e5058-198">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="e5058-199">針對執行 .NET 5.0 或更新版本的應用程式，您可以使用 dotnet 來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="e5058-199">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="e5058-200">這會 `hello.exe` 以 `arg1` 和它的 `arg2` 命令列引數啟動，並從其執行時間啟動中收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="e5058-200">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="e5058-201">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="e5058-201">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="e5058-202">您可以按或鍵來停止收集 `<Enter>` 追蹤 `<Ctrl + C>` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-202">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="e5058-203">這樣做也會結束 `hello.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-203">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="e5058-204">透過 `hello.exe` dotnet 追蹤會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 互動。</span><span class="sxs-lookup"><span data-stu-id="e5058-204">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="e5058-205">透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。</span><span class="sxs-lookup"><span data-stu-id="e5058-205">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="e5058-206">如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-206">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="e5058-207">使用診斷埠從應用程式啟動收集追蹤</span><span class="sxs-lookup"><span data-stu-id="e5058-207">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e5058-208">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5058-208">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="e5058-209">診斷埠是新增在 .NET 5 中的新執行時間功能，可讓您從應用程式啟動開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-209">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="e5058-210">若要使用來執行此作業， `dotnet-trace` 您可以使用 `dotnet-trace collect -- <command>` 如上述範例中所述，或使用 `--diagnostic-port` 選項。</span><span class="sxs-lookup"><span data-stu-id="e5058-210">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="e5058-211">使用 `dotnet-trace <collect|monitor> -- <command>` 以子進程的形式啟動應用程式，是從啟動時快速追蹤它的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="e5058-211">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="e5058-212">但是，當您想要更精確地控制追蹤的應用程式存留期 (例如，只在前10分鐘內監視應用程式並繼續執行) 或者，如果您需要使用 CLI 與應用程式互動，使用 `--diagnostic-port` 選項可讓您控制受監視的目標應用程式和 `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-212">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="e5058-213">下列命令會建立 `dotnet-trace` 名為的診斷通訊端 `myport.sock` ，並等候連接。</span><span class="sxs-lookup"><span data-stu-id="e5058-213">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="e5058-214">輸出：</span><span class="sxs-lookup"><span data-stu-id="e5058-214">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="e5058-215">在個別的主控台中，啟動目標應用程式，並將環境變數 `DOTNET_DiagnosticPorts` 設為輸出中的值 `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-215">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="e5058-216">如此一 `dotnet-trace` 來，就可以開始追蹤 `my-dotnet-app` ：</span><span class="sxs-lookup"><span data-stu-id="e5058-216">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="e5058-217">啟動您的應用程式可能 `dotnet run` 會造成問題，因為 DOTNET CLI 可能會產生許多不是您應用程式的子進程，而且它們可以在您的應用 `dotnet-trace` 程式之前連線，讓您的應用程式在執行時間暫停。</span><span class="sxs-lookup"><span data-stu-id="e5058-217">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="e5058-218">建議您直接使用應用程式的獨立版本，或用 `dotnet exec` 來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5058-218">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="e5058-219">查看從 dotnet 捕捉的追蹤</span><span class="sxs-lookup"><span data-stu-id="e5058-219">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="e5058-220">在 Windows 中，可以在 [PerfView](https://github.com/microsoft/perfview)上查看 *nettrace* 檔案以供分析：對於在其他平臺上收集的追蹤，追蹤檔案可以移至要在 PerfView 上查看的 Windows 機器。</span><span class="sxs-lookup"><span data-stu-id="e5058-220">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="e5058-221">在 Linux 上，您可以藉由將的輸出格式變更 `dotnet-trace` 為來查看追蹤 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-221">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="e5058-222">您可以使用選項來變更輸出檔案格式 `-f|--format` - `-f speedscope` 將會 `dotnet-trace` 產生檔案 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-222">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="e5058-223">您可以選擇 `nettrace` (預設選項) 和 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-223">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="e5058-224">`Speedscope` 您可以在中開啟檔案 <https://www.speedscope.app> 。</span><span class="sxs-lookup"><span data-stu-id="e5058-224">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="e5058-225">.NET Core 執行時間會以格式產生追蹤 `nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="e5058-225">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="e5058-226">追蹤會轉換成 speedscope (如果在追蹤完成後指定) 。</span><span class="sxs-lookup"><span data-stu-id="e5058-226">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="e5058-227">因為某些轉換可能會導致資料遺失，所以 `nettrace` 已轉換的檔案旁邊會保留原始檔案。</span><span class="sxs-lookup"><span data-stu-id="e5058-227">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="e5058-228">使用 dotnet 來收集一段時間內的計數器值</span><span class="sxs-lookup"><span data-stu-id="e5058-228">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="e5058-229">`dotnet-trace` 可以：</span><span class="sxs-lookup"><span data-stu-id="e5058-229">`dotnet-trace` can:</span></span>

* <span data-ttu-id="e5058-230">用於 `EventCounter` 效能敏感性環境中的基本健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="e5058-230">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="e5058-231">例如，在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="e5058-231">For example, in production.</span></span>
* <span data-ttu-id="e5058-232">收集追蹤，讓它們不需要即時觀看。</span><span class="sxs-lookup"><span data-stu-id="e5058-232">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="e5058-233">例如，若要收集執行時間效能計數器值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="e5058-233">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="e5058-234">上述命令會告知執行時間計數器每秒回報一次，以進行輕量健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="e5058-234">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="e5058-235">以 `EventCounterIntervalSec=1` 較高的值取代 (例如，60) 可讓您以較少的資料細微性收集計數器資料中較小的追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-235">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="e5058-236">下列命令可減少額外負荷和追蹤大小，而不是前一個：</span><span class="sxs-lookup"><span data-stu-id="e5058-236">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="e5058-237">上述命令會停用運行時間事件和 managed stack profiler。</span><span class="sxs-lookup"><span data-stu-id="e5058-237">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="e5058-238">.NET 提供者</span><span class="sxs-lookup"><span data-stu-id="e5058-238">.NET Providers</span></span>

<span data-ttu-id="e5058-239">.NET Core 執行時間支援下列 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="e5058-239">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="e5058-240">.NET Core 會使用相同的關鍵字來啟用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5058-240">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="e5058-241">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="e5058-241">Provider name</span></span>                            | <span data-ttu-id="e5058-242">資訊</span><span class="sxs-lookup"><span data-stu-id="e5058-242">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="e5058-243">執行階段提供者</span><span class="sxs-lookup"><span data-stu-id="e5058-243">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="e5058-244">CLR 執行時間關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5058-244">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="e5058-245">取消提供者</span><span class="sxs-lookup"><span data-stu-id="e5058-245">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="e5058-246">CLR 取消關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5058-246">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="e5058-247">啟用範例 profiler。</span><span class="sxs-lookup"><span data-stu-id="e5058-247">Enables the sample profiler.</span></span> |
