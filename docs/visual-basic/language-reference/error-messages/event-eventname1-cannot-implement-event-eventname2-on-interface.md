---
title: 事件&#39; &lt;eventname1&gt; &#39;無法實作事件&#39;&lt;事件名稱 2>&gt; &#39;介面上&#39;&lt;介面&gt;&#39;因為它們的委派類型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不相符
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="97662-102">事件&#39; &lt;eventname1&gt; &#39;無法實作事件&#39;&lt;事件名稱 2>&gt; &#39;介面上&#39;&lt;介面&gt;&#39;因為它們的委派類型&#39; &lt;delegate1&gt; &#39;和&#39; &lt;delegate2&gt; &#39;不相符</span><span class="sxs-lookup"><span data-stu-id="97662-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="97662-103">Visual Basic 無法實作事件，因為事件的委派類型的介面中的事件委派類型不相符。</span><span class="sxs-lookup"><span data-stu-id="97662-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="97662-104">如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="97662-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="97662-105">只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。</span><span class="sxs-lookup"><span data-stu-id="97662-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="97662-106">**錯誤 ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="97662-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97662-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="97662-107">To correct this error</span></span>  
  
-   <span data-ttu-id="97662-108">請分別實作這些事件。</span><span class="sxs-lookup"><span data-stu-id="97662-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="97662-109">-或-</span><span class="sxs-lookup"><span data-stu-id="97662-109">—or—</span></span>  
  
-   <span data-ttu-id="97662-110">在介面中使用定義的事件`As`語法，並指定相同的委派類型。</span><span class="sxs-lookup"><span data-stu-id="97662-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97662-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97662-111">See Also</span></span>  
 [<span data-ttu-id="97662-112">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="97662-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="97662-113">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="97662-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="97662-114">事件</span><span class="sxs-lookup"><span data-stu-id="97662-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
