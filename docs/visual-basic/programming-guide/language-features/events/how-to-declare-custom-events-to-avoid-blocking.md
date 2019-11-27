---
title: 如何：宣告自訂事件以避免封鎖
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345140"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="aa9fe-102">如何：宣告自訂事件以避免封鎖 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa9fe-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="aa9fe-103">有幾種情況很重要：一個事件處理常式不會封鎖後續的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="aa9fe-104">自訂事件可讓事件以非同步方式呼叫其事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="aa9fe-105">根據預設，事件宣告的「備份存放區」欄位是一個多播委派，可將所有事件處理常式序列結合在一起。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="aa9fe-106">這表示如果某個處理常式需要很長的時間才能完成，它會封鎖其他處理常式，直到它完成為止。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="aa9fe-107">（行為良好的事件處理常式應該永遠不會執行冗長或可能封鎖的作業）。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="aa9fe-108">您可以使用自訂事件，以非同步方式執行事件處理常式，而不是使用 Visual Basic 提供之事件的預設執行。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa9fe-109">範例</span><span class="sxs-lookup"><span data-stu-id="aa9fe-109">Example</span></span>  
 <span data-ttu-id="aa9fe-110">在此範例中，`AddHandler` 存取子會將 `Click` 事件之每個處理常式的委派加入至儲存在 `EventHandlerList` 欄位中的 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="aa9fe-111">當程式碼引發 `Click` 事件時，`RaiseEvent` 存取子會使用 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> 方法，以非同步方式叫用所有的事件處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="aa9fe-112">該方法會叫用工作者執行緒上的每個處理常式，並立即傳回，因此處理程式無法彼此封鎖。</span><span class="sxs-lookup"><span data-stu-id="aa9fe-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="aa9fe-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa9fe-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="aa9fe-114">事件</span><span class="sxs-lookup"><span data-stu-id="aa9fe-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="aa9fe-115">如何：宣告自訂事件以節省記憶體</span><span class="sxs-lookup"><span data-stu-id="aa9fe-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
