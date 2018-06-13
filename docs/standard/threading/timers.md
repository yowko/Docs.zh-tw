---
title: 計時器
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584953"
---
# <a name="timers"></a><span data-ttu-id="83730-102">計時器</span><span class="sxs-lookup"><span data-stu-id="83730-102">Timers</span></span>
<span data-ttu-id="83730-103">計時器是輕量型物件，可讓您指定要在指定時間呼叫的委派。</span><span class="sxs-lookup"><span data-stu-id="83730-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="83730-104">執行緒集區中的執行緒會執行等候作業。</span><span class="sxs-lookup"><span data-stu-id="83730-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="83730-105">使用 <xref:System.Threading.Timer?displayProperty=nameWithType> 類別的方式相當直接明瞭。</span><span class="sxs-lookup"><span data-stu-id="83730-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="83730-106">您建立**計時器**，將 <xref:System.Threading.TimerCallback> 委派傳遞至回呼方法、代表將傳遞至回呼之狀態的物件、最初引發時間，以及代表介於回呼引動過程間之期間的時間。</span><span class="sxs-lookup"><span data-stu-id="83730-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="83730-107">若要取消擱置中的計時器，請呼叫 **Timer.Dispose** 函式。</span><span class="sxs-lookup"><span data-stu-id="83730-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83730-108">另外還有兩個計時器類別。</span><span class="sxs-lookup"><span data-stu-id="83730-108">There are two other timer classes.</span></span> <span data-ttu-id="83730-109"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType> 類別是搭配視覺化設計工具運作且要用於使用者介面內容的控制項；它會在使用者介面執行緒上引發事件。</span><span class="sxs-lookup"><span data-stu-id="83730-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="83730-110"><xref:System.Timers.Timer?displayProperty=nameWithType> 類別衍生自<xref:System.ComponentModel.Component>，因此可將它與視覺化設計工具搭配使用；它也會引發事件，但會在 <xref:System.Threading.ThreadPool> 執行緒上引發它們。</span><span class="sxs-lookup"><span data-stu-id="83730-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="83730-111"><xref:System.Threading.Timer?displayProperty=nameWithType> 類別會在 <xref:System.Threading.ThreadPool> 執行緒上進行回呼，完全不會使用事件模型。</span><span class="sxs-lookup"><span data-stu-id="83730-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="83730-112">它也會將狀態物件提供給回呼方法，其他計時器則不會。</span><span class="sxs-lookup"><span data-stu-id="83730-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="83730-113">它極為精簡。</span><span class="sxs-lookup"><span data-stu-id="83730-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="83730-114">下列程式碼範例會在一秒 (1000 毫秒) 後啟動計時器且每秒都有滴答聲，直到您按下 **Enter** 鍵為止。</span><span class="sxs-lookup"><span data-stu-id="83730-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="83730-115">包含計時器參考的變數是類別層級的欄位，確保計時器仍在執行時不會受到記憶體回收限制。</span><span class="sxs-lookup"><span data-stu-id="83730-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="83730-116">如需積極型記憶體回收的詳細資訊，請參閱 <xref:System.GC.KeepAlive%2A>。</span><span class="sxs-lookup"><span data-stu-id="83730-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="83730-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="83730-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="83730-118">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="83730-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
