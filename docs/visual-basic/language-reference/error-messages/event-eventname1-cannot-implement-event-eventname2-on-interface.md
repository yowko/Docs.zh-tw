---
title: 事件&#39; &lt;eventname1&gt; &#39;無法實作事件&#39;&lt;事件名稱 2>&gt; &#39;介面上&#39;&lt;介面&gt;&#39;因為它們的委派類型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不相符
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 5c62b2f3e94de1c2a8919ec30b1ef106186bee11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589152"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="00dab-102">事件&#39; &lt;eventname1&gt; &#39;無法實作事件&#39;&lt;事件名稱 2>&gt; &#39;介面上&#39;&lt;介面&gt;&#39;因為它們的委派類型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不相符</span><span class="sxs-lookup"><span data-stu-id="00dab-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="00dab-103">Visual Basic 無法實作事件，因為事件的委派類型的介面中的事件委派類型不相符。</span><span class="sxs-lookup"><span data-stu-id="00dab-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="00dab-104">如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="00dab-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="00dab-105">只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。</span><span class="sxs-lookup"><span data-stu-id="00dab-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="00dab-106">**錯誤 ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="00dab-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00dab-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="00dab-107">To correct this error</span></span>  
  
-   <span data-ttu-id="00dab-108">請分別實作這些事件。</span><span class="sxs-lookup"><span data-stu-id="00dab-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="00dab-109">-或-</span><span class="sxs-lookup"><span data-stu-id="00dab-109">—or—</span></span>  
  
-   <span data-ttu-id="00dab-110">在介面中使用定義的事件`As`語法，並指定相同的委派類型。</span><span class="sxs-lookup"><span data-stu-id="00dab-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00dab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00dab-111">See Also</span></span>  
 [<span data-ttu-id="00dab-112">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="00dab-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="00dab-113">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="00dab-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="00dab-114">事件</span><span class="sxs-lookup"><span data-stu-id="00dab-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
