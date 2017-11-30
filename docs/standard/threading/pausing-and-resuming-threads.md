---
title: "暫止和繼續執行緒"
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
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="b6e05-102">暫止和繼續執行緒</span><span class="sxs-lookup"><span data-stu-id="b6e05-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="b6e05-103">最常見之同步處理執行緒活動的方式為封鎖及釋放執行緒、鎖定物件或程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="b6e05-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="b6e05-104">如需有關這些鎖定和封鎖機制的詳細資訊，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e05-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="b6e05-105">您也可以讓執行緒自己進入睡眠。</span><span class="sxs-lookup"><span data-stu-id="b6e05-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="b6e05-106">當執行緒已封鎖或睡眠中，您可以使用 <xref:System.Threading.ThreadInterruptedException> 解除其等候狀態。</span><span class="sxs-lookup"><span data-stu-id="b6e05-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="b6e05-107">Thread.Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="b6e05-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="b6e05-108">呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>方法會導致目前的執行緒可立即封鎖毫秒，或是您傳遞給方法的時間間隔的數目，並產生另一個執行緒的時間配量的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="b6e05-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="b6e05-109">該時間間隔過去後，睡眠中的執行緒便會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b6e05-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="b6e05-110">執行緒無法呼叫另一個執行緒上的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b6e05-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="b6e05-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>是一律會導致目前的執行緒睡眠的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="b6e05-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="b6e05-112">呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>值是<xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>造成執行緒睡眠，直到另一個執行緒呼叫中斷<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>方法睡眠中的執行緒，或直到它就會終止由呼叫其<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="b6e05-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="b6e05-113">下列範例說明這兩種可中斷睡眠中執行緒的方法。</span><span class="sxs-lookup"><span data-stu-id="b6e05-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="b6e05-114">中斷執行緒</span><span class="sxs-lookup"><span data-stu-id="b6e05-114">Interrupting Threads</span></span>  
 <span data-ttu-id="b6e05-115">您可以藉由呼叫中斷等候執行緒<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>方法擲回封鎖的執行緒上<xref:System.Threading.ThreadInterruptedException>，這會中斷的封鎖呼叫執行緒。</span><span class="sxs-lookup"><span data-stu-id="b6e05-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="b6e05-116">執行緒應該攔截 <xref:System.Threading.ThreadInterruptedException>並執行任何適合繼續進行的工作。</span><span class="sxs-lookup"><span data-stu-id="b6e05-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="b6e05-117">如果執行緒忽略例外狀況，則執行階段會攔截例外狀況，並停止執行緒。</span><span class="sxs-lookup"><span data-stu-id="b6e05-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6e05-118">在呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 時，如果未封鎖目標執行緒，則到封鎖之前，執行緒不會中斷。</span><span class="sxs-lookup"><span data-stu-id="b6e05-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="b6e05-119">如果執行緒永不封鎖，它可在沒有任何中斷的情況下完成。</span><span class="sxs-lookup"><span data-stu-id="b6e05-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="b6e05-120">如果等候是 Managed 等候，那麼 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 兩者都會立即喚醒執行緒。</span><span class="sxs-lookup"><span data-stu-id="b6e05-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="b6e05-121">如果等候是 unmanaged 的等候 (例如平台叫用呼叫 Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx)函式)，都沒有<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>也<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>可能需要控制執行緒，直到它傳回或呼叫 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6e05-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="b6e05-122">在 Managed 程式碼中，行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="b6e05-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="b6e05-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadInterruptedException> 在目的執行緒中被擲回。</span><span class="sxs-lookup"><span data-stu-id="b6e05-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="b6e05-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>喚醒時可能會在中，並造成任何等候執行緒<xref:System.Threading.ThreadAbortException>執行緒上擲回。</span><span class="sxs-lookup"><span data-stu-id="b6e05-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="b6e05-125">如需詳細資訊，請參閱[終結執行緒](../../../docs/standard/threading/destroying-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e05-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e05-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e05-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="b6e05-127">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="b6e05-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="b6e05-128">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="b6e05-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="b6e05-129">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="b6e05-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
