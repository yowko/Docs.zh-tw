---
title: Managed 執行緒處理的最佳實施方針
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8319424c82327fd9743c573846663bdd76ed1b9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644617"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="002ef-102">受控執行緒處理最佳做法</span><span class="sxs-lookup"><span data-stu-id="002ef-102">Managed threading best practices</span></span>
<span data-ttu-id="002ef-103">在為多執行緒功能設計程式時需要非常小心。</span><span class="sxs-lookup"><span data-stu-id="002ef-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="002ef-104">您可以藉由將要求排入佇列以供執行緒集區的執行緒執行，來降低大部分工作的複雜性。</span><span class="sxs-lookup"><span data-stu-id="002ef-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="002ef-105">本主題要解決的是更困難的情況，例如協調多個執行緒的工作，或處理封鎖起來的執行緒。</span><span class="sxs-lookup"><span data-stu-id="002ef-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="002ef-106">從 .NET Framework 4 開始，工作平行程式庫和 PLINQ 會提供 API，來為多執行緒的程式設計工作降低一定的複雜度和風險。</span><span class="sxs-lookup"><span data-stu-id="002ef-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="002ef-107">如需詳細資訊，請參閱 [.NET 的平行程式設計](../../../docs/standard/parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="002ef-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="002ef-108">死結和競爭條件</span><span class="sxs-lookup"><span data-stu-id="002ef-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="002ef-109">多執行緒可透過輸送量和回應性來解決問題，但這麼做又會引發新的問題︰死結和競爭情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="002ef-110">死結</span><span class="sxs-lookup"><span data-stu-id="002ef-110">Deadlocks</span></span>  
 <span data-ttu-id="002ef-111">當兩個執行緒各自嘗試鎖定彼此已鎖定的資源時，系統就會發生死結。</span><span class="sxs-lookup"><span data-stu-id="002ef-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="002ef-112">這兩個執行緒都無法再有所進展。</span><span class="sxs-lookup"><span data-stu-id="002ef-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="002ef-113">Managed 執行緒類別有許多方法會提供逾時機制，以幫助您偵測死結情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="002ef-114">例如，下列程式碼會嘗試在名為 `lockObject` 的物件上取得鎖定。</span><span class="sxs-lookup"><span data-stu-id="002ef-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="002ef-115">如果未在 300 毫秒內取得鎖定，<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> 就會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="002ef-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="002ef-116">競爭條件</span><span class="sxs-lookup"><span data-stu-id="002ef-116">Race conditions</span></span>  
 <span data-ttu-id="002ef-117">當程式的結果取決於兩個以上的執行緒何者先到達特定程式碼區塊時，系統便會發生競爭情形這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="002ef-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="002ef-118">執行程式多次會產生不同的結果，因而讓系統無法預測當回執行的結果。</span><span class="sxs-lookup"><span data-stu-id="002ef-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="002ef-119">遞增欄位值的作業就是簡單的競爭情形範例。</span><span class="sxs-lookup"><span data-stu-id="002ef-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="002ef-120">假設某個類別具有 **static** 私用欄位 (在 Visual Basic 中是 **Shared**)，每當該類別建立了執行個體，該欄位就會使用 `objCt++;` (C#) 或 `objCt += 1` (Visual Basic) 之類的程式碼來遞增值。</span><span class="sxs-lookup"><span data-stu-id="002ef-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="002ef-121">這項作業需要將 `objCt` 的值載入到暫存器、將值遞增，然後儲存在 `objCt` 中。</span><span class="sxs-lookup"><span data-stu-id="002ef-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="002ef-122">在多執行緒應用程式中，已經載入並遞增值的執行緒可能會讓另一個將三個步驟全都執行完畢的執行緒來先佔；當第一個執行緒繼續執行並儲存其值時，它會不顧值已在過渡期間變更的事實而覆寫 `objCt`。</span><span class="sxs-lookup"><span data-stu-id="002ef-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="002ef-123">您可以使用 <xref:System.Threading.Interlocked> 類別的方法 (例如 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 方法)，輕鬆地避免這個特定的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="002ef-124">若要了解其他可用來在多個執行緒之間同步處理資料的技術，請參閱[同步處理多執行緒的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)。</span><span class="sxs-lookup"><span data-stu-id="002ef-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="002ef-125">當您同步處理多個執行緒的活動時，系統也會發生競爭情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="002ef-126">每當您編寫一行程式碼時，您必須考慮如果某個執行緒在執行該行程式碼之前 (或在構成該行程式碼的個別電腦指令之前) 就讓其他執行緒先佔，而且另一個執行緒超過該執行緒時，系統可能會發生什麼狀況。</span><span class="sxs-lookup"><span data-stu-id="002ef-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="002ef-127">靜態成員和靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="002ef-127">Static members and static constructors</span></span>  
 <span data-ttu-id="002ef-128">類別要等到其類別建構函式 (C# 中是 `static` 建構函式，Visual Basic 中是 `Shared Sub New`) 執行完畢後才會初始化。</span><span class="sxs-lookup"><span data-stu-id="002ef-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="002ef-129">為避免程式碼在未初始化的型別上執行，通用語言執行平台會在類別建構函式執行完畢前，封鎖其他執行緒對該類別之 `static` 成員 (Visual Basic 中是 `Shared` 成員) 的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="002ef-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="002ef-130">例如，如果類別建構函式會開始新的執行緒，而執行緒程序會呼叫該類別的 `static` 成員，則新的執行緒會封鎖起來，直到類別建構函式完成。</span><span class="sxs-lookup"><span data-stu-id="002ef-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="002ef-131">這適用於任何可以具有 `static` 建構函式的型別。</span><span class="sxs-lookup"><span data-stu-id="002ef-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="002ef-132">處理器數目</span><span class="sxs-lookup"><span data-stu-id="002ef-132">Number of processors</span></span>

<span data-ttu-id="002ef-133">系統上無論有多個處理器或只有一個處理器，都會影響多執行緒的架構。</span><span class="sxs-lookup"><span data-stu-id="002ef-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="002ef-134">如需詳細資訊，請參閱 [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors) (處理器數目)。</span><span class="sxs-lookup"><span data-stu-id="002ef-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="002ef-135">使用 <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> 屬性來判斷執行階段可用的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="002ef-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="002ef-136">一般建議</span><span class="sxs-lookup"><span data-stu-id="002ef-136">General recommendations</span></span>  
 <span data-ttu-id="002ef-137">在使用多執行緒時，請考慮下列指導方針︰</span><span class="sxs-lookup"><span data-stu-id="002ef-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="002ef-138">請勿使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 來終止其他執行緒。</span><span class="sxs-lookup"><span data-stu-id="002ef-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="002ef-139">對另一個執行緒呼叫 **Abort** 就像對該執行緒擲回例外狀況，卻不知道該執行緒已到達哪個處理階段。</span><span class="sxs-lookup"><span data-stu-id="002ef-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="002ef-140">請勿使用 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> 來同步處理多個執行緒的活動。</span><span class="sxs-lookup"><span data-stu-id="002ef-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="002ef-141">請使用 <xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.Monitor>。</span><span class="sxs-lookup"><span data-stu-id="002ef-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="002ef-142">不要從主要程式控制背景工作執行緒的執行 (例如，使用事件)。</span><span class="sxs-lookup"><span data-stu-id="002ef-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="002ef-143">相反地，請設計您的程式，讓背景工作執行緒負責等候到可進行工作、執行工作，並在工作完成時通知程式的其他組件。</span><span class="sxs-lookup"><span data-stu-id="002ef-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="002ef-144">如果背景工作執行緒不會封鎖起來，請考慮使用執行緒集區的執行緒。</span><span class="sxs-lookup"><span data-stu-id="002ef-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="002ef-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> 在背景工作執行緒封鎖的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="002ef-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="002ef-146">請勿使用型別來作為鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="002ef-146">Don't use types as lock objects.</span></span> <span data-ttu-id="002ef-147">也就是避免像是 C# 中的 `lock(typeof(X))` 或 Visual Basic 中的 `SyncLock(GetType(X))` 的程式碼，或避免搭配 <xref:System.Type> 物件使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="002ef-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="002ef-148">針對指定的類型，每個應用程式定義域都會有 <xref:System.Type?displayProperty=nameWithType> 的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="002ef-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="002ef-149">如果您鎖定的型別是公用的，則不是您自有的程式碼也可鎖定該型別，而導致死結。</span><span class="sxs-lookup"><span data-stu-id="002ef-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="002ef-150">若要了解其他問題，請參閱[可靠性最佳作法](../../../docs/framework/performance/reliability-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="002ef-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="002ef-151">鎖定執行個體時請小心，例如 C# 中的 `lock(this)` 或 Visual Basic 中的 `SyncLock(Me)`。</span><span class="sxs-lookup"><span data-stu-id="002ef-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="002ef-152">如果您應用程式中屬於該型別之外的其他程式碼鎖定物件，系統可能會發生死結。</span><span class="sxs-lookup"><span data-stu-id="002ef-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="002ef-153">請務必要確定已進入監視器的執行緒一律會離開該監視器，即使執行緒還在監視器內卻發生例外狀況時亦然。</span><span class="sxs-lookup"><span data-stu-id="002ef-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="002ef-154">C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) 陳述式和 Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) 陳述式會自動提供這種行為，利用 **finally** 區塊來確保系統會呼叫 <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="002ef-154">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="002ef-155">如果您無法確保系統會呼叫 **Exit**，請考慮將您的設計改為使用 **Mutex**。</span><span class="sxs-lookup"><span data-stu-id="002ef-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="002ef-156">目前擁有 Mutex 的執行緒在終止時會自動將其釋放。</span><span class="sxs-lookup"><span data-stu-id="002ef-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="002ef-157">對於需要不同資源的工作，請使用多個執行緒，並避免將多個執行緒指派給單一資源。</span><span class="sxs-lookup"><span data-stu-id="002ef-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="002ef-158">例如，任何涉及 I/O 的工作都可受惠於擁有自己的執行緒，因為該執行緒會在 I/O 作業期間封鎖起來，進而讓其他執行緒得以執行。</span><span class="sxs-lookup"><span data-stu-id="002ef-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="002ef-159">使用者輸入是受惠於專用執行緒的另一項資源。</span><span class="sxs-lookup"><span data-stu-id="002ef-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="002ef-160">在單一處理器電腦上，涉及大量計算的工作會與使用者輸入共存，並與涉及 I/O 的工作共存，但多個需要大量計算的工作會彼此爭用。</span><span class="sxs-lookup"><span data-stu-id="002ef-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="002ef-161">請考慮使用 <xref:System.Threading.Interlocked> 類別的方法來處理簡單的狀態變更，而不要使用 `lock` 陳述式 (Visual Basic 中是 `SyncLock`)。</span><span class="sxs-lookup"><span data-stu-id="002ef-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="002ef-162">`lock` 陳述式是很好的泛用工具，但 <xref:System.Threading.Interlocked> 類別可為必須是不可部分完成的更新提供較好的效能。</span><span class="sxs-lookup"><span data-stu-id="002ef-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="002ef-163">就內部而言，如果沒有爭用的情況，它會執行單一鎖定前置詞。</span><span class="sxs-lookup"><span data-stu-id="002ef-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="002ef-164">在檢閱程式碼時，請注意如下列範例所示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="002ef-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="002ef-165">在第一個範例中，狀態變數會遞增︰</span><span class="sxs-lookup"><span data-stu-id="002ef-165">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="002ef-166">您可以使用 <xref:System.Threading.Interlocked.Increment%2A> 方法而非 `lock` 陳述式來改善效能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="002ef-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="002ef-167">在 .NET Framework 2.0 和更新版本中，為大於 1 的不可部分完成增量使用 <xref:System.Threading.Interlocked.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="002ef-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="002ef-168">在第二個範例中，只有當參考型別變數是 Null 參考 (在 Visual Basic 中是 `Nothing`) 時，該變數才會更新。</span><span class="sxs-lookup"><span data-stu-id="002ef-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="002ef-169">您可以使用 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法來改善效能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="002ef-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="002ef-170">從 .NET Framework 2.0 開始，<xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> 方法多載會為參考型別提供型別安全的替代方法。</span><span class="sxs-lookup"><span data-stu-id="002ef-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="002ef-171">類別庫的建議</span><span class="sxs-lookup"><span data-stu-id="002ef-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="002ef-172">在設計類別庫的多執行緒功能時，請考慮下列指導方針︰</span><span class="sxs-lookup"><span data-stu-id="002ef-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="002ef-173">盡可能避免同步處理需求。</span><span class="sxs-lookup"><span data-stu-id="002ef-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="002ef-174">經常使用的程式碼更該避免這一點。</span><span class="sxs-lookup"><span data-stu-id="002ef-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="002ef-175">例如，您可以調整演算法，使它容許競爭情形，而非消除此情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="002ef-176">不必要的同步處理會降低效能，並有可能產生死結和競爭情形。</span><span class="sxs-lookup"><span data-stu-id="002ef-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="002ef-177">讓 static 資料 (在 Visual Basic 中是 `Shared`) 的執行緒預設保有安全性。</span><span class="sxs-lookup"><span data-stu-id="002ef-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="002ef-178">不要讓執行個體資料的執行緒預設保有安全性。</span><span class="sxs-lookup"><span data-stu-id="002ef-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="002ef-179">新增鎖定以建立安全執行緒程式碼的作法，會降低效能、增加鎖定爭用並可能導致死結發生。</span><span class="sxs-lookup"><span data-stu-id="002ef-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="002ef-180">在一般的應用程式模型中，一次只會有一個執行緒執行使用者程式碼，這種方式可將執行緒安全性的需求降到最低。</span><span class="sxs-lookup"><span data-stu-id="002ef-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="002ef-181">為此，.NET Framework 類別庫依預設不會保有執行緒安全性。</span><span class="sxs-lookup"><span data-stu-id="002ef-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="002ef-182">避免提供會變更靜態狀態的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="002ef-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="002ef-183">在一般的伺服器案例中，所有要求會共用靜態狀態，這表示多個執行緒可以同時執行該程式碼。</span><span class="sxs-lookup"><span data-stu-id="002ef-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="002ef-184">這可能會讓執行緒發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="002ef-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="002ef-185">請考慮使用某種設計模式，以將資料封裝到不會讓所有要求共用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="002ef-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="002ef-186">此外，如果靜態資料會同步處理，會在靜態方法之間改變狀態的呼叫將會導致死結或多餘的同步處理，而對效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="002ef-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002ef-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="002ef-187">See also</span></span>

- [<span data-ttu-id="002ef-188">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="002ef-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="002ef-189">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="002ef-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
