---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="f1f0d-102">衍生的類別無法引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="f1f0d-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="f1f0d-103">只能從宣告它的宣告空間，可以引發事件。</span><span class="sxs-lookup"><span data-stu-id="f1f0d-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="f1f0d-104">因此，類別無法引發任何其他類別，即使其中從中衍生的事件。</span><span class="sxs-lookup"><span data-stu-id="f1f0d-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="f1f0d-105">**錯誤 ID:** BC30029</span><span class="sxs-lookup"><span data-stu-id="f1f0d-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1f0d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f1f0d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="f1f0d-107">移動`Event`陳述式或`RaiseEvent`陳述式，使它們位於相同的類別。</span><span class="sxs-lookup"><span data-stu-id="f1f0d-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f0d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f0d-108">See Also</span></span>  
 [<span data-ttu-id="f1f0d-109">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f0d-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="f1f0d-110">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f0d-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
