---
title: "計時器"
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a><span data-ttu-id="5f720-102">計時器</span><span class="sxs-lookup"><span data-stu-id="5f720-102">Timers</span></span>
<span data-ttu-id="5f720-103">計時器是輕量級物件，可讓您指定要在指定時間呼叫的委派。</span><span class="sxs-lookup"><span data-stu-id="5f720-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="5f720-104">執行緒集區中的執行緒執行等候作業。</span><span class="sxs-lookup"><span data-stu-id="5f720-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="5f720-105">使用<xref:System.Threading.Timer?displayProperty=nameWithType>類別相當簡單。</span><span class="sxs-lookup"><span data-stu-id="5f720-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="5f720-106">您建立**計時器**，並傳遞<xref:System.Threading.TimerCallback>委派至回呼方法，代表物件的狀態，會傳遞給回呼、 初始的引發時間，以及代表回撥的引動過程之間的期間的時間。</span><span class="sxs-lookup"><span data-stu-id="5f720-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="5f720-107">若要取消暫止計時器，請呼叫**Timer.Dispose**函式。</span><span class="sxs-lookup"><span data-stu-id="5f720-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f720-108">有兩個其他計時器類別。</span><span class="sxs-lookup"><span data-stu-id="5f720-108">There are two other timer classes.</span></span> <span data-ttu-id="5f720-109"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>類別是控制項的視覺化設計工具的運作方式，要用於使用者介面的內容; 它會引發使用者介面執行緒上的事件。</span><span class="sxs-lookup"><span data-stu-id="5f720-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="5f720-110"><xref:System.Timers.Timer?displayProperty=nameWithType>類別衍生自<xref:System.ComponentModel.Component>，所以使用它的視覺化設計工具; 它也會引發事件，但它在引發<xref:System.Threading.ThreadPool>執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f720-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="5f720-111"><xref:System.Threading.Timer?displayProperty=nameWithType>類別上會回呼<xref:System.Threading.ThreadPool>執行緒，而完全不使用的事件模型。</span><span class="sxs-lookup"><span data-stu-id="5f720-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="5f720-112">它也會提供狀態物件給回呼方法中，其他的計時器不相符。</span><span class="sxs-lookup"><span data-stu-id="5f720-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="5f720-113">它是極為輕量型。</span><span class="sxs-lookup"><span data-stu-id="5f720-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="5f720-114">下列程式碼範例會啟動計時器啟動後每秒 （1000年毫秒為單位） 和刻度每秒，直到您按下**Enter**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5f720-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="5f720-115">包含計時器參考的變數是類別層級欄位，以確保計時器時仍在執行不受記憶體回收限制。</span><span class="sxs-lookup"><span data-stu-id="5f720-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="5f720-116">如需有關積極記憶體回收的詳細資訊，請參閱<xref:System.GC.KeepAlive%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f720-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5f720-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f720-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="5f720-118">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="5f720-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
