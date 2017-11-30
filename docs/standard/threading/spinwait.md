---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a><span data-ttu-id="8eacb-102">SpinWait</span><span class="sxs-lookup"><span data-stu-id="8eacb-102">SpinWait</span></span>
<span data-ttu-id="8eacb-103"><xref:System.Threading.SpinWait?displayProperty=nameWithType>是輕量型同步處理類型，您可以使用低層級的案例中，以避免昂貴的內容切換和核心轉換所需的核心事件。</span><span class="sxs-lookup"><span data-stu-id="8eacb-103"><xref:System.Threading.SpinWait?displayProperty=nameWithType> is a lightweight synchronization type that you can use in low-level scenarios to avoid the expensive context switches and kernel transitions that are required for kernel events.</span></span> <span data-ttu-id="8eacb-104">多核心電腦上，當資源不會保留很長一段時間，可能很少數數十個或少數幾個數百個週期，微調以使用者模式，然後重試以取得此資源等候執行緒比較有效率。</span><span class="sxs-lookup"><span data-stu-id="8eacb-104">On multicore computers, when a resource is not expected to be held for long periods of time, it can be more efficient for a waiting thread to spin in user mode for a few dozen or a few hundred cycles, and then retry to acquire the resource.</span></span> <span data-ttu-id="8eacb-105">如果在旋轉之後有可用資源，就會儲存數個數千個循環。</span><span class="sxs-lookup"><span data-stu-id="8eacb-105">If the resource is available after spinning, then you have saved several thousand cycles.</span></span> <span data-ttu-id="8eacb-106">如果仍然無法使用的資源，您只有少數的循環花了，並且輸入核心為基礎的等候。</span><span class="sxs-lookup"><span data-stu-id="8eacb-106">If the resource is still not available, then you have spent only a few cycles and can still enter a kernel-based wait.</span></span> <span data-ttu-id="8eacb-107">這種旋轉然後等待組合有時稱為*兩階段等候作業*。</span><span class="sxs-lookup"><span data-stu-id="8eacb-107">This spinning-then-waiting combination is sometimes referred to as a *two-phase wait operation*.</span></span>  
  
 <span data-ttu-id="8eacb-108"><xref:System.Threading.SpinWait>設計為可搭配.NET Framework 型別，例如包裝核心事件<xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="8eacb-108"><xref:System.Threading.SpinWait> is designed to be used in conjunction with the .NET Framework types that wrap kernel events such as <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="8eacb-109"><xref:System.Threading.SpinWait>也可用本身在只有一個程式中執行基本微調功能。</span><span class="sxs-lookup"><span data-stu-id="8eacb-109"><xref:System.Threading.SpinWait> can also be used by itself for basic spinning functionality in just one program.</span></span>  
  
 <span data-ttu-id="8eacb-110"><xref:System.Threading.SpinWait>是不只是空的迴圈。</span><span class="sxs-lookup"><span data-stu-id="8eacb-110"><xref:System.Threading.SpinWait> is more than just an empty loop.</span></span> <span data-ttu-id="8eacb-111">小心地實作一般案例中，提供正確的旋轉行為，並且將本身起始內容切換如果旋轉表示足夠的時間 （大約核心轉換所需的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="8eacb-111">It is carefully implemented to provide correct spinning behavior for the general case, and will itself initiate context switches if it spins long enough (roughly the length of time required for a kernel transition).</span></span> <span data-ttu-id="8eacb-112">例如，在單一核心電腦<xref:System.Threading.SpinWait>之執行緒的時間配量，會產生立即因為微調區塊轉送所有執行緒上的進度。</span><span class="sxs-lookup"><span data-stu-id="8eacb-112">For example, on single-core computers, <xref:System.Threading.SpinWait> yields the time slice of the thread immediately because spinning blocks forward progress on all threads.</span></span> <span data-ttu-id="8eacb-113"><xref:System.Threading.SpinWait>若要防止封鎖較高優先權的執行緒或記憶體回收行程等候執行緒的多核心電腦上，甚至也會產生。</span><span class="sxs-lookup"><span data-stu-id="8eacb-113"><xref:System.Threading.SpinWait> also yields even on multi-core machines to prevent the waiting thread from blocking higher-priority threads or the garbage collector.</span></span> <span data-ttu-id="8eacb-114">因此，如果您使用<xref:System.Threading.SpinWait>在兩階段等候作業中，我們建議您叫用核心等候<xref:System.Threading.SpinWait>本身會起始內容切換。</span><span class="sxs-lookup"><span data-stu-id="8eacb-114">Therefore, if you are using a <xref:System.Threading.SpinWait> in a two-phase wait operation, we recommend that you invoke the kernel wait before the <xref:System.Threading.SpinWait> itself initiates a context switch.</span></span> <span data-ttu-id="8eacb-115"><xref:System.Threading.SpinWait>提供<xref:System.Threading.SpinWait.NextSpinWillYield%2A>屬性，您可以檢查之前的每個呼叫<xref:System.Threading.SpinWait.SpinOnce%2A>。</span><span class="sxs-lookup"><span data-stu-id="8eacb-115"><xref:System.Threading.SpinWait> provides the <xref:System.Threading.SpinWait.NextSpinWillYield%2A> property, which you can check before every call to <xref:System.Threading.SpinWait.SpinOnce%2A>.</span></span> <span data-ttu-id="8eacb-116">當屬性傳回`true`，起始您自己的等候作業。</span><span class="sxs-lookup"><span data-stu-id="8eacb-116">When the property returns `true`, initiate your own Wait operation.</span></span> <span data-ttu-id="8eacb-117">如需範例，請參閱[How to： 使用 SpinWait 實作兩階段等候作業](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="8eacb-117">For an example, see [How to: Use SpinWait to Implement a Two-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).</span></span>  
  
 <span data-ttu-id="8eacb-118">如果您不會執行兩階段等候作業，但正在只微調，直到某些條件為真，您可以啟用<xref:System.Threading.SpinWait>執行其內容會切換以便在 Windows 作業系統環境中的優良。</span><span class="sxs-lookup"><span data-stu-id="8eacb-118">If you are not performing a two-phase wait operation but are just spinning until some condition is true, you can enable <xref:System.Threading.SpinWait> to perform its context switches so that it is a good citizen in the Windows operating system environment.</span></span> <span data-ttu-id="8eacb-119">下列基本範例會示範<xref:System.Threading.SpinWait>無鎖定的堆疊中。</span><span class="sxs-lookup"><span data-stu-id="8eacb-119">The following basic example shows a <xref:System.Threading.SpinWait> in a lock-free stack.</span></span> <span data-ttu-id="8eacb-120">如果您需要高效能、 安全執行緒的堆疊，請考慮使用<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8eacb-120">If you require a high-performance, thread-safe stack, consider using <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a><span data-ttu-id="8eacb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eacb-121">See Also</span></span>  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [<span data-ttu-id="8eacb-122">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="8eacb-122">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
