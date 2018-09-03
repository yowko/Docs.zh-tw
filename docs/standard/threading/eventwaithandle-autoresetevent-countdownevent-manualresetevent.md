---
title: EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f818ecf52ae1179d6d32d0b76cea3cc2a8f36ea8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43416408"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="41ddc-102">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="41ddc-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="41ddc-103">事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。</span><span class="sxs-lookup"><span data-stu-id="41ddc-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="41ddc-104">這些同步處理事件是以 Win32 等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。</span><span class="sxs-lookup"><span data-stu-id="41ddc-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="41ddc-105">在與 <xref:System.Threading.Monitor> 類別相同的許多同步處理案例中，事件等候控制代碼很有用。</span><span class="sxs-lookup"><span data-stu-id="41ddc-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="41ddc-106">事件等候控制代碼通常會比 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> 方法更容易使用，而且它們更能掌控訊號的傳送。</span><span class="sxs-lookup"><span data-stu-id="41ddc-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="41ddc-107">具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。</span><span class="sxs-lookup"><span data-stu-id="41ddc-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41ddc-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="41ddc-108">In This Section</span></span>  
 [<span data-ttu-id="41ddc-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="41ddc-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="41ddc-110"><xref:System.Threading.EventWaitHandle> 類別可代表自動或手動重設事件以及本機事件或具名系統事件。</span><span class="sxs-lookup"><span data-stu-id="41ddc-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="41ddc-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="41ddc-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="41ddc-112"><xref:System.Threading.AutoResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表會自動重設的本機事件。</span><span class="sxs-lookup"><span data-stu-id="41ddc-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="41ddc-113">ManualResetEvent 和 ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="41ddc-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="41ddc-114"><xref:System.Threading.ManualResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表必須手動重設的本機事件。</span><span class="sxs-lookup"><span data-stu-id="41ddc-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="41ddc-115"><xref:System.Threading.ManualResetEventSlim> 類別是更快速的輕量型版本，可用於相同處理序中的事件。</span><span class="sxs-lookup"><span data-stu-id="41ddc-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="41ddc-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="41ddc-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="41ddc-117"><xref:System.Threading.CountdownEvent> 類別提供一個簡化的方式，可在使用等候控制代碼的程式碼中實作分支/聯結平行處理原則模式。</span><span class="sxs-lookup"><span data-stu-id="41ddc-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41ddc-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="41ddc-118">Related Sections</span></span>  
 [<span data-ttu-id="41ddc-119">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="41ddc-119">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="41ddc-120"><xref:System.Threading.WaitHandle> 類別是 <xref:System.Threading.EventWaitHandle>、<xref:System.Threading.Semaphore> 及 <xref:System.Threading.Mutex> 類別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="41ddc-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="41ddc-121">其中包含 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 和 <xref:System.Threading.WaitHandle.WaitAll%2A> 之類的靜態方法，在搭配所有類型的等候控制代碼運作時很實用。</span><span class="sxs-lookup"><span data-stu-id="41ddc-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ddc-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="41ddc-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="41ddc-123">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="41ddc-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="41ddc-124">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="41ddc-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
