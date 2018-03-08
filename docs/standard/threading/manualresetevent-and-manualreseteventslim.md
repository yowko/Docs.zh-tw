---
title: "ManualResetEvent 和 ManualResetEventSlim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b90a84cf87c6c64d48d89840e2213d83b2e39d44
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="1012c-102">ManualResetEvent 和 ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="1012c-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="1012c-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別代表必須在收到訊號之後手動重設的本機等候控制代碼事件。</span><span class="sxs-lookup"><span data-stu-id="1012c-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="1012c-104">此類別代表其基底類別 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="1012c-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1012c-105">如需手動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。</span><span class="sxs-lookup"><span data-stu-id="1012c-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="1012c-106"><xref:System.Threading.ManualResetEvent> 物件會維持收到訊號的狀態，直到其 <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> 方法被呼叫為止。</span><span class="sxs-lookup"><span data-stu-id="1012c-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="1012c-107">任何數目的等候執行緒或在收到訊號之後等候事件的執行緒，皆可在物件的狀態為收到訊號時加以釋放。</span><span class="sxs-lookup"><span data-stu-id="1012c-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="1012c-108"><xref:System.Threading.ManualResetEvent> 對應至 Win32 `CreateEvent` 呼叫，針對 `bManualReset` 引數指定 `true`。</span><span class="sxs-lookup"><span data-stu-id="1012c-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="1012c-109">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以在預期等候時間非常短暫時，以及事件不會跨越處理序界限時，使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別來提升效能。</span><span class="sxs-lookup"><span data-stu-id="1012c-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="1012c-110"><xref:System.Threading.ManualResetEventSlim> 在等候事件變成收到訊號時會短暫使用忙碌微調。</span><span class="sxs-lookup"><span data-stu-id="1012c-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="1012c-111">若等候時間很短，旋轉功能的成本會遠低於使用等候控制代碼來等候。</span><span class="sxs-lookup"><span data-stu-id="1012c-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="1012c-112">不過，如果事件未在一定時間內變成收到訊號，<xref:System.Threading.ManualResetEventSlim> 就會訴諸於一般的事件控制代碼等候。</span><span class="sxs-lookup"><span data-stu-id="1012c-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1012c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="1012c-113">See Also</span></span>  
 [<span data-ttu-id="1012c-114">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="1012c-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="1012c-115">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="1012c-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="1012c-116">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="1012c-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="1012c-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="1012c-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="1012c-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1012c-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="1012c-119">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="1012c-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
