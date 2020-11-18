---
title: 暫停和中斷執行緒
description: 瞭解如何在 .NET 中暫停 & 中斷線程。 瞭解如何使用 Thread 之類的方法。睡眠 & Thread，& 例外狀況，例如 System.threading.threadinterruptedexception>。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 157109ad9e9009516b107b271a59267f982c784d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826218"
---
# <a name="pausing-and-interrupting-threads"></a><span data-ttu-id="09f81-104">暫停和中斷執行緒</span><span class="sxs-lookup"><span data-stu-id="09f81-104">Pausing and interrupting threads</span></span>

<span data-ttu-id="09f81-105">最常見之同步處理執行緒活動的方式為封鎖及釋放執行緒、鎖定物件或程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="09f81-105">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="09f81-106">如需有關這些鎖定和封鎖機制的詳細資訊，請參閱[同步處理原始物件概觀](overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="09f81-106">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="09f81-107">您也可以讓執行緒自己進入睡眠。</span><span class="sxs-lookup"><span data-stu-id="09f81-107">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="09f81-108">當執行緒已封鎖或睡眠中，您可以使用 <xref:System.Threading.ThreadInterruptedException> 解除其等候狀態。</span><span class="sxs-lookup"><span data-stu-id="09f81-108">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="09f81-109">Thread.Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="09f81-109">The Thread.Sleep method</span></span>

 <span data-ttu-id="09f81-110">呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 方法會導致立即封鎖目前執行緒，封鎖時間為您傳遞至方法的毫秒數或時間間隔，並且會將剩餘的時間配量讓與另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="09f81-110">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="09f81-111">該時間間隔過去後，睡眠中的執行緒便會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09f81-111">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="09f81-112">執行緒無法呼叫另一個執行緒上的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="09f81-112">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="09f81-113"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 是一律會導致目前執行緒進入睡眠的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="09f81-113"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="09f81-114">呼叫具有 <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> 值的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 會造成執行緒進入睡眠，直到被另一個在睡眠中執行緒上呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 的執行緒中斷，或直到它由其 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法的呼叫終止。</span><span class="sxs-lookup"><span data-stu-id="09f81-114">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="09f81-115">下列範例說明這兩種可中斷睡眠中執行緒的方法。</span><span class="sxs-lookup"><span data-stu-id="09f81-115">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="09f81-116">中斷執行緒</span><span class="sxs-lookup"><span data-stu-id="09f81-116">Interrupting threads</span></span>

 <span data-ttu-id="09f81-117">您可藉由在封鎖的執行緒上呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 方法來中斷等候中的執行緒，以擲回 <xref:System.Threading.ThreadInterruptedException>，這會中斷執行緒的封鎖呼叫。</span><span class="sxs-lookup"><span data-stu-id="09f81-117">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="09f81-118">執行緒應該攔截 <xref:System.Threading.ThreadInterruptedException>並執行任何適合繼續進行的工作。</span><span class="sxs-lookup"><span data-stu-id="09f81-118">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="09f81-119">如果執行緒忽略例外狀況，則執行階段會攔截例外狀況，並停止執行緒。</span><span class="sxs-lookup"><span data-stu-id="09f81-119">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09f81-120">在呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 時，如果未封鎖目標執行緒，則到封鎖之前，執行緒不會中斷。</span><span class="sxs-lookup"><span data-stu-id="09f81-120">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="09f81-121">如果執行緒永不封鎖，它可在沒有任何中斷的情況下完成。</span><span class="sxs-lookup"><span data-stu-id="09f81-121">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="09f81-122">如果等候是 Managed 等候，那麼 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 兩者都會立即喚醒執行緒。</span><span class="sxs-lookup"><span data-stu-id="09f81-122">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="09f81-123">如果等候是非受控的等候 (例如，平台叫用 Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) 函式的呼叫)，則 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 都無法控制執行緒，直到它傳回或呼叫受控程式碼為止。</span><span class="sxs-lookup"><span data-stu-id="09f81-123">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="09f81-124">在 Managed 程式碼中，行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="09f81-124">In managed code, the behavior is as follows:</span></span>  
  
- <span data-ttu-id="09f81-125"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadInterruptedException> 在目的執行緒中被擲回。</span><span class="sxs-lookup"><span data-stu-id="09f81-125"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
- <span data-ttu-id="09f81-126"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadAbortException> 在執行緒中被擲回。</span><span class="sxs-lookup"><span data-stu-id="09f81-126"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="09f81-127">如需詳細資訊，請參閱[終結執行緒](destroying-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="09f81-127">For details, see [Destroying Threads](destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f81-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="09f81-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [<span data-ttu-id="09f81-129">執行緒</span><span class="sxs-lookup"><span data-stu-id="09f81-129">Threading</span></span>](index.md)
- [<span data-ttu-id="09f81-130">使用執行緒和執行緒</span><span class="sxs-lookup"><span data-stu-id="09f81-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="09f81-131">同步處理原始物件總覽</span><span class="sxs-lookup"><span data-stu-id="09f81-131">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)
