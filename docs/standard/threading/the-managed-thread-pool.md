---
title: Managed 執行緒集區
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592414"
---
# <a name="the-managed-thread-pool"></a><span data-ttu-id="a5f0a-102">Managed 執行緒集區</span><span class="sxs-lookup"><span data-stu-id="a5f0a-102">The Managed Thread Pool</span></span>
<span data-ttu-id="a5f0a-103"><xref:System.Threading.ThreadPool> 類別為您的應用程式提供了受到系統管理的背景工作執行緒集區，讓您專注於應用程式工作上，而不是執行緒的管理。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-103">The <xref:System.Threading.ThreadPool> class provides your application with a pool of worker threads that are managed by the system, allowing you to concentrate on application tasks rather than thread management.</span></span> <span data-ttu-id="a5f0a-104">如果您有需要在背景處理的簡短工作，Managed 執行緒集區是利用多重執行緒的一個簡單方式。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-104">If you have short tasks that require background processing, the managed thread pool is an easy way to take advantage of multiple threads.</span></span> <span data-ttu-id="a5f0a-105">例如，從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以建立 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件，這兩個物件會在執行緒集區執行緒上執行非同步工作。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-105">For example, beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] you can create <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects, which perform asynchronous tasks on thread pool threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5f0a-106">從 [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 開始，執行緒集區的輸送量在三個關鍵領域有了重大改進：佇列工作、分派執行緒集區執行緒，以及分派 I/O 完成執行緒。這三個領域在舊版 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中，被視為是瓶頸所在。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-106">Starting with the [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], the throughput of the thread pool is significantly improved in three key areas that were identified as bottlenecks in previous releases of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: queuing tasks, dispatching thread pool threads, and dispatching I/O completion threads.</span></span> <span data-ttu-id="a5f0a-107">若要使用這項功能，您的應用程式應將目標設為 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] (含) 以後版本。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-107">To use this functionality, your application should target the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] or later.</span></span>  
  
 <span data-ttu-id="a5f0a-108">對於與使用者介面互動的背景工作而言，.NET Framework 2.0 版也提供了 <xref:System.ComponentModel.BackgroundWorker> 類別，這個類別透過使用者介面執行緒上所引發的事件來通訊。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-108">For background tasks that interact with the user interface, the .NET Framework version 2.0 also provides the <xref:System.ComponentModel.BackgroundWorker> class, which communicates using events raised on the user interface thread.</span></span>  
  
 <span data-ttu-id="a5f0a-109">.NET Framework 使用執行緒集區執行緒的目的有許多個，其中包括非同步的 I/O 完成、計時器回呼、註冊的等候作業、使用委派的非同步方法，以及 <xref:System.Net> 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-109">The .NET Framework uses thread pool threads for many purposes, including asynchronous I/O completion, timer callbacks, registered wait operations, asynchronous method calls using delegates, and <xref:System.Net> socket connections.</span></span>  
  
## <a name="when-not-to-use-thread-pool-threads"></a><span data-ttu-id="a5f0a-110">何時不該使用執行緒集區執行緒</span><span class="sxs-lookup"><span data-stu-id="a5f0a-110">When Not to Use Thread Pool Threads</span></span>  
 <span data-ttu-id="a5f0a-111">有好幾種情況適合建立及管理自己的執行緒，而不是使用執行緒集區執行緒：</span><span class="sxs-lookup"><span data-stu-id="a5f0a-111">There are several scenarios in which it is appropriate to create and manage your own threads instead of using thread pool threads:</span></span>  
  
-   <span data-ttu-id="a5f0a-112">您需要前景執行緒。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-112">You require a foreground thread.</span></span>  
  
-   <span data-ttu-id="a5f0a-113">您需要執行緒有特定的優先權。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-113">You require a thread to have a particular priority.</span></span>  
  
-   <span data-ttu-id="a5f0a-114">您有一些工作會造成執行緒封鎖一段很長的時間。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-114">You have tasks that cause the thread to block for long periods of time.</span></span> <span data-ttu-id="a5f0a-115">執行緒集區有執行緒數目上限，因此大量已封鎖的執行緒集區執行緒可能會導致工作無法啟動。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-115">The thread pool has a maximum number of threads, so a large number of blocked thread pool threads might prevent tasks from starting.</span></span>  
  
-   <span data-ttu-id="a5f0a-116">您需要將執行緒放在單一執行緒 Apartment 中。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-116">You need to place threads into a single-threaded apartment.</span></span> <span data-ttu-id="a5f0a-117">所有 <xref:System.Threading.ThreadPool> 執行緒都會在多執行緒 Apartment 中。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-117">All <xref:System.Threading.ThreadPool> threads are in the multithreaded apartment.</span></span>  
  
-   <span data-ttu-id="a5f0a-118">您需要有一個與執行緒關聯的固定識別，或是讓執行緒專屬於某項工作。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-118">You need to have a stable identity associated with the thread, or to dedicate a thread to a task.</span></span>  
  
## <a name="thread-pool-characteristics"></a><span data-ttu-id="a5f0a-119">執行緒集區特性</span><span class="sxs-lookup"><span data-stu-id="a5f0a-119">Thread Pool Characteristics</span></span>  
 <span data-ttu-id="a5f0a-120">執行緒集區執行緒為背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-120">Thread pool threads are background threads.</span></span> <span data-ttu-id="a5f0a-121">請參閱[前景和背景執行緒](../../../docs/standard/threading/foreground-and-background-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-121">See [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md).</span></span> <span data-ttu-id="a5f0a-122">每個執行緒都會使用預設堆疊大小、以預先優先權執行，並且位於多執行緒 Apartment 中。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-122">Each thread uses the default stack size, runs at the default priority, and is in the multithreaded apartment.</span></span>  
  
 <span data-ttu-id="a5f0a-123">每個處理序只有一個執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-123">There is only one thread pool per process.</span></span>  
  
### <a name="exceptions-in-thread-pool-threads"></a><span data-ttu-id="a5f0a-124">執行緒集區執行緒中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="a5f0a-124">Exceptions in Thread Pool Threads</span></span>  
 <span data-ttu-id="a5f0a-125">執行緒集區執行緒上未處理的例外狀況會結束處理序。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-125">Unhandled exceptions on thread pool threads terminate the process.</span></span> <span data-ttu-id="a5f0a-126">這項規則有三個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="a5f0a-126">There are three exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="a5f0a-127">執行緒集區執行緒擲回 <xref:System.Threading.ThreadAbortException>，因為已呼叫 <xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-127">A <xref:System.Threading.ThreadAbortException> is thrown in a thread pool thread, because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="a5f0a-128">執行緒集區執行緒擲回 <xref:System.AppDomainUnloadedException>，因為正在卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-128">An <xref:System.AppDomainUnloadedException> is thrown in a thread pool thread, because the application domain is being unloaded.</span></span>  
  
-   <span data-ttu-id="a5f0a-129">Common Language Runtime 或主應用程式處理序會結束這個執行緒。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-129">The common language runtime or a host process terminates the thread.</span></span>  
  
 <span data-ttu-id="a5f0a-130">如需詳細資訊，請參閱[受控執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-130">For more information, see [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5f0a-131">在 .NET Framework 1.0 和 1.1 版中，Common Language Runtime 會以無訊息模式在執行緒集區執行緒中截獲未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-131">In the .NET Framework versions 1.0 and 1.1, the common language runtime silently traps unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="a5f0a-132">這可能會破壞應用程式狀態，最終導致應用程式沒有回應，而可能讓偵錯工作變得相當困難。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-132">This might corrupt application state and eventually cause applications to hang, which might be very difficult to debug.</span></span>  
  
### <a name="maximum-number-of-thread-pool-threads"></a><span data-ttu-id="a5f0a-133">執行緒集區執行緒最大數目</span><span class="sxs-lookup"><span data-stu-id="a5f0a-133">Maximum Number of Thread Pool Threads</span></span>  
 <span data-ttu-id="a5f0a-134">可排入執行緒集區佇列中的作業數目只會受到可用記憶體的限制；不過，執行緒集區會限制可同時在處理序中使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-134">The number of operations that can be queued to the thread pool is limited only by available memory; however, the thread pool limits the number of threads that can be active in the process simultaneously.</span></span> <span data-ttu-id="a5f0a-135">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，處理序的執行緒集區預設大小取決於數個因素，例如虛擬位址空間的大小。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-135">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the default size of the thread pool for a process depends on several factors, such as the size of the virtual address space.</span></span> <span data-ttu-id="a5f0a-136">處理序可以呼叫 <xref:System.Threading.ThreadPool.GetMaxThreads%2A> 方法來決定執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-136">A process can call the <xref:System.Threading.ThreadPool.GetMaxThreads%2A> method to determine the number of threads.</span></span>  
  
 <span data-ttu-id="a5f0a-137">您可以使用 <xref:System.Threading.ThreadPool.GetMaxThreads%2A> 和 <xref:System.Threading.ThreadPool.SetMaxThreads%2A> 方法來控制執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-137">You can control the maximum number of threads by using the <xref:System.Threading.ThreadPool.GetMaxThreads%2A> and <xref:System.Threading.ThreadPool.SetMaxThreads%2A> methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5f0a-138">在 .NET Framework 1.0 和 1.1 版中，無法從 Managed 程式碼設定執行緒集區的大小。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-138">In the .NET Framework versions 1.0 and 1.1, the size of the thread pool cannot be set from managed code.</span></span> <span data-ttu-id="a5f0a-139">裝載 Common Language Runtime 的程式碼可以使用 mscoree.h 中定義的 `CorSetMaxThreads` 來設定大小。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-139">Code that hosts the common language runtime can set the size using `CorSetMaxThreads`, defined in mscoree.h.</span></span>  
  
### <a name="thread-pool-minimums"></a><span data-ttu-id="a5f0a-140">執行緒集區最小值</span><span class="sxs-lookup"><span data-stu-id="a5f0a-140">Thread Pool Minimums</span></span>  
 <span data-ttu-id="a5f0a-141">執行緒集區會視需要提供新的背景工作執行緒或 I/O 完成執行緒，直到達到每個分類的指定最小值為止。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-141">The thread pool provides new worker threads or I/O completion threads on demand until it reaches a specified minimum for each category.</span></span> <span data-ttu-id="a5f0a-142">您可以使用 <xref:System.Threading.ThreadPool.GetMinThreads%2A> 方法取得這些最小值。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-142">You can use the <xref:System.Threading.ThreadPool.GetMinThreads%2A> method to obtain these minimum values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5f0a-143">當需求很低時，執行緒集區執行緒的實際數目可能低於最小值。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-143">When demand is low, the actual number of thread pool threads can fall below the minimum values.</span></span>  
  
 <span data-ttu-id="a5f0a-144">當達到最小值時，執行緒集區可以建立額外的執行緒，或是等候部分工作完成。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-144">When a minimum is reached, the thread pool can create additional threads or wait until some tasks complete.</span></span> <span data-ttu-id="a5f0a-145">從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，執行緒集區會建立並終結背景工作執行緒，以便最佳化輸送量，輸送量的定義為每個時間單位完成的工作數目。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-145">Beginning with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the thread pool creates and destroys worker threads in order to optimize throughput, which is defined as the number of tasks that complete per unit of time.</span></span> <span data-ttu-id="a5f0a-146">執行緒太少可能無法最有效地利用可用資源，而執行緒太多則可能增加資源爭用的情況。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-146">Too few threads might not make optimal use of available resources, whereas too many threads could increase resource contention.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a5f0a-147">您可以使用 <xref:System.Threading.ThreadPool.SetMinThreads%2A> 方法來提高閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-147">You can use the <xref:System.Threading.ThreadPool.SetMinThreads%2A> method to increase the minimum number of idle threads.</span></span> <span data-ttu-id="a5f0a-148">不過，不必要地增加這些值，可能會造成效能問題。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-148">However, unnecessarily increasing these values can cause performance problems.</span></span> <span data-ttu-id="a5f0a-149">如果太多工作同時啟動，則所有工作可能都會變慢。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-149">If too many tasks start at the same time, all of them might appear to be slow.</span></span> <span data-ttu-id="a5f0a-150">在大部分情況下，執行緒集區使用自己的演算法來配置執行緒的效能較佳。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-150">In most cases the thread pool will perform better with its own algorithm for allocating threads.</span></span>  
  
## <a name="skipping-security-checks"></a><span data-ttu-id="a5f0a-151">略過安全性檢查</span><span class="sxs-lookup"><span data-stu-id="a5f0a-151">Skipping Security Checks</span></span>  
 <span data-ttu-id="a5f0a-152">執行緒集區也提供 <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> 和 <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-152">The thread pool also provides the <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> and <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="a5f0a-153">只有在您確定呼叫端的堆疊與排入佇列之工作的執行期間所做的任何安全性檢查無關時，才能使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-153">Use these methods only when you are certain that the caller's stack is irrelevant to any security checks performed during the execution of the queued task.</span></span> <span data-ttu-id="a5f0a-154"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 和 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 都可擷取呼叫端的堆疊，這個堆疊會在執行緒開始執行工作時，合併到執行緒集區執行緒的堆疊中。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-154"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> and <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> both capture the caller's stack, which is merged into the stack of the thread pool thread when the thread begins to execute a task.</span></span> <span data-ttu-id="a5f0a-155">如果需要安全性檢查，則必須檢查整個堆疊。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-155">If a security check is required, the entire stack must be checked.</span></span> <span data-ttu-id="a5f0a-156">雖然檢查能夠提供安全性，但是也帶來效能成本。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-156">Although the check provides safety, it also has a performance cost.</span></span>  
  
## <a name="using-the-thread-pool"></a><span data-ttu-id="a5f0a-157">使用執行緒集區</span><span class="sxs-lookup"><span data-stu-id="a5f0a-157">Using the Thread Pool</span></span>  
 <span data-ttu-id="a5f0a-158">從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，使用執行緒集區的最簡單方式是使用[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-158">Beginning with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the easiest way to use the thread pool is to use the [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md).</span></span> <span data-ttu-id="a5f0a-159">根據預設，平行程式庫類型 (例如 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601>) 會使用執行緒集區執行緒來執行工作。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-159">By default, parallel library types like <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> use thread pool threads to run tasks.</span></span> <span data-ttu-id="a5f0a-160">您也可以透過下列方式使用執行緒集區：從 Managed 程式碼呼叫 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> (或從 Unmanaged 程式碼呼叫 `CorQueueUserWorkItem`)，並傳遞代表執行工作之方法的 <xref:System.Threading.WaitCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-160">You can also use the thread pool by calling <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> from managed code (or `CorQueueUserWorkItem` from unmanaged code) and passing a <xref:System.Threading.WaitCallback> delegate representing the method that performs the task.</span></span> <span data-ttu-id="a5f0a-161">使用執行緒集區的另一種方式，是使用 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法並傳遞 <xref:System.Threading.WaitHandle> (它在收到信號或逾時的時候會呼叫由 <xref:System.Threading.WaitOrTimerCallback> 委派表示的方法)，藉以將與等候作業有關的工作項目排入佇列。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-161">Another way to use the thread pool is to queue work items that are related to a wait operation by using the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method and passing a <xref:System.Threading.WaitHandle> that, when signaled or when timed out, calls the method represented by the <xref:System.Threading.WaitOrTimerCallback> delegate.</span></span> <span data-ttu-id="a5f0a-162">執行緒集區執行緒可用來叫用回呼方法。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-162">Thread pool threads are used to invoke callback methods.</span></span>  
  
## <a name="threadpool-examples"></a><span data-ttu-id="a5f0a-163">ThreadPool 範例</span><span class="sxs-lookup"><span data-stu-id="a5f0a-163">ThreadPool Examples</span></span>  
 <span data-ttu-id="a5f0a-164">本節中的程式碼範例使用 <xref:System.Threading.Tasks.Task> 類別、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 方法和 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法，來示範執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-164">The code examples in this section demonstrate the thread pool by using the <xref:System.Threading.Tasks.Task> class, the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method, and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method.</span></span>  
  
-   [<span data-ttu-id="a5f0a-165">使用工作平行程式庫執行非同步工作</span><span class="sxs-lookup"><span data-stu-id="a5f0a-165">Executing Asynchronous Tasks with the Task Parallel Library</span></span>](#TaskParallelLibrary)  
  
-   [<span data-ttu-id="a5f0a-166">使用 QueueUserWorkItem 以非同步方式執行程式碼</span><span class="sxs-lookup"><span data-stu-id="a5f0a-166">Executing Code Asynchronously with QueueUserWorkItem</span></span>](#ExecuteCodeWithQUWI)  
  
-   [<span data-ttu-id="a5f0a-167">提供工作資料给 QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="a5f0a-167">Supplying Task Data for QueueUserWorkItem</span></span>](#TaskDataForQUWI)  
  
-   [<span data-ttu-id="a5f0a-168">使用 RegisterWaitForSingleObject</span><span class="sxs-lookup"><span data-stu-id="a5f0a-168">Using RegisterWaitForSingleObject</span></span>](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a><span data-ttu-id="a5f0a-169">使用工作平行程式庫執行非同步工作</span><span class="sxs-lookup"><span data-stu-id="a5f0a-169">Executing Asynchronous Tasks with the Task Parallel Library</span></span>  
 <span data-ttu-id="a5f0a-170">下列範例示範如何透過呼叫 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法，建立及使用 <xref:System.Threading.Tasks.Task> 物件。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-170">The following example shows how to create and use a <xref:System.Threading.Tasks.Task> object by calling the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5f0a-171">如需使用 <xref:System.Threading.Tasks.Task%601> 類別從非同步工作傳回值的範例，請參閱[如何：傳回工作的值](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-171">For an example that uses the <xref:System.Threading.Tasks.Task%601> class to return a value from an asynchronous task, see [How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).</span></span>  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a><span data-ttu-id="a5f0a-172">使用 QueueUserWorkItem 以非同步方式執行程式碼</span><span class="sxs-lookup"><span data-stu-id="a5f0a-172">Executing Code Asynchronously with QueueUserWorkItem</span></span>  
 <span data-ttu-id="a5f0a-173">下列範例使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法來查詢一個非常簡單的工作，這個工作是由 `ThreadProc` 方法表示。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-173">The following example queues a very simple task, represented by the `ThreadProc` method, using the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a><span data-ttu-id="a5f0a-174">提供工作資料给 QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="a5f0a-174">Supplying Task Data for QueueUserWorkItem</span></span>  
 <span data-ttu-id="a5f0a-175">下列程式碼範例使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法將工作排入佇列，並提供工作的資料。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-175">The following code example uses the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method to queue a task and supply the data for the task.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a><span data-ttu-id="a5f0a-176">使用 RegisterWaitForSingleObject</span><span class="sxs-lookup"><span data-stu-id="a5f0a-176">Using RegisterWaitForSingleObject</span></span>  
 <span data-ttu-id="a5f0a-177">下列範例示範幾個執行緒處理功能。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-177">The following example demonstrates several threading features.</span></span>  
  
-   <span data-ttu-id="a5f0a-178">使用 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 方法將工作排入佇列，以供 <xref:System.Threading.ThreadPool> 執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-178">Queuing a task for execution by <xref:System.Threading.ThreadPool> threads, with the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method.</span></span>  
  
-   <span data-ttu-id="a5f0a-179">使用 <xref:System.Threading.AutoResetEvent> 向要執行的工作發出信號。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-179">Signaling a task to execute, with <xref:System.Threading.AutoResetEvent>.</span></span> <span data-ttu-id="a5f0a-180">[EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-180">See [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).</span></span>  
  
-   <span data-ttu-id="a5f0a-181">使用 <xref:System.Threading.WaitOrTimerCallback> 委派處理逾時和信號。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-181">Handling both time-outs and signals with a <xref:System.Threading.WaitOrTimerCallback> delegate.</span></span>  
  
-   <span data-ttu-id="a5f0a-182">使用 <xref:System.Threading.RegisteredWaitHandle> 取消已排入佇列的工作。</span><span class="sxs-lookup"><span data-stu-id="a5f0a-182">Canceling a queued task with <xref:System.Threading.RegisteredWaitHandle>.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f0a-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5f0a-183">See Also</span></span>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [<span data-ttu-id="a5f0a-184">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="a5f0a-184">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [<span data-ttu-id="a5f0a-185">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="a5f0a-185">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [<span data-ttu-id="a5f0a-186">操作說明：傳回工作的值</span><span class="sxs-lookup"><span data-stu-id="a5f0a-186">How to: Return a Value from a Task</span></span>](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [<span data-ttu-id="a5f0a-187">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="a5f0a-187">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="a5f0a-188">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="a5f0a-188">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 [<span data-ttu-id="a5f0a-189">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="a5f0a-189">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="a5f0a-190">計時器</span><span class="sxs-lookup"><span data-stu-id="a5f0a-190">Timers</span></span>](../../../docs/standard/threading/timers.md)
