---
title: 點網轉儲 - .NET 核心
description: 安裝和使用點網轉儲命令列工具。
ms.date: 10/14/2019
ms.openlocfilehash: 3c0e28d4efc96ae53ec7dfae243725ab400e6b8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737666"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="fa870-103">轉儲收集和分析實用程式 （`dotnet-dump`）</span><span class="sxs-lookup"><span data-stu-id="fa870-103">Dump collection and analysis utility (`dotnet-dump`)</span></span>

<span data-ttu-id="fa870-104">**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="fa870-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="fa870-105">`dotnet-dump`macOS 上不受支援。</span><span class="sxs-lookup"><span data-stu-id="fa870-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="installing-dotnet-dump"></a><span data-ttu-id="fa870-106">安裝 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="fa870-106">Installing `dotnet-dump`</span></span>

<span data-ttu-id="fa870-107">要安裝最新版本的`dotnet-dump` [NuGet 包](https://www.nuget.org/packages/dotnet-dump)，請使用[dotnet 工具安裝](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="fa870-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="fa870-108">概要</span><span class="sxs-lookup"><span data-stu-id="fa870-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="fa870-109">描述</span><span class="sxs-lookup"><span data-stu-id="fa870-109">Description</span></span>

<span data-ttu-id="fa870-110">全域`dotnet-dump`工具是收集和分析 Windows 和 Linux 轉儲的方法，無需像 Linux 那樣`lldb`涉及任何本機調試器。</span><span class="sxs-lookup"><span data-stu-id="fa870-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="fa870-111">此工具在阿爾卑斯 Linux 等平臺中非常重要，因為平臺無法`lldb`完全工作。</span><span class="sxs-lookup"><span data-stu-id="fa870-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="fa870-112">該工具`dotnet-dump`允許您運行 SOS 命令來分析崩潰和垃圾回收器 （GC），但它不是本機調試器，因此不支援顯示本機堆疊幀之類的內容。</span><span class="sxs-lookup"><span data-stu-id="fa870-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="fa870-113">選項。</span><span class="sxs-lookup"><span data-stu-id="fa870-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="fa870-114">顯示點網計數器實用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="fa870-114">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fa870-115">顯示命令列説明。</span><span class="sxs-lookup"><span data-stu-id="fa870-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="fa870-116">命令</span><span class="sxs-lookup"><span data-stu-id="fa870-116">Commands</span></span>

| <span data-ttu-id="fa870-117">Command</span><span class="sxs-lookup"><span data-stu-id="fa870-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="fa870-118">點網轉儲收集</span><span class="sxs-lookup"><span data-stu-id="fa870-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="fa870-119">點網轉儲分析</span><span class="sxs-lookup"><span data-stu-id="fa870-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="fa870-120">點網轉儲收集</span><span class="sxs-lookup"><span data-stu-id="fa870-120">dotnet-dump collect</span></span>

<span data-ttu-id="fa870-121">從進程捕獲轉儲。</span><span class="sxs-lookup"><span data-stu-id="fa870-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="fa870-122">概要</span><span class="sxs-lookup"><span data-stu-id="fa870-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="fa870-123">選項。</span><span class="sxs-lookup"><span data-stu-id="fa870-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="fa870-124">顯示命令列説明。</span><span class="sxs-lookup"><span data-stu-id="fa870-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="fa870-125">指定要從中收集記憶體傾印的進程 ID 號。</span><span class="sxs-lookup"><span data-stu-id="fa870-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="fa870-126">指定轉儲類型，該類型確定從進程收集的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="fa870-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="fa870-127">有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="fa870-127">There are two types:</span></span>

  - <span data-ttu-id="fa870-128">`Heap`- 一個大型且相對全面的轉儲，其中包含模組清單、執行緒清單、所有堆疊、異常資訊、控制碼資訊和映射圖像之外的所有記憶體。</span><span class="sxs-lookup"><span data-stu-id="fa870-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="fa870-129">`Mini`- 包含模組清單、執行緒清單、異常資訊和所有堆疊的小轉儲。</span><span class="sxs-lookup"><span data-stu-id="fa870-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="fa870-130">如果未指定，`Heap`則為預設值。</span><span class="sxs-lookup"><span data-stu-id="fa870-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="fa870-131">應寫入收集的轉儲的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="fa870-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="fa870-132">如果未指定：</span><span class="sxs-lookup"><span data-stu-id="fa870-132">If not specified:</span></span>

  - <span data-ttu-id="fa870-133">在 Windows 上預設為 *._dump_YYYYMMDD_HHMMSS.dmp。*</span><span class="sxs-lookup"><span data-stu-id="fa870-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="fa870-134">預設值為 linux 上的 *./core_YYYYMMDD_HHMMSS。*</span><span class="sxs-lookup"><span data-stu-id="fa870-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="fa870-135">YYYYMMD是年/月/日，HHMMSS為小時/分鐘/秒。</span><span class="sxs-lookup"><span data-stu-id="fa870-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="fa870-136">啟用轉儲集合診斷日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="fa870-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="fa870-137">點網轉儲分析</span><span class="sxs-lookup"><span data-stu-id="fa870-137">dotnet-dump analyze</span></span>

<span data-ttu-id="fa870-138">啟動互動式 shell 以探索轉儲。</span><span class="sxs-lookup"><span data-stu-id="fa870-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="fa870-139">shell 接受各種[SOS 命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="fa870-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="fa870-140">概要</span><span class="sxs-lookup"><span data-stu-id="fa870-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="fa870-141">引數</span><span class="sxs-lookup"><span data-stu-id="fa870-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="fa870-142">指定要分析的轉儲檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="fa870-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="fa870-143">選項。</span><span class="sxs-lookup"><span data-stu-id="fa870-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="fa870-144">指定在啟動時要在 shell 中運行[的命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="fa870-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="fa870-145">分析 SOS 命令</span><span class="sxs-lookup"><span data-stu-id="fa870-145">Analyze SOS commands</span></span>

| <span data-ttu-id="fa870-146">Command</span><span class="sxs-lookup"><span data-stu-id="fa870-146">Command</span></span>                             | <span data-ttu-id="fa870-147">函式</span><span class="sxs-lookup"><span data-stu-id="fa870-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="fa870-148">顯示所有可用命令</span><span class="sxs-lookup"><span data-stu-id="fa870-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="fa870-149">顯示指定的命令。</span><span class="sxs-lookup"><span data-stu-id="fa870-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="fa870-150">退出交互模式。</span><span class="sxs-lookup"><span data-stu-id="fa870-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="fa870-151">僅提供 Managed 程式碼的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="fa870-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="fa870-152">列出正在運行的託管執行緒。</span><span class="sxs-lookup"><span data-stu-id="fa870-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="fa870-153">顯示有關垃圾回收堆上非同步狀態電腦的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="fa870-154">顯示有關程式集的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="fa870-155">在指定位址顯示有關 EE 類結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="fa870-156">顯示有關委託的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="fa870-157">顯示域中所有 AppDomains 和所有程式集的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="fa870-158">顯示有關垃圾回收的堆和有關物件的收集統計資訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="fa870-159">顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="fa870-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="fa870-160">將記憶體中壓力記錄檔的內容寫入指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa870-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="fa870-161">在指定位址顯示有關 MethodDesc 結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="fa870-162">在指定位址顯示有關 EE 模組結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="fa870-163">顯示在所指定位址之方法資料表的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="fa870-164">在指定位址顯示有關物件的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="fa870-165">顯示可在目前堆疊界限內找到的所有 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="fa870-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="fa870-166">顯示有關內部運行時資料結構消耗的進程記憶體的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="fa870-167">顯示所有已註冊為完成項的物件。</span><span class="sxs-lookup"><span data-stu-id="fa870-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="fa870-168">顯示有關指定位址對物件的引用（或根）的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="fa870-169">顯示傳入的參數的 GC 堆中的位置。</span><span class="sxs-lookup"><span data-stu-id="fa870-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="fa870-170">在 JIT 代碼中顯示指定位址上的 MethodDesc 結構。</span><span class="sxs-lookup"><span data-stu-id="fa870-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="fa870-171">釋放 `hist*` 命令系列所使用的任何資源。</span><span class="sxs-lookup"><span data-stu-id="fa870-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="fa870-172">初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。</span><span class="sxs-lookup"><span data-stu-id="fa870-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="fa870-173">顯示與 的`<arguments>`垃圾回收應力日誌重新置放。</span><span class="sxs-lookup"><span data-stu-id="fa870-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="fa870-174">顯示參考位於指定位址之物件的所有記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="fa870-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="fa870-175">顯示與指定之根的提升和重新配置都相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="fa870-176">在此過程中顯示本機模組。</span><span class="sxs-lookup"><span data-stu-id="fa870-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="fa870-177">顯示 的方法表結構和 EEClass`<argument>`結構。</span><span class="sxs-lookup"><span data-stu-id="fa870-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="fa870-178">在 位址`<argument>`顯示從異常類派生的任何物件。</span><span class="sxs-lookup"><span data-stu-id="fa870-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="fa870-179">啟用符號伺服器支援</span><span class="sxs-lookup"><span data-stu-id="fa870-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="fa870-180">顯示 SyncBlock 持有者資訊。</span><span class="sxs-lookup"><span data-stu-id="fa870-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="fa870-181">設置或顯示 SOS 命令的當前執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="fa870-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="fa870-182">使用 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="fa870-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="fa870-183">第一步是收集轉儲。</span><span class="sxs-lookup"><span data-stu-id="fa870-183">The first step is to collect a dump.</span></span> <span data-ttu-id="fa870-184">如果已生成核心轉儲，則可以跳過此步驟。</span><span class="sxs-lookup"><span data-stu-id="fa870-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="fa870-185">作業系統或 .NET Core 運行時的內置[轉儲生成功能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md)可以各自創建核心轉儲。</span><span class="sxs-lookup"><span data-stu-id="fa870-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="fa870-186">現在使用`analyze`命令分析核心轉儲：</span><span class="sxs-lookup"><span data-stu-id="fa870-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="fa870-187">此操作將啟動一個互動式會話，該會話接受以下命令：</span><span class="sxs-lookup"><span data-stu-id="fa870-187">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="fa870-188">要查看終止應用的未處理異常：：</span><span class="sxs-lookup"><span data-stu-id="fa870-188">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="fa870-189">碼頭塢碼頭的特殊說明</span><span class="sxs-lookup"><span data-stu-id="fa870-189">Special instructions for Docker</span></span>

<span data-ttu-id="fa870-190">如果在 Docker 下運行，轉儲集合需要`SYS_PTRACE`功能 （`--cap-add=SYS_PTRACE` `--privileged`或 。</span><span class="sxs-lookup"><span data-stu-id="fa870-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="fa870-191">在 Microsoft .NET 核心 SDK `dotnet-dump` Linux Docker 映射上，某些命令可能會引發以下異常：</span><span class="sxs-lookup"><span data-stu-id="fa870-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="fa870-192">未處理的異常：System.DllNotFoundException：無法載入共用庫"libdl.so"或其依賴項之一的異常。</span><span class="sxs-lookup"><span data-stu-id="fa870-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="fa870-193">要解決此問題，請安裝"libc6-dev"包。</span><span class="sxs-lookup"><span data-stu-id="fa870-193">To work around this problem, install the "libc6-dev" package.</span></span>
