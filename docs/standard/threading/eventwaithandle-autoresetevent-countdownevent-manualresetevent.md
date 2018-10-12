---
title: EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9c858d7c76fdcc1b3e02485eb0b459f4e7555c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47205914"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="3bee8-102">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="3bee8-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>

<span data-ttu-id="3bee8-103">事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。</span><span class="sxs-lookup"><span data-stu-id="3bee8-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="3bee8-104">這些同步處理事件是以作業系統等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。</span><span class="sxs-lookup"><span data-stu-id="3bee8-104">These synchronization events are based on operating system wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
<span data-ttu-id="3bee8-105">在與 <xref:System.Threading.Monitor> 類別相同的許多同步處理案例中，事件等候控制代碼很有用。</span><span class="sxs-lookup"><span data-stu-id="3bee8-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="3bee8-106">事件等候控制代碼通常會比 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> 方法更容易使用，而且它們更能掌控訊號的傳送。</span><span class="sxs-lookup"><span data-stu-id="3bee8-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="3bee8-107">具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。</span><span class="sxs-lookup"><span data-stu-id="3bee8-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bee8-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="3bee8-108">In this section</span></span>

 [<span data-ttu-id="3bee8-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="3bee8-109">EventWaitHandle</span></span>](eventwaithandle.md)  
 <span data-ttu-id="3bee8-110"><xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 類別可代表自動或手動重設事件以及本機事件或具名系統事件。</span><span class="sxs-lookup"><span data-stu-id="3bee8-110">The <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="3bee8-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3bee8-111">AutoResetEvent</span></span>](autoresetevent.md)  
 <span data-ttu-id="3bee8-112"><xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表會自動重設的本機事件。</span><span class="sxs-lookup"><span data-stu-id="3bee8-112">The <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="3bee8-113">ManualResetEvent 和 ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="3bee8-113">ManualResetEvent and ManualResetEventSlim</span></span>](manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="3bee8-114"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表必須手動重設的本機事件。</span><span class="sxs-lookup"><span data-stu-id="3bee8-114">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="3bee8-115"><xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別是更快速的輕量型版本，可用於相同處理序中的事件。</span><span class="sxs-lookup"><span data-stu-id="3bee8-115">The <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="3bee8-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="3bee8-116">CountdownEvent</span></span>](countdownevent.md)  
 <span data-ttu-id="3bee8-117"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 類別提供一個簡化的方式，可在使用等候控制代碼的程式碼中實作分支/聯結平行處理原則模式。</span><span class="sxs-lookup"><span data-stu-id="3bee8-117">The <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3bee8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bee8-118">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [<span data-ttu-id="3bee8-119">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="3bee8-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="3bee8-120">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="3bee8-120">Managed threading basics</span></span>](managed-threading-basics.md)
