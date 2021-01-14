---
title: dotnet-追蹤診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet 追蹤 CLI 工具，以使用 .NET EventPipe 來收集執行中進程的 .NET 追蹤，而不使用原生 profiler。
ms.date: 11/17/2020
ms.openlocfilehash: 93698882e94f58eda84abebc277e1eacfe22a3da
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189695"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="288ae-103">dotnet-追蹤效能分析公用程式</span><span class="sxs-lookup"><span data-stu-id="288ae-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="288ae-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="288ae-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="288ae-105">安裝</span><span class="sxs-lookup"><span data-stu-id="288ae-105">Install</span></span>

<span data-ttu-id="288ae-106">有兩種方式可以下載和安裝 `dotnet-trace` ：</span><span class="sxs-lookup"><span data-stu-id="288ae-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="288ae-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="288ae-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="288ae-108">若要安裝 `dotnet-trace` [NuGet 套件](https://www.nuget.org/packages/dotnet-trace)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="288ae-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="288ae-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="288ae-109">**Direct download:**</span></span>

  <span data-ttu-id="288ae-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="288ae-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="288ae-111">OS</span><span class="sxs-lookup"><span data-stu-id="288ae-111">OS</span></span>  | <span data-ttu-id="288ae-112">平台</span><span class="sxs-lookup"><span data-stu-id="288ae-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="288ae-113">Windows</span><span class="sxs-lookup"><span data-stu-id="288ae-113">Windows</span></span> | <span data-ttu-id="288ae-114">[x86](https://aka.ms/dotnet-trace/win-x86) \|[x64](https://aka.ms/dotnet-trace/win-x64) \|[arm](https://aka.ms/dotnet-trace/win-arm) \|[arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="288ae-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="288ae-115">macOS</span><span class="sxs-lookup"><span data-stu-id="288ae-115">macOS</span></span>   | [<span data-ttu-id="288ae-116">x64</span><span class="sxs-lookup"><span data-stu-id="288ae-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="288ae-117">Linux</span><span class="sxs-lookup"><span data-stu-id="288ae-117">Linux</span></span>   | <span data-ttu-id="288ae-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \|[arm](https://aka.ms/dotnet-trace/linux-arm) \|[arm64](https://aka.ms/dotnet-trace/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="288ae-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="288ae-119">若要 `dotnet-trace` 在 x86 應用程式上使用，您需要工具的對應 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="288ae-119">To use `dotnet-trace` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="288ae-120">概要</span><span class="sxs-lookup"><span data-stu-id="288ae-120">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="288ae-121">Description</span><span class="sxs-lookup"><span data-stu-id="288ae-121">Description</span></span>

<span data-ttu-id="288ae-122">`dotnet-trace`工具：</span><span class="sxs-lookup"><span data-stu-id="288ae-122">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="288ae-123">是跨平臺 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="288ae-123">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="288ae-124">在不使用原生分析工具的情況下，啟用正在執行之進程的 .NET Core 追蹤收集。</span><span class="sxs-lookup"><span data-stu-id="288ae-124">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="288ae-125">是以 [`EventPipe`](./eventpipe.md) .Net Core 執行時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="288ae-125">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="288ae-126">在 Windows、Linux 或 macOS 上提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="288ae-126">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="288ae-127">選項</span><span class="sxs-lookup"><span data-stu-id="288ae-127">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="288ae-128">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="288ae-128">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="288ae-129">顯示 dotnet 追蹤公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="288ae-129">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="288ae-130">命令</span><span class="sxs-lookup"><span data-stu-id="288ae-130">Commands</span></span>

| <span data-ttu-id="288ae-131">命令</span><span class="sxs-lookup"><span data-stu-id="288ae-131">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="288ae-132">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="288ae-132">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="288ae-133">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="288ae-133">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="288ae-134">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="288ae-134">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="288ae-135">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="288ae-135">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="288ae-136">dotnet-追蹤收集</span><span class="sxs-lookup"><span data-stu-id="288ae-136">dotnet-trace collect</span></span>

<span data-ttu-id="288ae-137">從正在執行的進程收集診斷追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-137">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="288ae-138">概要</span><span class="sxs-lookup"><span data-stu-id="288ae-138">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="288ae-139">選項</span><span class="sxs-lookup"><span data-stu-id="288ae-139">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="288ae-140">設定記憶體中的圓形緩衝區大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="288ae-140">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="288ae-141">預設值為 256 MB。</span><span class="sxs-lookup"><span data-stu-id="288ae-141">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="288ae-142">要發出之 CLR 事件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="288ae-142">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="288ae-143">要啟用以符號分隔的 CLR 執行時間提供者關鍵字清單 `+` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-143">A list of CLR runtime provider keywords to enable separated by `+` signs.</span></span> <span data-ttu-id="288ae-144">這是簡單的對應，可讓您透過字串別名（而非其十六進位值）指定事件關鍵字。</span><span class="sxs-lookup"><span data-stu-id="288ae-144">This is a simple mapping that lets you specify event keywords via string aliases rather than their hex values.</span></span> <span data-ttu-id="288ae-145">例如，會 `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` 要求與相同的一組事件 `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-145">For example, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` requests the same set of events as `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span></span> <span data-ttu-id="288ae-146">下表顯示可用關鍵字的清單：</span><span class="sxs-lookup"><span data-stu-id="288ae-146">The table below shows the list of available keywords:</span></span>

  | <span data-ttu-id="288ae-147">關鍵字字串別名</span><span class="sxs-lookup"><span data-stu-id="288ae-147">Keyword String Alias</span></span> | <span data-ttu-id="288ae-148">關鍵字十六進位值</span><span class="sxs-lookup"><span data-stu-id="288ae-148">Keyword Hex Value</span></span> |
  | ------------ | ------------------- |
  | `gc` | `0x1` |
  | `gchandle` | `0x2` |
  | `fusion` | `0x4` |
  | `loader` | `0x8` |
  | `jit` | `0x10` |
  | `ngen` | `0x20` |
  | `startenumeration` | `0x40` |
  | `endenumeration` | `0x80` |
  | `security` | `0x400` |
  | `appdomainresourcemanagement` | `0x800` |
  | `jittracing` | `0x1000` |
  | `interop` | `0x2000` |
  | `contention` | `0x4000` |
  | `exception` | `0x8000` |
  | `threading` | `0x10000` |
  | `jittedmethodiltonativemap` | `0x20000` |
  | `overrideandsuppressngenevents` | `0x40000` |
  | `type` | `0x80000` |
  | `gcheapdump` | `0x100000` |
  | `gcsampledobjectallocationhigh` | `0x200000` |
  | `gcheapsurvivalandmovement` | `0x400000` |
  | `gcheapcollect` | `0x800000` |
  | `gcheapandtypenames` | `0x1000000` |
  | `gcsampledobjectallocationlow` | `0x2000000` |
  | `perftrack` | `0x20000000` |
  | `stack` | `0x40000000` |
  | `threadtransfer` | `0x80000000` |
  | `debugger` | `0x100000000` |
  | `monitoring` | `0x200000000` |
  | `codesymbols` | `0x400000000` |
  | `eventsource` | `0x800000000` |
  | `compilation` | `0x1000000000` |
  | `compilationdiagnostic` | `0x2000000000` |
  | `methoddiagnostic` | `0x4000000000` |
  | `typediagnostic` | `0x8000000000` |

  <span data-ttu-id="288ae-149">您可以進一步瞭解有關 CLR 提供者的詳細資訊，請參閱 [.net 執行時間提供者參考檔](../../fundamentals/diagnostics/runtime-events.md)。</span><span class="sxs-lookup"><span data-stu-id="288ae-149">You can read about the CLR provider more in detail on the [.NET runtime provider reference documentation](../../fundamentals/diagnostics/runtime-events.md).</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="288ae-150">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="288ae-150">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="288ae-151">預設為 `NetTrace`。</span><span class="sxs-lookup"><span data-stu-id="288ae-151">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="288ae-152">要從中收集追蹤的進程名稱。</span><span class="sxs-lookup"><span data-stu-id="288ae-152">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="288ae-153">要建立之診斷埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="288ae-153">The name of the diagnostic port to create.</span></span> <span data-ttu-id="288ae-154">請參閱 [使用診斷埠從應用程式啟動收集追蹤](#use-diagnostic-port-to-collect-a-trace-from-app-startup) ，以瞭解如何使用此選項從應用程式啟動收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-154">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="288ae-155">所收集之追蹤資料的輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="288ae-155">The output path for the collected trace data.</span></span> <span data-ttu-id="288ae-156">如果未指定，則預設為 `trace.nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-156">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="288ae-157">從中收集追蹤的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="288ae-157">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="288ae-158">一組名為預先定義的提供者設定，可讓您簡潔地指定常見的追蹤案例。</span><span class="sxs-lookup"><span data-stu-id="288ae-158">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="288ae-159">可用設定檔如下：</span><span class="sxs-lookup"><span data-stu-id="288ae-159">The following profiles are available:</span></span>

 | <span data-ttu-id="288ae-160">設定檔</span><span class="sxs-lookup"><span data-stu-id="288ae-160">Profile</span></span> | <span data-ttu-id="288ae-161">說明</span><span class="sxs-lookup"><span data-stu-id="288ae-161">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="288ae-162">適用于追蹤 CPU 使用量和一般 .NET 執行時間資訊。</span><span class="sxs-lookup"><span data-stu-id="288ae-162">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="288ae-163">如果未指定任何設定檔或提供者，這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="288ae-163">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="288ae-164">追蹤 GC 集合和範例物件配置。</span><span class="sxs-lookup"><span data-stu-id="288ae-164">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="288ae-165">只會以極低的負荷追蹤 GC 集合。</span><span class="sxs-lookup"><span data-stu-id="288ae-165">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="288ae-166">要啟用的提供者清單（以逗號分隔） `EventPipe` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-166">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="288ae-167">這些提供者補充了所暗示的任何提供者 `--profile <profile-name>` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-167">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="288ae-168">如果特定提供者有任何不一致的情況，此設定會優先于設定檔中的隱含設定。</span><span class="sxs-lookup"><span data-stu-id="288ae-168">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="288ae-169">這份提供者清單的格式如下：</span><span class="sxs-lookup"><span data-stu-id="288ae-169">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="288ae-170">`Provider` 的格式為： `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-170">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="288ae-171">`KeyValueArgs` 的格式為： `[key1=value1][;key2=value2]` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-171">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="288ae-172">**`-- <command>` 僅執行 .NET 5.0 的目標應用程式 ()**</span><span class="sxs-lookup"><span data-stu-id="288ae-172">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="288ae-173">在收集設定參數之後，使用者可以在後面附加一個 `--` 命令，以啟動至少包含5.0 執行時間的 .net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="288ae-173">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="288ae-174">這在診斷程式早期發生的問題（例如啟動效能問題或元件載入器和系結器錯誤）時，可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="288ae-174">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="288ae-175">使用這個選項會監視第一個與工具通訊的 .NET 5.0 進程，這表示如果您的命令會啟動多個 .NET 應用程式，則只會收集第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="288ae-175">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="288ae-176">因此，建議您在獨立應用程式上使用此選項，或使用 `dotnet exec <app.dll>` 選項。</span><span class="sxs-lookup"><span data-stu-id="288ae-176">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-177">針對大型應用程式，停止追蹤可能需要很長的時間 (最多幾分鐘的時間) 。</span><span class="sxs-lookup"><span data-stu-id="288ae-177">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="288ae-178">執行時間必須針對追蹤中所捕捉的所有 managed 程式碼，傳送類型快取。</span><span class="sxs-lookup"><span data-stu-id="288ae-178">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-179">在 Linux 和 macOS 上，此命令會預期目標應用程式，並 `dotnet-trace` 共用相同的 `TMPDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="288ae-179">On Linux and macOS, this command expects the target application and `dotnet-trace` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="288ae-180">否則，此命令將會超時。</span><span class="sxs-lookup"><span data-stu-id="288ae-180">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-181">若要使用收集追蹤 `dotnet-trace` ，必須以執行目標進程的使用者和根使用者的相同使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="288ae-181">To collect a trace using `dotnet-trace`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="288ae-182">否則，此工具將無法建立與目標進程的連接。</span><span class="sxs-lookup"><span data-stu-id="288ae-182">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="288ae-183">dotnet-追蹤轉換</span><span class="sxs-lookup"><span data-stu-id="288ae-183">dotnet-trace convert</span></span>

<span data-ttu-id="288ae-184">將 `nettrace` 追蹤轉換成替代的格式，以搭配使用替代的追蹤分析工具。</span><span class="sxs-lookup"><span data-stu-id="288ae-184">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="288ae-185">概要</span><span class="sxs-lookup"><span data-stu-id="288ae-185">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="288ae-186">引數</span><span class="sxs-lookup"><span data-stu-id="288ae-186">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="288ae-187">要轉換的輸入追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="288ae-187">Input trace file to be converted.</span></span> <span data-ttu-id="288ae-188">預設值為 *nettrace*。</span><span class="sxs-lookup"><span data-stu-id="288ae-188">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="288ae-189">選項</span><span class="sxs-lookup"><span data-stu-id="288ae-189">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="288ae-190">設定追蹤檔案轉換的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="288ae-190">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="288ae-191">輸出檔案名。</span><span class="sxs-lookup"><span data-stu-id="288ae-191">Output filename.</span></span> <span data-ttu-id="288ae-192">將會新增目標格式的擴充。</span><span class="sxs-lookup"><span data-stu-id="288ae-192">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-193">將檔案轉換 `nettrace` 成或檔案無法 `chromium` `speedscope` 復原。</span><span class="sxs-lookup"><span data-stu-id="288ae-193">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="288ae-194">`speedscope` 和檔案 `chromium` 沒有重建檔案所需的所有資訊 `nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-194">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="288ae-195">不過，此 `convert` 命令會保留原始檔案 `nettrace` ，因此，如果您打算在未來開啟此檔案，請勿刪除此檔案。</span><span class="sxs-lookup"><span data-stu-id="288ae-195">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="288ae-196">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="288ae-196">dotnet-trace ps</span></span>

 <span data-ttu-id="288ae-197">列出可從中收集追蹤的 dotnet 進程。</span><span class="sxs-lookup"><span data-stu-id="288ae-197">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="288ae-198">概要</span><span class="sxs-lookup"><span data-stu-id="288ae-198">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="288ae-199">dotnet-追蹤清單-設定檔</span><span class="sxs-lookup"><span data-stu-id="288ae-199">dotnet-trace list-profiles</span></span>

<span data-ttu-id="288ae-200">列出預先建立的追蹤設定檔，其中包含每個設定檔中提供者和篩選器的描述。</span><span class="sxs-lookup"><span data-stu-id="288ae-200">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="288ae-201">概要</span><span class="sxs-lookup"><span data-stu-id="288ae-201">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="288ae-202">使用 dotnet 收集追蹤</span><span class="sxs-lookup"><span data-stu-id="288ae-202">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="288ae-203">若要使用 `dotnet-trace` 下列內容收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="288ae-203">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="288ae-204">取得 .NET Core 應用程式 (PID) 的處理序識別碼，以從中收集追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-204">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="288ae-205">例如，在 Windows 上，您可以使用工作管理員或 `tasklist` 命令。</span><span class="sxs-lookup"><span data-stu-id="288ae-205">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="288ae-206">例如，在 Linux 上， `ps` 命令。</span><span class="sxs-lookup"><span data-stu-id="288ae-206">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="288ae-207">dotnet-追蹤 ps</span><span class="sxs-lookup"><span data-stu-id="288ae-207">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="288ae-208">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="288ae-208">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="288ae-209">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="288ae-209">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="288ae-210">按下按鍵以停止收集 `<Enter>` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-210">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="288ae-211">`dotnet-trace` 將會完成 *nettrace* 檔案的記錄事件。</span><span class="sxs-lookup"><span data-stu-id="288ae-211">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="288ae-212">啟動子應用程式，並使用 dotnet 從啟動中收集追蹤</span><span class="sxs-lookup"><span data-stu-id="288ae-212">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="288ae-213">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="288ae-213">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="288ae-214">有時候，從啟動時收集處理常式的追蹤可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="288ae-214">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="288ae-215">針對執行 .NET 5.0 或更新版本的應用程式，您可以使用 dotnet 來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="288ae-215">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="288ae-216">這會 `hello.exe` 以 `arg1` 和它的 `arg2` 命令列引數啟動，並從其執行時間啟動中收集追蹤：</span><span class="sxs-lookup"><span data-stu-id="288ae-216">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="288ae-217">上述命令會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="288ae-217">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="288ae-218">您可以按或鍵來停止收集 `<Enter>` 追蹤 `<Ctrl + C>` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-218">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="288ae-219">這樣做也會結束 `hello.exe` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-219">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-220">透過 `hello.exe` dotnet 追蹤會將其輸入/輸出重新導向，而您將無法與其 stdin/stdout 互動。</span><span class="sxs-lookup"><span data-stu-id="288ae-220">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="288ae-221">透過 CTRL + C 或 SIGTERM 結束工具會安全地結束工具和子進程。</span><span class="sxs-lookup"><span data-stu-id="288ae-221">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="288ae-222">如果子進程在工具之前結束，則工具也會結束，而且應該安全地查看追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-222">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="288ae-223">使用診斷埠從應用程式啟動收集追蹤</span><span class="sxs-lookup"><span data-stu-id="288ae-223">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="288ae-224">這僅適用于執行 .NET 5.0 或更新版本的應用程式。</span><span class="sxs-lookup"><span data-stu-id="288ae-224">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="288ae-225">診斷埠是新增在 .NET 5 中的新執行時間功能，可讓您從應用程式啟動開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-225">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="288ae-226">若要使用來執行此作業， `dotnet-trace` 您可以使用 `dotnet-trace collect -- <command>` 如上述範例中所述，或使用 `--diagnostic-port` 選項。</span><span class="sxs-lookup"><span data-stu-id="288ae-226">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="288ae-227">使用 `dotnet-trace <collect|monitor> -- <command>` 以子進程的形式啟動應用程式，是從啟動時快速追蹤它的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="288ae-227">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="288ae-228">但是，當您想要更精確地控制追蹤的應用程式存留期 (例如，只在前10分鐘內監視應用程式並繼續執行) 或者，如果您需要使用 CLI 與應用程式互動，使用 `--diagnostic-port` 選項可讓您控制受監視的目標應用程式和 `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-228">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="288ae-229">下列命令會建立 `dotnet-trace` 名為的診斷通訊端 `myport.sock` ，並等候連接。</span><span class="sxs-lookup"><span data-stu-id="288ae-229">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="288ae-230">輸出：</span><span class="sxs-lookup"><span data-stu-id="288ae-230">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="288ae-231">在個別的主控台中，啟動目標應用程式，並將環境變數 `DOTNET_DiagnosticPorts` 設為輸出中的值 `dotnet-trace` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-231">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="288ae-232">如此一 `dotnet-trace` 來，就可以開始追蹤 `my-dotnet-app` ：</span><span class="sxs-lookup"><span data-stu-id="288ae-232">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="288ae-233">啟動您的應用程式可能 `dotnet run` 會造成問題，因為 DOTNET CLI 可能會產生許多不是您應用程式的子進程，而且它們可以在您的應用 `dotnet-trace` 程式之前連線，讓您的應用程式在執行時間暫停。</span><span class="sxs-lookup"><span data-stu-id="288ae-233">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="288ae-234">建議您直接使用應用程式的獨立版本，或用 `dotnet exec` 來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="288ae-234">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="288ae-235">查看從 dotnet 捕捉的追蹤</span><span class="sxs-lookup"><span data-stu-id="288ae-235">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="288ae-236">在 Windows 中，可以在 [PerfView](https://github.com/microsoft/perfview)上查看 *nettrace* 檔案以供分析：對於在其他平臺上收集的追蹤，追蹤檔案可以移至要在 PerfView 上查看的 Windows 機器。</span><span class="sxs-lookup"><span data-stu-id="288ae-236">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="288ae-237">在 Linux 上，您可以藉由將的輸出格式變更 `dotnet-trace` 為來查看追蹤 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-237">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="288ae-238">您可以使用選項來變更輸出檔案格式 `-f|--format` - `-f speedscope` 將會 `dotnet-trace` 產生檔案 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-238">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="288ae-239">您可以選擇 `nettrace` (預設選項) 和 `speedscope` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-239">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="288ae-240">`Speedscope` 您可以在中開啟檔案 <https://www.speedscope.app> 。</span><span class="sxs-lookup"><span data-stu-id="288ae-240">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="288ae-241">.NET Core 執行時間會以格式產生追蹤 `nettrace` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-241">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="288ae-242">追蹤會轉換成 speedscope (如果在追蹤完成後指定) 。</span><span class="sxs-lookup"><span data-stu-id="288ae-242">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="288ae-243">因為某些轉換可能會導致資料遺失，所以 `nettrace` 已轉換的檔案旁邊會保留原始檔案。</span><span class="sxs-lookup"><span data-stu-id="288ae-243">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="288ae-244">使用 dotnet 來收集一段時間內的計數器值</span><span class="sxs-lookup"><span data-stu-id="288ae-244">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="288ae-245">`dotnet-trace` 可以：</span><span class="sxs-lookup"><span data-stu-id="288ae-245">`dotnet-trace` can:</span></span>

* <span data-ttu-id="288ae-246">用於 `EventCounter` 效能敏感性環境中的基本健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="288ae-246">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="288ae-247">例如，在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="288ae-247">For example, in production.</span></span>
* <span data-ttu-id="288ae-248">收集追蹤，讓它們不需要即時觀看。</span><span class="sxs-lookup"><span data-stu-id="288ae-248">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="288ae-249">例如，若要收集執行時間效能計數器值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="288ae-249">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="288ae-250">上述命令會告知執行時間計數器每秒回報一次，以進行輕量健康情況監視。</span><span class="sxs-lookup"><span data-stu-id="288ae-250">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="288ae-251">以 `EventCounterIntervalSec=1` 較高的值取代 (例如，60) 可讓您以較少的資料細微性收集計數器資料中較小的追蹤。</span><span class="sxs-lookup"><span data-stu-id="288ae-251">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="288ae-252">下列命令可減少額外負荷和追蹤大小，而不是前一個：</span><span class="sxs-lookup"><span data-stu-id="288ae-252">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="288ae-253">上述命令會停用運行時間事件和 managed stack profiler。</span><span class="sxs-lookup"><span data-stu-id="288ae-253">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="288ae-254">使用 .rsp 檔案以避免輸入較長的命令</span><span class="sxs-lookup"><span data-stu-id="288ae-254">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="288ae-255">您可以 `dotnet-trace` 使用 `.rsp` 包含要傳遞之引數的檔案來啟動。</span><span class="sxs-lookup"><span data-stu-id="288ae-255">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="288ae-256">當啟用的提供者需要冗長的引數，或使用會去除字元的 shell 環境時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="288ae-256">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="288ae-257">例如，下列提供者在您每次想要進行追蹤時，可能會很麻煩地輸入：</span><span class="sxs-lookup"><span data-stu-id="288ae-257">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="288ae-258">此外，上述範例會包含 `"` 做為引數的一部分。</span><span class="sxs-lookup"><span data-stu-id="288ae-258">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="288ae-259">因為每個 shell 都不會平均處理引號，所以使用不同的 shell 時，您可能會遇到各種問題。</span><span class="sxs-lookup"><span data-stu-id="288ae-259">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="288ae-260">例如，在中輸入的命令與 `zsh` 中的命令不同 `cmd` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-260">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="288ae-261">您可以將下列文字儲存到名為的檔案中，而不是每次都輸入此名稱 `myprofile.rsp` 。</span><span class="sxs-lookup"><span data-stu-id="288ae-261">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="288ae-262">儲存之後 `myprofile.rsp` ，您可以 `dotnet-trace` 使用下列命令來啟動此設定：</span><span class="sxs-lookup"><span data-stu-id="288ae-262">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="288ae-263">另請參閱</span><span class="sxs-lookup"><span data-stu-id="288ae-263">See also</span></span>

- [<span data-ttu-id="288ae-264">來自 .NET 的知名事件提供者</span><span class="sxs-lookup"><span data-stu-id="288ae-264">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
