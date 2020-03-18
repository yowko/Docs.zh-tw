---
title: 如何使用 .NET Core 中的組件卸載功能及對其進行偵錯
description: 了解如何使用可回收 AssemblyLoadContext 來載入和卸載受控組件，以及如何對導致卸載失敗的問題進行偵錯。
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159737"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="63918-103">如何使用 .NET Core 中的組件卸載功能及對其進行偵錯</span><span class="sxs-lookup"><span data-stu-id="63918-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="63918-104">從 .NET Core 3.0 開始，支援載入及稍後卸載一組組件的功能。</span><span class="sxs-lookup"><span data-stu-id="63918-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="63918-105">在 .NET Framework 中，自訂應用程式定義域已用於此用途，但 .NET Core 僅支援單一預設應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="63918-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="63918-106">.NET Core 3.0 和更新版本透過 <xref:System.Runtime.Loader.AssemblyLoadContext> 支援卸載功能。</span><span class="sxs-lookup"><span data-stu-id="63918-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="63918-107">您可以將一組組件載入可回收 `AssemblyLoadContext`，在其中執行方法，或只使用反映進行檢查，最後卸載 `AssemblyLoadContext`。</span><span class="sxs-lookup"><span data-stu-id="63918-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="63918-108">將卸載載入到 的`AssemblyLoadContext`程式集。</span><span class="sxs-lookup"><span data-stu-id="63918-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="63918-109">使用 `AssemblyLoadContext` 與使用 AppDomain 卸載之間有一個值得注意的差異。</span><span class="sxs-lookup"><span data-stu-id="63918-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="63918-110">使用 AppDomain 時，會強制卸載。</span><span class="sxs-lookup"><span data-stu-id="63918-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="63918-111">卸載時，目標 AppDomain 中運行的所有線程都已中止，目標 AppDomain 中創建的託管 COM 物件將銷毀，等等。</span><span class="sxs-lookup"><span data-stu-id="63918-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="63918-112">使用 `AssemblyLoadContext` 時，卸載為「合作」。</span><span class="sxs-lookup"><span data-stu-id="63918-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="63918-113">呼叫 <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> 方法只會起始卸載。</span><span class="sxs-lookup"><span data-stu-id="63918-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="63918-114">卸載會在下列情況之後完成：</span><span class="sxs-lookup"><span data-stu-id="63918-114">The unloading finishes after:</span></span>

- <span data-ttu-id="63918-115">沒有任何執行緒會將組件中方法載入到其呼叫堆疊上的 `AssemblyLoadContext`。</span><span class="sxs-lookup"><span data-stu-id="63918-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="63918-116">載入到這些類型的 的`AssemblyLoadContext`程式集中，沒有一種類型的類型，並且程式集本身都引用於：</span><span class="sxs-lookup"><span data-stu-id="63918-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="63918-117">`AssemblyLoadContext` 外部的參考，但弱式參考 (<xref:System.WeakReference> 或 <xref:System.WeakReference%601>) 除外。</span><span class="sxs-lookup"><span data-stu-id="63918-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="63918-118">強垃圾回收器 （GC） 控制碼 （[GCHandleType.正常](xref:System.Runtime.InteropServices.GCHandleType.Normal)或[GCHandleType.固定](xref:System.Runtime.InteropServices.GCHandleType.Pinned)）`AssemblyLoadContext`從 內部和外部 。</span><span class="sxs-lookup"><span data-stu-id="63918-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="63918-119">使用可收集程式集載入上下文</span><span class="sxs-lookup"><span data-stu-id="63918-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="63918-120">本節包含詳細的逐步教學課程，示範將 .NET Core 應用程式載入可回收 `AssemblyLoadContext`，執行其進入點，然後將其卸載的簡單方式。</span><span class="sxs-lookup"><span data-stu-id="63918-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="63918-121">您可以在 中找到完整的示例。 [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)</span><span class="sxs-lookup"><span data-stu-id="63918-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="63918-122">建立可回收 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="63918-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="63918-123">您必須從 <xref:System.Runtime.Loader.AssemblyLoadContext> 衍生類別，並多載其 <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="63918-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="63918-124">該方法會解析所有組件的參考，這些組件是載入到該 `AssemblyLoadContext` 的組件相依性。</span><span class="sxs-lookup"><span data-stu-id="63918-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="63918-125">下列程式碼是最簡單的自訂 `AssemblyLoadContext` 範例：</span><span class="sxs-lookup"><span data-stu-id="63918-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="63918-126">如您所見，`Load` 方法會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="63918-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="63918-127">這表示所有相依性組件都會載入到預設內容，而新的內容只會包含明確載入其中的組件。</span><span class="sxs-lookup"><span data-stu-id="63918-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="63918-128">如果您也想要將部分或所有相依性載入到 `AssemblyLoadContext`，則可以在 `Load` 方法中使用 `AssemblyDependencyResolver`。</span><span class="sxs-lookup"><span data-stu-id="63918-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="63918-129">將`AssemblyDependencyResolver`程式集名稱解析為絕對程式集檔路徑。</span><span class="sxs-lookup"><span data-stu-id="63918-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="63918-130">解析程式使用載入到上下文中的主程式集目錄中的 *.deps.json*檔和程式集檔。</span><span class="sxs-lookup"><span data-stu-id="63918-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="63918-131">使用自訂的可回收 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="63918-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="63918-132">本節假設使用的是較簡單的 `TestAssemblyLoadContext` 版本。</span><span class="sxs-lookup"><span data-stu-id="63918-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="63918-133">您可以建立自訂 `AssemblyLoadContext` 的執行個體，並將組件載入到其中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="63918-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="63918-134">針對已載入組件所參考的每個組件，會呼叫 `TestAssemblyLoadContext.Load` 方法，讓 `TestAssemblyLoadContext` 能夠決定從中取得組件的位置。</span><span class="sxs-lookup"><span data-stu-id="63918-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="63918-135">在我們的案例中，它會傳回 `null`，指出應該從執行階段預設用來載入組件的位置載入預設內容。</span><span class="sxs-lookup"><span data-stu-id="63918-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="63918-136">現在已載入組件，您就可以從中執行一個方法。</span><span class="sxs-lookup"><span data-stu-id="63918-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="63918-137">請執行 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="63918-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="63918-138">在 `Main` 方法傳回之後，您可以藉由在自訂的 `AssemblyLoadContext` 上呼叫 `Unload` 方法，或去除您對 `AssemblyLoadContext` 的參考來起始卸載：</span><span class="sxs-lookup"><span data-stu-id="63918-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="63918-139">這便足以卸載測試組件。</span><span class="sxs-lookup"><span data-stu-id="63918-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="63918-140">讓我們將這些全都放入個別的非內嵌方法，以確保 `TestAssemblyLoadContext`、`Assembly` 和 `MethodInfo` (`Assembly.EntryPoint`) 無法透過堆疊位置參考 (實際或 JIT 引入的區域變數) 保持運作。</span><span class="sxs-lookup"><span data-stu-id="63918-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="63918-141">這可能會使 `TestAssemblyLoadContext` 保持運作，並防止其卸載。</span><span class="sxs-lookup"><span data-stu-id="63918-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="63918-142">此外，會傳回對 `AssemblyLoadContext` 的弱式參考，讓您能夠在稍後使用它來偵測卸載是否完成。</span><span class="sxs-lookup"><span data-stu-id="63918-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="63918-143">現在，您可以執行此函式來載入、執行及卸載組件。</span><span class="sxs-lookup"><span data-stu-id="63918-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="63918-144">不過，卸載不會立即完成。</span><span class="sxs-lookup"><span data-stu-id="63918-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="63918-145">如前所述，它依賴于垃圾回收器從測試程式集收集所有物件。</span><span class="sxs-lookup"><span data-stu-id="63918-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="63918-146">在許多情況下，並不需要等候卸載完成。</span><span class="sxs-lookup"><span data-stu-id="63918-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="63918-147">不過，在某些情況下，知道卸載已經完成是很有用的。</span><span class="sxs-lookup"><span data-stu-id="63918-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="63918-148">例如，您可能想要刪除從磁碟載入到自訂 `AssemblyLoadContext` 的組件檔。</span><span class="sxs-lookup"><span data-stu-id="63918-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="63918-149">在這種情況下，可以使用下列程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="63918-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="63918-150">它觸發垃圾回收，並在迴圈中等待掛起的終端子，直到對自訂`AssemblyLoadContext`的弱引用設置為`null`，指示已收集目標物件。</span><span class="sxs-lookup"><span data-stu-id="63918-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="63918-151">在大多數情況下，只需要一個通過迴圈。</span><span class="sxs-lookup"><span data-stu-id="63918-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="63918-152">不過，針對在 `AssemblyLoadContext` 中執行之程式碼所建立物件具有完成項的更複雜案例，可能需要更多的傳遞。</span><span class="sxs-lookup"><span data-stu-id="63918-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="63918-153">卸載事件</span><span class="sxs-lookup"><span data-stu-id="63918-153">The Unloading event</span></span>

<span data-ttu-id="63918-154">在某些情況下，載入到自訂 `AssemblyLoadContext` 中的程式碼可能需要在起始卸載時執行一些清除。</span><span class="sxs-lookup"><span data-stu-id="63918-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="63918-155">例如，它可能需要停止執行緒或清理強大的 GC 控制碼。</span><span class="sxs-lookup"><span data-stu-id="63918-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="63918-156">`Unloading` 事件可用於這類情況。</span><span class="sxs-lookup"><span data-stu-id="63918-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="63918-157">執行必要清除的處理常式可以連結到這個事件。</span><span class="sxs-lookup"><span data-stu-id="63918-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="63918-158">針對卸載功能問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="63918-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="63918-159">由於卸載的協作性質，很容易忘記可能將材料保留在收藏品`AssemblyLoadContext`中並防止卸載的引用。</span><span class="sxs-lookup"><span data-stu-id="63918-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="63918-160">下面是可以保存引用的實體（其中一些非明顯）的摘要：</span><span class="sxs-lookup"><span data-stu-id="63918-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="63918-161">從存儲在堆疊插槽或處理器寄存器中的`AssemblyLoadContext`收藏品外部持有的常規引用（方法區域變數，由使用者代碼顯式創建，或由及時 （JIT） 編譯器隱式創建）、靜態變數或強（固定）GC 控制碼，並傳遞指向：</span><span class="sxs-lookup"><span data-stu-id="63918-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="63918-162">載入到可回收 `AssemblyLoadContext` 中的組件。</span><span class="sxs-lookup"><span data-stu-id="63918-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="63918-163">來自這類組件的類型。</span><span class="sxs-lookup"><span data-stu-id="63918-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="63918-164">來自這類組件類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63918-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="63918-165">從載入到可回收 `AssemblyLoadContext` 之組件執行程式碼的執行緒。</span><span class="sxs-lookup"><span data-stu-id="63918-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="63918-166">在收藏品`AssemblyLoadContext``AssemblyLoadContext`中創建的自訂、不可收藏類型的實例。</span><span class="sxs-lookup"><span data-stu-id="63918-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="63918-167">將<xref:System.Threading.RegisteredWaitHandle>回檔設置為自訂`AssemblyLoadContext`中的方法的掛起實例。</span><span class="sxs-lookup"><span data-stu-id="63918-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="63918-168">存儲在堆疊插槽或處理器寄存器中且可能阻止卸載的物件引用`AssemblyLoadContext`可能發生在以下情況下：</span><span class="sxs-lookup"><span data-stu-id="63918-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="63918-169">當函式呼叫結果直接傳遞到另一個函數時，即使沒有使用者創建的區域變數。</span><span class="sxs-lookup"><span data-stu-id="63918-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="63918-170">當 JIT 編譯器保留對方法中某個點可用的物件的引用時。</span><span class="sxs-lookup"><span data-stu-id="63918-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="63918-171">對卸載問題進行偵錯</span><span class="sxs-lookup"><span data-stu-id="63918-171">Debug unloading issues</span></span>

<span data-ttu-id="63918-172">對卸載問題進行偵錯可能很繁瑣。</span><span class="sxs-lookup"><span data-stu-id="63918-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="63918-173">您可能會遇到以下狀況：您不知道哪些項目可以使 `AssemblyLoadContext` 保持運作，但是卸載會失敗。</span><span class="sxs-lookup"><span data-stu-id="63918-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="63918-174">協助此問題之最佳武器是含有 SOS 外掛程式的 WinDbg (UNIX 上的 LLDB)。</span><span class="sxs-lookup"><span data-stu-id="63918-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="63918-175">您必須找出讓 `LoaderAllocator` (其屬於特定 `AssemblyLoadContext`) 保持運作的項目。</span><span class="sxs-lookup"><span data-stu-id="63918-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="63918-176">SOS 外掛程式允許您查看 GC 堆物件、其層次結構和根。</span><span class="sxs-lookup"><span data-stu-id="63918-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="63918-177">若要將外掛程式載入到偵錯工具，請在偵錯工具命令列中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="63918-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="63918-178">在 WinDbg 中 (WinDbg 似乎會在中斷至 .NET Core 應用程式時自動執行該操作)：</span><span class="sxs-lookup"><span data-stu-id="63918-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="63918-179">在 LLDB 中：</span><span class="sxs-lookup"><span data-stu-id="63918-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="63918-180">讓我們調試一個在卸載時出現問題的示常式序。</span><span class="sxs-lookup"><span data-stu-id="63918-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="63918-181">原始程式碼包含在以下內容中。</span><span class="sxs-lookup"><span data-stu-id="63918-181">Source code is included below.</span></span> <span data-ttu-id="63918-182">當您在 WinDbg 底下執行它時，程式會在嘗試檢查卸載是否成功之後，立即中斷至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="63918-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="63918-183">然後，您就可以開始尋找原因。</span><span class="sxs-lookup"><span data-stu-id="63918-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="63918-184">如果在 Unix 上使用 LLDB 進行調試，則以下示例中的 SOS 命令`!`前面沒有。</span><span class="sxs-lookup"><span data-stu-id="63918-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="63918-185">此命令會傾印 GC 堆積中類型名稱包含 `LoaderAllocator` 的所有物件。</span><span class="sxs-lookup"><span data-stu-id="63918-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="63918-186">範例如下：</span><span class="sxs-lookup"><span data-stu-id="63918-186">Here is an example:</span></span>

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

<span data-ttu-id="63918-187">在下面的 "Statistics:" 部分中，檢查屬於 `System.Reflection.LoaderAllocator` 的 `MT` (`MethodTable`)，這是我們關注的物件。</span><span class="sxs-lookup"><span data-stu-id="63918-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="63918-188">然後，在開頭的清單中，找到匹配`MT`該條目的條目，並獲取物件本身的位址。</span><span class="sxs-lookup"><span data-stu-id="63918-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="63918-189">在我們的例子中，它是"000002b78000ce40"。</span><span class="sxs-lookup"><span data-stu-id="63918-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="63918-190">現在我們知道了物件的位址，`LoaderAllocator`我們可以使用另一個命令來查找其 GC 根：</span><span class="sxs-lookup"><span data-stu-id="63918-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="63918-191">此命令會傾印導致 `LoaderAllocator` 執行個體的物件參考鏈。</span><span class="sxs-lookup"><span data-stu-id="63918-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="63918-192">清單從根開始，根是保持我們`LoaderAllocator`生存的實體，因此是問題的核心。</span><span class="sxs-lookup"><span data-stu-id="63918-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="63918-193">根可以是堆疊位置、處理器暫存器、GC 控制代碼或靜態變數。</span><span class="sxs-lookup"><span data-stu-id="63918-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="63918-194">以下是 `gcroot` 命令的輸出範例：</span><span class="sxs-lookup"><span data-stu-id="63918-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="63918-195">下一步是找出根的位置，以便您可以修復它。</span><span class="sxs-lookup"><span data-stu-id="63918-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="63918-196">最簡單的情況是當根為堆疊位置或處理器暫存器時。</span><span class="sxs-lookup"><span data-stu-id="63918-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="63918-197">在這種情況下，`gcroot`將顯示其幀包含根和執行該函數的執行緒的函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="63918-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="63918-198">困難的情況是當根為靜態變數或 GC 控制代碼時。</span><span class="sxs-lookup"><span data-stu-id="63918-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="63918-199">在上一個範例中，第一個根是類型為 `System.Reflection.RuntimeMethodInfo` 的區域變數，儲存在函式 `example.Program.Main(System.String[])` 的框架中，位址為 `rbp-20` (`rbp` 是處理器暫存器 `rbp`，-20 是該暫存器中的十六進位位移)。</span><span class="sxs-lookup"><span data-stu-id="63918-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="63918-200">第二個根是標準 (強式) `GCHandle`，它會保存 `test.Test` 類別執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="63918-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="63918-201">第三個根是固定的 `GCHandle`。</span><span class="sxs-lookup"><span data-stu-id="63918-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="63918-202">這個實際上是一個靜態變數，但不幸的是，沒有辦法告訴。</span><span class="sxs-lookup"><span data-stu-id="63918-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="63918-203">參考型別靜態變數會儲存在內部執行階段結構的受控物件陣列中。</span><span class="sxs-lookup"><span data-stu-id="63918-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="63918-204">另一個可以防止卸載 `AssemblyLoadContext` 的情況，就是當執行緒具有組件的方法框架，而該組件已載入到其堆疊的 `AssemblyLoadContext` 時。</span><span class="sxs-lookup"><span data-stu-id="63918-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="63918-205">您可以藉由傾印所有執行緒的受控呼叫堆疊來進行檢查：</span><span class="sxs-lookup"><span data-stu-id="63918-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="63918-206">此命令表示「將 `!clrstack` 命令套用到所有執行緒」。</span><span class="sxs-lookup"><span data-stu-id="63918-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="63918-207">下列是此範例中該命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="63918-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="63918-208">遺憾的是，Unix 上的 LLDB 沒有任何方法對所有線程應用命令，因此您必須手動切換執行緒並重複該`clrstack`命令。</span><span class="sxs-lookup"><span data-stu-id="63918-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="63918-209">忽略調試器說"無法遍歷託管堆疊"的所有線程。</span><span class="sxs-lookup"><span data-stu-id="63918-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="63918-210">如您所見，最後一個執行緒具有 `test.Program.ThreadProc()`。</span><span class="sxs-lookup"><span data-stu-id="63918-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="63918-211">這是載入到 `AssemblyLoadContext` 的組件中函式，因此它會使 `AssemblyLoadContext` 保持運作。</span><span class="sxs-lookup"><span data-stu-id="63918-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="63918-212">具有卸載功能問題的範例來源</span><span class="sxs-lookup"><span data-stu-id="63918-212">Example source with unloadability issues</span></span>

<span data-ttu-id="63918-213">在先前的偵錯範例中使用了下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="63918-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="63918-214">主要測試程式</span><span class="sxs-lookup"><span data-stu-id="63918-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="63918-215">載入到 TestAssemblyLoadContext 的程式</span><span class="sxs-lookup"><span data-stu-id="63918-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="63918-216">以下代碼表示傳遞給主測試程式中`ExecuteAndUnload`的方法的*test.dll。*</span><span class="sxs-lookup"><span data-stu-id="63918-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
