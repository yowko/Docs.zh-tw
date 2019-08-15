---
title: 如何使用 .NET Core 中的組件卸載功能及對其進行偵錯
description: 了解如何使用可回收 AssemblyLoadContext 來載入和卸載受控組件，以及如何對導致卸載失敗的問題進行偵錯。
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: a3ba2c2809aedd0af03ec965089f8779c430a335
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68671243"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>如何使用 .NET Core 中的組件卸載功能及對其進行偵錯

從 .NET Core 3.0 開始，支援載入及稍後卸載一組組件的功能。 在 .NET Framework 中，自訂應用程式定義域已用於此用途，但 .NET Core 僅支援單一預設應用程式定義域。

.NET Core 3.0 和更新版本透過 <xref:System.Runtime.Loader.AssemblyLoadContext> 支援卸載功能。 您可以將一組組件載入可回收 `AssemblyLoadContext`，在其中執行方法，或只使用反映進行檢查，最後卸載 `AssemblyLoadContext`。 這會卸載載入到該 `AssemblyLoadContext` 中的組件。

使用 `AssemblyLoadContext` 與使用 AppDomain 卸載之間有一個值得注意的差異。 使用 AppDomain 時，會強制卸載。 卸載時，在目標 AppDomain 中執行的所有執行緒都會中止，在目標 AppDomain 中建立的受控 COM 物件會被終結等。使用 `AssemblyLoadContext` 時，卸載為「合作」。 呼叫 <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> 方法只會起始卸載。 卸載會在下列情況之後完成：

- 沒有任何執行緒會將組件中方法載入到其呼叫堆疊上的 `AssemblyLoadContext`。
- 載入到 `AssemblyLoadContext` 的任何組件類型、這些類型的執行個體，以及 `AssemblyLoadContext` 外部的組件本身都不會透過下列方法參考：
  - `AssemblyLoadContext` 外部的參考，但弱式參考 (<xref:System.WeakReference> 或 <xref:System.WeakReference%601>) 除外。
  - 強式 GC 控制代碼 (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> 或 <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>)，來自 `AssemblyLoadContext` 內部和外部。

## <a name="using-collectible-assemblyloadcontext"></a>使用可回收 AssemblyLoadContext

本節包含詳細的逐步教學課程，示範將 .NET Core 應用程式載入可回收 `AssemblyLoadContext`，執行其進入點，然後將其卸載的簡單方式。 您可以在 <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading> 上找到完整的範例。

### <a name="create-a-collectible-assemblyloadcontext"></a>建立可回收 AssemblyLoadContext

您必須從 <xref:System.Runtime.Loader.AssemblyLoadContext> 衍生類別，並多載其 <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> 方法。 該方法會解析所有組件的參考，這些組件是載入到該 `AssemblyLoadContext` 的組件相依性。
下列程式碼是最簡單的自訂 `AssemblyLoadContext` 範例：

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

如您所見，`Load` 方法會傳回 `null`。 這表示所有相依性組件都會載入到預設內容，而新的內容只會包含明確載入其中的組件。

如果您也想要將部分或所有相依性載入到 `AssemblyLoadContext`，則可以在 `Load` 方法中使用 `AssemblyDependencyResolver`。 `AssemblyDependencyResolver` 使用主要組件 (已載入到內容) 目錄中包含的 *.deps.json* 檔案，並使用該目錄中的組件檔，將組件名稱解析為絕對組件檔案路徑。

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>使用自訂的可回收 AssemblyLoadContext

本節假設使用的是較簡單的 `TestAssemblyLoadContext` 版本。

您可以建立自訂 `AssemblyLoadContext` 的執行個體，並將組件載入到其中，如下所示：

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

針對已載入組件所參考的每個組件，會呼叫 `TestAssemblyLoadContext.Load` 方法，讓 `TestAssemblyLoadContext` 能夠決定從中取得組件的位置。 在我們的案例中，它會傳回 `null`，指出應該從執行階段預設用來載入組件的位置載入預設內容。

現在已載入組件，您就可以從中執行一個方法。 請執行 `Main` 方法：

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

在 `Main` 方法傳回之後，您可以藉由在自訂的 `AssemblyLoadContext` 上呼叫 `Unload` 方法，或去除您對 `AssemblyLoadContext` 的參考來起始卸載：

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

這便足以卸載測試組件。 讓我們將這些全都放入個別的非內嵌方法，以確保 `TestAssemblyLoadContext`、`Assembly` 和 `MethodInfo` (`Assembly.EntryPoint`) 無法透過堆疊位置參考 (實際或 JIT 引入的區域變數) 保持運作。 這可能會使 `TestAssemblyLoadContext` 保持運作，並防止其卸載。

此外，會傳回對 `AssemblyLoadContext` 的弱式參考，讓您能夠在稍後使用它來偵測卸載是否完成。

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

現在，您可以執行此函式來載入、執行及卸載組件。

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

不過，卸載不會立即完成。 如先前所述，它會依賴 GC 來收集測試組件中的所有物件。 在許多情況下，並不需要等候卸載完成。 不過，在某些情況下，知道卸載已經完成是很有用的。 例如，您可能想要刪除從磁碟載入到自訂 `AssemblyLoadContext` 的組件檔。 在這種情況下，可以使用下列程式碼片段。 它會觸發 GC 並等候迴圈中的擱置完成項，直到自訂 `AssemblyLoadContext` 的弱式參考設定為 `null` (表示已收集目標物件) 為止。 請注意，在大多數情況下，只需要透過迴圈傳遞一次。 不過，針對在 `AssemblyLoadContext` 中執行之程式碼所建立物件具有完成項的更複雜案例，可能需要更多的傳遞。

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>卸載事件

在某些情況下，載入到自訂 `AssemblyLoadContext` 中的程式碼可能需要在起始卸載時執行一些清除。 例如，可能需要停止執行緒、清除一些強大的 GC 控制代碼等。`Unloading` 事件可用於這類情況。 執行必要清除的處理常式可以連結到這個事件。

### <a name="troubleshoot-unloadability-issues"></a>針對卸載功能問題進行疑難排解

由於卸載的合作本質，您很容易忘記有參考使可回收 `AssemblyLoadContext` 的內容保持運作並防止其卸載。 以下摘要說明可以保存參考的項目 (其中一些不明顯)：

- 從可回收 `AssemblyLoadContext` 外部保留，儲存於堆疊位置或處理器暫存器 (方法區域變數，由使用者程式碼明確建立或由 JIT 隱含建立)、靜態變數或強式/固定 GC 控制代碼，以及以可傳遞方式指向下列項目的一般參考：
  - 載入到可回收 `AssemblyLoadContext` 中的組件。
  - 來自這類組件的類型。
  - 來自這類組件類型的執行個體。
- 從載入到可回收 `AssemblyLoadContext` 之組件執行程式碼的執行緒。
- 在可回收 `AssemblyLoadContext` 內部建立之自訂非可回收 `AssemblyLoadContext` 類型的執行個體
- 將回呼設定為自訂 `AssemblyLoadContext` 中方法的擱置 <xref:System.Threading.RegisteredWaitHandle> 執行個體

尋找將物件設為根的堆疊位置/處理器暫存器提示：

- 直接將函式呼叫結果傳遞至另一個函式可能會建立根，即使沒有任何使用者建立的區域變數也一樣。
- 如果在方法的任何時間點都可以使用物件參考，JIT 可能會決定在堆疊位置/處理器暫存器中保留參考，只要它想在目前的函式中如此做時。

## <a name="debug-unloading-issues"></a>對卸載問題進行偵錯

對卸載問題進行偵錯可能很繁瑣。 您可能會遇到以下狀況：您不知道哪些項目可以使 `AssemblyLoadContext` 保持運作，但是卸載會失敗。
協助此問題之最佳武器是含有 SOS 外掛程式的 WinDbg (UNIX 上的 LLDB)。 您必須找出讓 `LoaderAllocator` (其屬於特定 `AssemblyLoadContext`) 保持運作的項目。
此外掛程式可讓您查看 GC 堆積物件、其階層及根。
若要將外掛程式載入到偵錯工具，請在偵錯工具命令列中輸入下列命令：

在 WinDbg 中 (WinDbg 似乎會在中斷至 .NET Core 應用程式時自動執行該操作)：

```console
.loadby sos coreclr
```

在 LLDB 中：

```console
plugin load /path/to/libsosplugin.so
```

讓我們嘗試對卸載發生問題的範例程式進行偵錯。 原始程式碼包含在以下內容中。 當您在 WinDbg 底下執行它時，程式會在嘗試檢查卸載是否成功之後，立即中斷至偵錯工具。 然後，您就可以開始尋找原因。

請注意，如果您在 UNIX 上使用 LLDB 進行偵錯，則下列範例中 SOS 命令的前面不會有 `!`。

```console
!dumpheap -type LoaderAllocator
```

此命令會傾印 GC 堆積中類型名稱包含 `LoaderAllocator` 的所有物件。 請看以下範例：

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

在下面的 "Statistics:" 部分中，檢查屬於 `System.Reflection.LoaderAllocator` 的 `MT` (`MethodTable`)，這是我們關注的物件。 然後在開頭的清單中，尋找 `MT` 與其相符的項目，並取得物件本身的位址。 在我們的案例中，其為 "000002b78000ce40"

現在我們知道 `LoaderAllocator` 物件的位址，就可以使用另一個命令來尋找其 GC 根

```console
!gcroot -all 0x000002b78000ce40 
```

此命令會傾印導致 `LoaderAllocator` 執行個體的物件參考鏈。 此清單以根為開頭，這是可使 `LoaderAllocator` 保持運作的實體，因此是您進行偵錯的問題核心。 根可以是堆疊位置、處理器暫存器、GC 控制代碼或靜態變數。

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

現在您必須找出根的所在位置，以便能夠進行修正。 最簡單的情況是當根為堆疊位置或處理器暫存器時。 在此情況下，`gcroot` 會顯示其框架包含根的函式名稱；以及執行該函式的執行緒。 困難的情況是當根為靜態變數或 GC 控制代碼時。 

在上一個範例中，第一個根是類型為 `System.Reflection.RuntimeMethodInfo` 的區域變數，儲存在函式 `example.Program.Main(System.String[])` 的框架中，位址為 `rbp-20` (`rbp` 是處理器暫存器 `rbp`，-20 是該暫存器中的十六進位位移)。

第二個根是標準 (強式) `GCHandle`，它會保存 `test.Test` 類別執行個體的參考。 

第三個根是固定的 `GCHandle`。 這個根實際上是靜態變數。 可惜的是，沒有辦法加以確認。 參考型別靜態變數會儲存在內部執行階段結構的受控物件陣列中。

另一個可以防止卸載 `AssemblyLoadContext` 的情況，就是當執行緒具有組件的方法框架，而該組件已載入到其堆疊的 `AssemblyLoadContext` 時。 您可以藉由傾印所有執行緒的受控呼叫堆疊來進行檢查：

```console
~*e !clrstack
```

此命令表示「將 `!clrstack` 命令套用到所有執行緒」。 下列是此範例中該命令的輸出。 可惜的是，UNIX 上的 LLDB 沒有任何方法可以將命令套用到所有執行緒，因此您必須設法手動切換執行緒，並重複 `clrstack` 命令。
請忽略偵錯工具顯示「無法查核受控堆疊」的所有執行緒。

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

下列程式碼表示在主要測試程式中傳遞至 `ExecuteAndUnload` 方法的 `test.dll`。

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
