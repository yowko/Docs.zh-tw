---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="23fb7-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="23fb7-102">AutoResetEvent</span></span>
<span data-ttu-id="23fb7-103"><xref:System.Threading.AutoResetEvent>類別表示收到信號時，發行單一等候中執行緒後自動重設本機等候控制代碼事件。</span><span class="sxs-lookup"><span data-stu-id="23fb7-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="23fb7-104">此類別代表其基底類別的特殊案例<xref:System.Threading.EventWaitHandle>。</span><span class="sxs-lookup"><span data-stu-id="23fb7-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="23fb7-105">如需自動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。</span><span class="sxs-lookup"><span data-stu-id="23fb7-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="23fb7-106"><xref:System.Threading.AutoResetEvent>物件會自動重設為未收到訊號系統釋放單一等候中執行緒之後。</span><span class="sxs-lookup"><span data-stu-id="23fb7-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="23fb7-107">如果沒有執行緒在等候，事件物件的狀態會維持已收到信號。</span><span class="sxs-lookup"><span data-stu-id="23fb7-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="23fb7-108"><xref:System.Threading.AutoResetEvent>對應至 Win32`CreateEvent`呼叫時，指定`false`如`bManualReset`引數。</span><span class="sxs-lookup"><span data-stu-id="23fb7-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="23fb7-109">如需範例，會使用<xref:System.Threading.AutoResetEvent>，請參閱[監視器](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)。</span><span class="sxs-lookup"><span data-stu-id="23fb7-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23fb7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23fb7-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="23fb7-111">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="23fb7-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="23fb7-112">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="23fb7-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="23fb7-113">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="23fb7-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="23fb7-114">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="23fb7-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
