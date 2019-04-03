---
title: HOW TO：宣告自訂事件以避免封鎖 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 6eea47ea2c8aee697eb34ca904dad22ca88e6ce4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821253"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="adfad-102">HOW TO：宣告自訂事件以避免封鎖 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adfad-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="adfad-103">有幾種情況時很重要的一個事件處理常式不會封鎖後續的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="adfad-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="adfad-104">自訂事件可讓要以非同步方式呼叫其事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="adfad-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="adfad-105">根據預設，事件宣告備份存放區欄位會是以序列方式結合了所有事件處理常式的多點傳送的委派。</span><span class="sxs-lookup"><span data-stu-id="adfad-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="adfad-106">這表示，如果有一個處理常式會花很長的時間才能完成，它會封鎖其他處理常式到完成為止。</span><span class="sxs-lookup"><span data-stu-id="adfad-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="adfad-107">（正常運作的事件處理常式應該永遠不會執行長時間或潛在的封鎖作業）。</span><span class="sxs-lookup"><span data-stu-id="adfad-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="adfad-108">而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，以非同步方式執行的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="adfad-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adfad-109">範例</span><span class="sxs-lookup"><span data-stu-id="adfad-109">Example</span></span>  
 <span data-ttu-id="adfad-110">在此範例中，`AddHandler`存取子新增的每個處理常式的委派`Click`事件，以<xref:System.Collections.ArrayList>儲存在`EventHandlerList`欄位。</span><span class="sxs-lookup"><span data-stu-id="adfad-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="adfad-111">當程式碼會引發`Click`事件，`RaiseEvent`存取子會以非同步方式使用的所有事件處理常式委派叫都用<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="adfad-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="adfad-112">該方法會叫用背景工作執行緒上的每個處理常式，並會立即傳回，讓處理常式無法封鎖彼此。</span><span class="sxs-lookup"><span data-stu-id="adfad-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="adfad-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adfad-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="adfad-114">事件</span><span class="sxs-lookup"><span data-stu-id="adfad-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="adfad-115">如何：宣告自訂事件以節省記憶體</span><span class="sxs-lookup"><span data-stu-id="adfad-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
