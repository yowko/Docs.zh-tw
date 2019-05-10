---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913166"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="65459-102">衍生的類別無法引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="65459-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="65459-103">只能從其宣告的宣告空間，就可以引發事件。</span><span class="sxs-lookup"><span data-stu-id="65459-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="65459-104">因此，類別無法引發任何其他類別，即使其中從中衍生的事件。</span><span class="sxs-lookup"><span data-stu-id="65459-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="65459-105">**錯誤 ID:** BC30029</span><span class="sxs-lookup"><span data-stu-id="65459-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65459-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="65459-106">To correct this error</span></span>  
  
- <span data-ttu-id="65459-107">移動`Event`陳述式或`RaiseEvent`陳述式，使它們位於相同的類別。</span><span class="sxs-lookup"><span data-stu-id="65459-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65459-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65459-108">See also</span></span>

- [<span data-ttu-id="65459-109">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="65459-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="65459-110">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="65459-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
