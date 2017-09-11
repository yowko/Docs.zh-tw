---
title: "多執行緒應用程式 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 63692a5d62359a5f6f9f3c2d08f469c24ed9f0f3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="multithreaded-applications-c"></a><span data-ttu-id="ae00e-102">多執行緒應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="ae00e-102">Multithreaded Applications (C#)</span></span>
<span data-ttu-id="ae00e-103">使用 C#，您可以撰寫一次執行多項工作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae00e-103">With C#, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="ae00e-104">可能妨礙其他工作的工作可以另外的執行緒執行，此等程序稱之為「多執行緒」**或「無限制執行緒」**。</span><span class="sxs-lookup"><span data-stu-id="ae00e-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="ae00e-105">使用多執行緒的應用程式回應使用者輸入會更快，因為當處理器密集工作在另外的執行緒上執行時，使用者介面會保持使用中。</span><span class="sxs-lookup"><span data-stu-id="ae00e-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="ae00e-106">當您建立可擴充的應用程式時，多執行緒也很有幫助，因為您可以隨著工作負載增加而新增執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="ae00e-107">建立和使用執行緒</span><span class="sxs-lookup"><span data-stu-id="ae00e-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="ae00e-108">如果您需要對應用程式執行緒行為有更大的掌控力，您可以自行管理執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="ae00e-109">但請了解撰寫正確的多執行緒應用程式十分困難︰您的應用程式可能會停止回應，或因競爭情形造成暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae00e-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="ae00e-110">如需詳細資訊，請參閱[安全執行緒的元件](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)。</span><span class="sxs-lookup"><span data-stu-id="ae00e-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="ae00e-111">宣告 <xref:System.Threading.Thread> 型別的變數並呼叫建構函式，提供您要在新執行緒執行的程序或方法名稱，以建立新的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="ae00e-112">下列程式碼提供一個範例。</span><span class="sxs-lookup"><span data-stu-id="ae00e-112">The following code provides an example.</span></span>  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="ae00e-113">開始和停止執行緒</span><span class="sxs-lookup"><span data-stu-id="ae00e-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="ae00e-114">若要開始執行新的執行緒，請使用 <xref:System.Threading.Thread.Start%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ae00e-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Start();  
```  
  
 <span data-ttu-id="ae00e-115">若要停止執行執行緒，請使用 <xref:System.Threading.Thread.Abort%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ae00e-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Abort();  
```  
  
 <span data-ttu-id="ae00e-116">除了開始和停止執行緒，您也可以呼叫 <xref:System.Threading.Thread.Sleep%2A> 或 <xref:System.Threading.Thread.Suspend%2A> 方法暫停執行緒，使用 <xref:System.Threading.Thread.Resume%2A> 方法恢復暫停的執行緒，以及使用 <xref:System.Threading.Thread.Abort%2A> 方法終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="ae00e-117">執行緒方法</span><span class="sxs-lookup"><span data-stu-id="ae00e-117">Thread Methods</span></span>  
 <span data-ttu-id="ae00e-118">下表顯示可用來控制個別執行緒的一些方法。</span><span class="sxs-lookup"><span data-stu-id="ae00e-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="ae00e-119">方法</span><span class="sxs-lookup"><span data-stu-id="ae00e-119">Method</span></span>|<span data-ttu-id="ae00e-120">動作</span><span class="sxs-lookup"><span data-stu-id="ae00e-120">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="ae00e-121"><xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-121"><xref:System.Threading.Thread.Start%2A></span></span>|<span data-ttu-id="ae00e-122">讓執行緒開始執行。</span><span class="sxs-lookup"><span data-stu-id="ae00e-122">Causes a thread to start to run.</span></span>|  
|<span data-ttu-id="ae00e-123"><xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-123"><xref:System.Threading.Thread.Sleep%2A></span></span>|<span data-ttu-id="ae00e-124">讓執行緒暫停指定的時間。</span><span class="sxs-lookup"><span data-stu-id="ae00e-124">Pauses a thread for a specified time.</span></span>|  
|<span data-ttu-id="ae00e-125"><xref:System.Threading.Thread.Suspend%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-125"><xref:System.Threading.Thread.Suspend%2A></span></span>|<span data-ttu-id="ae00e-126">當執行緒到達安全點時暫停。</span><span class="sxs-lookup"><span data-stu-id="ae00e-126">Pauses a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="ae00e-127"><xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-127"><xref:System.Threading.Thread.Abort%2A></span></span>|<span data-ttu-id="ae00e-128">當執行緒到達安全點時停止。</span><span class="sxs-lookup"><span data-stu-id="ae00e-128">Stops a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="ae00e-129"><xref:System.Threading.Thread.Resume%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-129"><xref:System.Threading.Thread.Resume%2A></span></span>|<span data-ttu-id="ae00e-130">重新開始暫止的執行緒</span><span class="sxs-lookup"><span data-stu-id="ae00e-130">Restarts a suspended thread</span></span>|  
|<span data-ttu-id="ae00e-131"><xref:System.Threading.Thread.Join%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-131"><xref:System.Threading.Thread.Join%2A></span></span>|<span data-ttu-id="ae00e-132">讓目前的執行緒等候另一個執行緒完成。</span><span class="sxs-lookup"><span data-stu-id="ae00e-132">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="ae00e-133">如果搭配逾時值使用，當執行緒於配置時間內完成時，此方法會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="ae00e-133">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="ae00e-134">安全點</span><span class="sxs-lookup"><span data-stu-id="ae00e-134">Safe Points</span></span>  
 <span data-ttu-id="ae00e-135">這些方法大多都一目了然，但您可能不熟悉「安全點」**的概念。</span><span class="sxs-lookup"><span data-stu-id="ae00e-135">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="ae00e-136">安全點是程式碼中，通用語言執行平台執行自動「記憶體回收」**的安全位置，記憶體回收是釋放未使用的變數並回收記憶體的程序。</span><span class="sxs-lookup"><span data-stu-id="ae00e-136">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="ae00e-137">當您呼叫執行緒的 <xref:System.Threading.Thread.Abort%2A> 或 <xref:System.Threading.Thread.Suspend%2A> 方法時，通用語言執行平台會分析程式碼，並決定適當的位置供執行緒停止執行。</span><span class="sxs-lookup"><span data-stu-id="ae00e-137">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="ae00e-138">執行緒屬性</span><span class="sxs-lookup"><span data-stu-id="ae00e-138">Thread Properties</span></span>  
 <span data-ttu-id="ae00e-139">執行緒也包含多個有用的屬性，如下表所示︰</span><span class="sxs-lookup"><span data-stu-id="ae00e-139">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="ae00e-140">屬性</span><span class="sxs-lookup"><span data-stu-id="ae00e-140">Property</span></span>|<span data-ttu-id="ae00e-141">值</span><span class="sxs-lookup"><span data-stu-id="ae00e-141">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="ae00e-142"><xref:System.Threading.Thread.IsAlive%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-142"><xref:System.Threading.Thread.IsAlive%2A></span></span>|<span data-ttu-id="ae00e-143">如果執行緒在使用中，即包含值 `True`。</span><span class="sxs-lookup"><span data-stu-id="ae00e-143">Contains the value `True` if a thread is active.</span></span>|  
|<span data-ttu-id="ae00e-144"><xref:System.Threading.Thread.IsBackground%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-144"><xref:System.Threading.Thread.IsBackground%2A></span></span>|<span data-ttu-id="ae00e-145">取得或設定布林值，指出執行緒是否為或應該是背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-145">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="ae00e-146">背景執行緒類似前景執行緒，但是背景執行緒不會防止處理程序停止。</span><span class="sxs-lookup"><span data-stu-id="ae00e-146">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="ae00e-147">一旦屬於處理程序的所有前景執行緒停止，通用語言執行平台會呼叫背景執行緒上仍在執行的 <xref:System.Threading.Thread.Abort%2A> 方法結束處理程序。</span><span class="sxs-lookup"><span data-stu-id="ae00e-147">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<span data-ttu-id="ae00e-148"><xref:System.Threading.Thread.Name%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-148"><xref:System.Threading.Thread.Name%2A></span></span>|<span data-ttu-id="ae00e-149">取得或設定執行緒名稱。</span><span class="sxs-lookup"><span data-stu-id="ae00e-149">Gets or sets the name of a thread.</span></span> <span data-ttu-id="ae00e-150">最常用於在偵錯時探索個別執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-150">Most frequently used to discover individual threads when you debug.</span></span>|  
|<span data-ttu-id="ae00e-151"><xref:System.Threading.Thread.Priority%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-151"><xref:System.Threading.Thread.Priority%2A></span></span>|<span data-ttu-id="ae00e-152">取得或設定作業系統使用的值，以設定執行緒排程的優先權。</span><span class="sxs-lookup"><span data-stu-id="ae00e-152">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<span data-ttu-id="ae00e-153"><xref:System.Threading.Thread.ThreadState%2A></span><span class="sxs-lookup"><span data-stu-id="ae00e-153"><xref:System.Threading.Thread.ThreadState%2A></span></span>|<span data-ttu-id="ae00e-154">包含說明執行緒狀態的值。</span><span class="sxs-lookup"><span data-stu-id="ae00e-154">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="ae00e-155">執行緒優先順序</span><span class="sxs-lookup"><span data-stu-id="ae00e-155">Thread Priorities</span></span>  
 <span data-ttu-id="ae00e-156">每個執行緒都有優先順序屬性，決定它必須執行多大或多小的處理器時段。</span><span class="sxs-lookup"><span data-stu-id="ae00e-156">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="ae00e-157">作業系統會配置較長的時段給高優先順序的執行緒，較短的時間配量給低優先順序的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ae00e-157">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="ae00e-158">新執行緒使用 `Normal` 值建立，但是您可以將 <xref:System.Threading.Thread.Priority%2A> 屬性變更成 <xref:System.Threading.ThreadPriority> 列舉中的任一值。</span><span class="sxs-lookup"><span data-stu-id="ae00e-158">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="ae00e-159">如需各種執行緒優先順序的詳細說明，請參閱 <xref:System.Threading.ThreadPriority>。</span><span class="sxs-lookup"><span data-stu-id="ae00e-159">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="ae00e-160">前景和背景執行緒</span><span class="sxs-lookup"><span data-stu-id="ae00e-160">Foreground and Background Threads</span></span>  
 <span data-ttu-id="ae00e-161">「前景執行緒」**無限期執行，而「背景執行緒」**會在最後一個前景執行緒停止後立刻停止。</span><span class="sxs-lookup"><span data-stu-id="ae00e-161">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="ae00e-162">您可以使用 <xref:System.Threading.Thread.IsBackground%2A> 屬性來判斷或變更執行緒的背景狀態。</span><span class="sxs-lookup"><span data-stu-id="ae00e-162">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae00e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae00e-163">See Also</span></span>  
 <span data-ttu-id="ae00e-164"><xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="ae00e-164"><xref:System.Threading.Thread></span></span>   
<span data-ttu-id="ae00e-165"> [執行緒同步處理 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="ae00e-165"> [Thread Synchronization (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="ae00e-166"> [多執行緒程序的參數和傳回值 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ae00e-166"> [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span></span>  
<span data-ttu-id="ae00e-167"> [執行緒處理 (C++)](../../../../csharp/programming-guide/concepts/threading/index.md)</span><span class="sxs-lookup"><span data-stu-id="ae00e-167"> [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)</span></span>
