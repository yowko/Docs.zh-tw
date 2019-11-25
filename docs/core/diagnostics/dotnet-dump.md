---
title: dotnet-傾印-.NET Core
description: 安裝和使用 dotnet-傾印命令列工具。
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: bb4f7827f898431c55603b070f5b7a23fe44cba5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973460"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="e6535-103">傾印集合和分析公用程式（`dotnet-dump`）</span><span class="sxs-lookup"><span data-stu-id="e6535-103">Dump collection and analysis utility (`dotnet-dump`)</span></span>

<span data-ttu-id="e6535-104">**本文適用于：✓** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e6535-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="e6535-105">macOS 不支援 `dotnet-dump`。</span><span class="sxs-lookup"><span data-stu-id="e6535-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="installing-dotnet-dump"></a><span data-ttu-id="e6535-106">安裝 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="e6535-106">Installing `dotnet-dump`</span></span>

<span data-ttu-id="e6535-107">若要安裝 `dotnet-dump` [NuGet 套件](https://www.nuget.org/packages/dotnet-dump)的最新發行版本，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="e6535-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="e6535-108">概要</span><span class="sxs-lookup"><span data-stu-id="e6535-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e6535-109">描述</span><span class="sxs-lookup"><span data-stu-id="e6535-109">Description</span></span>

<span data-ttu-id="e6535-110">`dotnet-dump` 的全域工具可讓您收集和分析 Windows 和 Linux 傾印，而不需要任何與 Linux `lldb` 相關的原生偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e6535-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="e6535-111">這項工具在 Alpine Linux 這類平臺上很重要，因為無法使用完整的 `lldb`。</span><span class="sxs-lookup"><span data-stu-id="e6535-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="e6535-112">`dotnet-dump` 工具可讓您執行 SOS 命令來分析損毀和垃圾收集行程（GC），但它不是原生偵錯工具，因此不支援顯示原生堆疊框架之類的動作。</span><span class="sxs-lookup"><span data-stu-id="e6535-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="e6535-113">選項</span><span class="sxs-lookup"><span data-stu-id="e6535-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="e6535-114">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="e6535-114">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e6535-115">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="e6535-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="e6535-116">命令</span><span class="sxs-lookup"><span data-stu-id="e6535-116">Commands</span></span>

| <span data-ttu-id="e6535-117">命令</span><span class="sxs-lookup"><span data-stu-id="e6535-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="e6535-118">dotnet-傾印收集</span><span class="sxs-lookup"><span data-stu-id="e6535-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="e6535-119">dotnet-傾印分析</span><span class="sxs-lookup"><span data-stu-id="e6535-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="e6535-120">dotnet-傾印收集</span><span class="sxs-lookup"><span data-stu-id="e6535-120">dotnet-dump collect</span></span>

<span data-ttu-id="e6535-121">從進程中捕捉傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6535-122">概要</span><span class="sxs-lookup"><span data-stu-id="e6535-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="e6535-123">選項</span><span class="sxs-lookup"><span data-stu-id="e6535-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e6535-124">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="e6535-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e6535-125">指定要從中收集記憶體傾印的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6535-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="e6535-126">指定傾印類型，它會決定從進程收集的資訊種類。</span><span class="sxs-lookup"><span data-stu-id="e6535-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="e6535-127">有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="e6535-127">There are two types:</span></span>

  - <span data-ttu-id="e6535-128">`Heap`-包含模組清單、執行緒清單、所有堆疊、例外狀況資訊、處理資訊和所有記憶體（對應的影像除外）的大型且較完整的傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="e6535-129">`Mini`-包含模組清單、執行緒清單、例外狀況資訊和所有堆疊的小型傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="e6535-130">如果未指定，`Heap` 為預設值。</span><span class="sxs-lookup"><span data-stu-id="e6535-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="e6535-131">應在其中寫入所收集傾印的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="e6535-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="e6535-132">如果未指定：</span><span class="sxs-lookup"><span data-stu-id="e6535-132">If not specified:</span></span>

  - <span data-ttu-id="e6535-133">預設為 Windows 上的 *. \ dump_YYYYMMDD_HHMMSS dmp* 。</span><span class="sxs-lookup"><span data-stu-id="e6535-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="e6535-134">預設為 *./core_YYYYMMDD_HHMMSS* on Linux。</span><span class="sxs-lookup"><span data-stu-id="e6535-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="e6535-135">YYYYMMDD 是年/月/日，而 HHMMSS 是小時/分鐘/秒。</span><span class="sxs-lookup"><span data-stu-id="e6535-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="e6535-136">啟用傾印收集診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="e6535-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="e6535-137">dotnet-傾印分析</span><span class="sxs-lookup"><span data-stu-id="e6535-137">dotnet-dump analyze</span></span>

<span data-ttu-id="e6535-138">啟動互動式 shell 以探索傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="e6535-139">Shell 會接受各種[SOS 命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="e6535-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="e6535-140">概要</span><span class="sxs-lookup"><span data-stu-id="e6535-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="e6535-141">引數</span><span class="sxs-lookup"><span data-stu-id="e6535-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="e6535-142">指定要分析之傾印檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6535-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="e6535-143">選項</span><span class="sxs-lookup"><span data-stu-id="e6535-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="e6535-144">指定啟動時要在 shell 中執行的[命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="e6535-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="e6535-145">分析 SOS 命令</span><span class="sxs-lookup"><span data-stu-id="e6535-145">Analyze SOS commands</span></span>

| <span data-ttu-id="e6535-146">命令</span><span class="sxs-lookup"><span data-stu-id="e6535-146">Command</span></span>                             | <span data-ttu-id="e6535-147">功能</span><span class="sxs-lookup"><span data-stu-id="e6535-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="e6535-148">顯示所有可用的命令</span><span class="sxs-lookup"><span data-stu-id="e6535-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="e6535-149">顯示指定的命令。</span><span class="sxs-lookup"><span data-stu-id="e6535-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="e6535-150">結束互動模式。</span><span class="sxs-lookup"><span data-stu-id="e6535-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="e6535-151">僅提供 Managed 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6535-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="e6535-152">列出正在執行的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="e6535-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="e6535-153">顯示垃圾收集堆積上非同步狀態機器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="e6535-154">顯示元件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e6535-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="e6535-155">顯示指定位址之 EE 類別結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="e6535-156">顯示委派的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="e6535-157">顯示所有 Appdomain 和網域中所有元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="e6535-158">顯示有關垃圾收集堆積和物件相關集合統計資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="e6535-159">顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="e6535-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="e6535-160">將記憶體中壓力記錄檔的內容寫入指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6535-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="e6535-161">在指定的位址顯示 MethodDesc 結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="e6535-162">在指定的位址顯示 EE 模組結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="e6535-163">顯示在所指定位址之方法資料表的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="e6535-164">顯示位於指定位址之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="e6535-165">顯示可在目前堆疊界限內找到的所有 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="e6535-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="e6535-166">顯示內部執行時間資料結構所耗用之進程記憶體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="e6535-167">顯示所有已註冊為完成項的物件。</span><span class="sxs-lookup"><span data-stu-id="e6535-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="e6535-168">顯示指定位址之物件的參考資訊（或根）。</span><span class="sxs-lookup"><span data-stu-id="e6535-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="e6535-169">顯示傳入之引數的 GC 堆積中的位置。</span><span class="sxs-lookup"><span data-stu-id="e6535-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="e6535-170">在 JIT 程式碼中，以指定的位址顯示 MethodDesc 結構。</span><span class="sxs-lookup"><span data-stu-id="e6535-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="e6535-171">釋放 `hist*` 命令系列所使用的任何資源。</span><span class="sxs-lookup"><span data-stu-id="e6535-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="e6535-172">初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。</span><span class="sxs-lookup"><span data-stu-id="e6535-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="e6535-173">顯示與 `<arguments>` 相關的垃圾收集壓力記錄重設。</span><span class="sxs-lookup"><span data-stu-id="e6535-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="e6535-174">顯示參考位於指定位址之物件的所有記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="e6535-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="e6535-175">顯示與指定之根的提升和重新配置都相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="e6535-176">顯示進程中的原生模組。</span><span class="sxs-lookup"><span data-stu-id="e6535-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="e6535-177">顯示 `<argument>` 的 MethodTable 結構和 EEClass 結構。</span><span class="sxs-lookup"><span data-stu-id="e6535-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="e6535-178">顯示從位址 `<argument>` 的例外狀況類別衍生的任何物件。</span><span class="sxs-lookup"><span data-stu-id="e6535-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="e6535-179">啟用符號伺服器支援</span><span class="sxs-lookup"><span data-stu-id="e6535-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="e6535-180">顯示 SyncBlock 持有者資訊。</span><span class="sxs-lookup"><span data-stu-id="e6535-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="e6535-181">設定或顯示 SOS 命令的目前線程識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6535-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="e6535-182">使用 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="e6535-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="e6535-183">第一個步驟是收集傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-183">The first step is to collect a dump.</span></span> <span data-ttu-id="e6535-184">如果已產生核心傾印，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="e6535-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="e6535-185">作業系統或 .NET Core 執行時間的內建傾印[功能](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy)，都可以建立核心傾印。</span><span class="sxs-lookup"><span data-stu-id="e6535-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="e6535-186">現在使用 `analyze` 命令來分析核心傾印：</span><span class="sxs-lookup"><span data-stu-id="e6535-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="e6535-187">此動作會啟動一個互動式會話，它會接受類似下列的命令：</span><span class="sxs-lookup"><span data-stu-id="e6535-187">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="e6535-188">若要查看終止應用程式的未處理例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e6535-188">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="e6535-189">Docker 的特殊指示</span><span class="sxs-lookup"><span data-stu-id="e6535-189">Special instructions for Docker</span></span>

<span data-ttu-id="e6535-190">如果您是在 Docker 底下執行，傾印集合需要 `SYS_PTRACE` 功能（`--cap-add=SYS_PTRACE` 或 `--privileged`）。</span><span class="sxs-lookup"><span data-stu-id="e6535-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="e6535-191">在 Microsoft .NET Core SDK Linux Docker 映射上，某些 `dotnet-dump` 命令可能會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e6535-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="e6535-192">未處理的例外狀況： System.dllnotfoundexception：無法載入共用程式庫 ' libdl.so ' 或其相依性的其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6535-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="e6535-193">若要解決此問題，請安裝 "libc6-dev" 套件。</span><span class="sxs-lookup"><span data-stu-id="e6535-193">To work around this problem, install the "libc6-dev" package.</span></span>
