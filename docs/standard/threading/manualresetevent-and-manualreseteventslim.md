---
title: ManualResetEvent 和 ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85d0c5c291743c6daac549e15d479fcf332235c
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452819"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="64bfd-102">ManualResetEvent 和 ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="64bfd-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="64bfd-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別代表必須在收到訊號之後手動重設的本機等候控制代碼事件。</span><span class="sxs-lookup"><span data-stu-id="64bfd-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="64bfd-104">此類別代表其基底類別 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="64bfd-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64bfd-105">如需手動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。</span><span class="sxs-lookup"><span data-stu-id="64bfd-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="64bfd-106"><xref:System.Threading.ManualResetEvent> 物件會維持收到訊號的狀態，直到其 <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> 方法被呼叫為止。</span><span class="sxs-lookup"><span data-stu-id="64bfd-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="64bfd-107">任何數目的等候執行緒或在收到訊號之後等候事件的執行緒，皆可在物件的狀態為收到訊號時加以釋放。</span><span class="sxs-lookup"><span data-stu-id="64bfd-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="64bfd-108">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以在預期等候時間非常短暫時，以及事件不會跨越處理序界限時，使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別來提升效能。</span><span class="sxs-lookup"><span data-stu-id="64bfd-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="64bfd-109"><xref:System.Threading.ManualResetEventSlim> 在等候事件變成收到訊號時會短暫使用忙碌微調。</span><span class="sxs-lookup"><span data-stu-id="64bfd-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="64bfd-110">若等候時間很短，旋轉功能的成本會遠低於使用等候控制代碼來等候。</span><span class="sxs-lookup"><span data-stu-id="64bfd-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="64bfd-111">不過，如果事件未在一定時間內變成收到訊號，<xref:System.Threading.ManualResetEventSlim> 就會訴諸於一般的事件控制代碼等候。</span><span class="sxs-lookup"><span data-stu-id="64bfd-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64bfd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64bfd-112">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="64bfd-113">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="64bfd-113">AutoResetEvent</span></span>](autoresetevent.md)  
- [<span data-ttu-id="64bfd-114">SpinWait</span><span class="sxs-lookup"><span data-stu-id="64bfd-114">SpinWait</span></span>](spinwait.md)  
- [<span data-ttu-id="64bfd-115">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="64bfd-115">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)
- [<span data-ttu-id="64bfd-116">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="64bfd-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="64bfd-117">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="64bfd-117">Threading objects and features</span></span>](threading-objects-and-features.md)  
- [<span data-ttu-id="64bfd-118">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="64bfd-118">Threading</span></span>](index.md)  
