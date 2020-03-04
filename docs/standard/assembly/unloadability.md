---
title: 如何使用 .NET Core 中的組件卸載功能及對其進行偵錯
description: 了解如何使用可回收 AssemblyLoadContext 來載入和卸載受控組件，以及如何對導致卸載失敗的問題進行偵錯。
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159737"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>如何使用 .NET Core 中的組件卸載功能及對其進行偵錯

從 .NET Core 3.0 開始，支援載入及稍後卸載一組組件的功能。 在 .NET Framework 中，自訂應用程式定義域已用於此用途，但 .NET Core 僅支援單一預設應用程式定義域。

.NET Core 3.0 和更新版本透過 <xref:System.Runtime.Loader.AssemblyLoadContext> 支援卸載功能。 您可以將一組組件載入可回收 `AssemblyLoadContext`，在其中執行方法，或只使用反映進行檢查，最後卸載 `AssemblyLoadContext`。 這會卸載載入 `AssemblyLoadContext`中的元件。

使用 `AssemblyLoadContext` 與使用 AppDomain 卸載之間有一個值得注意的差異。 使用 AppDomain 時，會強制卸載。 在卸載時，在目標 AppDomain 中執行的所有線程都會中止，在目標 AppDomain 中建立的 managed COM 物件會損毀，依此類推。 使用 `AssemblyLoadContext` 時，卸載為「合作」。 呼叫 <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> 方法只會起始卸載。 卸載會在下列情況之後完成：

- 沒有任何執行緒會將組件中方法載入到其呼叫堆疊上的 `AssemblyLoadContext`。
- 從載入 `AssemblyLoadContext`的任何類型、這些類型的實例，以及元件本身都是由所參考：
  - `AssemblyLoadContext` 外部的參考，但弱式參考 (<xref:System.WeakReference> 或 <xref:System.WeakReference%601>) 除外。
  - 來自 `AssemblyLoadContext`內外的強式垃圾收集行程（GC）控制碼（[GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal)或[GCHandleType](xref:System.Runtime.InteropServices.GCHandleType.Pinned)）。

## <a name="use-collectible-assemblyloadcontext"></a>使用可回收的 AssemblyLoadCoNtext

本節包含詳細的逐步教學課程，示範將 .NET Core 應用程式載入可回收 `AssemblyLoadContext`，執行其進入點，然後將其卸載的簡單方式。 您可以在[https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)找到完整的範例。

### <a name="create-a-collectible-assemblyloadcontext"></a>建立可回收 AssemblyLoadContext

您必須從 <xref:System.Runtime.Loader.AssemblyLoadContext> 衍生類別，並多載其 <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> 方法。 該方法會解析所有組件的參考，這些組件是載入到該 `AssemblyLoadContext` 的組件相依性。

下列程式碼是最簡單的自訂 `AssemblyLoadContext` 範例：

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

如您所見，`Load` 方法會傳回 `null`。 這表示所有相依性組件都會載入到預設內容，而新的內容只會包含明確載入其中的組件。

如果您也想要將部分或所有相依性載入到 `AssemblyLoadContext`，則可以在 `AssemblyDependencyResolver` 方法中使用 `Load`。 `AssemblyDependencyResolver` 會將元件名稱解析成絕對元件檔案路徑。 解析程式會使用載入內容之主要元件目錄中的 *.deps.json*檔案和元件檔。

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>使用自訂的可回收 AssemblyLoadContext

本節假設使用的是較簡單的 `TestAssemblyLoadContext` 版本。

您可以建立自訂 `AssemblyLoadContext` 的執行個體，並將組件載入到其中，如下所示：

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

針對已載入組件所參考的每個組件，會呼叫 `TestAssemblyLoadContext.Load` 方法，讓 `TestAssemblyLoadContext` 能夠決定從中取得組件的位置。 在我們的案例中，它會傳回 `null`，指出應該從執行階段預設用來載入組件的位置載入預設內容。

現在已載入組件，您就可以從中執行一個方法。 請執行 `Main` 方法：

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

在 `Main` 方法傳回之後，您可以藉由在自訂的 `Unload` 上呼叫 `AssemblyLoadContext` 方法，或去除您對 `AssemblyLoadContext` 的參考來起始卸載：

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

這便足以卸載測試組件。 讓我們將這些全都放入個別的非內嵌方法，以確保 `TestAssemblyLoadContext`、`Assembly` 和 `MethodInfo` (`Assembly.EntryPoint`) 無法透過堆疊位置參考 (實際或 JIT 引入的區域變數) 保持運作。 這可能會使 `TestAssemblyLoadContext` 保持運作，並防止其卸載。

此外，會傳回對 `AssemblyLoadContext` 的弱式參考，讓您能夠在稍後使用它來偵測卸載是否完成。

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

現在，您可以執行此函式來載入、執行及卸載組件。

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

不過，卸載不會立即完成。 如先前所述，它會依賴垃圾收集行程來收集測試元件中的所有物件。 在許多情況下，並不需要等候卸載完成。 不過，在某些情況下，知道卸載已經完成是很有用的。 例如，您可能想要刪除從磁碟載入到自訂 `AssemblyLoadContext` 的組件檔。 在這種情況下，可以使用下列程式碼片段。 它會觸發垃圾收集並等候迴圈中的暫止完成項，直到自訂 `AssemblyLoadContext` 的弱式參考設定為 `null`（表示已收集目標物件）為止。 在大部分情況下，只需要一個通過迴圈的傳遞。 不過，針對在 `AssemblyLoadContext` 中執行之程式碼所建立物件具有完成項的更複雜案例，可能需要更多的傳遞。

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>卸載事件

在某些情況下，載入到自訂 `AssemblyLoadContext` 中的程式碼可能需要在起始卸載時執行一些清除。 例如，它可能需要停止執行緒或清除強式 GC 控制碼。 `Unloading` 事件可用於這類情況。 執行必要清除的處理常式可以連結到這個事件。

### <a name="troubleshoot-unloadability-issues"></a>針對卸載功能問題進行疑難排解

由於卸載的關係，這很容易忘記可能會讓 `AssemblyLoadContext` 運作，並防止卸載的參考。 以下是可以保存參考的實體（其中一些不明顯）摘要：

- 保留自可回收 `AssemblyLoadContext` 外部的一般參考，儲存于堆疊位置或處理器暫存器中（方法區域變數是由使用者程式碼明確建立，或由即時（JIT）編譯器隱含建立）、靜態變數或強式（釘選） GC 控制碼，以及可直接指向：
  - 載入到可回收 `AssemblyLoadContext` 中的組件。
  - 來自這類組件的類型。
  - 來自這類組件類型的執行個體。
- 從載入到可回收 `AssemblyLoadContext` 之組件執行程式碼的執行緒。
- 在可回收 `AssemblyLoadContext`內建立之自訂、非可回收 `AssemblyLoadContext` 類型的實例。
- 暫止 <xref:System.Threading.RegisteredWaitHandle> 實例，並將回呼設定為自訂 `AssemblyLoadContext`中的方法。

> [!TIP]
> 儲存在堆疊位置或處理器暫存器中，而且可能會導致無法卸載 `AssemblyLoadContext` 的物件參考，可能會在下列情況下發生：
>
> - 當函式呼叫結果直接傳遞至另一個函式時，即使沒有使用者建立的本機變數也一樣。
> - 當 JIT 編譯程式保留方法中某個點上可用之物件的參考時。

## <a name="debug-unloading-issues"></a>對卸載問題進行偵錯

對卸載問題進行偵錯可能很繁瑣。 您可能會遇到以下狀況：您不知道哪些項目可以使 `AssemblyLoadContext` 保持運作，但是卸載會失敗。 協助此問題之最佳武器是含有 SOS 外掛程式的 WinDbg (UNIX 上的 LLDB)。 您必須找出讓 `LoaderAllocator` (其屬於特定 `AssemblyLoadContext`) 保持運作的項目。 SOS 外掛程式可讓您查看 GC 堆積物件、其階層和根。

若要將外掛程式載入到偵錯工具，請在偵錯工具命令列中輸入下列命令：

在 WinDbg 中 (WinDbg 似乎會在中斷至 .NET Core 應用程式時自動執行該操作)：

```console
.loadby sos coreclr
```

在 LLDB 中：

```console
plugin load /path/to/libsosplugin.so
```

讓我們來 debug 一個發生卸載問題的範例程式。 原始程式碼包含在以下內容中。 當您在 WinDbg 底下執行它時，程式會在嘗試檢查卸載是否成功之後，立即中斷至偵錯工具。 然後，您就可以開始尋找原因。

> [!TIP]
> 如果您使用 Unix 上的 LLDB 進行偵錯工具，下列範例中的 SOS 命令前面不會有 `!`。

```console
!dumpheap -type LoaderAllocator
```

此命令會傾印 GC 堆積中類型名稱包含 `LoaderAllocator` 的所有物件。 範例如下：

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

在下面的 "Statistics:" 部分中，檢查屬於 `MT` 的 `MethodTable` (`System.Reflection.LoaderAllocator`)，這是我們關注的物件。 然後，在清單中，尋找 `MT` 符合的專案，並取得物件本身的位址。 在我們的案例中，它是 "000002b78000ce40"。

既然我們知道 `LoaderAllocator` 物件的位址，就可以使用另一個命令來尋找其 GC 根：

```console
!gcroot -all 0x000002b78000ce40
```

此命令會傾印導致 `LoaderAllocator` 執行個體的物件參考鏈。 此清單會以根節點開頭，這是讓我們的 `LoaderAllocator` 保持運作的實體，因此是問題的核心。 根可以是堆疊位置、處理器暫存器、GC 控制代碼或靜態變數。

以下是 `gcroot` 命令的輸出範例：

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

下一步是找出根所在的位置，以便您可以修正它。 最簡單的情況是當根為堆疊位置或處理器暫存器時。 在此情況下，`gcroot` 會顯示其框架包含根的函式名稱，以及執行該函式的執行緒。 困難的情況是當根為靜態變數或 GC 控制代碼時。

在上一個範例中，第一個根是類型為 `System.Reflection.RuntimeMethodInfo` 的區域變數，儲存在函式 `example.Program.Main(System.String[])` 的框架中，位址為 `rbp-20` (`rbp` 是處理器暫存器 `rbp`，-20 是該暫存器中的十六進位位移)。

第二個根是標準 (強式) `GCHandle`，它會保存 `test.Test` 類別執行個體的參考。

第三個根是固定的 `GCHandle`。 這是一個靜態變數，但是可惜的是，沒有辦法告訴您。 參考型別靜態變數會儲存在內部執行階段結構的受控物件陣列中。

另一個可以防止卸載 `AssemblyLoadContext` 的情況，就是當執行緒具有組件的方法框架，而該組件已載入到其堆疊的 `AssemblyLoadContext` 時。 您可以藉由傾印所有執行緒的受控呼叫堆疊來進行檢查：

```console
~*e !clrstack
```

此命令表示「將 `!clrstack` 命令套用到所有執行緒」。 下列是此範例中該命令的輸出。 可惜的是，LLDB on Unix 沒有任何方法可將命令套用至所有線程，因此您必須手動切換執行緒，並重複 `clrstack` 命令。 忽略偵錯工具顯示「無法進行 managed 堆疊」的所有線程。

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

如您所見，最後一個執行緒具有 `test.Program.ThreadProc()`。 這是載入到 `AssemblyLoadContext` 的組件中函式，因此它會使 `AssemblyLoadContext` 保持運作。

## <a name="example-source-with-unloadability-issues"></a>具有卸載功能問題的範例來源

在先前的偵錯範例中使用了下列程式碼。

### <a name="main-testing-program"></a>主要測試程式

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>載入到 TestAssemblyLoadContext 的程式

下列程式碼代表在主要測試程式中傳遞至 `ExecuteAndUnload` 方法的*test .dll* 。

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
