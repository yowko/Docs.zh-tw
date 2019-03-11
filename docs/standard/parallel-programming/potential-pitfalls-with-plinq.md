---
title: 使用 PLINQ 時可能出現的錯誤
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b996b09ed3973125d4d848d5e00c18ab02a6967
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673739"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="91a5b-102">使用 PLINQ 時可能出現的錯誤</span><span class="sxs-lookup"><span data-stu-id="91a5b-102">Potential Pitfalls with PLINQ</span></span>

<span data-ttu-id="91a5b-103">在許多情況下，相較於循序 LINQ to Objects 查詢，PLINQ 更能提供顯著的效能改良。</span><span class="sxs-lookup"><span data-stu-id="91a5b-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="91a5b-104">不過，平行處理查詢執行的工作所帶來的複雜性可能會造成問題，而在循序程式碼中，這些問題不是不常見，就是完全不會發生。</span><span class="sxs-lookup"><span data-stu-id="91a5b-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="91a5b-105">本主題列出一些您在撰寫 PLINQ 查詢時應該避免的作法。</span><span class="sxs-lookup"><span data-stu-id="91a5b-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="91a5b-106">不要認為平行一定比較快</span><span class="sxs-lookup"><span data-stu-id="91a5b-106">Do Not Assume That Parallel Is Always Faster</span></span>

<span data-ttu-id="91a5b-107">有時平行處理會導致 PLINQ 查詢的執行速度比其 LINQ to Objects 對等項慢。</span><span class="sxs-lookup"><span data-stu-id="91a5b-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="91a5b-108">基本的經驗法則是，來源元素不多且使用者委派速度很快的查詢不太可能加快多少速度。</span><span class="sxs-lookup"><span data-stu-id="91a5b-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="91a5b-109">不過，因為效能牽涉到許多因素，建議您先測量實際的結果後再決定是否要使用 PLINQ。</span><span class="sxs-lookup"><span data-stu-id="91a5b-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="91a5b-110">如需詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="91a5b-111">避免寫入共用的記憶體位置</span><span class="sxs-lookup"><span data-stu-id="91a5b-111">Avoid Writing to Shared Memory Locations</span></span>

<span data-ttu-id="91a5b-112">循序程式碼經常會讀取或寫入靜態變數或類別欄位。</span><span class="sxs-lookup"><span data-stu-id="91a5b-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="91a5b-113">不過，每當有多個執行緒同時存取這類變數時，就很可能產生競爭情形。</span><span class="sxs-lookup"><span data-stu-id="91a5b-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="91a5b-114">即便您可以使用鎖定來同步處理變數的存取，同步處理的成本也會減損效能。</span><span class="sxs-lookup"><span data-stu-id="91a5b-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="91a5b-115">因此，建議您盡可能避免在 PLINQ 查詢中存取共用狀態，或至少做出限制。</span><span class="sxs-lookup"><span data-stu-id="91a5b-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="91a5b-116">避免過度平行處理</span><span class="sxs-lookup"><span data-stu-id="91a5b-116">Avoid Over-Parallelization</span></span>

<span data-ttu-id="91a5b-117">使用 `AsParallel` 運算子時，您會因為分割來源集合和同步處理背景工作執行緒而產生額外成本。</span><span class="sxs-lookup"><span data-stu-id="91a5b-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="91a5b-118">電腦上的處理器數目則會進一步限制平行處理的好處。</span><span class="sxs-lookup"><span data-stu-id="91a5b-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="91a5b-119">多個計算繫結執行緒若只在一個處理器上執行，系統並不會獲得任何加速效果。</span><span class="sxs-lookup"><span data-stu-id="91a5b-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="91a5b-120">因此，您必須注意不要過度平行處理查詢。</span><span class="sxs-lookup"><span data-stu-id="91a5b-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="91a5b-121">最常發生過度平行處理的情況是在巢狀查詢中，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="91a5b-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="91a5b-122">在此情況下，除非適用下列一或多個條件，否則最好只平行處理外部資料來源 (客戶)︰</span><span class="sxs-lookup"><span data-stu-id="91a5b-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="91a5b-123">目前已知內部資料來源 (cust.Orders) 很長。</span><span class="sxs-lookup"><span data-stu-id="91a5b-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="91a5b-124">您正在對每個順序執行昂貴的計算 </span><span class="sxs-lookup"><span data-stu-id="91a5b-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="91a5b-125">(範例所示作業並不昂貴)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="91a5b-126">已知目標系統有足夠的處理器，可處理因為在 `cust.Orders` 上平行處理查詢而會產生的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="91a5b-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="91a5b-127">在上述所有情況下，若要判斷最佳的查詢形狀，最好的方式是測試和測量。</span><span class="sxs-lookup"><span data-stu-id="91a5b-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="91a5b-128">如需詳細資訊，請參閱[如何：測量 PLINQ 查詢效能](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="91a5b-129">避免呼叫非安全執行緒的方法</span><span class="sxs-lookup"><span data-stu-id="91a5b-129">Avoid Calls to Non-Thread-Safe Methods</span></span>

<span data-ttu-id="91a5b-130">從 PLINQ 查詢寫入到非安全執行緒執行個體方法的作業，可能會導致資料損毀，而您的程式不一定會偵測到。</span><span class="sxs-lookup"><span data-stu-id="91a5b-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="91a5b-131">這樣的作業也可能會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91a5b-131">It can also lead to exceptions.</span></span> <span data-ttu-id="91a5b-132">在下列範例中，多個執行緒會嘗試同時呼叫 `FileStream.Write` 方法，但該類別並不支援這麼做。</span><span class="sxs-lookup"><span data-stu-id="91a5b-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="91a5b-133">限制安全執行緒方法的呼叫</span><span class="sxs-lookup"><span data-stu-id="91a5b-133">Limit Calls to Thread-Safe Methods</span></span>

<span data-ttu-id="91a5b-134">.NET Framework 中的大部分靜態方法都是安全執行緒，並可從多個執行緒同時呼叫。</span><span class="sxs-lookup"><span data-stu-id="91a5b-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="91a5b-135">不過，即使在這些情況下，所牽涉到的同步處理作業也可能會導致查詢速度顯著變慢。</span><span class="sxs-lookup"><span data-stu-id="91a5b-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="91a5b-136">您可以自行測試這一點，方法是在您的查詢中插入一些 <xref:System.Console.WriteLine%2A> 呼叫。</span><span class="sxs-lookup"><span data-stu-id="91a5b-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="91a5b-137">雖然本文件的範例使用這個方法來做示範，但請勿將它用在 PLINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="91a5b-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="91a5b-138">避免不必要的排序作業</span><span class="sxs-lookup"><span data-stu-id="91a5b-138">Avoid Unnecessary Ordering Operations</span></span>

<span data-ttu-id="91a5b-139">當 PLINQ 以平行方式執行查詢時，它會將來源序列分割成可在多個執行緒同時運作的分割區。</span><span class="sxs-lookup"><span data-stu-id="91a5b-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="91a5b-140">根據預設，處理分割區和傳送結果的順序是無法預測的 (除了 `OrderBy` 之類的運算子以外)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="91a5b-141">您可以指示 PLINQ 保留任一來源序列的順序，但這對效能有負面影響。</span><span class="sxs-lookup"><span data-stu-id="91a5b-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="91a5b-142">可能的話，最佳做法是建構查詢，讓它們不會依賴順序保留。</span><span class="sxs-lookup"><span data-stu-id="91a5b-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="91a5b-143">如需詳細資訊，請參閱 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="91a5b-144">盡可能使用 ForAll 代替 ForEach</span><span class="sxs-lookup"><span data-stu-id="91a5b-144">Prefer ForAll to ForEach When It Is Possible</span></span>

<span data-ttu-id="91a5b-145">雖然 PLINQ 會在多個執行緒上執行查詢，如果您在 `foreach` 迴圈 (Visual Basic 中的 `For Each`) 中使用結果，則必須將查詢結果合併回一個執行緒，並由列舉程式依序存取。</span><span class="sxs-lookup"><span data-stu-id="91a5b-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="91a5b-146">在某些情況下，這是無法避免的；不過，您應該盡可能使用 `ForAll` 方法讓每個執行緒輸出其結果，例如，透過寫入安全執行緒集合 (例如 <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="91a5b-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="91a5b-147">相同問題適用於 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。換句話說，`source.AsParallel().Where().ForAll(...)` 應該比</span><span class="sxs-lookup"><span data-stu-id="91a5b-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>

<span data-ttu-id="91a5b-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="91a5b-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="91a5b-149">注意執行緒相似性問題</span><span class="sxs-lookup"><span data-stu-id="91a5b-149">Be Aware of Thread Affinity Issues</span></span>

<span data-ttu-id="91a5b-150">有些技術 (例如，適用於單一執行緒 Apartment (STA) 元件、Windows Forms 和 Windows Presentation Foundation (WPF) 的 COM 互通性) 會施加執行緒相似性限制，以要求程式碼在特定執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="91a5b-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="91a5b-151">例如，在 Windows Forms 和 WPF 中，只有用來建立控制項的執行緒能夠存取該控制項。</span><span class="sxs-lookup"><span data-stu-id="91a5b-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="91a5b-152">如果您嘗試存取 PLINQ 查詢中 Windows Forms 控制項的共用狀態，在偵錯工具中執行時會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91a5b-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="91a5b-153">(這項設定可以關閉。)不過，如果您的查詢是在 UI 執行緒上使用，您就能從列舉查詢結果的 `foreach` 迴圈存取控制項，因為該程式碼只會在一個執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="91a5b-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="91a5b-154">不要認為 ForEach、For 和 ForAll 的反覆項目一定要以平行方式執行</span><span class="sxs-lookup"><span data-stu-id="91a5b-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>

<span data-ttu-id="91a5b-155">請記住 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 或 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 迴圈中個別的反覆項目可能會以平行方式執行，但不見得需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="91a5b-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="91a5b-156">因此，您所撰寫的程式碼不應依靠系統是否有正確地平行執行反覆項目，也不應依靠系統是否有正確地以特定順序執行反覆項目。</span><span class="sxs-lookup"><span data-stu-id="91a5b-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="91a5b-157">例如，下列程式碼有可能會發生死結︰</span><span class="sxs-lookup"><span data-stu-id="91a5b-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="91a5b-158">在此範例中，一個反覆項目會設定事件，而其他所有反覆項目則是等候事件。</span><span class="sxs-lookup"><span data-stu-id="91a5b-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="91a5b-159">在事件設定反覆項目完成之前，沒有任何等候中的反覆項目可以完成。</span><span class="sxs-lookup"><span data-stu-id="91a5b-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="91a5b-160">不過，等待中的反覆項目有可能會在事件設定反覆項目有機會執行之前，就封鎖所有用來執行平行迴圈的執行緒。</span><span class="sxs-lookup"><span data-stu-id="91a5b-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="91a5b-161">這會導致死結，事件設定反覆項目永遠不會執行，而等待中的反覆項目也永遠不會醒來。</span><span class="sxs-lookup"><span data-stu-id="91a5b-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="91a5b-162">特別是，平行迴圈的反覆項目永遠不應該等候該迴圈的另一個反覆項目才能繼續。</span><span class="sxs-lookup"><span data-stu-id="91a5b-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="91a5b-163">如果平行迴圈決定以循序方式排程反覆項目，但順序相反，系統就會發生死結。</span><span class="sxs-lookup"><span data-stu-id="91a5b-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="91a5b-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a5b-164">See also</span></span>

- [<span data-ttu-id="91a5b-165">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="91a5b-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
