---
title: "事件 &quot;&lt;eventname1&gt;&quot;無法實作事件&quot;&lt;eventname2&gt;&quot;在介面&quot;&lt;介面&gt;&quot; 因為其委派型別&lt;delegate1&gt;&quot;和&quot;&lt;delegate2&gt;&quot; 不符 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
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
ms.openlocfilehash: 340547d3673b651e988a6c1167bf7043360b04e4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="04c8f-102">事件 '&lt;eventname1&gt;'無法實作事件'&lt;eventname2&gt;'在介面'&lt;介面&gt;' 因為其委派型別&lt;delegate1&gt;'和'&lt;delegate2&gt;' 不相符</span><span class="sxs-lookup"><span data-stu-id="04c8f-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="04c8f-103">無法實作事件，因為事件之委派型別和介面中的事件之委派型別不相符。</span><span class="sxs-lookup"><span data-stu-id="04c8f-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="04c8f-104">如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="04c8f-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="04c8f-105">只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。</span><span class="sxs-lookup"><span data-stu-id="04c8f-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="04c8f-106">**錯誤識別碼︰** BC31423</span><span class="sxs-lookup"><span data-stu-id="04c8f-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04c8f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="04c8f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="04c8f-108">請分別實作這些事件。</span><span class="sxs-lookup"><span data-stu-id="04c8f-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="04c8f-109">-或-</span><span class="sxs-lookup"><span data-stu-id="04c8f-109">—or—</span></span>  
  
-   <span data-ttu-id="04c8f-110">使用的介面中定義之事件`As`語法，並指定相同的委派型別。</span><span class="sxs-lookup"><span data-stu-id="04c8f-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c8f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04c8f-111">See Also</span></span>  
 <span data-ttu-id="04c8f-112">[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="04c8f-112">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="04c8f-113"> [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="04c8f-113"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="04c8f-114"> [事件](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="04c8f-114"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
