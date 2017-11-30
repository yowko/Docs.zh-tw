---
title: "使用 PLINQ 時可能出現的錯誤"
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
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="79dfd-102">使用 PLINQ 時可能出現的錯誤</span><span class="sxs-lookup"><span data-stu-id="79dfd-102">Potential Pitfalls with PLINQ</span></span>
<span data-ttu-id="79dfd-103">在許多情況下，PLINQ 可透過物件查詢的循序 LINQ 提供顯著的效能改進。</span><span class="sxs-lookup"><span data-stu-id="79dfd-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="79dfd-104">不過，平行查詢執行的工作會帶來可能會造成問題，在循序程式碼，並不常用，或發生的不完全的複雜性。</span><span class="sxs-lookup"><span data-stu-id="79dfd-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="79dfd-105">本主題列出一些作法，以避免當您撰寫 PLINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="79dfd-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="79dfd-106">不要認為平行一定比較快</span><span class="sxs-lookup"><span data-stu-id="79dfd-106">Do Not Assume That Parallel Is Always Faster</span></span>  
 <span data-ttu-id="79dfd-107">有時平行化作業會導致 PLINQ 查詢執行速度比其 LINQ 物件相等。</span><span class="sxs-lookup"><span data-stu-id="79dfd-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="79dfd-108">基本的經驗法則是，有幾個來源項目和快速的使用者委派的查詢通常不太可能很多。</span><span class="sxs-lookup"><span data-stu-id="79dfd-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="79dfd-109">不過，因為許多因素所相關的效能，建議您在決定是否要使用 PLINQ 之前測量實際結果。</span><span class="sxs-lookup"><span data-stu-id="79dfd-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="79dfd-110">如需詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="79dfd-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="79dfd-111">避免寫入共用的記憶體位置</span><span class="sxs-lookup"><span data-stu-id="79dfd-111">Avoid Writing to Shared Memory Locations</span></span>  
 <span data-ttu-id="79dfd-112">循序程式碼經常會讀取或寫入靜態變數或類別欄位。</span><span class="sxs-lookup"><span data-stu-id="79dfd-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="79dfd-113">不過，每當有多個執行緒同時存取這類變數時，就很可能產生競爭情形。</span><span class="sxs-lookup"><span data-stu-id="79dfd-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="79dfd-114">即便您可以使用鎖定來同步處理變數的存取，同步處理的成本也會減損效能。</span><span class="sxs-lookup"><span data-stu-id="79dfd-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="79dfd-115">因此，我們建議您避免，或至少限制，以盡可能 PLINQ 查詢中的共用狀態存取。</span><span class="sxs-lookup"><span data-stu-id="79dfd-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>  
  
## <a name="avoid-over-parallelization"></a><span data-ttu-id="79dfd-116">避免過度平行處理</span><span class="sxs-lookup"><span data-stu-id="79dfd-116">Avoid Over-Parallelization</span></span>  
 <span data-ttu-id="79dfd-117">使用`AsParallel`運算子，造成資料分割來源集合和同步處理的背景工作執行緒的額外負荷成本。</span><span class="sxs-lookup"><span data-stu-id="79dfd-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="79dfd-118">電腦上的處理器數目則會進一步限制平行處理的好處。</span><span class="sxs-lookup"><span data-stu-id="79dfd-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="79dfd-119">多個計算繫結執行緒若只在一個處理器上執行，系統並不會獲得任何加速效果。</span><span class="sxs-lookup"><span data-stu-id="79dfd-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="79dfd-120">因此，您必須非常小心不過度平行處理查詢。</span><span class="sxs-lookup"><span data-stu-id="79dfd-120">Therefore, you must be careful not to over-parallelize a query.</span></span>  
  
 <span data-ttu-id="79dfd-121">最常見的案例中哪些過度平行處理可以是便會發生中巢狀查詢，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="79dfd-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 <span data-ttu-id="79dfd-122">在此情況下，最好平行處理僅外部資料來源 （客戶），除非套用一或多個下列條件：</span><span class="sxs-lookup"><span data-stu-id="79dfd-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>  
  
-   <span data-ttu-id="79dfd-123">內部資料來源 (cust。訂單） 是否已知為很長。</span><span class="sxs-lookup"><span data-stu-id="79dfd-123">The inner data source (cust.Orders) is known to be very long.</span></span>  
  
-   <span data-ttu-id="79dfd-124">您正在對每個順序執行昂貴的計算 </span><span class="sxs-lookup"><span data-stu-id="79dfd-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="79dfd-125">(範例所示作業並不昂貴)。</span><span class="sxs-lookup"><span data-stu-id="79dfd-125">(The operation shown in the example is not expensive.)</span></span>  
  
-   <span data-ttu-id="79dfd-126">已知目標系統有足夠的處理器，可處理因為在 `cust.Orders` 上平行處理查詢而會產生的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="79dfd-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>  
  
 <span data-ttu-id="79dfd-127">在上述所有情況下，若要判斷最佳的查詢形狀，最好的方式是測試和測量。</span><span class="sxs-lookup"><span data-stu-id="79dfd-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="79dfd-128">如需詳細資訊，請參閱[如何： 測量 PLINQ 查詢效能](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="79dfd-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="79dfd-129">避免呼叫非安全執行緒的方法</span><span class="sxs-lookup"><span data-stu-id="79dfd-129">Avoid Calls to Non-Thread-Safe Methods</span></span>  
 <span data-ttu-id="79dfd-130">寫入至非安全執行緒的執行個體方法，從 PLINQ 查詢可能會導致資料損毀可能會或可能不會在程式中未偵測到。</span><span class="sxs-lookup"><span data-stu-id="79dfd-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="79dfd-131">這樣的作業也可能會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="79dfd-131">It can also lead to exceptions.</span></span> <span data-ttu-id="79dfd-132">在下列範例中，將多個執行緒嘗試呼叫`Filestream.Write`方法同時，不支援類別。</span><span class="sxs-lookup"><span data-stu-id="79dfd-132">In the following example, multiple threads would be attempting to call the `Filestream.Write` method simultaneously, which is not supported by the class.</span></span>  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="79dfd-133">限制安全執行緒方法的呼叫</span><span class="sxs-lookup"><span data-stu-id="79dfd-133">Limit Calls to Thread-Safe Methods</span></span>  
 <span data-ttu-id="79dfd-134">.NET Framework 中的大部分靜態方法都是安全執行緒，並可從多個執行緒同時呼叫。</span><span class="sxs-lookup"><span data-stu-id="79dfd-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="79dfd-135">不過，即使在這些情況下，所牽涉到的同步處理作業也可能會導致查詢速度顯著變慢。</span><span class="sxs-lookup"><span data-stu-id="79dfd-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79dfd-136">您可以測試這個自行插入某些呼叫<xref:System.Console.WriteLine%2A>在查詢中。</span><span class="sxs-lookup"><span data-stu-id="79dfd-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="79dfd-137">雖然此方法用於文件範例中，供示範之用，請勿使用 PLINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="79dfd-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>  
  
## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="79dfd-138">避免不必要的排序作業</span><span class="sxs-lookup"><span data-stu-id="79dfd-138">Avoid Unnecessary Ordering Operations</span></span>  
 <span data-ttu-id="79dfd-139">當 PLINQ 以平行方式執行查詢時，它會將來源序列分割成可在多個執行緒同時運作的資料分割中。</span><span class="sxs-lookup"><span data-stu-id="79dfd-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="79dfd-140">根據預設，資料分割經過處理和傳遞結果的順序不是可預測 (除了運算子，例如`OrderBy`)。</span><span class="sxs-lookup"><span data-stu-id="79dfd-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="79dfd-141">您可以指示要保留的任何來源順序，排序 PLINQ，但這對效能有負面影響。</span><span class="sxs-lookup"><span data-stu-id="79dfd-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="79dfd-142">最佳作法，您應該盡可能是建構查詢，讓它們不會依賴順序保留。</span><span class="sxs-lookup"><span data-stu-id="79dfd-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="79dfd-143">如需詳細資訊，請參閱 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="79dfd-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="79dfd-144">願意 ForAll ForEach 時很可能</span><span class="sxs-lookup"><span data-stu-id="79dfd-144">Prefer ForAll to ForEach When It Is Possible</span></span>  
 <span data-ttu-id="79dfd-145">雖然 PLINQ 查詢上執行多個執行緒，如果您使用中的結果`foreach`迴圈 (`For Each`在 Visual Basic 中)，則查詢結果必須合併回一個執行緒，並循序存取列舉值。</span><span class="sxs-lookup"><span data-stu-id="79dfd-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="79dfd-146">在某些情況下，這是無法避免的。不過，您應該盡可能使用`ForAll`方法，以啟用輸出自己結果，例如，例如寫入安全執行緒集合的每個執行緒<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="79dfd-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="79dfd-147">相同問題適用於 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。換句話說，`source.AsParallel().Where().ForAll(...)` 應該比</span><span class="sxs-lookup"><span data-stu-id="79dfd-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>  
  
 <span data-ttu-id="79dfd-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="79dfd-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>  
  
## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="79dfd-149">注意執行緒相似性問題</span><span class="sxs-lookup"><span data-stu-id="79dfd-149">Be Aware of Thread Affinity Issues</span></span>  
 <span data-ttu-id="79dfd-150">有些技術 (例如，適用於單一執行緒 Apartment (STA) 元件、Windows Forms 和 Windows Presentation Foundation (WPF) 的 COM 互通性) 會施加執行緒相似性限制，以要求程式碼在特定執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="79dfd-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="79dfd-151">例如，在 Windows Forms 和 WPF 中，只有用來建立控制項的執行緒能夠存取該控制項。</span><span class="sxs-lookup"><span data-stu-id="79dfd-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="79dfd-152">如果您嘗試存取的 Windows Form 控制項 PLINQ 查詢中的共用的狀態，如果您正在偵錯工具中，會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="79dfd-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="79dfd-153">（這項設定可以關閉。）不過，如果 UI 執行緒上取用您的查詢，然後您可以存取控制項`foreach`迴圈列舉查詢結果，因為只有一個執行緒上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="79dfd-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="79dfd-154">不要認為 ForEach、For 和 ForAll 的反覆項目一定要以平行方式執行</span><span class="sxs-lookup"><span data-stu-id="79dfd-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>  
 <span data-ttu-id="79dfd-155">請務必記住該個別的反覆項目中<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>，<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>或<xref:System.Linq.ParallelEnumerable.ForAll%2A>迴圈年，但不是需要以平行方式執行。</span><span class="sxs-lookup"><span data-stu-id="79dfd-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="79dfd-156">因此，您所撰寫的程式碼不應依靠系統是否有正確地平行執行反覆項目，也不應依靠系統是否有正確地以特定順序執行反覆項目。</span><span class="sxs-lookup"><span data-stu-id="79dfd-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>  
  
 <span data-ttu-id="79dfd-157">例如，下列程式碼有可能會發生死結︰</span><span class="sxs-lookup"><span data-stu-id="79dfd-157">For example, this code is likely to deadlock:</span></span>  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
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
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
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
  
 <span data-ttu-id="79dfd-158">在此範例中，一個反覆項目會設定事件，而其他所有反覆項目則是等候事件。</span><span class="sxs-lookup"><span data-stu-id="79dfd-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="79dfd-159">在事件設定反覆項目完成之前，沒有任何等候中的反覆項目可以完成。</span><span class="sxs-lookup"><span data-stu-id="79dfd-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="79dfd-160">不過，等待中的反覆項目有可能會在事件設定反覆項目有機會執行之前，就封鎖所有用來執行平行迴圈的執行緒。</span><span class="sxs-lookup"><span data-stu-id="79dfd-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="79dfd-161">這會導致死結，事件設定反覆項目永遠不會執行，而等待中的反覆項目也永遠不會醒來。</span><span class="sxs-lookup"><span data-stu-id="79dfd-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>  
  
 <span data-ttu-id="79dfd-162">特別是，平行迴圈的反覆項目永遠不應該等候該迴圈的另一個反覆項目才能繼續。</span><span class="sxs-lookup"><span data-stu-id="79dfd-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="79dfd-163">如果平行迴圈決定以循序方式排程反覆項目，但順序相反，系統就會發生死結。</span><span class="sxs-lookup"><span data-stu-id="79dfd-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dfd-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79dfd-164">See Also</span></span>  
 [<span data-ttu-id="79dfd-165">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="79dfd-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
