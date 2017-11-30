---
title: "執行緒同步處理 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 643dbb6fdceb4e1cfd074d3a532787562dbfd03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="thread-synchronization-visual-basic"></a><span data-ttu-id="dcfbe-102">執行緒同步處理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcfbe-102">Thread Synchronization (Visual Basic)</span></span>
<span data-ttu-id="dcfbe-103">下列各節描述可用來同步處理多執行緒應用程式中資源存取的功能和類別。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-103">The following sections describe features and classes that can be used to synchronize access to resources in multithreaded applications.</span></span>  
  
 <span data-ttu-id="dcfbe-104">在應用程式中使用多個執行緒的其中一個優點是每個執行緒都是以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-104">One of the benefits of using multiple threads in an application is that each thread executes asynchronously.</span></span> <span data-ttu-id="dcfbe-105">針對 Windows 應用程式，這可在應用程式視窗和控制項保持回應時，於背景執行耗時工作。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-105">For Windows applications, this allows time-consuming tasks to be performed in the background while the application window and controls remain responsive.</span></span> <span data-ttu-id="dcfbe-106">針對伺服器應用程式，多執行緒處理會提供可使用不同執行緒來處理每個傳入要求的能力。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-106">For server applications, multithreading provides the ability to handle each incoming request with a different thread.</span></span> <span data-ttu-id="dcfbe-107">否則，在完全滿足前一個要求之前，不會服務每個新的要求。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-107">Otherwise, each new request would not get serviced until the previous request had been fully satisfied.</span></span>  
  
 <span data-ttu-id="dcfbe-108">不過，執行緒的非同步性質表示必須協調檔案控制代碼、網路連線和記憶體這類資源的存取。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-108">However, the asynchronous nature of threads means that access to resources such as file handles, network connections, and memory must be coordinated.</span></span> <span data-ttu-id="dcfbe-109">否則，兩個以上的執行緒可以同時存取相同的資源，而每個都不知道對方的動作。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-109">Otherwise, two or more threads could access the same resource at the same time, each unaware of the other's actions.</span></span> <span data-ttu-id="dcfbe-110">結果是無法預期的資料損毀。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-110">The result is unpredictable data corruption.</span></span>  
  
 <span data-ttu-id="dcfbe-111">針對整數數值資料類型的一些簡單運算，使用 <xref:System.Threading.Interlocked> 類別的成員可以完成執行緒的同步處理。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-111">For simple operations on integral numeric data types, synchronizing threads can be accomplished with members of the <xref:System.Threading.Interlocked> class.</span></span> <span data-ttu-id="dcfbe-112">對於所有其他資料類型和非執行緒安全資源，只能使用本主題中的建構安全地執行多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-112">For all other data types and non thread-safe resources, multithreading can only be safely performed using the constructs in this topic.</span></span>  
  
 <span data-ttu-id="dcfbe-113">如需多執行緒程式設計的背景資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="dcfbe-113">For background information on multithreaded programming, see:</span></span>  
  
-   [<span data-ttu-id="dcfbe-114">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="dcfbe-114">Managed Threading Basics</span></span>](../../../../standard/threading/managed-threading-basics.md)  
  
-   [<span data-ttu-id="dcfbe-115">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="dcfbe-115">Using Threads and Threading</span></span>](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [<span data-ttu-id="dcfbe-116">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="dcfbe-116">Managed Threading Best Practices</span></span>](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-and-synclock-keywords"></a><span data-ttu-id="dcfbe-117">鎖定和 SyncLock 關鍵字</span><span class="sxs-lookup"><span data-stu-id="dcfbe-117">The lock and SyncLock Keywords</span></span>  
 <span data-ttu-id="dcfbe-118">Visual Basic`SyncLock`陳述式可以由其他執行緒用來確保一段程式碼會執行到完成為止，而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-118">The Visual Basic `SyncLock` statement can be used to ensure that a block of code runs to completion without interruption by other threads.</span></span> <span data-ttu-id="dcfbe-119">這項作業的完成方式是取得程式碼區塊期間內所指定物件的互斥鎖定。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-119">This is accomplished by obtaining a mutual-exclusion lock for a given object for the duration of the code block.</span></span>  
  
 <span data-ttu-id="dcfbe-120">`SyncLock` 陳述式是將物件指定為引數，而且後面接著一次只由一個執行緒執行的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-120">A `SyncLock` statement is given an object as an argument, and is followed by a code block that is to be executed by only one thread at a time.</span></span> <span data-ttu-id="dcfbe-121">例如: </span><span class="sxs-lookup"><span data-stu-id="dcfbe-121">For example:</span></span>  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="dcfbe-122">提供給 `SyncLock` 關鍵字的引數必須是根據參考型別的物件，並且用來定義鎖定範圍。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-122">The argument provided to the `SyncLock` keyword must be an object based on a reference type, and is used to define the scope of the lock.</span></span> <span data-ttu-id="dcfbe-123">在上述範例中，因為函式外部沒有 `lockThis` 物件的參考，所以鎖定範圍限於此函式。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-123">In the example above, the lock scope is limited to this function because no references to the object `lockThis` exist outside the function.</span></span> <span data-ttu-id="dcfbe-124">如果存在這類的參考，則鎖定範圍會延伸至該物件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-124">If such a reference did exist, lock scope would extend to that object.</span></span> <span data-ttu-id="dcfbe-125">嚴格來說，提供的物件僅用於唯一識別在多個執行緒之間共用的資源，因此它可以是任意類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-125">Strictly speaking, the object provided is used solely to uniquely identify the resource being shared among multiple threads, so it can be an arbitrary class instance.</span></span> <span data-ttu-id="dcfbe-126">不過，實際上，這個物件通常代表需要執行緒同步處理的資源。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-126">In practice, however, this object usually represents the resource for which thread synchronization is necessary.</span></span> <span data-ttu-id="dcfbe-127">例如，如果容器物件是要供多個執行緒使用，則可以將容器傳遞至鎖定，而鎖定後面的已同步處理程式碼區塊將會存取容器。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-127">For example, if a container object is to be used by multiple threads, then the container can be passed to lock, and the synchronized code block following the lock would access the container.</span></span> <span data-ttu-id="dcfbe-128">只要其他執行緒在存取相同容器之前先將它鎖定，則可以放心地同步處理物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-128">As long as other threads locks on the same contain before accessing it, then access to the object is safely synchronized.</span></span>  
  
 <span data-ttu-id="dcfbe-129">一般而言，最好是避免鎖定 `public` 類型，或鎖定不受您應用程式控制的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-129">Generally, it is best to avoid locking on a `public` type, or on object instances beyond the control of your application.</span></span> <span data-ttu-id="dcfbe-130">例如，因為不受您控制的程式碼可能也會鎖定物件，所以如果可以公開存取執行個體，則 `lockThis` 可能會有問題。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-130">For example, `lockThis` can be problematic if the instance can be accessed publicly, because code beyond your control may lock on the object as well.</span></span> <span data-ttu-id="dcfbe-131">這樣可能會建立兩個以上執行緒等待釋放相同物件的死結狀況。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-131">This could create deadlock situations where two or more threads wait for the release of the same object.</span></span> <span data-ttu-id="dcfbe-132">鎖定公用資料類型，而不是物件，可能會因相同原因而造成問題。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-132">Locking on a public data type, as opposed to an object, can cause problems for the same reason.</span></span> <span data-ttu-id="dcfbe-133">鎖定常值字串特別危險，因為 Common Language Runtime (CLR) 會「保留」常值字串。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-133">Locking on literal strings is especially risky because literal strings are *interned* by the common language runtime (CLR).</span></span> <span data-ttu-id="dcfbe-134">這表示整個程式之任何指定的字串常值都有一個執行個體，而完全相同的物件代表所有執行緒上所有執行中應用程式定義域中的常值。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-134">This means that there is one instance of any given string literal for the entire program, the exact same object represents the literal in all running application domains, on all threads.</span></span> <span data-ttu-id="dcfbe-135">因此，鎖定應用程式處理序中任意位置且內容相同的字串，即會鎖定應用程式中該字串的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-135">As a result, a lock placed on a string with the same contents anywhere in the application process locks all instances of that string in the application.</span></span> <span data-ttu-id="dcfbe-136">因此，最好鎖定未保留的私用或受保護成員。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-136">As a result, it is best to lock a private or protected member that is not interned.</span></span> <span data-ttu-id="dcfbe-137">某些類別會提供特別用於鎖定的成員。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-137">Some classes provide members specifically for locking.</span></span> <span data-ttu-id="dcfbe-138">例如，<xref:System.Array> 類型會提供 <xref:System.Array.SyncRoot%2A>。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-138">The <xref:System.Array> type, for example, provides <xref:System.Array.SyncRoot%2A>.</span></span> <span data-ttu-id="dcfbe-139">許多集合類型也都會提供 `SyncRoot` 成員。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-139">Many collection types provide a `SyncRoot` member as well.</span></span>  
  
 <span data-ttu-id="dcfbe-140">如需 `SyncLock` 陳述式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="dcfbe-140">For more information about the `SyncLock` statement, see the following topics:</span></span>  
  
-   [<span data-ttu-id="dcfbe-141">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="dcfbe-141">SyncLock Statement</span></span>](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a><span data-ttu-id="dcfbe-142">監視</span><span class="sxs-lookup"><span data-stu-id="dcfbe-142">Monitors</span></span>  
 <span data-ttu-id="dcfbe-143">與 `SyncLock` 關鍵字類似，監視器會防止多個執行緒同時執行程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-143">Like the `SyncLock` keyword, monitors prevent blocks of code from simultaneous execution by multiple threads.</span></span> <span data-ttu-id="dcfbe-144"><xref:System.Threading.Monitor.Enter%2A> 方法只允許在下列陳述式中繼續執行一個執行緒；除非執行中執行緒呼叫 <xref:System.Threading.Monitor.Exit%2A>，否則會封鎖所有其他執行緒。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-144">The <xref:System.Threading.Monitor.Enter%2A> method allows one and only one thread to proceed into the following statements; all other threads are blocked until the executing thread calls <xref:System.Threading.Monitor.Exit%2A>.</span></span> <span data-ttu-id="dcfbe-145">這只要使用 `SyncLock` 關鍵字即可。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-145">This is just like using the `SyncLock` keyword.</span></span> <span data-ttu-id="dcfbe-146">例如: </span><span class="sxs-lookup"><span data-stu-id="dcfbe-146">For example:</span></span>  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 <span data-ttu-id="dcfbe-147">這相當於：</span><span class="sxs-lookup"><span data-stu-id="dcfbe-147">This is equivalent to:</span></span>  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 <span data-ttu-id="dcfbe-148">通常會優先使用 `SyncLock` 關鍵字，而不是直接使用 <xref:System.Threading.Monitor> 類別，因為 `SyncLock` 更為精簡，而且 `SyncLock` 確保釋放基準監視器，即使受保護程式碼擲回例外狀況也是一樣。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-148">Using the `SyncLock` keyword is generally preferred over using the <xref:System.Threading.Monitor> class directly, both because `SyncLock` is more concise, and because `SyncLock` insures that the underlying monitor is released, even if the protected code throws an exception.</span></span> <span data-ttu-id="dcfbe-149">這是使用 `Finally` 關鍵字所完成，而不論是否擲回例外狀況，這個關鍵字都會執行其關聯的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-149">This is accomplished with the `Finally` keyword, which executes its associated code block regardless of whether an exception is thrown.</span></span>  
  
## <a name="synchronization-events-and-wait-handles"></a><span data-ttu-id="dcfbe-150">同步處理事件和等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="dcfbe-150">Synchronization Events and Wait Handles</span></span>  
 <span data-ttu-id="dcfbe-151">使用鎖定或監視器適用於防止同時執行執行緒敏感程式碼區塊，但這些建構不允許某個執行緒與另一個執行緒針對事件進行通訊。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-151">Using a lock or monitor is useful for preventing the simultaneous execution of thread-sensitive blocks of code, but these constructs do not allow one thread to communicate an event to another.</span></span> <span data-ttu-id="dcfbe-152">這需要「同步處理事件」，這是一個具有可用來啟動和暫止執行緒的兩種狀態 (發出訊號和未發出訊號) 之一的物件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-152">This requires *synchronization events*, which are objects that have one of two states, signaled and un-signaled, that can be used to activate and suspend threads.</span></span> <span data-ttu-id="dcfbe-153">執行緒的暫止方式是等候未發出訊號的同步處理事件，而啟動方式是將事件狀態變更為發出訊號。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-153">Threads can be suspended by being made to wait on a synchronization event that is unsignaled, and can be activated by changing the event state to signaled.</span></span> <span data-ttu-id="dcfbe-154">如果執行緒嘗試等候已收到訊號的事件，則執行緒會繼續執行，而不會延遲。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-154">If a thread attempts to wait on an event that is already signaled, then the thread continues to execute without delay.</span></span>  
  
 <span data-ttu-id="dcfbe-155">有兩種類型的同步處理事件：<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-155">There are two kinds of synchronization events: <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="dcfbe-156">它們的差異只在於 <xref:System.Threading.AutoResetEvent> 會在啟動執行緒時即自動從發出訊號變更為未發出訊號。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-156">They differ only in that <xref:System.Threading.AutoResetEvent> changes from signaled to unsignaled automatically any time it activates a thread.</span></span> <span data-ttu-id="dcfbe-157">相之，<xref:System.Threading.ManualResetEvent> 允許透過其發出信號狀態來啟動任意數目的執行緒，並只在呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法時還原為未發出信號狀態。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-157">Conversely, a <xref:System.Threading.ManualResetEvent> allows any number of threads to be activated by its signaled state, and will only revert to an unsignaled state when its <xref:System.Threading.EventWaitHandle.Reset%2A> method is called.</span></span>  
  
 <span data-ttu-id="dcfbe-158">讓執行緒等候事件的方式，就是呼叫其中一個等待方法，例如 <xref:System.Threading.WaitHandle.WaitOne%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A> 或 <xref:System.Threading.WaitHandle.WaitAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-158">Threads can be made to wait on events by calling one of the wait methods, such as <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, or <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span> <span data-ttu-id="dcfbe-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> 會使得執行緒等到單一事件變成發出信號狀態為止，<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> 則會封鎖執行緒，直到一或多個指定的事件變成發出信號狀態，而 <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> 會封鎖執行緒，直到所有指定的事件變成發出信號狀態。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> causes the thread to wait until a single event becomes signaled, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blocks a thread until one or more indicated events become signaled, and <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blocks the thread until all of the indicated events become signaled.</span></span> <span data-ttu-id="dcfbe-160">呼叫事件的 <xref:System.Threading.EventWaitHandle.Set%2A> 方法時，該事件就會變成發出信號狀態。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-160">An event becomes signaled when its <xref:System.Threading.EventWaitHandle.Set%2A> method is called.</span></span>  
  
 <span data-ttu-id="dcfbe-161">在下列範例中，`Main` 函式會建立並啟動執行緒。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-161">In the following example, a thread is created and started by the `Main` function.</span></span> <span data-ttu-id="dcfbe-162">新的執行緒會使用 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法等候事件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-162">The new thread waits on an event using the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span> <span data-ttu-id="dcfbe-163">除非執行 `Main` 函式的主要執行緒讓事件變成發出訊號，否則會暫止執行緒。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-163">The thread is suspended until the event becomes signaled by the primary thread that is executing the `Main` function.</span></span> <span data-ttu-id="dcfbe-164">一旦事件變成發出訊號，就會傳回輔助執行緒。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-164">Once the event becomes signaled, the auxiliary thread returns.</span></span> <span data-ttu-id="dcfbe-165">在此情況下，由於事件僅用於啟動某個執行緒，因此可以使用 <xref:System.Threading.AutoResetEvent> 或 <xref:System.Threading.ManualResetEvent> 類別。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-165">In this case, because the event is only used for one thread activation, either the <xref:System.Threading.AutoResetEvent> or <xref:System.Threading.ManualResetEvent> classes could be used.</span></span>  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a><span data-ttu-id="dcfbe-166">Mutex 物件</span><span class="sxs-lookup"><span data-stu-id="dcfbe-166">Mutex Object</span></span>  
 <span data-ttu-id="dcfbe-167">*Mutex* 與監視器類似，可防止多個執行緒一次同時執行程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-167">A *mutex* is similar to a monitor; it prevents the simultaneous execution of a block of code by more than one thread at a time.</span></span> <span data-ttu-id="dcfbe-168">事實上，名稱 "Mutex" 是「互斥」這個詞彙的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-168">In fact, the name "mutex" is a shortened form of the term "mutually exclusive."</span></span> <span data-ttu-id="dcfbe-169">不過，與監視器不同，Mutex 可以用來跨處理序同步處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-169">Unlike monitors, however, a mutex can be used to synchronize threads across processes.</span></span> <span data-ttu-id="dcfbe-170">Mutex 由 <xref:System.Threading.Mutex> 類別代表。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-170">A mutex is represented by the <xref:System.Threading.Mutex> class.</span></span>  
  
 <span data-ttu-id="dcfbe-171">用於處理序間同步處理時，Mutex 稱為「具名 Mutex」，因為它是要用在另一個應用程式中，因此無法透過全域或靜態變數共用。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-171">When used for inter-process synchronization, a mutex is called a *named mutex* because it is to be used in another application, and therefore it cannot be shared by means of a global or static variable.</span></span> <span data-ttu-id="dcfbe-172">必須指定它的名稱，以讓兩個應用程式可以存取相同的 Mutex 物件。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-172">It must be given a name so that both applications can access the same mutex object.</span></span>  
  
 <span data-ttu-id="dcfbe-173">雖然 Mutex 可以用於處理序間執行緒同步處理，但是一般偏好使用 <xref:System.Threading.Monitor>，因為已特別針對 .NET Framework 設計監視器，因此能夠更恰當地使用資源。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-173">Although a mutex can be used for intra-process thread synchronization, using <xref:System.Threading.Monitor> is generally preferred, because monitors were designed specifically for the .NET Framework and therefore make better use of resources.</span></span> <span data-ttu-id="dcfbe-174">相反地，<xref:System.Threading.Mutex> 類別是 Win32 建構的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-174">In contrast, the <xref:System.Threading.Mutex> class is a wrapper to a Win32 construct.</span></span> <span data-ttu-id="dcfbe-175">雖然 Mutex 比監視器的功能更為強大，但是所需的 Interop 轉換比 <xref:System.Threading.Monitor> 類別所需的 Interop 轉換耗費更大量的運算資源。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-175">While it is more powerful than a monitor, a mutex requires interop transitions that are more computationally expensive than those required by the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="dcfbe-176">如需使用 Mutex 的範例，請參閱 [Mutex](../../../../standard/threading/mutexes.md)。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-176">For an example of using a mutex, see [Mutexes](../../../../standard/threading/mutexes.md).</span></span>  
  
## <a name="interlocked-class"></a><span data-ttu-id="dcfbe-177">Interlocked 類別</span><span class="sxs-lookup"><span data-stu-id="dcfbe-177">Interlocked Class</span></span>  
 <span data-ttu-id="dcfbe-178">您可以使用 <xref:System.Threading.Interlocked> 類別的方法，防止多個執行緒嘗試同時更新或比較相同值時可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-178">You can use the methods of the <xref:System.Threading.Interlocked> class to prevent problems that can occur when multiple threads attempt to simultaneously update or compare the same value.</span></span> <span data-ttu-id="dcfbe-179">這個類別的方法可讓您安全地遞增、遞減、交換和比較任何執行緒中的值。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-179">The methods of this class let you safely increment, decrement, exchange, and compare values from any thread.</span></span>  
  
## <a name="readerwriter-locks"></a><span data-ttu-id="dcfbe-180">ReaderWriter 鎖定</span><span class="sxs-lookup"><span data-stu-id="dcfbe-180">ReaderWriter Locks</span></span>  
 <span data-ttu-id="dcfbe-181">在某些情況下，只有正在寫入資料時，才會想要鎖定資源，並允許多個用戶端在未更新資料時同時讀取資料。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-181">In some cases, you may want to lock a resource only when data is being written and permit multiple clients to simultaneously read data when data is not being updated.</span></span> <span data-ttu-id="dcfbe-182"><xref:System.Threading.ReaderWriterLock> 類別會在執行緒正在修改資源時強制獨佔資源存取，但在讀取資源時允許非獨佔存取。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-182">The <xref:System.Threading.ReaderWriterLock> class enforces exclusive access to a resource while a thread is modifying the resource, but it allows non-exclusive access when reading the resource.</span></span> <span data-ttu-id="dcfbe-183">ReaderWriter 鎖定是造成其他執行緒等待之獨佔鎖定的有用替代方式，即使這些執行緒不需要更新資料時也是一樣。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-183">ReaderWriter locks are a useful alternative to exclusive locks, which cause other threads to wait, even when those threads do not need to update data.</span></span>  
  
## <a name="deadlocks"></a><span data-ttu-id="dcfbe-184">死結</span><span class="sxs-lookup"><span data-stu-id="dcfbe-184">Deadlocks</span></span>  
 <span data-ttu-id="dcfbe-185">執行緒同步處理是多執行緒應用程式中十分寶貴的功能，但建立 `deadlock` 一律有其危險性；在其中，多個執行緒將等候彼此，而應用程式就像停止一樣。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-185">Thread synchronization is invaluable in multithreaded applications, but there is always the danger of creating a `deadlock`, where multiple threads are waiting for each other and the application comes to a halt.</span></span> <span data-ttu-id="dcfbe-186">死結類似汽車停在四方停車再開的位置，而每個人都在等候其他人先離開。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-186">A deadlock is analogous to a situation in which cars are stopped at a four-way stop and each person is waiting for the other to go.</span></span> <span data-ttu-id="dcfbe-187">避免死結十分重要；關鍵在於仔細規劃。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-187">Avoiding deadlocks is important; the key is careful planning.</span></span> <span data-ttu-id="dcfbe-188">在開始撰寫程式碼之前，先將多執行緒應用程式圖表化，通常就可以預測死結狀況。</span><span class="sxs-lookup"><span data-stu-id="dcfbe-188">You can often predict deadlock situations by diagramming multithreaded applications before you start coding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfbe-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcfbe-189">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="dcfbe-190">多執行緒應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcfbe-190">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="dcfbe-191">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="dcfbe-191">SyncLock Statement</span></span>](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
 [<span data-ttu-id="dcfbe-192">Mutex</span><span class="sxs-lookup"><span data-stu-id="dcfbe-192">Mutexes</span></span>](../../../../standard/threading/mutexes.md)  
 [<span data-ttu-id="dcfbe-193">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="dcfbe-193">Interlocked Operations</span></span>](../../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="dcfbe-194">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="dcfbe-194">AutoResetEvent</span></span>](../../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="dcfbe-195">同步處理多執行緒處理的資料</span><span class="sxs-lookup"><span data-stu-id="dcfbe-195">Synchronizing Data for Multithreading</span></span>](../../../../standard/threading/synchronizing-data-for-multithreading.md)
