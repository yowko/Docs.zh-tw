---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409695"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="12df7-102">衍生的類別無法引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="12df7-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="12df7-103">事件只能從其宣告所在的宣告空間引發。</span><span class="sxs-lookup"><span data-stu-id="12df7-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="12df7-104">因此，類別無法從任何其他類別引發事件，甚至是衍生自它的來源。</span><span class="sxs-lookup"><span data-stu-id="12df7-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="12df7-105">**錯誤識別碼：** BC30029</span><span class="sxs-lookup"><span data-stu-id="12df7-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12df7-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="12df7-106">To correct this error</span></span>  
  
- <span data-ttu-id="12df7-107">移動 `Event` 語句或 `RaiseEvent` 語句，使其位於相同的類別中。</span><span class="sxs-lookup"><span data-stu-id="12df7-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12df7-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12df7-108">See also</span></span>

- [<span data-ttu-id="12df7-109">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="12df7-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="12df7-110">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="12df7-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
