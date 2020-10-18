---
title: 事件 '<eventname1>' 無法在介面 '<eventname2>' 上實作事件 '<interface>'，因為它們的委派類型 '<delegate1>' 和 '<delegate2>' 不相符
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d0b2b095ed355b420b28e87ed0b9d6a31f049ebf
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162020"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="b6c3a-102">BC31423：事件 ' \<eventname1> ' 無法 \<eventname2> 在介面 ' ' 上執行事件 ' ' \<interface> ，因為它們的委派類型 ' \<delegate1> ' 和 ' \<delegate2> ' 不相符</span><span class="sxs-lookup"><span data-stu-id="b6c3a-102">BC31423: Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>

<span data-ttu-id="b6c3a-103">Visual Basic 無法執行事件，因為事件的委派類型與介面中事件的委派類型不相符。</span><span class="sxs-lookup"><span data-stu-id="b6c3a-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="b6c3a-104">如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6c3a-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="b6c3a-105">只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。</span><span class="sxs-lookup"><span data-stu-id="b6c3a-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>

 <span data-ttu-id="b6c3a-106">**錯誤識別碼：** BC31423</span><span class="sxs-lookup"><span data-stu-id="b6c3a-106">**Error ID:** BC31423</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b6c3a-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b6c3a-107">To correct this error</span></span>

- <span data-ttu-id="b6c3a-108">請分別實作這些事件。</span><span class="sxs-lookup"><span data-stu-id="b6c3a-108">Implement the events separately.</span></span>

     <span data-ttu-id="b6c3a-109">– 或 –</span><span class="sxs-lookup"><span data-stu-id="b6c3a-109">—or—</span></span>

- <span data-ttu-id="b6c3a-110">使用語法定義介面中的事件 `As` ，並指定相同的委派類型。</span><span class="sxs-lookup"><span data-stu-id="b6c3a-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c3a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c3a-111">See also</span></span>

- [<span data-ttu-id="b6c3a-112">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6c3a-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="b6c3a-113">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6c3a-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="b6c3a-114">事件</span><span class="sxs-lookup"><span data-stu-id="b6c3a-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
