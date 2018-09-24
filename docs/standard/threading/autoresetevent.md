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
ms.openlocfilehash: 38efbe0ecd88c02752d610de4b1eec8b62eca1f8
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540813"
---
# <a name="autoresetevent"></a><span data-ttu-id="a5c36-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a5c36-102">AutoResetEvent</span></span>
<span data-ttu-id="a5c36-103"><xref:System.Threading.AutoResetEvent> 類別代表在釋出單一等候執行緒後，收到信號時會自動重設的本機等候控制代碼事件。</span><span class="sxs-lookup"><span data-stu-id="a5c36-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="a5c36-104">此類別代表其基底類別 <xref:System.Threading.EventWaitHandle> 的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="a5c36-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="a5c36-105">如需自動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。</span><span class="sxs-lookup"><span data-stu-id="a5c36-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="a5c36-106">在單一等候執行緒釋出之後，系統自動會將 <xref:System.Threading.AutoResetEvent> 物件重設為未收到信號。</span><span class="sxs-lookup"><span data-stu-id="a5c36-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="a5c36-107">如果沒有執行緒在等候，事件物件的狀態會維持已收到信號。</span><span class="sxs-lookup"><span data-stu-id="a5c36-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="a5c36-108">如需使用 <xref:System.Threading.AutoResetEvent> 的範例，請參閱 <xref:System.Threading.Monitor>。</span><span class="sxs-lookup"><span data-stu-id="a5c36-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c36-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c36-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [<span data-ttu-id="a5c36-110">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a5c36-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="a5c36-111">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="a5c36-111">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="a5c36-112">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="a5c36-112">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="a5c36-113">等候控制代碼</span><span class="sxs-lookup"><span data-stu-id="a5c36-113">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
