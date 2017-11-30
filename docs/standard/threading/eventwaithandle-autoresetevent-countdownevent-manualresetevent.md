---
title: "EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="f64e2-102">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="f64e2-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="f64e2-103">事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。</span><span class="sxs-lookup"><span data-stu-id="f64e2-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="f64e2-104">這些同步處理事件是以 Win32 等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。</span><span class="sxs-lookup"><span data-stu-id="f64e2-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="f64e2-105">事件等候控制代碼可用於許多相同的同步處理案例，做為<xref:System.Threading.Monitor>類別。</span><span class="sxs-lookup"><span data-stu-id="f64e2-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="f64e2-106">事件等候控制代碼通常會比容易使用<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>和<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>方法，而且它們提供更充分掌控發出訊號。</span><span class="sxs-lookup"><span data-stu-id="f64e2-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="f64e2-107">具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。</span><span class="sxs-lookup"><span data-stu-id="f64e2-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f64e2-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f64e2-108">In This Section</span></span>  
 [<span data-ttu-id="f64e2-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="f64e2-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="f64e2-110"><xref:System.Threading.EventWaitHandle>類別可代表可能是自動或手動重設事件，以及其中一個本機事件，或具名系統事件。</span><span class="sxs-lookup"><span data-stu-id="f64e2-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="f64e2-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="f64e2-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="f64e2-112"><xref:System.Threading.AutoResetEvent>類別衍生自<xref:System.Threading.EventWaitHandle>和表示本機事件，會自動重設。</span><span class="sxs-lookup"><span data-stu-id="f64e2-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="f64e2-113">ManualResetEvent 和 ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="f64e2-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="f64e2-114"><xref:System.Threading.ManualResetEvent>類別衍生自<xref:System.Threading.EventWaitHandle>代表必須以手動方式重設本機事件。</span><span class="sxs-lookup"><span data-stu-id="f64e2-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="f64e2-115"><xref:System.Threading.ManualResetEventSlim>類別是輕量型、 更快速的版本可以用於在相同的程序中的事件。</span><span class="sxs-lookup"><span data-stu-id="f64e2-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="f64e2-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="f64e2-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="f64e2-117"><xref:System.Threading.CountdownEvent>類別會提供一個簡化的方式來使用等候控制代碼的程式碼中實作分岔/聯結的平行處理原則的模式。</span><span class="sxs-lookup"><span data-stu-id="f64e2-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f64e2-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="f64e2-118">Related Sections</span></span>  
 [<span data-ttu-id="f64e2-119">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="f64e2-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="f64e2-120"><xref:System.Threading.WaitHandle>類別是基底類別<xref:System.Threading.EventWaitHandle>， <xref:System.Threading.Semaphore>，和<xref:System.Threading.Mutex>類別。</span><span class="sxs-lookup"><span data-stu-id="f64e2-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="f64e2-121">其中包含靜態方法，例如<xref:System.Threading.WaitHandle.SignalAndWait%2A>和<xref:System.Threading.WaitHandle.WaitAll%2A>使用所有類型的等候控制代碼時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="f64e2-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64e2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f64e2-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="f64e2-123">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="f64e2-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="f64e2-124">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="f64e2-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
