---
title: dotnet-傾印診斷工具-.NET CLI
description: 瞭解如何在不使用任何原生偵錯工具的情況下，安裝和使用 dotnet 傾印 CLI 工具來收集和分析 Windows 和 Linux 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: eaffbb1f2959dba5c25a603b6f785c7480e4a8c0
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765042"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>傾印收集和分析公用程式 (dotnet-傾印) 

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

> [!NOTE]
> `dotnet-dump` 只有 .NET 5.0 和更新版本才支援 macOS。

## <a name="install"></a>安裝

有兩種方式可以下載和安裝 `dotnet-dump` ：

- **dotnet global tool：**

  若要安裝 `dotnet-dump` [NuGet 套件](https://www.nuget.org/packages/dotnet-dump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- **直接下載：**

  下載符合您平臺的工具可執行檔：

  | OS  | 平台 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-dump/win-x86) \|[x64](https://aka.ms/dotnet-dump/win-x64) \|[arm](https://aka.ms/dotnet-dump/win-arm) \|[arm-x64](https://aka.ms/dotnet-dump/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-dump/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-dump/linux-x64) \|[arm](https://aka.ms/dotnet-dump/linux-arm) \|[arm64](https://aka.ms/dotnet-dump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64) |

## <a name="synopsis"></a>概要

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-dump`全域工具可收集和分析 Windows 和 linux 傾印，而不需要任何與 Linux 相關的原生偵錯工具 `lldb` 。 這項工具在 Alpine Linux 等平臺上很重要，因為無法使用完整的工作 `lldb` 。 此 `dotnet-dump` 工具可讓您執行 SOS 命令來分析損毀和垃圾收集行程 (GC) ，但它不是原生偵錯工具，因此不支援顯示原生堆疊框架之類的動作。

## <a name="options"></a>選項

- **`--version`**

  顯示 dotnet 傾印公用程式的版本。

- **`-h|--help`**

  顯示命令列說明。

## <a name="commands"></a>命令

| 命令                                     |
| ------------------------------------------- |
| [dotnet-傾印收集](#dotnet-dump-collect) |
| [dotnet-傾印分析](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-傾印收集

從進程中捕獲傾印。

### <a name="synopsis"></a>概要

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>選項

- **`-h|--help`**

  顯示命令列說明。

- **`-p|--process-id <PID>`**

  指定要從中收集傾印的處理序識別碼。

- **`-n|--name <name>`**

  指定要從中收集傾印之進程的名稱。

- **`--type <Full|Heap|Mini>`**

  指定傾印類型，以決定從進程收集的資訊類型。 有三種類型：

  - `Full` -最大傾印，包含模組映射在內的所有記憶體。
  - `Heap` -包含模組清單、執行緒清單、所有堆疊、例外狀況資訊、處理資訊，以及所有記憶體（除了對應的影像以外）的大型較完整傾印。
  - `Mini` -包含模組清單、執行緒清單、例外狀況資訊和所有堆疊的小型傾印。

  如果未指定， `Full` 則為預設值。

- **`-o|--output <output_dump_path>`**

  應寫入所收集傾印的完整路徑和檔案名。

  如果未指定：

  - 預設為在 Windows 上 *dump_YYYYMMDD_HHMMSS dmp* 。
  - 預設為 Linux 上的 *./core_YYYYMMDD_HHMMSS。*

  YYYYMMDD 是年/月/日，而 HHMMSS 是小時/分鐘/秒。

- **`--diag`**

  啟用傾印收集診斷記錄。

## <a name="dotnet-dump-analyze"></a>dotnet-傾印分析

啟動互動式 shell 以探索傾印。 Shell 接受各種 [SOS 命令](#analyze-sos-commands)。

### <a name="synopsis"></a>概要

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>引數

- **`<dump_path>`**

  指定要分析之傾印檔案的路徑。

### <a name="options"></a>選項

- **`-c|--command <debug_command>`**

  指定在啟動時要在 shell 中執行的 [命令](#analyze-sos-commands) 。

### <a name="analyze-sos-commands"></a>分析 SOS 命令

| 命令                             | 函數                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | 顯示所有可用的命令                                                               |
| `soshelp|help <command>`            | 顯示指定的命令。                                                               |
| `exit|quit`                         | 結束互動模式。                                                                       |
| `clrstack <arguments>`              | 僅提供 Managed 程式碼的堆疊追蹤。                                                  |
| `clrthreads <arguments>`            | 列出正在執行的 managed 執行緒。                                                            |
| `dumpasync <arguments>`             | 顯示垃圾收集堆積上的非同步狀態機器的相關資訊。                |
| `dumpassembly <arguments>`          | 顯示位於指定位址之元件的詳細資料。                                 |
| `dumpclass <arguments>`             | 顯示指定位址之結構的相關資訊 `EEClass` 。                  |
| `dumpdelegate <arguments>`          | 顯示指定位址之委派的相關資訊。                             |
| `dumpdomain <arguments>`            | 顯示指定網域內所有 Appdomain 和所有元件的資訊。       |
| `dumpheap <arguments>`              | 顯示垃圾收集堆積的相關資訊，以及物件的集合統計資料。       |
| `dumpil <arguments>`                | 顯示與 Managed 方法相關聯的 Microsoft 中繼語言 (MSIL)。 |
| `dumplog <arguments>`               | 將記憶體中壓力記錄檔的內容寫入指定的檔案。                         |
| `dumpmd <arguments>`                | 顯示指定位址之結構的相關資訊 `MethodDesc` 。               |
| `dumpmodule <arguments>`            | 顯示指定位址上模組的相關資訊。                               |
| `dumpmt <arguments>`                | 顯示指定位址的相關資訊 `MethodTable` 。                        |
| `dumpobj <arguments>`               | 顯示指定位址之物件的相關資訊。                                      |
| `dso|dumpstackobjects <arguments>`  | 顯示可在目前堆疊界限內找到的所有 Managed 物件。                    |
| `eeheap <arguments>`                | 顯示內部執行時間資料結構所耗用的進程記憶體相關資訊。              |
| `finalizequeue <arguments>`         | 顯示所有已註冊為完成項的物件。                                             |
| `gcroot <arguments>`                | 在指定的位址上，顯示物件 (或根) 參考的相關資訊。             |
| `gcwhere <arguments>`               | 顯示傳入的引數 GC 堆積中的位置。                               |
| `ip2md <arguments>`                 | `MethodDesc`以 JIT 程式碼顯示指定位址的結構。                     |
| `histclear <arguments>`             | 釋放 `hist*` 命令系列所使用的任何資源。                                |
| `histinit <arguments>`              | 初始化在偵錯項目中儲存之壓力記錄檔中的 SOS 結構。                     |
| `histobj <arguments>`               | 顯示與相關的垃圾收集壓力記錄重新調整 `<arguments>` 。              |
| `histobjfind <arguments>`           | 顯示在指定的位址參考物件的所有記錄專案。              |
| `histroot <arguments>`              | 顯示與指定之根的提升和重新配置都相關的資訊。        |
| `lm|modules`                        | 顯示進程中的原生模組。                                                   |
| `name2ee <arguments>`               | 顯示的 `MethodTable` 和 `EEClass` 結構 `<argument>` 。                     |
| `pe|printexception <arguments>`     | 顯示衍生自之類別的任何物件 <xref:System.Exception> `<argument>` 。      |
| `setsymbolserver <arguments>`       | 啟用符號伺服器支援                                                             |
| `syncblk <arguments>`               | 顯示 SyncBlock 持有者資訊。                                                           |
| `threads|setthread <threadid>`      | 設定或顯示 SOS 命令的目前線程識別碼。                                  |

> [!NOTE]
> 您可以在 [適用于 .net 的 SOS 偵錯工具擴充](sos-debugging-extension.md)功能中找到其他詳細資料。

## <a name="using-dotnet-dump"></a>使用 `dotnet-dump`

第一個步驟是收集傾印。 如果已產生核心傾印，則可以略過此步驟。 作業系統或 .NET Core 執行時間的內建傾印 [產生功能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) ，都可以建立核心傾印。

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

現在使用下列命令來分析核心傾印 `analyze` ：

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

此動作會啟動可接受下列命令的互動式會話：

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

若要查看已終止應用程式的未處理例外狀況：

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

## <a name="special-instructions-for-docker"></a>Docker 的特殊指示

如果您是在 Docker 下執行，傾印收集需要 `SYS_PTRACE` (`--cap-add=SYS_PTRACE` 或 `--privileged`) 的功能。

在 Microsoft .NET Core SDK Linux Docker 映射上，某些 `dotnet-dump` 命令可能會擲回下列例外狀況：

> 未處理的例外狀況： System.DllNotFoundException：無法載入共用程式庫 ' libdl.so ' 或其相依性的其中一個例外狀況。

若要解決這個問題，請安裝 "libc6-dev" 套件。

## <a name="see-also"></a>請參閱

- [收集和分析記憶體傾印的 blog](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [堆積分析工具 (dotnet-gcdump) ](dotnet-gcdump.md)
