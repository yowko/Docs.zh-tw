---
title: 執行緒物件和功能
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02f88faab6ddbaa026e73ad61bc63fbe8e5e00ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591321"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="e0900-102">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="e0900-102">Threading Objects and Features</span></span>
<span data-ttu-id="e0900-103">.NET Framework 提供一些物件，可協助您建立及管理多執行緒應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0900-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="e0900-104">Managed 執行緒是以 <xref:System.Threading.Thread> 類別來表示。</span><span class="sxs-lookup"><span data-stu-id="e0900-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="e0900-105"><xref:System.Threading.ThreadPool> 類別可讓您輕鬆建立及管理多執行緒的背景工作。</span><span class="sxs-lookup"><span data-stu-id="e0900-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="e0900-106"><xref:System.ComponentModel.BackgroundWorker> 類別會針對與使用者介面互動的工作執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="e0900-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="e0900-107"><xref:System.Threading.Timer> 類別會定期執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="e0900-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="e0900-108">此外，還有一些類別會同步處理執行緒的活動，其中包括在 .NET Framework 2.0 版中引入的 <xref:System.Threading.Semaphore> 和 <xref:System.Threading.EventWaitHandle> 類別。</span><span class="sxs-lookup"><span data-stu-id="e0900-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e0900-109">[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)中將比較這些類別的功能。</span><span class="sxs-lookup"><span data-stu-id="e0900-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0900-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="e0900-110">In This Section</span></span>  
 [<span data-ttu-id="e0900-111">Managed 執行緒集區</span><span class="sxs-lookup"><span data-stu-id="e0900-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="e0900-112">說明 **ThreadPool** 類別，這個類別可讓您要求執行緒執行工作，而不需要自行進行任何執行緒管理。</span><span class="sxs-lookup"><span data-stu-id="e0900-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="e0900-113">計時器</span><span class="sxs-lookup"><span data-stu-id="e0900-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="e0900-114">說明如何使用 **Timer** 來指定要在指定時間呼叫的委派。</span><span class="sxs-lookup"><span data-stu-id="e0900-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="e0900-115">監視</span><span class="sxs-lookup"><span data-stu-id="e0900-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="e0900-116">說明如何使用 **Monitor** 類別來同步存取成員，或建置自己的執行緒管理型別。</span><span class="sxs-lookup"><span data-stu-id="e0900-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="e0900-117">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="e0900-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="e0900-118">描述 <xref:System.Threading.WaitHandle> 類別，這是事件等候控制代碼、Mutex 和信號的抽象基底類別，可用來等候多個同步處理事件。</span><span class="sxs-lookup"><span data-stu-id="e0900-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="e0900-119">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="e0900-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="e0900-120">描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。</span><span class="sxs-lookup"><span data-stu-id="e0900-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="e0900-121">Mutex</span><span class="sxs-lookup"><span data-stu-id="e0900-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="e0900-122">說明如何使用 <xref:System.Threading.Mutex> 來同步處理對物件的存取，或建置自己的同步處理機制。</span><span class="sxs-lookup"><span data-stu-id="e0900-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="e0900-123">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="e0900-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="e0900-124">說明如何使用 <xref:System.Threading.Interlocked> 類別來遞增或遞減值，並在單一不可部分完成的作業中儲存這個值。</span><span class="sxs-lookup"><span data-stu-id="e0900-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="e0900-125">Reader-Writer 鎖定</span><span class="sxs-lookup"><span data-stu-id="e0900-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="e0900-126">定義實作單一寫入器/多個讀取器語意的鎖定。</span><span class="sxs-lookup"><span data-stu-id="e0900-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="e0900-127">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="e0900-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="e0900-128">描述 <xref:System.Threading.Semaphore> 物件，並說明如何使用這些物件來控制對有限資源的存取。</span><span class="sxs-lookup"><span data-stu-id="e0900-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="e0900-129">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="e0900-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="e0900-130">比較提供用以鎖定及同步處理 Managed 執行緒之 .NET Framework 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="e0900-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="e0900-131">barrier</span><span class="sxs-lookup"><span data-stu-id="e0900-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="e0900-132">描述 <xref:System.Threading.Barrier> 物件，這些物件會實作屏障模式以便協調階段式作業中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e0900-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="e0900-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="e0900-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="e0900-134">描述 <xref:System.Threading.SpinLock>，這是適用於特定低階案例之 Monitor 類別的輕量型替代方案。</span><span class="sxs-lookup"><span data-stu-id="e0900-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="e0900-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="e0900-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="e0900-136">描述 <xref:System.Threading.SpinWait>，這是在起始核心架構等候之前執行忙碌空轉的低階同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="e0900-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e0900-137">參考資料</span><span class="sxs-lookup"><span data-stu-id="e0900-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="e0900-138">提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="e0900-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="e0900-139">啟用與使用者介面互動的背景工作，透過使用者介面執行緒上引發的事件來通訊。</span><span class="sxs-lookup"><span data-stu-id="e0900-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0900-140">相關章節</span><span class="sxs-lookup"><span data-stu-id="e0900-140">Related Sections</span></span>  
 [<span data-ttu-id="e0900-141">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="e0900-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="e0900-142">描述 I/O 非同步完成通訊埠如何使用執行緒集區，要求只有在輸入/輸出作業完成時才進行處理。</span><span class="sxs-lookup"><span data-stu-id="e0900-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="e0900-143">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="e0900-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="e0900-144">描述在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] (含) 以後版本中進行多執行緒程式設計的建議方法。</span><span class="sxs-lookup"><span data-stu-id="e0900-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
