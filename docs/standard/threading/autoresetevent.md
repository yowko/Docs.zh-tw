---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="autoresetevent"></a><span data-ttu-id="b6593-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="b6593-102">AutoResetEvent</span></span>
<span data-ttu-id="b6593-103"><xref:System.Threading.AutoResetEvent> 類別代表在釋出單一等候執行緒後，收到信號時會自動重設的本機等候控制代碼事件。</span><span class="sxs-lookup"><span data-stu-id="b6593-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="b6593-104">此類別代表其基底類別 <xref:System.Threading.EventWaitHandle> 的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="b6593-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="b6593-105">如需自動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。</span><span class="sxs-lookup"><span data-stu-id="b6593-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="b6593-106">在單一等候執行緒釋出之後，系統自動會將 <xref:System.Threading.AutoResetEvent> 物件重設為未收到信號。</span><span class="sxs-lookup"><span data-stu-id="b6593-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="b6593-107">如果沒有執行緒在等候，事件物件的狀態會維持已收到信號。</span><span class="sxs-lookup"><span data-stu-id="b6593-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="b6593-108"><xref:System.Threading.AutoResetEvent> 對應至 Win32 `CreateEvent` 呼叫，針對 `bManualReset` 引數指定 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6593-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="b6593-109">如需使用 <xref:System.Threading.AutoResetEvent> 的範例，請參閱 [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)。</span><span class="sxs-lookup"><span data-stu-id="b6593-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6593-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6593-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="b6593-111">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="b6593-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="b6593-112">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="b6593-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="b6593-113">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="b6593-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="b6593-114">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="b6593-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
