---
title: "如何︰ 宣告自訂事件以避免封鎖 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 52181d1c307e4e312f4511719e540fd6d5bfcfa8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="b96b8-102">如何：宣告自訂事件以避免封鎖 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b96b8-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="b96b8-103">重要的一個事件處理常式不會封鎖後續的事件處理常式時，有幾種情況。</span><span class="sxs-lookup"><span data-stu-id="b96b8-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="b96b8-104">自訂事件可讓您以非同步方式呼叫其事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="b96b8-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="b96b8-105">根據預設，事件宣告備份存放區欄位會是連續結合所有事件處理常式的多點傳送的委派。</span><span class="sxs-lookup"><span data-stu-id="b96b8-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="b96b8-106">這表示，如果某個處理常式需要很長的時間才能完成，它會封鎖其他處理常式到完成為止。</span><span class="sxs-lookup"><span data-stu-id="b96b8-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="b96b8-107">（正常運作的事件處理常式應該永遠不會執行時間較長或潛在的封鎖作業）。</span><span class="sxs-lookup"><span data-stu-id="b96b8-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="b96b8-108">而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，以非同步方式執行的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b96b8-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b96b8-109">範例</span><span class="sxs-lookup"><span data-stu-id="b96b8-109">Example</span></span>  
 <span data-ttu-id="b96b8-110">在此範例中，`AddHandler`存取子會將每個處理常式的委派加入`Click`事件<xref:System.Collections.ArrayList>儲存在`EventHandlerList`欄位。</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="b96b8-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="b96b8-111">當程式碼會引發`Click`事件，`RaiseEvent`存取子會以非同步方式使用的所有事件處理常式委派叫都用<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>方法。</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="b96b8-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="b96b8-112">該方法會叫用背景工作執行緒上的每個處理常式，並會立即傳回，所以處理常式無法封鎖彼此。</span><span class="sxs-lookup"><span data-stu-id="b96b8-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 <span data-ttu-id="b96b8-113">[!code-vb[VbVbalrEvents #&27;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b96b8-113">[!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96b8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b96b8-114">See Also</span></span>  
 <span data-ttu-id="b96b8-115"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="b96b8-115"><xref:System.Collections.ArrayList></span></span>   
 <span data-ttu-id="b96b8-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="b96b8-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span></span>   
<span data-ttu-id="b96b8-117"> [事件](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="b96b8-117"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="b96b8-118"> [如何：宣告自訂事件以節省記憶體](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span><span class="sxs-lookup"><span data-stu-id="b96b8-118"> [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span></span>
