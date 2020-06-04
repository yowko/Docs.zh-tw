---
title: 事件 '<eventname1>' 無法在介面 '<eventname2>' 上實作事件 '<interface>'，因為它們的委派類型 '<delegate1>' 和 '<delegate2>' 不相符
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 32d6733580de8798a66c30d486b8439befd2af19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409604"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="92cab-102">事件 '\<eventname1>' 無法在介面 '\<eventname2>' 上實作事件 '\<interface>'，因為它們的委派類型 '\<delegate1>' 和 '\<delegate2>' 不相符</span><span class="sxs-lookup"><span data-stu-id="92cab-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="92cab-103">Visual Basic 無法執行事件，因為事件的委派類型與介面中事件的委派類型不相符。</span><span class="sxs-lookup"><span data-stu-id="92cab-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="92cab-104">如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="92cab-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="92cab-105">只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。</span><span class="sxs-lookup"><span data-stu-id="92cab-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="92cab-106">**錯誤識別碼：** BC31423</span><span class="sxs-lookup"><span data-stu-id="92cab-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="92cab-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="92cab-107">To correct this error</span></span>  
  
- <span data-ttu-id="92cab-108">請分別實作這些事件。</span><span class="sxs-lookup"><span data-stu-id="92cab-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="92cab-109">– 或 –</span><span class="sxs-lookup"><span data-stu-id="92cab-109">—or—</span></span>  
  
- <span data-ttu-id="92cab-110">使用語法在介面中定義事件 `As` ，並指定相同的委派類型。</span><span class="sxs-lookup"><span data-stu-id="92cab-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92cab-111">See also</span></span>

- [<span data-ttu-id="92cab-112">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="92cab-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="92cab-113">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="92cab-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="92cab-114">事件</span><span class="sxs-lookup"><span data-stu-id="92cab-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
