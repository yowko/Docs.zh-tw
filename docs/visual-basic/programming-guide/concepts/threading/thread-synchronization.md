---
title: "執行緒同步處理 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 240937905254120f777ce140049084279c35005c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="thread-synchronization-visual-basic"></a><span data-ttu-id="0a187-102">執行緒同步處理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a187-102">Thread Synchronization (Visual Basic)</span></span>
<span data-ttu-id="0a187-103">下列章節說明功能和類別，可用來同步處理多執行緒應用程式資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="0a187-103">The following sections describe features and classes that can be used to synchronize access to resources in multithreaded applications.</span></span>  
  
 <span data-ttu-id="0a187-104">其中一個應用程式中使用多執行緒的優點是每個執行緒以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="0a187-104">One of the benefits of using multiple threads in an application is that each thread executes asynchronously.</span></span> <span data-ttu-id="0a187-105">對於 Windows 應用程式，這可讓應用程式視窗時在背景執行耗時的工作和控制項仍能繼續回應。</span><span class="sxs-lookup"><span data-stu-id="0a187-105">For Windows applications, this allows time-consuming tasks to be performed in the background while the application window and controls remain responsive.</span></span> <span data-ttu-id="0a187-106">伺服器應用程式，進行多執行緒處理會提供能夠處理不同的執行緒與每個傳入要求。</span><span class="sxs-lookup"><span data-stu-id="0a187-106">For server applications, multithreading provides the ability to handle each incoming request with a different thread.</span></span> <span data-ttu-id="0a187-107">否則，每個新的要求會取得之前無法提供服務一個要求已完全沒有問題。</span><span class="sxs-lookup"><span data-stu-id="0a187-107">Otherwise, each new request would not get serviced until the previous request had been fully satisfied.</span></span>  
  
 <span data-ttu-id="0a187-108">不過，例如檔案控制代碼、 網路連線和記憶體資源存取權的執行緒方法的非同步性質，必須進行協調。</span><span class="sxs-lookup"><span data-stu-id="0a187-108">However, the asynchronous nature of threads means that access to resources such as file handles, network connections, and memory must be coordinated.</span></span> <span data-ttu-id="0a187-109">否則，兩個或多個執行緒可以存取相同資源一次，每個都不知道對方的動作。</span><span class="sxs-lookup"><span data-stu-id="0a187-109">Otherwise, two or more threads could access the same resource at the same time, each unaware of the other's actions.</span></span> <span data-ttu-id="0a187-110">結果是無法預期的資料損毀。</span><span class="sxs-lookup"><span data-stu-id="0a187-110">The result is unpredictable data corruption.</span></span>  
  
 <span data-ttu-id="0a187-111">整數的數值資料型別上的簡單運算，如同步處理執行緒可以完成與成員的<xref:System.Threading.Interlocked>類別。</xref:System.Threading.Interlocked></span><span class="sxs-lookup"><span data-stu-id="0a187-111">For simple operations on integral numeric data types, synchronizing threads can be accomplished with members of the <xref:System.Threading.Interlocked> class.</span></span> <span data-ttu-id="0a187-112">所有其他資料型別和多執行緒處理的非執行緒安全資源只能安全地執行本主題中使用的建構。</span><span class="sxs-lookup"><span data-stu-id="0a187-112">For all other data types and non thread-safe resources, multithreading can only be safely performed using the constructs in this topic.</span></span>  
  
 <span data-ttu-id="0a187-113">如需多執行緒程式設計的背景資訊，請參閱︰</span><span class="sxs-lookup"><span data-stu-id="0a187-113">For background information on multithreaded programming, see:</span></span>  
  
-   [<span data-ttu-id="0a187-114">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="0a187-114">Managed Threading Basics</span></span>](http://msdn.microsoft.com/library/b2944911-0e8f-427d-a8bb-077550618935)  
  
-   [<span data-ttu-id="0a187-115">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="0a187-115">Using Threads and Threading</span></span>](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)  
  
-   [<span data-ttu-id="0a187-116">Managed 執行緒處理最佳作法</span><span class="sxs-lookup"><span data-stu-id="0a187-116">Managed Threading Best Practices</span></span>](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)  
  
## <a name="the-lock-and-synclock-keywords"></a><span data-ttu-id="0a187-117">Lock 和 SyncLock 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0a187-117">The lock and SyncLock Keywords</span></span>  
 <span data-ttu-id="0a187-118">Visual Basic`SyncLock`陳述式可以由其他執行緒用來確保程式碼區塊執行到完成為止，而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="0a187-118">The Visual Basic `SyncLock` statement can be used to ensure that a block of code runs to completion without interruption by other threads.</span></span> <span data-ttu-id="0a187-119">這被透過程式碼區塊的持續時間內取得指定物件的互斥鎖定。</span><span class="sxs-lookup"><span data-stu-id="0a187-119">This is accomplished by obtaining a mutual-exclusion lock for a given object for the duration of the code block.</span></span>  
  
 <span data-ttu-id="0a187-120">A`SyncLock`陳述式指定的物件做為引數，且後面接著一次只能由一個執行緒執行的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0a187-120">A `SyncLock` statement is given an object as an argument, and is followed by a code block that is to be executed by only one thread at a time.</span></span> <span data-ttu-id="0a187-121">例如: </span><span class="sxs-lookup"><span data-stu-id="0a187-121">For example:</span></span>  
  
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
  
 <span data-ttu-id="0a187-122">若要提供的引數`SyncLock`關鍵字必須是參考型別為基礎的物件和用來定義鎖定的範圍。</span><span class="sxs-lookup"><span data-stu-id="0a187-122">The argument provided to the `SyncLock` keyword must be an object based on a reference type, and is used to define the scope of the lock.</span></span> <span data-ttu-id="0a187-123">在上述範例中，鎖定的範圍僅限於此函式因為物件未參考`lockThis`存在外部函式。</span><span class="sxs-lookup"><span data-stu-id="0a187-123">In the example above, the lock scope is limited to this function because no references to the object `lockThis` exist outside the function.</span></span> <span data-ttu-id="0a187-124">如果存在這類的參考，鎖定範圍會延伸至該物件。</span><span class="sxs-lookup"><span data-stu-id="0a187-124">If such a reference did exist, lock scope would extend to that object.</span></span> <span data-ttu-id="0a187-125">嚴格來說，提供的物件僅用於唯一識別的資源，因此它可以是任意的類別執行個體在多個執行緒之間共用。</span><span class="sxs-lookup"><span data-stu-id="0a187-125">Strictly speaking, the object provided is used solely to uniquely identify the resource being shared among multiple threads, so it can be an arbitrary class instance.</span></span> <span data-ttu-id="0a187-126">在實務上，不過，這個物件通常代表執行緒同步處理所需要的資源。</span><span class="sxs-lookup"><span data-stu-id="0a187-126">In practice, however, this object usually represents the resource for which thread synchronization is necessary.</span></span> <span data-ttu-id="0a187-127">比方說，如果容器物件是可供多個執行緒，然後容器可以傳遞至鎖定，並在鎖定之後的同步處理的程式碼區塊會存取容器。</span><span class="sxs-lookup"><span data-stu-id="0a187-127">For example, if a container object is to be used by multiple threads, then the container can be passed to lock, and the synchronized code block following the lock would access the container.</span></span> <span data-ttu-id="0a187-128">只要其他執行緒會在相同鎖定包含之前存取它，然後安全地進行同步處理物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="0a187-128">As long as other threads locks on the same contain before accessing it, then access to the object is safely synchronized.</span></span>  
  
 <span data-ttu-id="0a187-129">一般而言，最好是避免鎖定`public`型別，或您的應用程式所控制的物件執行個體上。</span><span class="sxs-lookup"><span data-stu-id="0a187-129">Generally, it is best to avoid locking on a `public` type, or on object instances beyond the control of your application.</span></span> <span data-ttu-id="0a187-130">例如，`lockThis`可能會造成問題，如果公開，存取的執行個體，因為您控制範圍之外的程式碼可能會鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="0a187-130">For example, `lockThis` can be problematic if the instance can be accessed publicly, because code beyond your control may lock on the object as well.</span></span> <span data-ttu-id="0a187-131">這樣可能會建立兩個或多個執行緒會等待相同的物件版本的死結狀況。</span><span class="sxs-lookup"><span data-stu-id="0a187-131">This could create deadlock situations where two or more threads wait for the release of the same object.</span></span> <span data-ttu-id="0a187-132">鎖定在公用資料型別，而不是物件，可能會造成問題的理由。</span><span class="sxs-lookup"><span data-stu-id="0a187-132">Locking on a public data type, as opposed to an object, can cause problems for the same reason.</span></span> <span data-ttu-id="0a187-133">常值字串鎖定是特別危險，因為常值字串完全*被保留了*common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="0a187-133">Locking on literal strings is especially risky because literal strings are *interned* by the common language runtime (CLR).</span></span> <span data-ttu-id="0a187-134">這表示沒有任何指定之字串的一個執行個體的整個程式常值，完全相同的物件表示中所有的常值的所有執行緒上執行應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="0a187-134">This means that there is one instance of any given string literal for the entire program, the exact same object represents the literal in all running application domains, on all threads.</span></span> <span data-ttu-id="0a187-135">如此一來，鎖定放在具有相同內容的字串中應用程式的處理序鎖定該字串的應用程式中的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a187-135">As a result, a lock placed on a string with the same contents anywhere in the application process locks all instances of that string in the application.</span></span> <span data-ttu-id="0a187-136">因此，最好鎖定不會被保留了私用或受保護成員。</span><span class="sxs-lookup"><span data-stu-id="0a187-136">As a result, it is best to lock a private or protected member that is not interned.</span></span> <span data-ttu-id="0a187-137">某些類別會提供成員特別為鎖定。</span><span class="sxs-lookup"><span data-stu-id="0a187-137">Some classes provide members specifically for locking.</span></span> <span data-ttu-id="0a187-138">的<xref:System.Array>型別，例如，提供<xref:System.Array.SyncRoot%2A>.</xref:System.Array.SyncRoot%2A> </xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="0a187-138">The <xref:System.Array> type, for example, provides <xref:System.Array.SyncRoot%2A>.</span></span> <span data-ttu-id="0a187-139">許多集合型別提供`SyncRoot`以及成員。</span><span class="sxs-lookup"><span data-stu-id="0a187-139">Many collection types provide a `SyncRoot` member as well.</span></span>  
  
 <span data-ttu-id="0a187-140">如需詳細資訊`SyncLock`陳述式，請參閱下列主題︰</span><span class="sxs-lookup"><span data-stu-id="0a187-140">For more information about the `SyncLock` statement, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0a187-141">SyncLock 陳述式</span><span class="sxs-lookup"><span data-stu-id="0a187-141">SyncLock Statement</span></span>](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a><span data-ttu-id="0a187-142">監視</span><span class="sxs-lookup"><span data-stu-id="0a187-142">Monitors</span></span>  
 <span data-ttu-id="0a187-143">像`SyncLock`關鍵字，監視器會避免由多個執行緒同時執行的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0a187-143">Like the `SyncLock` keyword, monitors prevent blocks of code from simultaneous execution by multiple threads.</span></span> <span data-ttu-id="0a187-144"><xref:System.Threading.Monitor.Enter%2A>方法可讓只有一個執行緒繼續執行下列陳述式; 所有其他執行緒會被封鎖，直到執行的執行緒呼叫<xref:System.Threading.Monitor.Exit%2A>。</xref:System.Threading.Monitor.Exit%2A> </xref:System.Threading.Monitor.Enter%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-144">The <xref:System.Threading.Monitor.Enter%2A> method allows one and only one thread to proceed into the following statements; all other threads are blocked until the executing thread calls <xref:System.Threading.Monitor.Exit%2A>.</span></span> <span data-ttu-id="0a187-145">就像使用`SyncLock`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0a187-145">This is just like using the `SyncLock` keyword.</span></span> <span data-ttu-id="0a187-146">例如: </span><span class="sxs-lookup"><span data-stu-id="0a187-146">For example:</span></span>  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 <span data-ttu-id="0a187-147">這相當於︰</span><span class="sxs-lookup"><span data-stu-id="0a187-147">This is equivalent to:</span></span>  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 <span data-ttu-id="0a187-148">使用`SyncLock`關鍵字通常會優先使用<xref:System.Threading.Monitor>類別目錄，同時由於`SyncLock`更為精簡，而且因為`SyncLock`car 的基準監視會釋放，即使受保護的程式碼擲回例外狀況。</xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="0a187-148">Using the `SyncLock` keyword is generally preferred over using the <xref:System.Threading.Monitor> class directly, both because `SyncLock` is more concise, and because `SyncLock` insures that the underlying monitor is released, even if the protected code throws an exception.</span></span> <span data-ttu-id="0a187-149">這是與`Finally`關鍵字，它會執行其相關聯的程式碼區塊，不論是否擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0a187-149">This is accomplished with the `Finally` keyword, which executes its associated code block regardless of whether an exception is thrown.</span></span>  
  
## <a name="synchronization-events-and-wait-handles"></a><span data-ttu-id="0a187-150">同步處理事件和等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="0a187-150">Synchronization Events and Wait Handles</span></span>  
 <span data-ttu-id="0a187-151">使用鎖定或監視器可用於防止同時執行的執行緒敏感程式碼區塊，但這些建構並不允許進行通訊的事件到另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a187-151">Using a lock or monitor is useful for preventing the simultaneous execution of thread-sensitive blocks of code, but these constructs do not allow one thread to communicate an event to another.</span></span> <span data-ttu-id="0a187-152">這需要*同步處理事件*，這是具有兩種狀態的其中一個物件收到信號，未收到信號，可以用來啟動和暫止執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a187-152">This requires *synchronization events*, which are objects that have one of two states, signaled and un-signaled, that can be used to activate and suspend threads.</span></span> <span data-ttu-id="0a187-153">執行緒會暫停等候信號，同步處理事件未發出，而且可以透過啟動變更為已收到訊號的事件狀態。</span><span class="sxs-lookup"><span data-stu-id="0a187-153">Threads can be suspended by being made to wait on a synchronization event that is unsignaled, and can be activated by changing the event state to signaled.</span></span> <span data-ttu-id="0a187-154">如果執行緒嘗試等候已收到信號的事件時，執行緒會繼續執行而不會延遲。</span><span class="sxs-lookup"><span data-stu-id="0a187-154">If a thread attempts to wait on an event that is already signaled, then the thread continues to execute without delay.</span></span>  
  
 <span data-ttu-id="0a187-155">有兩種類型的同步處理事件︰ <xref:System.Threading.AutoResetEvent>，和<xref:System.Threading.ManualResetEvent>.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-155">There are two kinds of synchronization events: <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="0a187-156">它們之間的差異只在於<xref:System.Threading.AutoResetEvent>變更通知到信號自動每當它會啟動執行緒。</xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-156">They differ only in that <xref:System.Threading.AutoResetEvent> changes from signaled to unsignaled automatically any time it activates a thread.</span></span> <span data-ttu-id="0a187-157">相反地，<xref:System.Threading.ManualResetEvent>允許任意數目的執行緒，其已收到信號的狀態，來啟動，並只將會還原成未發出信號狀態時其<xref:System.Threading.EventWaitHandle.Reset%2A>方法稱為 「。</xref:System.Threading.EventWaitHandle.Reset%2A> </xref:System.Threading.ManualResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-157">Conversely, a <xref:System.Threading.ManualResetEvent> allows any number of threads to be activated by its signaled state, and will only revert to an unsignaled state when its <xref:System.Threading.EventWaitHandle.Reset%2A> method is called.</span></span>  
  
 <span data-ttu-id="0a187-158">可以讓執行緒等待事件由呼叫其中一個等候方法，例如<xref:System.Threading.WaitHandle.WaitOne%2A>， <xref:System.Threading.WaitHandle.WaitAny%2A>，或<xref:System.Threading.WaitHandle.WaitAll%2A>.</xref:System.Threading.WaitHandle.WaitAll%2A> </xref:System.Threading.WaitHandle.WaitAny%2A> </xref:System.Threading.WaitHandle.WaitOne%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-158">Threads can be made to wait on events by calling one of the wait methods, such as <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, or <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span> <span data-ttu-id="0a187-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>造成執行緒等候單一事件發出信號，<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>封鎖執行緒，直到一或多個指定的事件變成已收到訊號，和<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>封鎖執行緒，直到所有指定的事件變成已收到訊號。</xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> </xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName></xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0a187-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> causes the thread to wait until a single event becomes signaled, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> blocks a thread until one or more indicated events become signaled, and <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> blocks the thread until all of the indicated events become signaled.</span></span> <span data-ttu-id="0a187-160">事件發出信號時其<xref:System.Threading.EventWaitHandle.Set%2A>方法稱為 「。</xref:System.Threading.EventWaitHandle.Set%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-160">An event becomes signaled when its <xref:System.Threading.EventWaitHandle.Set%2A> method is called.</span></span>  
  
 <span data-ttu-id="0a187-161">在下列範例中，執行緒會建立並啟動`Main`函式。</span><span class="sxs-lookup"><span data-stu-id="0a187-161">In the following example, a thread is created and started by the `Main` function.</span></span> <span data-ttu-id="0a187-162">新的執行緒在等待事件使用<xref:System.Threading.WaitHandle.WaitOne%2A>方法。</xref:System.Threading.WaitHandle.WaitOne%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-162">The new thread waits on an event using the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span> <span data-ttu-id="0a187-163">執行緒會暫停，直到對事件發出信號的主要執行緒正在執行`Main`函式。</span><span class="sxs-lookup"><span data-stu-id="0a187-163">The thread is suspended until the event becomes signaled by the primary thread that is executing the `Main` function.</span></span> <span data-ttu-id="0a187-164">一旦對事件發出信號，就會傳回輔助執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a187-164">Once the event becomes signaled, the auxiliary thread returns.</span></span> <span data-ttu-id="0a187-165">在此情況下，事件僅用於一個執行緒啟動，或是因為<xref:System.Threading.AutoResetEvent>或<xref:System.Threading.ManualResetEvent>可用類別。</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-165">In this case, because the event is only used for one thread activation, either the <xref:System.Threading.AutoResetEvent> or <xref:System.Threading.ManualResetEvent> classes could be used.</span></span>  
  
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
  
## <a name="mutex-object"></a><span data-ttu-id="0a187-166">Mutex 物件</span><span class="sxs-lookup"><span data-stu-id="0a187-166">Mutex Object</span></span>  
 <span data-ttu-id="0a187-167">A *mutex*是類似於監視器; 它防止多個執行緒同時執行的程式碼區塊一次。</span><span class="sxs-lookup"><span data-stu-id="0a187-167">A *mutex* is similar to a monitor; it prevents the simultaneous execution of a block of code by more than one thread at a time.</span></span> <span data-ttu-id="0a187-168">事實上，名稱"mutex 」 是 「 互斥。 」 一詞縮寫格式</span><span class="sxs-lookup"><span data-stu-id="0a187-168">In fact, the name "mutex" is a shortened form of the term "mutually exclusive."</span></span> <span data-ttu-id="0a187-169">不同於監視器，不過，mutex 可以用於跨處理序同步處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a187-169">Unlike monitors, however, a mutex can be used to synchronize threads across processes.</span></span> <span data-ttu-id="0a187-170">Mutex 被以<xref:System.Threading.Mutex>類別。</xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="0a187-170">A mutex is represented by the <xref:System.Threading.Mutex> class.</span></span>  
  
 <span data-ttu-id="0a187-171">Mutex 時用於處理序間的同步處理時，會呼叫*具名 mutex*因為它是以供其他應用程式，因此它無法共用透過全域或靜態變數。</span><span class="sxs-lookup"><span data-stu-id="0a187-171">When used for inter-process synchronization, a mutex is called a *named mutex* because it is to be used in another application, and therefore it cannot be shared by means of a global or static variable.</span></span> <span data-ttu-id="0a187-172">必須授與它的名稱，讓兩個應用程式可以存取同一個 mutex 物件。</span><span class="sxs-lookup"><span data-stu-id="0a187-172">It must be given a name so that both applications can access the same mutex object.</span></span>  
  
 <span data-ttu-id="0a187-173">Mutex 可以用於進行了處理序的執行緒同步處理，但是使用<xref:System.Threading.Monitor>通常會優先，因為監視專為.NET Framework 設計，因此更妥善運用資源。</xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="0a187-173">Although a mutex can be used for intra-process thread synchronization, using <xref:System.Threading.Monitor> is generally preferred, because monitors were designed specifically for the .NET Framework and therefore make better use of resources.</span></span> <span data-ttu-id="0a187-174">相反地，<xref:System.Threading.Mutex>類別是 Win32 建構的包裝函式。</xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="0a187-174">In contrast, the <xref:System.Threading.Mutex> class is a wrapper to a Win32 construct.</span></span> <span data-ttu-id="0a187-175">雖然比監視器功能更強大，mutex 需要 interop 轉換時更耗費大量運算資源比所需的<xref:System.Threading.Monitor>類別。</xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="0a187-175">While it is more powerful than a monitor, a mutex requires interop transitions that are more computationally expensive than those required by the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="0a187-176">如需使用 mutex 的範例，請參閱[Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)。</span><span class="sxs-lookup"><span data-stu-id="0a187-176">For an example of using a mutex, see [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span></span>  
  
## <a name="interlocked-class"></a><span data-ttu-id="0a187-177">Interlocked 的類別</span><span class="sxs-lookup"><span data-stu-id="0a187-177">Interlocked Class</span></span>  
 <span data-ttu-id="0a187-178">您可以使用的方法<xref:System.Threading.Interlocked>類別來防止當多個執行緒嘗試同時更新，或相同的值相比較時可能發生的問題。</xref:System.Threading.Interlocked></span><span class="sxs-lookup"><span data-stu-id="0a187-178">You can use the methods of the <xref:System.Threading.Interlocked> class to prevent problems that can occur when multiple threads attempt to simultaneously update or compare the same value.</span></span> <span data-ttu-id="0a187-179">這個類別的方法可讓您安全地遞增、 遞減、 交換，並比較值，從任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a187-179">The methods of this class let you safely increment, decrement, exchange, and compare values from any thread.</span></span>  
  
## <a name="readerwriter-locks"></a><span data-ttu-id="0a187-180">ReaderWriter 鎖定</span><span class="sxs-lookup"><span data-stu-id="0a187-180">ReaderWriter Locks</span></span>  
 <span data-ttu-id="0a187-181">在某些情況下，您可以只會被寫入資料時，鎖定資源，並允許多個用戶端無法更新資料時，同時讀取資料。</span><span class="sxs-lookup"><span data-stu-id="0a187-181">In some cases, you may want to lock a resource only when data is being written and permit multiple clients to simultaneously read data when data is not being updated.</span></span> <span data-ttu-id="0a187-182"><xref:System.Threading.ReaderWriterLock>類別在執行緒正在修改資源，但它可讓非獨佔存取資源讀取時，會強制執行資源的獨佔存取權。</xref:System.Threading.ReaderWriterLock></span><span class="sxs-lookup"><span data-stu-id="0a187-182">The <xref:System.Threading.ReaderWriterLock> class enforces exclusive access to a resource while a thread is modifying the resource, but it allows non-exclusive access when reading the resource.</span></span> <span data-ttu-id="0a187-183">ReaderWriter 鎖定是有用的替代方式，會造成其他執行緒等待，即使當這些執行緒不需要更新資料的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="0a187-183">ReaderWriter locks are a useful alternative to exclusive locks, which cause other threads to wait, even when those threads do not need to update data.</span></span>  
  
## <a name="deadlocks"></a><span data-ttu-id="0a187-184">死結 （deadlock)</span><span class="sxs-lookup"><span data-stu-id="0a187-184">Deadlocks</span></span>  
 <span data-ttu-id="0a187-185">執行緒同步處理是非常寶貴的功能，在多執行緒應用程式，但總是有之上建立`deadlock`的多個執行緒正在等候彼此，且應用程式停止暫止。</span><span class="sxs-lookup"><span data-stu-id="0a187-185">Thread synchronization is invaluable in multithreaded applications, but there is always the danger of creating a `deadlock`, where multiple threads are waiting for each other and the application comes to a halt.</span></span> <span data-ttu-id="0a187-186">死結是類似於汽車停止在四個方向停止，且每個人等候到其他的情況。</span><span class="sxs-lookup"><span data-stu-id="0a187-186">A deadlock is analogous to a situation in which cars are stopped at a four-way stop and each person is waiting for the other to go.</span></span> <span data-ttu-id="0a187-187">避免死結的重要性;關鍵在於仔細規劃。</span><span class="sxs-lookup"><span data-stu-id="0a187-187">Avoiding deadlocks is important; the key is careful planning.</span></span> <span data-ttu-id="0a187-188">您通常可以圖表化多執行緒應用程式，然後再開始撰寫程式碼，以預測死結狀況的可能性。</span><span class="sxs-lookup"><span data-stu-id="0a187-188">You can often predict deadlock situations by diagramming multithreaded applications before you start coding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a187-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a187-189">See Also</span></span>  
 <span data-ttu-id="0a187-190"><xref:System.Threading.Thread></xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="0a187-190"><xref:System.Threading.Thread></span></span>   
 <span data-ttu-id="0a187-191"><xref:System.Threading.WaitHandle.WaitOne%2A></xref:System.Threading.WaitHandle.WaitOne%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-191"><xref:System.Threading.WaitHandle.WaitOne%2A></span></span>   
 <span data-ttu-id="0a187-192"><xref:System.Threading.WaitHandle.WaitAny%2A></xref:System.Threading.WaitHandle.WaitAny%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-192"><xref:System.Threading.WaitHandle.WaitAny%2A></span></span>   
 <span data-ttu-id="0a187-193"><xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-193"><xref:System.Threading.WaitHandle.WaitAll%2A></span></span>   
 <span data-ttu-id="0a187-194"><xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-194"><xref:System.Threading.Thread.Join%2A></span></span>   
 <span data-ttu-id="0a187-195"><xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-195"><xref:System.Threading.Thread.Start%2A></span></span>   
 <span data-ttu-id="0a187-196"><xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-196"><xref:System.Threading.Thread.Sleep%2A></span></span>   
 <span data-ttu-id="0a187-197"><xref:System.Threading.Monitor></xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="0a187-197"><xref:System.Threading.Monitor></span></span>   
 <span data-ttu-id="0a187-198"><xref:System.Threading.Mutex></xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="0a187-198"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="0a187-199"><xref:System.Threading.AutoResetEvent></xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-199"><xref:System.Threading.AutoResetEvent></span></span>   
 <span data-ttu-id="0a187-200"><xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent></span><span class="sxs-lookup"><span data-stu-id="0a187-200"><xref:System.Threading.ManualResetEvent></span></span>   
 <span data-ttu-id="0a187-201"><xref:System.Threading.Interlocked></xref:System.Threading.Interlocked></span><span class="sxs-lookup"><span data-stu-id="0a187-201"><xref:System.Threading.Interlocked></span></span>   
 <span data-ttu-id="0a187-202"><xref:System.Threading.WaitHandle></xref:System.Threading.WaitHandle></span><span class="sxs-lookup"><span data-stu-id="0a187-202"><xref:System.Threading.WaitHandle></span></span>   
 <span data-ttu-id="0a187-203"><xref:System.Threading.EventWaitHandle></xref:System.Threading.EventWaitHandle></span><span class="sxs-lookup"><span data-stu-id="0a187-203"><xref:System.Threading.EventWaitHandle></span></span>   
 <span data-ttu-id="0a187-204"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="0a187-204"><xref:System.Threading></span></span>   
 <span data-ttu-id="0a187-205"><xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A></span><span class="sxs-lookup"><span data-stu-id="0a187-205"><xref:System.Threading.EventWaitHandle.Set%2A></span></span>   
<span data-ttu-id="0a187-206"> [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0a187-206"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="0a187-207"> [SyncLock 陳述式](../../../../visual-basic/language-reference/statements/synclock-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0a187-207"> [SyncLock Statement](../../../../visual-basic/language-reference/statements/synclock-statement.md) </span></span>  
<span data-ttu-id="0a187-208"> [Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2) </span><span class="sxs-lookup"><span data-stu-id="0a187-208"> [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2) </span></span>  
 @System.Threading.Monitor   
<span data-ttu-id="0a187-209"> [連鎖的作業](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b) </span><span class="sxs-lookup"><span data-stu-id="0a187-209"> [Interlocked Operations](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b) </span></span>  
<span data-ttu-id="0a187-210"> [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18) </span><span class="sxs-lookup"><span data-stu-id="0a187-210"> [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18) </span></span>  
<span data-ttu-id="0a187-211"> [同步處理資料的多執行緒處理](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)</span><span class="sxs-lookup"><span data-stu-id="0a187-211"> [Synchronizing Data for Multithreading](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)</span></span>
