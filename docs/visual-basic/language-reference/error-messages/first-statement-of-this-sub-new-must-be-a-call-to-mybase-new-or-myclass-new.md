---
title: 第一個陳述式，這個&#39;Sub New&#39;必須是呼叫&#39;MyBase.New&#39;或&#39;MyClass.New&#39; （沒有可存取建構函式不含參數）
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 75832ae88908094c1cb74ce04ad84c0d2ae91e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728891"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="1c48a-102">第一個陳述式，這個&#39;Sub New&#39;必須是呼叫&#39;MyBase.New&#39;或&#39;MyClass.New&#39; （沒有可存取建構函式不含參數）</span><span class="sxs-lookup"><span data-stu-id="1c48a-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="1c48a-103">此 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New'，因為基底類別\<basename >' 的'\<derivedname >' 沒有可存取 ' Sub New' 可以不使用引數呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c48a-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="1c48a-104">在衍生類別中，每個建構函式必須呼叫基底類別建構函式 (`MyBase.New`)。</span><span class="sxs-lookup"><span data-stu-id="1c48a-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="1c48a-105">如果基底類別的建構函式不含任何參數是在衍生類別，可存取`MyBase.New`可以自動呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c48a-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="1c48a-106">若非如此，必須使用參數，呼叫的基底類別建構函式，並無法自動完成。</span><span class="sxs-lookup"><span data-stu-id="1c48a-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="1c48a-107">在此情況下，每個衍生的類別建構函式的第一個陳述式必須呼叫的參數化建構函式的基底類別，或衍生類別，可讓呼叫的基底類別建構函式中呼叫其他建構函式。</span><span class="sxs-lookup"><span data-stu-id="1c48a-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="1c48a-108">**錯誤 ID:** BC30148</span><span class="sxs-lookup"><span data-stu-id="1c48a-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c48a-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1c48a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="1c48a-110">呼叫`MyBase.New`提供必要的參數，或呼叫這類呼叫的對等個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="1c48a-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="1c48a-111">例如，如果基底類別建構函式宣告為`Public Sub New(ByVal index as Integer)`中，第一個陳述式在衍生類別建構函式可能`MyBase.New(100)`。</span><span class="sxs-lookup"><span data-stu-id="1c48a-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c48a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c48a-112">See also</span></span>
- [<span data-ttu-id="1c48a-113">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="1c48a-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
