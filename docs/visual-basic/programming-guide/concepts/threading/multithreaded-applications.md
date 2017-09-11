---
title: "多執行緒應用程式 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
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
ms.openlocfilehash: 8b68104fbc5eb0e0eb0f46401f3fcef0d3c4d023
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="multithreaded-applications-visual-basic"></a><span data-ttu-id="8ddae-102">多執行緒應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ddae-102">Multithreaded Applications (Visual Basic)</span></span>
<span data-ttu-id="8ddae-103">使用 Visual Basic 中，您可以撰寫同時執行多個工作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ddae-103">With Visual Basic, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="8ddae-104">可能會妨礙其他工作的工作可以執行個別的執行緒上這道程序*多執行緒*或*釋放執行緒*。</span><span class="sxs-lookup"><span data-stu-id="8ddae-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="8ddae-105">使用多執行緒會更快速地回應使用者輸入，因為使用者介面保持使用中，因為處理器密集工作在個別執行緒上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ddae-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="8ddae-106">多執行緒處理時，也建立可擴充的應用程式，因為您可以在工作負載增加時加入執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="8ddae-107">建立和使用執行緒</span><span class="sxs-lookup"><span data-stu-id="8ddae-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="8ddae-108">如果您需要更充分掌控您的應用程式執行緒的行為，您可以自行管理執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="8ddae-109">然而，了解撰寫正確的多執行緒應用程式十分困難︰ 您的應用程式可能會停止回應或發生競爭情形所造成的暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="8ddae-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="8ddae-110">如需詳細資訊，請參閱[安全執行緒的元件](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)。</span><span class="sxs-lookup"><span data-stu-id="8ddae-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="8ddae-111">宣告型別的變數建立新的執行緒<xref:System.Threading.Thread>和提供的程序或您想要在新的執行緒上執行的方法名稱的建構函式。</xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="8ddae-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="8ddae-112">下列程式碼提供一個範例。</span><span class="sxs-lookup"><span data-stu-id="8ddae-112">The following code provides an example.</span></span>  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="8ddae-113">啟動和停止執行緒</span><span class="sxs-lookup"><span data-stu-id="8ddae-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="8ddae-114">若要啟動新執行緒的執行，請使用<xref:System.Threading.Thread.Start%2A>方法，如下列程式碼所示。</xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Start()  
```  
  
 <span data-ttu-id="8ddae-115">若要停止的執行緒執行，請使用<xref:System.Threading.Thread.Abort%2A>方法，如下列程式碼所示。</xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Abort()  
```  
  
 <span data-ttu-id="8ddae-116">除了啟動和停止執行緒，您也可以暫停執行緒藉由呼叫<xref:System.Threading.Thread.Sleep%2A>或<xref:System.Threading.Thread.Suspend%2A>方法中，使用恢復暫停的執行緒<xref:System.Threading.Thread.Resume%2A>方法，和使用的<xref:System.Threading.Thread.Abort%2A>方法</xref:System.Threading.Thread.Abort%2A>終結執行緒</xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="8ddae-117">執行緒方法</span><span class="sxs-lookup"><span data-stu-id="8ddae-117">Thread Methods</span></span>  
 <span data-ttu-id="8ddae-118">下表顯示一些可用來控制的個別執行緒的方法。</span><span class="sxs-lookup"><span data-stu-id="8ddae-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="8ddae-119">方法</span><span class="sxs-lookup"><span data-stu-id="8ddae-119">Method</span></span>|<span data-ttu-id="8ddae-120">動作</span><span class="sxs-lookup"><span data-stu-id="8ddae-120">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="8ddae-121"><xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-121"><xref:System.Threading.Thread.Start%2A></span></span>|<span data-ttu-id="8ddae-122">使執行緒開始執行。</span><span class="sxs-lookup"><span data-stu-id="8ddae-122">Causes a thread to start to run.</span></span>|  
|<span data-ttu-id="8ddae-123"><xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-123"><xref:System.Threading.Thread.Sleep%2A></span></span>|<span data-ttu-id="8ddae-124">暫停執行緒，在指定的時間。</span><span class="sxs-lookup"><span data-stu-id="8ddae-124">Pauses a thread for a specified time.</span></span>|  
|<span data-ttu-id="8ddae-125"><xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Suspend%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-125"><xref:System.Threading.Thread.Suspend%2A></span></span>|<span data-ttu-id="8ddae-126">當它到達安全點暫停執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-126">Pauses a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="8ddae-127"><xref:System.Threading.Thread.Abort%2A></xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-127"><xref:System.Threading.Thread.Abort%2A></span></span>|<span data-ttu-id="8ddae-128">當它到達安全點停止執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-128">Stops a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="8ddae-129"><xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Resume%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-129"><xref:System.Threading.Thread.Resume%2A></span></span>|<span data-ttu-id="8ddae-130">重新啟動暫止的執行緒</span><span class="sxs-lookup"><span data-stu-id="8ddae-130">Restarts a suspended thread</span></span>|  
|<span data-ttu-id="8ddae-131"><xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-131"><xref:System.Threading.Thread.Join%2A></span></span>|<span data-ttu-id="8ddae-132">造成等候另一個執行緒完成目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-132">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="8ddae-133">如果搭配使用的逾時值，此方法會傳回`True`如果執行緒配置的時間內完成。</span><span class="sxs-lookup"><span data-stu-id="8ddae-133">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="8ddae-134">安全點</span><span class="sxs-lookup"><span data-stu-id="8ddae-134">Safe Points</span></span>  
 <span data-ttu-id="8ddae-135">這些方法大多都一目了然，但概念的*安全點*可能不熟悉。</span><span class="sxs-lookup"><span data-stu-id="8ddae-135">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="8ddae-136">安全點是很安全的 common language runtime 來執行自動程式碼中位置*回收*，釋放未使用的變數，並回收記憶體的程序。</span><span class="sxs-lookup"><span data-stu-id="8ddae-136">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="8ddae-137">當您呼叫<xref:System.Threading.Thread.Abort%2A>或<xref:System.Threading.Thread.Suspend%2A>方法的執行緒，common language runtime 會分析程式碼，並決定適當的位置停止執行的執行緒的位置。</xref:System.Threading.Thread.Suspend%2A> </xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-137">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="8ddae-138">執行緒屬性</span><span class="sxs-lookup"><span data-stu-id="8ddae-138">Thread Properties</span></span>  
 <span data-ttu-id="8ddae-139">執行緒也包含許多有用的內容下, 表所示︰</span><span class="sxs-lookup"><span data-stu-id="8ddae-139">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="8ddae-140">屬性</span><span class="sxs-lookup"><span data-stu-id="8ddae-140">Property</span></span>|<span data-ttu-id="8ddae-141">值</span><span class="sxs-lookup"><span data-stu-id="8ddae-141">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="8ddae-142"><xref:System.Threading.Thread.IsAlive%2A></xref:System.Threading.Thread.IsAlive%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-142"><xref:System.Threading.Thread.IsAlive%2A></span></span>|<span data-ttu-id="8ddae-143">包含值`True`如果執行緒在作用中。</span><span class="sxs-lookup"><span data-stu-id="8ddae-143">Contains the value `True` if a thread is active.</span></span>|  
|<span data-ttu-id="8ddae-144"><xref:System.Threading.Thread.IsBackground%2A></xref:System.Threading.Thread.IsBackground%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-144"><xref:System.Threading.Thread.IsBackground%2A></span></span>|<span data-ttu-id="8ddae-145">取得或設定布林值，表示是否執行緒或應該是背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-145">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="8ddae-146">背景執行緒就像前景執行緒一樣，但是背景執行緒無法停止防止處理程序。</span><span class="sxs-lookup"><span data-stu-id="8ddae-146">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="8ddae-147">停止所有處理程序所屬的前景執行緒之後，common language runtime 會藉由呼叫結束處理序<xref:System.Threading.Thread.Abort%2A>仍在執行的背景執行緒上的方法。</xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-147">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<span data-ttu-id="8ddae-148"><xref:System.Threading.Thread.Name%2A></xref:System.Threading.Thread.Name%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-148"><xref:System.Threading.Thread.Name%2A></span></span>|<span data-ttu-id="8ddae-149">取得或設定執行緒的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ddae-149">Gets or sets the name of a thread.</span></span> <span data-ttu-id="8ddae-150">最常用於探索的個別執行緒，當您偵錯。</span><span class="sxs-lookup"><span data-stu-id="8ddae-150">Most frequently used to discover individual threads when you debug.</span></span>|  
|<span data-ttu-id="8ddae-151"><xref:System.Threading.Thread.Priority%2A></xref:System.Threading.Thread.Priority%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-151"><xref:System.Threading.Thread.Priority%2A></span></span>|<span data-ttu-id="8ddae-152">取得或設定值，這個值，可由作業系統執行緒排程的優先順序。</span><span class="sxs-lookup"><span data-stu-id="8ddae-152">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<span data-ttu-id="8ddae-153"><xref:System.Threading.Thread.ThreadState%2A></xref:System.Threading.Thread.ThreadState%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-153"><xref:System.Threading.Thread.ThreadState%2A></span></span>|<span data-ttu-id="8ddae-154">包含說明執行緒的狀態的值。</span><span class="sxs-lookup"><span data-stu-id="8ddae-154">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="8ddae-155">執行緒優先順序</span><span class="sxs-lookup"><span data-stu-id="8ddae-155">Thread Priorities</span></span>  
 <span data-ttu-id="8ddae-156">每個執行緒都有 priority 屬性，用於判斷多少處理器時間後執行。</span><span class="sxs-lookup"><span data-stu-id="8ddae-156">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="8ddae-157">作業系統會配置較長的時間配量，以高優先順序的執行緒和較短的時間配量，以低優先順序的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8ddae-157">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="8ddae-158">建立新的執行緒，其值為`Normal`，但是您可以變更<xref:System.Threading.Thread.Priority%2A>屬性中的任何值<xref:System.Threading.ThreadPriority>列舉型別。</xref:System.Threading.ThreadPriority> </xref:System.Threading.Thread.Priority%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-158">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="8ddae-159">請參閱<xref:System.Threading.ThreadPriority>的各種不同的執行緒優先順序的詳細說明。</xref:System.Threading.ThreadPriority></span><span class="sxs-lookup"><span data-stu-id="8ddae-159">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="8ddae-160">前景和背景執行緒</span><span class="sxs-lookup"><span data-stu-id="8ddae-160">Foreground and Background Threads</span></span>  
 <span data-ttu-id="8ddae-161">A*幕前執行緒*無限期地執行，而*背景執行緒*會停止，因為最後一個幕前執行緒已停止。</span><span class="sxs-lookup"><span data-stu-id="8ddae-161">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="8ddae-162">您可以使用<xref:System.Threading.Thread.IsBackground%2A>屬性來判斷或變更背景執行緒的狀態。</xref:System.Threading.Thread.IsBackground%2A></span><span class="sxs-lookup"><span data-stu-id="8ddae-162">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddae-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ddae-163">See Also</span></span>  
 <span data-ttu-id="8ddae-164"><xref:System.Threading.Thread></xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="8ddae-164"><xref:System.Threading.Thread></span></span>   
<span data-ttu-id="8ddae-165"> [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="8ddae-165"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="8ddae-166"> [參數和傳回值的多執行緒程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="8ddae-166"> [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span></span>  
<span data-ttu-id="8ddae-167"> [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)</span><span class="sxs-lookup"><span data-stu-id="8ddae-167"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)</span></span>
