---
title: "如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6102274f75d2fe66b89f917cf9095d3a6dfaa3e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-parallelforeach-loop-with-thread-local-variables"></a><span data-ttu-id="5b661-102">如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="5b661-102">How to: Write a Parallel.ForEach Loop with Thread-Local Variables</span></span>
<span data-ttu-id="5b661-103">下列範例說明如何撰寫使用執行緒區域變數的 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5b661-103">The following example shows how to write a <xref:System.Threading.Tasks.Parallel.ForEach%2A> method that uses thread-local variables.</span></span> <span data-ttu-id="5b661-104">當 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈執行時，它會將其來源集合分成多個分割。</span><span class="sxs-lookup"><span data-stu-id="5b661-104">When a <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop executes, it divides its source collection into multiple partitions.</span></span> <span data-ttu-id="5b661-105">每個分割會有自己的「執行緒區域」變數複本</span><span class="sxs-lookup"><span data-stu-id="5b661-105">Each partition will get its own copy of the "thread-local" variable.</span></span> <span data-ttu-id="5b661-106">(這裡用「執行緒區域」一詞有點不正確，因為有時會有兩個分割在同一個執行緒上執行)。</span><span class="sxs-lookup"><span data-stu-id="5b661-106">(The term "thread-local" is slightly inaccurate here, because in some cases two partitions may run on the same thread.)</span></span>  
  
 <span data-ttu-id="5b661-107">這個範例中的程式碼和參數非常類似於對應的 <xref:System.Threading.Tasks.Parallel.For%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5b661-107">The code and parameters in this example closely resemble the corresponding <xref:System.Threading.Tasks.Parallel.For%2A> method.</span></span> <span data-ttu-id="5b661-108">如需詳細資訊，請參閱[How to： 撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="5b661-108">For more information, see [How to: Write a Parallel.For Loop with Thread-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).</span></span>  
  
 <span data-ttu-id="5b661-109">若要在 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈中使用執行緒區域變數，您必須呼叫使用兩個類型參數的其中一個方法多載。</span><span class="sxs-lookup"><span data-stu-id="5b661-109">To use a thread-local variable in a <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop, you must call one of the method overloads that takes two type parameters.</span></span> <span data-ttu-id="5b661-110">第一個類型參數 `TSource` 指定來源項目的類型，而第二個類型參數 `TLocal` 則指定執行緒區域變數的類型。</span><span class="sxs-lookup"><span data-stu-id="5b661-110">The first type parameter, `TSource`, specifies the type of the source element, and the second type parameter, `TLocal`, specifies the type of the thread-local variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b661-111">範例</span><span class="sxs-lookup"><span data-stu-id="5b661-111">Example</span></span>  
 <span data-ttu-id="5b661-112">下列範例呼叫 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 多載，以計算一百萬個項目之陣列的總和。</span><span class="sxs-lookup"><span data-stu-id="5b661-112">The following example calls <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> overload to compute the sum of an array of one million elements.</span></span> <span data-ttu-id="5b661-113">此多載包含四個參數：</span><span class="sxs-lookup"><span data-stu-id="5b661-113">This overload has four parameters:</span></span>  
  
-   <span data-ttu-id="5b661-114">`source`，這是資料來源。</span><span class="sxs-lookup"><span data-stu-id="5b661-114">`source`, which is the data source.</span></span> <span data-ttu-id="5b661-115">它必須實作 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="5b661-115">It must implement <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="5b661-116">在我們的範例中，資料來源是 `IEnumerable<Int32>` 方法傳回的一百萬個成員 <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="5b661-116">The data source in our example is the one million member `IEnumerable<Int32>` object returned by the <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="5b661-117">`localInit`，或初始化執行緒區域變數的函式。</span><span class="sxs-lookup"><span data-stu-id="5b661-117">`localInit`, or the function that initializes the thread-local variable.</span></span> <span data-ttu-id="5b661-118">此函式會針對 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 作業執行所在的每個分割呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="5b661-118">This function is called once for each partition in which the <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> operation executes.</span></span> <span data-ttu-id="5b661-119">我們的範例會將執行緒區域變數初始化為零。</span><span class="sxs-lookup"><span data-stu-id="5b661-119">Our example initializes the thread-local variable to zero.</span></span>  
  
-   <span data-ttu-id="5b661-120">`body`，這是平行迴圈在迴圈的每個反覆項目上叫用的 <xref:System.Func%604>。</span><span class="sxs-lookup"><span data-stu-id="5b661-120">`body`, a <xref:System.Func%604> that is invoked by the parallel loop on each iteration of the loop.</span></span> <span data-ttu-id="5b661-121">其簽章為 `Func\<TSource, ParallelLoopState, TLocal, TLocal>`。</span><span class="sxs-lookup"><span data-stu-id="5b661-121">Its signature is `Func\<TSource, ParallelLoopState, TLocal, TLocal>`.</span></span> <span data-ttu-id="5b661-122">您會提供委派的程式碼，而迴圈會傳入輸入參數，包括：</span><span class="sxs-lookup"><span data-stu-id="5b661-122">You supply the code for the delegate, and the loop passes in the input parameters, which are:</span></span>  
  
    -   <span data-ttu-id="5b661-123"><xref:System.Collections.Generic.IEnumerable%601> 的目前項目。</span><span class="sxs-lookup"><span data-stu-id="5b661-123">The current element of the <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
    -   <span data-ttu-id="5b661-124">可用於委派的程式碼中以檢查迴圈狀態的 <xref:System.Threading.Tasks.ParallelLoopState> 變數。</span><span class="sxs-lookup"><span data-stu-id="5b661-124">A <xref:System.Threading.Tasks.ParallelLoopState> variable that you can use in your delegate's code to examine the state of the loop.</span></span>  
  
    -   <span data-ttu-id="5b661-125">執行緒區域變數。</span><span class="sxs-lookup"><span data-stu-id="5b661-125">The thread-local variable.</span></span>  
  
     <span data-ttu-id="5b661-126">您的委派會傳回執行緒區域變數，該變數接著會傳遞給該特定分割中所執行之迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="5b661-126">Your delegate returns the thread-local variable, which is then passed to the next iteration of the loop that executes in that particular partition.</span></span> <span data-ttu-id="5b661-127">每個迴圈分割會保留此變數的個別執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b661-127">Each loop partition maintains a separate instance of this variable.</span></span>  
  
     <span data-ttu-id="5b661-128">在這個範例中，委派會將每個整數的值加入至執行緒區域變數，以維護該分割中整數值項目的累積總計。</span><span class="sxs-lookup"><span data-stu-id="5b661-128">In the example, the delegate adds the value of each integer to the thread-local variable, which maintains a running total of the values of the integer elements in that partition.</span></span>  
  
-   <span data-ttu-id="5b661-129">`localFinally`，這是當每個分割的迴圈作業完成時，`Action<TLocal>` 所叫用的 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 委派。</span><span class="sxs-lookup"><span data-stu-id="5b661-129">`localFinally`, an `Action<TLocal>` delegate that the <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> invokes when the looping operations in each partition have completed.</span></span> <span data-ttu-id="5b661-130"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法會將此執行緒 (或迴圈分割) 之執行緒區域變數的最後一個值傳遞給 `Action<TLocal>` 委派，而您會提供程式碼，以執行為了合併此分割中的結果與其餘分割中的結果所需的動作。</span><span class="sxs-lookup"><span data-stu-id="5b661-130">The <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> method passes your `Action<TLocal>` delegate the final value of the thread-local variable for this thread (or loop partition), and you provide the code that performs the required action for combining the result from this partition with the results from the other partitions.</span></span> <span data-ttu-id="5b661-131">這個委派可由多個工作同時叫用。</span><span class="sxs-lookup"><span data-stu-id="5b661-131">This delegate can be invoked concurrently by multiple tasks.</span></span> <span data-ttu-id="5b661-132">因此，此範例使用 <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> 方法來同步處理對 `total` 變數的存取。</span><span class="sxs-lookup"><span data-stu-id="5b661-132">Because of this, the example uses the <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> method to synchronize access to the `total` variable.</span></span> <span data-ttu-id="5b661-133">由於委派類型是 <xref:System.Action%601>，因此不會有傳回值。</span><span class="sxs-lookup"><span data-stu-id="5b661-133">Because the delegate type is an <xref:System.Action%601>, there is no return value.</span></span>  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="5b661-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b661-134">See Also</span></span>  
 [<span data-ttu-id="5b661-135">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="5b661-135">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="5b661-136">操作說明：撰寫含有執行緒區域變數的 Parallel.For 迴圈</span><span class="sxs-lookup"><span data-stu-id="5b661-136">How to: Write a Parallel.For Loop with Thread-Local Variables</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [<span data-ttu-id="5b661-137">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="5b661-137">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
