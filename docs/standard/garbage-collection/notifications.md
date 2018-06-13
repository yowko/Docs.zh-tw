---
title: 記憶體回收告知
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3470ebdd55adc97a60f07228c441cb7c94a53e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579154"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="e175c-102">記憶體回收告知</span><span class="sxs-lookup"><span data-stu-id="e175c-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="e175c-103">在某些情況下，通用語言執行平台 (CLR) 所執行的完整記憶體回收 (也就是層代 2 回收) 可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="e175c-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="e175c-104">這是一個問題，特別會發生在處理大量要求的伺服器上；在此情況下，完整記憶體回收可能會導致要求逾時。若要避免在關鍵期間發生完整回收，您可以在接近完整記憶體回收時收到通知，然後採取行動將工作負載重新導向至另一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e175c-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="e175c-105">您也可以自行引發回收，前提是目前的伺服器執行個體不需要處理要求。</span><span class="sxs-lookup"><span data-stu-id="e175c-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="e175c-106"><xref:System.GC.RegisterForFullGCNotification%2A> 方法會註冊一個當執行階段偵測到接近完整記憶體回收時要引發的通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="e175c-107">通知有兩個部分：當接近完整記憶體回收時，以及當完整記憶體回收完成時。</span><span class="sxs-lookup"><span data-stu-id="e175c-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e175c-108">只有進行封鎖的記憶體回收會引發通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="e175c-109">如果已啟用 [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 設定元素，背景記憶體回收將不會引發通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="e175c-110">若要判斷引發通知的時機，請使用 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="e175c-111">一般來說，您會在 `while` 迴圈中使用這些方法，以持續取得可顯示通知狀態的 <xref:System.GCNotificationStatus> 列舉。</span><span class="sxs-lookup"><span data-stu-id="e175c-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="e175c-112">如果值為 <xref:System.GCNotificationStatus.Succeeded>，您可以執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="e175c-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="e175c-113">為了回應使用 <xref:System.GC.WaitForFullGCApproach%2A> 方法取得的通知，您可以重新導向工作負載，並有可能自行引發回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="e175c-114">為了回應使用 <xref:System.GC.WaitForFullGCComplete%2A> 方法取得的通知，您可以讓目前的伺服器執行個體可用以重新處理要求。</span><span class="sxs-lookup"><span data-stu-id="e175c-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="e175c-115">您也可以收集資訊。</span><span class="sxs-lookup"><span data-stu-id="e175c-115">You can also gather information.</span></span> <span data-ttu-id="e175c-116">例如，您可以使用 <xref:System.GC.CollectionCount%2A> 方法來記錄回收的數目。</span><span class="sxs-lookup"><span data-stu-id="e175c-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="e175c-117"><xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法是設計來搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e175c-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="e175c-118">僅使用其中一個可能會產生不定的結果。</span><span class="sxs-lookup"><span data-stu-id="e175c-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="e175c-119">完整記憶體回收</span><span class="sxs-lookup"><span data-stu-id="e175c-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="e175c-120">當下列任何案例都成立時，執行階段會導致完整記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="e175c-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="e175c-121">足夠的記憶體已升階至層代 2，導致下一個層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="e175c-122">足夠的記憶體已升階至大型物件堆積，導致下一個層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="e175c-123">因為其他因素，層代 1 回收已擴大為層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="e175c-124">您在 <xref:System.GC.RegisterForFullGCNotification%2A> 方法中指定的閾值會套用到前兩個案例。</span><span class="sxs-lookup"><span data-stu-id="e175c-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="e175c-125">不過，在第一個案例中，您不一定會在指定的閾值成比例的時間收到通知，原因有兩個：</span><span class="sxs-lookup"><span data-stu-id="e175c-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="e175c-126">執行階段不會檢查每個小型物件配置 (基於效能考量)。</span><span class="sxs-lookup"><span data-stu-id="e175c-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="e175c-127">只有層代 1 回收會將記憶體升階為層代 2。</span><span class="sxs-lookup"><span data-stu-id="e175c-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="e175c-128">第三個案例也會造成您收到通知之時間的不確定性。</span><span class="sxs-lookup"><span data-stu-id="e175c-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="e175c-129">雖然這不是一種保證，但是透過在這段期間將要求重新導向或在更能容納的時候自行引發，確實已證明這是一種減輕不適當的完整記憶體回收之效果的有用方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="e175c-130">通知閾值參數</span><span class="sxs-lookup"><span data-stu-id="e175c-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="e175c-131"><xref:System.GC.RegisterForFullGCNotification%2A> 方法有兩個參數來指定層代 2 物件和大型物件堆積的閾值。</span><span class="sxs-lookup"><span data-stu-id="e175c-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="e175c-132">當符合那些值時，應該會引發記憶體回收通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="e175c-133">下列表格描述這些參數。</span><span class="sxs-lookup"><span data-stu-id="e175c-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="e175c-134">參數</span><span class="sxs-lookup"><span data-stu-id="e175c-134">Parameter</span></span>|<span data-ttu-id="e175c-135">描述</span><span class="sxs-lookup"><span data-stu-id="e175c-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="e175c-136">範圍從 1 到 99 的數字，指定何時應根據層代 2 中所升階的物件來引發通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="e175c-137">範圍從 1 到 99 的數字，指定何時應根據大型物件堆積中所配置的物件來引發通知。</span><span class="sxs-lookup"><span data-stu-id="e175c-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="e175c-138">如果您指定的值太高，則有很高的機率會收到通知，但是在執行階段引發回收之前，可能會有一段很長的等待期間。</span><span class="sxs-lookup"><span data-stu-id="e175c-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="e175c-139">如果您自行引發回收，則可能會回收比原本回收 (如果執行階段導致回收的話) 還要多的物件。</span><span class="sxs-lookup"><span data-stu-id="e175c-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="e175c-140">如果您指定的值太低，執行階段可能會在您有足夠的時間收到通知之前導致回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e175c-141">範例</span><span class="sxs-lookup"><span data-stu-id="e175c-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e175c-142">描述</span><span class="sxs-lookup"><span data-stu-id="e175c-142">Description</span></span>  
 <span data-ttu-id="e175c-143">在下列範例中，一組伺服器會處理傳入的 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="e175c-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="e175c-144">若要模擬處理要求的工作負載，請將位元組陣列加入至 <xref:System.Collections.Generic.List%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="e175c-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="e175c-145">每部伺服器都會註冊記憶體回收通知，然後在 `WaitForFullGCProc` 使用者方法上啟動執行緒以持續監視 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法所傳回的 <xref:System.GCNotificationStatus> 列舉。</span><span class="sxs-lookup"><span data-stu-id="e175c-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="e175c-146">當引發通知時，<xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法會呼叫各自的事件處理使用者方法：</span><span class="sxs-lookup"><span data-stu-id="e175c-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="e175c-147">這個方法會呼叫 `RedirectRequests` 使用者方法，此使用者方法會指示要求佇列伺服器暫停將要求傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="e175c-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="e175c-148">這會透過將類別層級變數 `bAllocate` 設定為 `false` 來進行模擬，如此便不會再配置任何物件。</span><span class="sxs-lookup"><span data-stu-id="e175c-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="e175c-149">接下來，會呼叫 `FinishExistingRequests` 使用者方法來完成處理擱置中伺服器要求。</span><span class="sxs-lookup"><span data-stu-id="e175c-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="e175c-150">這會透過清除 <xref:System.Collections.Generic.List%601> 集合來進行模擬。</span><span class="sxs-lookup"><span data-stu-id="e175c-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="e175c-151">最後，因為工作負載減輕，所以會引發記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="e175c-152">此方法會呼叫使用者方法 `AcceptRequests` 以繼續接受要求，因為伺服器不再容許完整記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e175c-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="e175c-153">此動作是透過將 `bAllocate` 變數設定為 `true` 來進行模擬，讓物件能夠繼續加入到 <xref:System.Collections.Generic.List%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="e175c-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="e175c-154">下列程式碼包含範例的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="e175c-155">下列程式碼包含 `WaitForFullGCProc` 使用者方法，其中包含用來檢查記憶體回收通知的連續 while 迴圈。</span><span class="sxs-lookup"><span data-stu-id="e175c-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="e175c-156">下列程式碼包含從下列方法呼叫的 `OnFullGCApproachNotify` 方法：</span><span class="sxs-lookup"><span data-stu-id="e175c-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="e175c-157">`WaitForFullGCProc` 方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="e175c-158">下列程式碼包含從下列方法呼叫的 `OnFullGCApproachComplete` 方法：</span><span class="sxs-lookup"><span data-stu-id="e175c-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="e175c-159">`WaitForFullGCProc` 方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="e175c-160">下列程式碼包含從 `OnFullGCApproachNotify` 和 `OnFullGCCompleteNotify` 方法呼叫的使用者方法。</span><span class="sxs-lookup"><span data-stu-id="e175c-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="e175c-161">使用者方法會將要求重新導向，然後在完整記憶體回收之後繼續要求。</span><span class="sxs-lookup"><span data-stu-id="e175c-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="e175c-162">完整的程式碼範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="e175c-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e175c-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="e175c-163">See Also</span></span>  
 [<span data-ttu-id="e175c-164">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="e175c-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
