---
title: Interop 與其他非同步模式和類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05b53016712f75e45636979d77bfd27116ce8e14
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "43892820"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="a066c-102">Interop 與其他非同步模式和類型</span><span class="sxs-lookup"><span data-stu-id="a066c-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="a066c-103">.NET Framework 1.0 導入了 <xref:System.IAsyncResult> 模式，亦稱為 [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)或 `Begin/End` 模式。</span><span class="sxs-lookup"><span data-stu-id="a066c-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="a066c-104">.NET Framework 2.0 加入了 [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。</span><span class="sxs-lookup"><span data-stu-id="a066c-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="a066c-105">從 .NET Framework 4 開始， [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 取代了 APM 和 EAP，但是可讓您從較早的模式輕鬆建置移轉常式。</span><span class="sxs-lookup"><span data-stu-id="a066c-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="a066c-106">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="a066c-106">In this topic:</span></span>  
  
-   <span data-ttu-id="a066c-107">[工作與 APM](#APM) ([從 APM 到 TAP](#ApmToTap) 或 [從 TAP 到 APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="a066c-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="a066c-108">工作與 EAP</span><span class="sxs-lookup"><span data-stu-id="a066c-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="a066c-109">[工作與等候控制代碼](#WaitHandles) ([從等候控制代碼到 TAP](#WHToTap) 或 [從 TAP 到等候控制代碼](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="a066c-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="a066c-110">工作與非同步程式設計模型 (APM)</span><span class="sxs-lookup"><span data-stu-id="a066c-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="a066c-111">從 APM 到 TAP</span><span class="sxs-lookup"><span data-stu-id="a066c-111">From APM to TAP</span></span>  
 <span data-ttu-id="a066c-112">由於 [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) 模式結構嚴謹，因此很容易就能建置包裝函式將 APM 實作公開為 TAP 實作。</span><span class="sxs-lookup"><span data-stu-id="a066c-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="a066c-113">事實上，以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]為開頭的 .NET Framework，以 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法多載的形式來包含 Helper 常式，以提供這項轉譯。</span><span class="sxs-lookup"><span data-stu-id="a066c-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="a066c-114">請考慮 <xref:System.IO.Stream> 類別以及其 <xref:System.IO.Stream.BeginRead%2A> 與 <xref:System.IO.Stream.EndRead%2A> 方法，此類方法代表同步 <xref:System.IO.Stream.Read%2A> 方法的 APM 對應項目：</span><span class="sxs-lookup"><span data-stu-id="a066c-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="a066c-115">您可以使用 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法來實作這項作業的 TAP 包裝函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a066c-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="a066c-116">這個實作相似下面這個：</span><span class="sxs-lookup"><span data-stu-id="a066c-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="a066c-117">從 TAP 到 APM</span><span class="sxs-lookup"><span data-stu-id="a066c-117">From TAP to APM</span></span>  
 <span data-ttu-id="a066c-118">如果您現有的基礎結構預期 APM 模式，則您也需進行 TAP 實作，並在預期 APM 實作的位置加以使用。</span><span class="sxs-lookup"><span data-stu-id="a066c-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="a066c-119">由於可以組成工作，並且 <xref:System.Threading.Tasks.Task> 類別會實作 <xref:System.IAsyncResult>，因此您可以使用簡單的 Helper 函式來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="a066c-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="a066c-120">下列程式碼會使用 <xref:System.Threading.Tasks.Task%601> 類別的擴充功能，但是您可以針對非泛型工作使用幾乎完全相同的函式。</span><span class="sxs-lookup"><span data-stu-id="a066c-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="a066c-121">現在，考量一下有下列 TAP 實作的案例：</span><span class="sxs-lookup"><span data-stu-id="a066c-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="a066c-122">而且您想要提供此 APM 實作：</span><span class="sxs-lookup"><span data-stu-id="a066c-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="a066c-123">下列範例將示範如何移轉至 APM：</span><span class="sxs-lookup"><span data-stu-id="a066c-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="a066c-124">工作與事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="a066c-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="a066c-125">包裝 [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) 實作會比包裝 APM 模式更為複雜，原因是 EAP 模式擁有較多的變化，結構也不如 APM 模式嚴謹。</span><span class="sxs-lookup"><span data-stu-id="a066c-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="a066c-126">供示範所用，下列程式碼包裝了 `DownloadStringAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="a066c-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="a066c-127">`DownloadStringAsync` 會接受 URI、在下載時引發 `DownloadProgressChanged` 事件，以報告多個進行中的統計資料，然後在完成時引發 `DownloadStringCompleted` 。</span><span class="sxs-lookup"><span data-stu-id="a066c-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="a066c-128">最終結果是字串，其中包含指定之 URI 頁面的內容。</span><span class="sxs-lookup"><span data-stu-id="a066c-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="a066c-129">工作與等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="a066c-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="a066c-130">從等候控制代碼到 TAP</span><span class="sxs-lookup"><span data-stu-id="a066c-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="a066c-131">雖然等候控制代碼不會實作非同步模式，但進階開發人員可能會在等候控制代碼設定完成後，使用 <xref:System.Threading.WaitHandle> 類別與 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法，用於非同步通知。</span><span class="sxs-lookup"><span data-stu-id="a066c-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="a066c-132">您可以包裝 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 方法，以啟用等候控制代碼上任何同步等候的工作式替代方案：</span><span class="sxs-lookup"><span data-stu-id="a066c-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="a066c-133">有了此方法，您可以使用非同步方法中現有的 <xref:System.Threading.WaitHandle> 實作。</span><span class="sxs-lookup"><span data-stu-id="a066c-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="a066c-134">例如，如果您想要節流處理任何特定時間執行的非同步作業數目，可以利用旗號 (<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> 物件)。</span><span class="sxs-lookup"><span data-stu-id="a066c-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="a066c-135">您可以節流處理至 *N* ，即同時執行的作業數，方法是透過將旗號的計數初始化至 *N*，在任何想執行作業時等待旗號，並在完成作業時釋放旗號：</span><span class="sxs-lookup"><span data-stu-id="a066c-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="a066c-136">您也可以建置非同步的旗號，而該旗號不會依賴等候控制代碼，並會完全與工作一同合作。</span><span class="sxs-lookup"><span data-stu-id="a066c-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="a066c-137">若要這樣做，您可以使用像是 [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) 中所討論的技術，用以在 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="a066c-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="a066c-138">從 TAP 到等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="a066c-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="a066c-139">如先前所述， <xref:System.Threading.Tasks.Task> 類別會實作 <xref:System.IAsyncResult>，且該實作會公開 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> 屬性，而該屬性會傳回 <xref:System.Threading.Tasks.Task> 完成時將進行設定的等候控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a066c-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="a066c-140">您可以取得 <xref:System.Threading.WaitHandle> 的 <xref:System.Threading.Tasks.Task> ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a066c-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="a066c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a066c-141">See also</span></span>

- [<span data-ttu-id="a066c-142">工作式非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="a066c-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
- [<span data-ttu-id="a066c-143">實作以工作為基礎的非同步模式</span><span class="sxs-lookup"><span data-stu-id="a066c-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
- [<span data-ttu-id="a066c-144">使用以工作為基礎的非同步模式</span><span class="sxs-lookup"><span data-stu-id="a066c-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
