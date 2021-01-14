---
title: dotnet-傾印診斷工具-.NET CLI
description: 瞭解如何在不使用任何原生偵錯工具的情況下，安裝和使用 dotnet 傾印 CLI 工具來收集和分析 Windows 和 Linux 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: 84b3796f4ee92880e6d432df606a6addfd2471b0
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189800"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="4e675-103">傾印收集和分析公用程式 (dotnet-傾印) </span><span class="sxs-lookup"><span data-stu-id="4e675-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="4e675-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="4e675-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="4e675-105">`dotnet-dump` 只有 .NET 5.0 和更新版本才支援 macOS。</span><span class="sxs-lookup"><span data-stu-id="4e675-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="4e675-106">安裝</span><span class="sxs-lookup"><span data-stu-id="4e675-106">Install</span></span>

<span data-ttu-id="4e675-107">有兩種方式可以下載和安裝 `dotnet-dump` ：</span><span class="sxs-lookup"><span data-stu-id="4e675-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="4e675-108">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="4e675-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="4e675-109">若要安裝 `dotnet-dump` [NuGet 套件](https://www.nuget.org/packages/dotnet-dump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="4e675-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="4e675-110">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="4e675-110">**Direct download:**</span></span>

  <span data-ttu-id="4e675-111">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="4e675-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="4e675-112">OS</span><span class="sxs-lookup"><span data-stu-id="4e675-112">OS</span></span>  | <span data-ttu-id="4e675-113">平台</span><span class="sxs-lookup"><span data-stu-id="4e675-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="4e675-114">Windows</span><span class="sxs-lookup"><span data-stu-id="4e675-114">Windows</span></span> | <span data-ttu-id="4e675-115">[x86](https://aka.ms/dotnet-dump/win-x86) \|[x64](https://aka.ms/dotnet-dump/win-x64) \|[arm](https://aka.ms/dotnet-dump/win-arm) \|[arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="4e675-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="4e675-116">macOS</span><span class="sxs-lookup"><span data-stu-id="4e675-116">macOS</span></span>   | [<span data-ttu-id="4e675-117">x64</span><span class="sxs-lookup"><span data-stu-id="4e675-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="4e675-118">Linux</span><span class="sxs-lookup"><span data-stu-id="4e675-118">Linux</span></span>   | <span data-ttu-id="4e675-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \|[arm](https://aka.ms/dotnet-dump/linux-arm) \|[arm64](https://aka.ms/dotnet-dump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="4e675-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="4e675-120">若要 `dotnet-dump` 在 x86 應用程式上使用，您需要工具的對應 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="4e675-120">To use `dotnet-dump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4e675-121">概要</span><span class="sxs-lookup"><span data-stu-id="4e675-121">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="4e675-122">Description</span><span class="sxs-lookup"><span data-stu-id="4e675-122">Description</span></span>

<span data-ttu-id="4e675-123">`dotnet-dump`全域工具可收集和分析 Windows 和 linux 傾印，而不需要任何與 Linux 相關的原生偵錯工具 `lldb` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-123">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="4e675-124">這項工具在 Alpine Linux 等平臺上很重要，因為無法使用完整的工作 `lldb` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-124">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="4e675-125">此 `dotnet-dump` 工具可讓您執行 SOS 命令來分析損毀和垃圾收集行程 (GC) ，但它不是原生偵錯工具，因此不支援顯示原生堆疊框架之類的動作。</span><span class="sxs-lookup"><span data-stu-id="4e675-125">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="4e675-126">選項</span><span class="sxs-lookup"><span data-stu-id="4e675-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="4e675-127">顯示 dotnet 傾印公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="4e675-127">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4e675-128">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="4e675-128">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="4e675-129">命令</span><span class="sxs-lookup"><span data-stu-id="4e675-129">Commands</span></span>

| <span data-ttu-id="4e675-130">命令</span><span class="sxs-lookup"><span data-stu-id="4e675-130">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="4e675-131">dotnet-傾印收集</span><span class="sxs-lookup"><span data-stu-id="4e675-131">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="4e675-132">dotnet-傾印分析</span><span class="sxs-lookup"><span data-stu-id="4e675-132">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="4e675-133">dotnet-傾印收集</span><span class="sxs-lookup"><span data-stu-id="4e675-133">dotnet-dump collect</span></span>

<span data-ttu-id="4e675-134">從進程中捕獲傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-134">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e675-135">概要</span><span class="sxs-lookup"><span data-stu-id="4e675-135">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="4e675-136">選項</span><span class="sxs-lookup"><span data-stu-id="4e675-136">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="4e675-137">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="4e675-137">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="4e675-138">指定要從中收集傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="4e675-138">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="4e675-139">指定要從中收集傾印之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e675-139">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="4e675-140">指定傾印類型，以決定從進程收集的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="4e675-140">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="4e675-141">有三種類型：</span><span class="sxs-lookup"><span data-stu-id="4e675-141">There are three types:</span></span>

  - <span data-ttu-id="4e675-142">`Full` -最大傾印，包含模組映射在內的所有記憶體。</span><span class="sxs-lookup"><span data-stu-id="4e675-142">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="4e675-143">`Heap` -包含模組清單、執行緒清單、所有堆疊、例外狀況資訊、處理資訊，以及所有記憶體（除了對應的影像以外）的大型較完整傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-143">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="4e675-144">`Mini` -包含模組清單、執行緒清單、例外狀況資訊和所有堆疊的小型傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-144">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="4e675-145">如果未指定， `Full` 則為預設值。</span><span class="sxs-lookup"><span data-stu-id="4e675-145">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="4e675-146">應寫入所收集傾印的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4e675-146">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="4e675-147">如果未指定：</span><span class="sxs-lookup"><span data-stu-id="4e675-147">If not specified:</span></span>

  - <span data-ttu-id="4e675-148">預設為在 Windows 上 *dump_YYYYMMDD_HHMMSS dmp* 。</span><span class="sxs-lookup"><span data-stu-id="4e675-148">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="4e675-149">預設為 Linux 上的 *./core_YYYYMMDD_HHMMSS。*</span><span class="sxs-lookup"><span data-stu-id="4e675-149">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="4e675-150">YYYYMMDD 是年/月/日，而 HHMMSS 是小時/分鐘/秒。</span><span class="sxs-lookup"><span data-stu-id="4e675-150">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="4e675-151">啟用傾印收集診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="4e675-151">Enables dump collection diagnostic logging.</span></span>

> [!NOTE]
> <span data-ttu-id="4e675-152">在 Linux 和 macOS 上，此命令會預期目標應用程式，並 `dotnet-dump` 共用相同的 `TMPDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e675-152">On Linux and macOS, this command expects the target application and `dotnet-dump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="4e675-153">否則，此命令將會超時。</span><span class="sxs-lookup"><span data-stu-id="4e675-153">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="4e675-154">若要使用收集傾印 `dotnet-dump` ，必須以執行目標進程的使用者和根使用者的相同使用者來執行。</span><span class="sxs-lookup"><span data-stu-id="4e675-154">To collect a dump using `dotnet-dump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="4e675-155">否則，此工具將無法建立與目標進程的連接。</span><span class="sxs-lookup"><span data-stu-id="4e675-155">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="4e675-156">dotnet-傾印分析</span><span class="sxs-lookup"><span data-stu-id="4e675-156">dotnet-dump analyze</span></span>

<span data-ttu-id="4e675-157">啟動互動式 shell 以探索傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-157">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="4e675-158">Shell 接受各種 [SOS 命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="4e675-158">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e675-159">概要</span><span class="sxs-lookup"><span data-stu-id="4e675-159">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="4e675-160">引數</span><span class="sxs-lookup"><span data-stu-id="4e675-160">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="4e675-161">指定要分析之傾印檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e675-161">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="4e675-162">選項</span><span class="sxs-lookup"><span data-stu-id="4e675-162">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="4e675-163">指定在啟動時要在 shell 中執行的 [命令](#analyze-sos-commands) 。</span><span class="sxs-lookup"><span data-stu-id="4e675-163">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="4e675-164">分析 SOS 命令</span><span class="sxs-lookup"><span data-stu-id="4e675-164">Analyze SOS commands</span></span>

| <span data-ttu-id="4e675-165">命令</span><span class="sxs-lookup"><span data-stu-id="4e675-165">Command</span></span>                             | <span data-ttu-id="4e675-166">函式</span><span class="sxs-lookup"><span data-stu-id="4e675-166">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="4e675-167">顯示所有可用的命令</span><span class="sxs-lookup"><span data-stu-id="4e675-167">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="4e675-168">顯示指定的命令。</span><span class="sxs-lookup"><span data-stu-id="4e675-168">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="4e675-169">結束互動模式。</span><span class="sxs-lookup"><span data-stu-id="4e675-169">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="4e675-170">僅提供 Managed 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e675-170">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="4e675-171">列出正在執行的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="4e675-171">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="4e675-172">顯示垃圾收集堆積上的非同步狀態機器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-172">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="4e675-173">顯示位於指定位址之元件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4e675-173">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="4e675-174">顯示指定位址之結構的相關資訊 `EEClass` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-174">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="4e675-175">顯示指定位址之委派的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-175">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="4e675-176">顯示指定網域內所有 Appdomain 和所有元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-176">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="4e675-177">顯示垃圾收集堆積的相關資訊，以及物件的集合統計資料。</span><span class="sxs-lookup"><span data-stu-id="4e675-177">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="4e675-178">顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="4e675-178">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="4e675-179">將記憶體中壓力記錄檔的內容寫入指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e675-179">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="4e675-180">顯示指定位址之結構的相關資訊 `MethodDesc` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-180">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="4e675-181">顯示指定位址上模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-181">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="4e675-182">顯示指定位址的相關資訊 `MethodTable` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-182">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="4e675-183">顯示指定位址之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-183">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="4e675-184">顯示可在目前堆疊界限內找到的所有 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="4e675-184">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="4e675-185">顯示內部執行時間資料結構所耗用的進程記憶體相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-185">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="4e675-186">顯示所有已註冊為完成項的物件。</span><span class="sxs-lookup"><span data-stu-id="4e675-186">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="4e675-187">在指定的位址上，顯示物件 (或根) 參考的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-187">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="4e675-188">顯示傳入的引數 GC 堆積中的位置。</span><span class="sxs-lookup"><span data-stu-id="4e675-188">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="4e675-189">`MethodDesc`以 JIT 程式碼顯示指定位址的結構。</span><span class="sxs-lookup"><span data-stu-id="4e675-189">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="4e675-190">釋放 `hist*` 命令系列所使用的任何資源。</span><span class="sxs-lookup"><span data-stu-id="4e675-190">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="4e675-191">初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。</span><span class="sxs-lookup"><span data-stu-id="4e675-191">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="4e675-192">顯示與相關的垃圾收集壓力記錄重新調整 `<arguments>` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-192">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="4e675-193">顯示在指定的位址參考物件的所有記錄專案。</span><span class="sxs-lookup"><span data-stu-id="4e675-193">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="4e675-194">顯示與指定之根的提升和重新配置都相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-194">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="4e675-195">顯示進程中的原生模組。</span><span class="sxs-lookup"><span data-stu-id="4e675-195">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="4e675-196">顯示的 `MethodTable` 和 `EEClass` 結構 `<argument>` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-196">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="4e675-197">顯示衍生自之類別的任何物件 <xref:System.Exception> `<argument>` 。</span><span class="sxs-lookup"><span data-stu-id="4e675-197">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="4e675-198">啟用符號伺服器支援</span><span class="sxs-lookup"><span data-stu-id="4e675-198">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="4e675-199">顯示 SyncBlock 持有者資訊。</span><span class="sxs-lookup"><span data-stu-id="4e675-199">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="4e675-200">設定或顯示 SOS 命令的目前線程識別碼。</span><span class="sxs-lookup"><span data-stu-id="4e675-200">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="4e675-201">您可以在 [適用于 .net 的 SOS 偵錯工具擴充](sos-debugging-extension.md)功能中找到其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4e675-201">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="4e675-202">使用 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="4e675-202">Using `dotnet-dump`</span></span>

<span data-ttu-id="4e675-203">第一個步驟是收集傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-203">The first step is to collect a dump.</span></span> <span data-ttu-id="4e675-204">如果已產生核心傾印，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="4e675-204">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="4e675-205">作業系統或 .NET Core 執行時間的內建傾印 [產生功能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) ，都可以建立核心傾印。</span><span class="sxs-lookup"><span data-stu-id="4e675-205">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="4e675-206">現在使用下列命令來分析核心傾印 `analyze` ：</span><span class="sxs-lookup"><span data-stu-id="4e675-206">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="4e675-207">此動作會啟動可接受下列命令的互動式會話：</span><span class="sxs-lookup"><span data-stu-id="4e675-207">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="4e675-208">若要查看已終止應用程式的未處理例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4e675-208">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="4e675-209">Docker 的特殊指示</span><span class="sxs-lookup"><span data-stu-id="4e675-209">Special instructions for Docker</span></span>

<span data-ttu-id="4e675-210">如果您是在 Docker 下執行，傾印收集需要 `SYS_PTRACE` (`--cap-add=SYS_PTRACE` 或 `--privileged`) 的功能。</span><span class="sxs-lookup"><span data-stu-id="4e675-210">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="4e675-211">在 Microsoft .NET Core SDK Linux Docker 映射上，某些 `dotnet-dump` 命令可能會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4e675-211">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="4e675-212">未處理的例外狀況： System.DllNotFoundException：無法載入共用程式庫 ' libdl.so ' 或其相依性的其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4e675-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="4e675-213">若要解決這個問題，請安裝 "libc6-dev" 套件。</span><span class="sxs-lookup"><span data-stu-id="4e675-213">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e675-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e675-214">See also</span></span>

- [<span data-ttu-id="4e675-215">收集和分析記憶體傾印的 blog</span><span class="sxs-lookup"><span data-stu-id="4e675-215">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="4e675-216">堆積分析工具 (dotnet-gcdump) </span><span class="sxs-lookup"><span data-stu-id="4e675-216">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
