---
title: 屏障
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e09f1464a5df751034639d8bc1cb5d79faacd0f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714187"
---
# <a name="barrier"></a><span data-ttu-id="6c05b-102">屏障</span><span class="sxs-lookup"><span data-stu-id="6c05b-102">Barrier</span></span>

<span data-ttu-id="6c05b-103"><xref:System.Threading.Barrier?displayProperty=nameWithType> 是同步處理原始物件，可讓多個執行緒 (也稱為「參與者」) 以並行方式分階段處理演算法。</span><span class="sxs-lookup"><span data-stu-id="6c05b-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="6c05b-104">每個參與者都會執行，直到它到達程式碼中的屏障點為止。</span><span class="sxs-lookup"><span data-stu-id="6c05b-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="6c05b-105">屏障代表一個工作階段的結束。</span><span class="sxs-lookup"><span data-stu-id="6c05b-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="6c05b-106">當參與者到達屏障時，它就會封鎖，直到所有參與者都到達相同的屏障為止。</span><span class="sxs-lookup"><span data-stu-id="6c05b-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="6c05b-107">在所有參與者都到達屏障之後，您就可以選擇性地叫用階段後動作。</span><span class="sxs-lookup"><span data-stu-id="6c05b-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="6c05b-108">當所有其他執行緒仍然處於封鎖狀態時，單一執行緒可以使用這個階段後動作來執行動作。</span><span class="sxs-lookup"><span data-stu-id="6c05b-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="6c05b-109">執行這個動作之後，這些參與者都會解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="6c05b-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="6c05b-110">下列程式碼片段示範基本屏障模式。</span><span class="sxs-lookup"><span data-stu-id="6c05b-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="6c05b-111">如需完整的範例，請參閱[操作說明：使用屏障同步處理並行作業](how-to-synchronize-concurrent-operations-with-a-barrier.md)。</span><span class="sxs-lookup"><span data-stu-id="6c05b-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="6c05b-112">新增和移除參與者</span><span class="sxs-lookup"><span data-stu-id="6c05b-112">Adding and removing participants</span></span>

 <span data-ttu-id="6c05b-113">當您建立 <xref:System.Threading.Barrier> 執行個體時，請指定參與者的數目。</span><span class="sxs-lookup"><span data-stu-id="6c05b-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="6c05b-114">您也可以隨時以動態方式加入或移除參與者。</span><span class="sxs-lookup"><span data-stu-id="6c05b-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="6c05b-115">例如，如果某個參與者解決了自己那部分的問題，您就能儲存結果、停止該執行緒上的執行，並呼叫 <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> 以減少屏障中的參與者數目。</span><span class="sxs-lookup"><span data-stu-id="6c05b-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="6c05b-116">當您透過呼叫 <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType> 來加入參與者時，傳回值就會指定目前的階段編號，而這個編號可用於初始化新參與者的工作。</span><span class="sxs-lookup"><span data-stu-id="6c05b-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="6c05b-117">中斷的屏障</span><span class="sxs-lookup"><span data-stu-id="6c05b-117">Broken barriers</span></span>

 <span data-ttu-id="6c05b-118">如果某個參與者無法到達屏障，可能會發生死結。</span><span class="sxs-lookup"><span data-stu-id="6c05b-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="6c05b-119">若要避免這些死結，請使用 <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> 方法的多載來指定逾時期限和取消語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6c05b-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="6c05b-120">這些多載會先傳回每個參與者可檢查的布林值，然後再繼續進行下一個階段。</span><span class="sxs-lookup"><span data-stu-id="6c05b-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="6c05b-121">階段後例外狀況</span><span class="sxs-lookup"><span data-stu-id="6c05b-121">Post-phase exceptions</span></span>

 <span data-ttu-id="6c05b-122">如果階段後委派擲回例外狀況，它就會包裝在 <xref:System.Threading.BarrierPostPhaseException> 物件中，然後傳播給所有參與者。</span><span class="sxs-lookup"><span data-stu-id="6c05b-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="6c05b-123">屏障與 ContinueWhenAll 的比較</span><span class="sxs-lookup"><span data-stu-id="6c05b-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="6c05b-124">當執行緒在迴圈中執行多個階段時，屏障會特別有用。</span><span class="sxs-lookup"><span data-stu-id="6c05b-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="6c05b-125">如果您的程式碼只需要一個或兩個工作階段，請考慮是否要使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件搭配任何一種隱含聯結，包括：</span><span class="sxs-lookup"><span data-stu-id="6c05b-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6c05b-126">如需詳細資訊，請參閱[使用接續工作鏈結工作](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="6c05b-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c05b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c05b-127">See also</span></span>

- [<span data-ttu-id="6c05b-128">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="6c05b-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="6c05b-129">操作說明：使用屏障同步處理並行作業</span><span class="sxs-lookup"><span data-stu-id="6c05b-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
