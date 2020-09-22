---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874485"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="54413-102">衍生的類別無法引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="54413-102">Derived classes cannot raise base class events</span></span>

<span data-ttu-id="54413-103">事件只能從宣告的宣告空間引發。</span><span class="sxs-lookup"><span data-stu-id="54413-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="54413-104">因此，類別無法從任何其他類別（甚至是衍生的類別）引發事件。</span><span class="sxs-lookup"><span data-stu-id="54413-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="54413-105">**錯誤識別碼：** BC30029</span><span class="sxs-lookup"><span data-stu-id="54413-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54413-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="54413-106">To correct this error</span></span>  
  
- <span data-ttu-id="54413-107">移動 `Event` 語句或 `RaiseEvent` 語句，使其位於相同的類別中。</span><span class="sxs-lookup"><span data-stu-id="54413-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54413-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54413-108">See also</span></span>

- [<span data-ttu-id="54413-109">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="54413-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="54413-110">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="54413-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
