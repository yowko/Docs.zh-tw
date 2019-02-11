---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d3825ef73a6ec312ff51d1bddf5360f3de6cc69
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758912"
---
# <a name="countdownevent"></a><span data-ttu-id="f00cd-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="f00cd-102">CountdownEvent</span></span>
<span data-ttu-id="f00cd-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 是一個同步處理基本類型，在發出了特定次數的訊號給它之後，就會解除封鎖其等候中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f00cd-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="f00cd-104"><xref:System.Threading.CountdownEvent> 是針對下列案例所設計：您必須使用 <xref:System.Threading.ManualResetEvent> 或 <xref:System.Threading.ManualResetEventSlim>，並在發出訊號給事件之前手動遞減變數。</span><span class="sxs-lookup"><span data-stu-id="f00cd-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="f00cd-105">例如，在分支/聯結案例中，您可以只建立訊號計數為 5 的 <xref:System.Threading.CountdownEvent>，然後在執行緒集區上啟動五個工作項目，並讓每個工作項目在其完成時呼叫 <xref:System.Threading.CountdownEvent.Signal%2A>。</span><span class="sxs-lookup"><span data-stu-id="f00cd-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="f00cd-106">每次呼叫 <xref:System.Threading.CountdownEvent.Signal%2A> 就會將訊號計數遞減 1。</span><span class="sxs-lookup"><span data-stu-id="f00cd-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="f00cd-107">在主執行緒上，對 <xref:System.Threading.CountdownEvent.Wait%2A> 的呼叫將會封鎖，直到訊號計數為零為止。</span><span class="sxs-lookup"><span data-stu-id="f00cd-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f00cd-108">對於不需與舊版 .NET Framework 同步處理 API 互動的程式碼，請考慮使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件或 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 方法，以甚至更簡單的方式表達分支-聯結的平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="f00cd-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="f00cd-109"><xref:System.Threading.CountdownEvent> 具有下列其他功能：</span><span class="sxs-lookup"><span data-stu-id="f00cd-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="f00cd-110">等候作業可以使用取消語彙基元來取消。</span><span class="sxs-lookup"><span data-stu-id="f00cd-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="f00cd-111">建立執行個體之後，即可遞增其訊號計數。</span><span class="sxs-lookup"><span data-stu-id="f00cd-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="f00cd-112">藉由呼叫 <xref:System.Threading.CountdownEvent.Reset%2A> 方法傳回 <xref:System.Threading.CountdownEvent.Wait%2A> 之後，就可重複使用執行個體。</span><span class="sxs-lookup"><span data-stu-id="f00cd-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="f00cd-113">執行個體會公開 <xref:System.Threading.WaitHandle>，以便與其他 .NET Framework 同步處理 API 整合，例如 <xref:System.Threading.WaitHandle.WaitAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="f00cd-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="f00cd-114">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="f00cd-114">Basic Usage</span></span>  
 <span data-ttu-id="f00cd-115">下列範例示範如何將 <xref:System.Threading.CountdownEvent> 與 <xref:System.Threading.ThreadPool> 工作項目搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f00cd-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="f00cd-116">含有取消的 CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="f00cd-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="f00cd-117">下列範例示範如何使用取消語彙基元，來取消 <xref:System.Threading.CountdownEvent> 上的等候作業。</span><span class="sxs-lookup"><span data-stu-id="f00cd-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="f00cd-118">基本模式會遵循適用於統一取消的模型，這是在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中引進的。</span><span class="sxs-lookup"><span data-stu-id="f00cd-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="f00cd-119">如需詳細資訊，請參閱[受控執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="f00cd-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="f00cd-120">請注意，等候作業不會取消正在發出訊號給它的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f00cd-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="f00cd-121">一般而言，會將取消套用至邏輯作業，其中可以包括在事件上等候，以及正在同步處理等候的所有工作項目。</span><span class="sxs-lookup"><span data-stu-id="f00cd-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="f00cd-122">在此範例中，會針對每個工作項目傳遞相同取消語彙基元的複本，讓它可以回應取消要求。</span><span class="sxs-lookup"><span data-stu-id="f00cd-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f00cd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f00cd-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
