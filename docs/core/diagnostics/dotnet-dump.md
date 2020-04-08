---
title: 點網傾印 - .NET 核心
description: 安裝和使用點網轉儲命令列工具。
ms.date: 10/14/2019
ms.openlocfilehash: c78ddb6447021f61f2452c075733b7d33e051ca0
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888198"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>傾印收集與分析實用程式`dotnet-dump`( )

**本文適用於:✔️** .NET Core 3.0 SDK 和更高版本

> [!NOTE]
> `dotnet-dump`macOS 上不受支援。

## <a name="installing-dotnet-dump"></a>安裝 `dotnet-dump`

要安裝最新版本的`dotnet-dump` [NuGet 套件](https://www.nuget.org/packages/dotnet-dump),請使用[dotnet 工具安裝](../tools/dotnet-tool-install.md)命令:

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>概要

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

全域`dotnet-dump`工具是收集和分析 Windows 和 Linux 轉儲的方法,無需`lldb`像 Linux 那樣 涉及任何本機調試器。 此工具在阿爾卑斯 Linux 等平臺中非常重要,因為`lldb`平臺無法 完全工作。 該工具`dotnet-dump`允許您運行 SOS 命令來分析崩潰和垃圾回收器 (GC),但它不是本機調試器,因此不支援顯示本機堆疊幀之類的內容。

## <a name="options"></a>選項。

- **`--version`**

  顯示點網轉儲實用程式的版本。

- **`-h|--help`**

  顯示命令行説明。

## <a name="commands"></a>命令

| Command                                     |
| ------------------------------------------- |
| [點網傾儲收集](#dotnet-dump-collect) |
| [點網轉儲分析](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>點網傾儲收集

從行程捕獲轉儲。

### <a name="synopsis"></a>概要

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>選項。

- **`-h|--help`**

  顯示命令行説明。

- **`-p|--process-id <PID>`**

  指定要從中收集記憶體轉儲的進程 ID 號。

- **`--type <Heap|Mini>`**

  指定轉儲類型,該類型確定從行程收集的資訊類型。 有兩種類型:

  - `Heap`- 一個大型且相對全面的轉儲,其中包含模組清單、線程清單、所有堆疊、異常資訊、句柄資訊和映射圖像之外的所有記憶體。
  - `Mini`- 包含模組清單、執行緒清單、異常資訊和所有堆疊的小轉儲。

  如果未指定,`Heap`則為預設值。

- **`-o|--output <output_dump_path>`**

  應寫入收集的轉儲的完整路徑和檔名。

  沒有未指定:

  - 在 Windows 上預設為 *._dump_YYYYMMDD_HHMMSS.dmp。*
  - 默認值為 linux 上的 *./core_YYYYMMDD_HHMMSS。*

  YYYYMMD是年/月/日,HHMMSS為小時/分鐘/秒。

- **`--diag`**

  啟用轉儲集合診斷日誌記錄。

## <a name="dotnet-dump-analyze"></a>點網轉儲分析

啟動互動式 shell 以探索轉儲。 shell 接受各種[SOS 命令](#analyze-sos-commands)。

### <a name="synopsis"></a>概要

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>引數

- **`<dump_path>`**

  指定要分析的轉儲文件的路徑。

### <a name="options"></a>選項。

- **`-c|--command <debug_command>`**

  指定在啟動時要在 shell 中執行[的指令](#analyze-sos-commands)。

### <a name="analyze-sos-commands"></a>分析 SOS 命令

| Command                             | 函式                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | 顯示所有可用指令                                                               |
| `soshelp|help <command>`            | 顯示指定的命令。                                                               |
| `exit|quit`                         | 退出交互模式。                                                                       |
| `clrstack <arguments>`              | 僅提供 Managed 程式碼的堆疊追蹤。                                                  |
| `clrthreads <arguments>`            | 列出正在運行的託管線程。                                                            |
| `dumpasync <arguments>`             | 顯示有關垃圾回收堆上異步狀態計算機的資訊。                |
| `dumpassembly <arguments>`          | 顯示有關程式集的詳細資訊。                                                           |
| `dumpclass <arguments>`             | 在指定地址顯示有關 EE 類結構的資訊。                     |
| `dumpdelegate <arguments>`          | 顯示有關委託的資訊。                                                        |
| `dumpdomain <arguments>`            | 顯示網域中所有 AppDomains 和所有程式集的資訊。                |
| `dumpheap <arguments>`              | 顯示有關垃圾回收的堆和有關物件的收集統計資訊的資訊。       |
| `dumpil <arguments>`                | 顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。 |
| `dumplog <arguments>`               | 將記憶體中壓力記錄檔的內容寫入指定的檔案。                         |
| `dumpmd <arguments>`                | 在指定地址顯示有關 MethodDesc 結構的資訊。                   |
| `dumpmodule <arguments>`            | 在指定地址顯示有關 EE 模組結構的資訊。                    |
| `dumpmt <arguments>`                | 顯示在所指定位址之方法資料表的相關資訊。                           |
| `dumpobj <arguments>`               | 在指定地址顯示有關物件的資訊。                                       |
| `dso|dumpstackobjects <arguments>`  | 顯示可在目前堆疊界限內找到的所有 Managed 物件。                    |
| `eeheap <arguments>`                | 顯示有關內部運行時數據結構消耗的進程記憶體的資訊。              |
| `finalizequeue <arguments>`         | 顯示所有已註冊為完成項的物件。                                             |
| `gcroot <arguments>`                | 顯示有關指定位址對物件的引用(或根)的資訊。              |
| `gcwhere <arguments>`               | 顯示傳入的參數的 GC 堆中的位置。                               |
| `ip2md <arguments>`                 | 在 JIT 代碼中顯示指定位址上的 MethodDesc 結構。                       |
| `histclear <arguments>`             | 釋放 `hist*` 命令系列所使用的任何資源。                                |
| `histinit <arguments>`              | 初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。                     |
| `histobj <arguments>`               | 顯示與的`<arguments>`垃圾回收應力日誌重新置放。              |
| `histobjfind <arguments>`           | 顯示參考位於指定位址之物件的所有記錄檔項目。               |
| `histroot <arguments>`              | 顯示與指定之根的提升和重新配置都相關的資訊。        |
| `lm|modules`                        | 在此過程中顯示本機模組。                                                   |
| `name2ee <arguments>`               | 顯示的方法表結構和 EEClass`<argument>`結構。                |
| `pe|printexception <arguments>`     | 在地址`<argument>`顯示從異常類派生的任何物件。             |
| `setsymbolserver <arguments>`       | 開啟符號伺服器支援                                                             |
| `syncblk <arguments>`               | 顯示 SyncBlock 持有者資訊。                                                           |
| `threads|setthread <threadid>`      | 設置或顯示 SOS 命令的當前線程 ID。                                  |

## <a name="using-dotnet-dump"></a>使用 `dotnet-dump`

第一步是收集轉儲。 如果已生成核心轉儲,則可以跳過此步驟。 操作系統或 .NET Core 運行時的內建[轉儲生成功能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md)可以各自創建核心轉儲。

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

現在使用`analyze`指令分析核心傾印:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

此操作將啟動一個互動式作業階段,該會話接受以下命令:

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

要檢視終止應用的未處理異常::

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

## <a name="special-instructions-for-docker"></a>碼頭塢碼頭的特殊說明

如果在 Docker 下執行,傾印`SYS_PTRACE`集合需要`--cap-add=SYS_PTRACE``--privileged`功能( 或 。

在 Microsoft .NET 核心`dotnet-dump`SDK Linux Docker 映像上,某些命令可能會引發以下異常:

> 未處理的異常:System.DllNotFoundException:無法載入共用庫"libdl.so"或其依賴項之一的異常。

要解決此問題,請安裝"libc6-dev"包。
