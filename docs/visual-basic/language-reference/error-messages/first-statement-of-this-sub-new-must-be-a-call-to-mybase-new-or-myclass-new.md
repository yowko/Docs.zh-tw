---
title: 這個 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New' (沒有不含參數的可存取建構函式)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402975"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="78997-102">這個 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New' (沒有不含參數的可存取建構函式)</span><span class="sxs-lookup"><span data-stu-id="78997-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="78997-103">這個 ' Sub New ' 的第一個語句必須呼叫 ' MyBase. New ' 或 ' MyClass. New ' \<basename> ，因為 ' ' 的基類 ' ' 沒有 \<derivedname> 可以使用任何引數呼叫的可存取 ' Sub New '。</span><span class="sxs-lookup"><span data-stu-id="78997-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="78997-104">在衍生類別中，每個函式都必須呼叫基類的「函數」（ `MyBase.New` ）。</span><span class="sxs-lookup"><span data-stu-id="78997-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="78997-105">如果基類具有不具有衍生類別可存取之參數的函式，則 `MyBase.New` 可以自動呼叫。</span><span class="sxs-lookup"><span data-stu-id="78997-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="78997-106">如果不是，則必須使用參數來呼叫基類的函式，而這無法自動完成。</span><span class="sxs-lookup"><span data-stu-id="78997-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="78997-107">在此情況下，每個衍生類別的函式的第一個語句必須在基類上呼叫參數化的函式，或呼叫衍生類別中的另一個函式，以進行基類的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="78997-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="78997-108">**錯誤識別碼：** BC30148</span><span class="sxs-lookup"><span data-stu-id="78997-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78997-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="78997-109">To correct this error</span></span>  
  
- <span data-ttu-id="78997-110">請呼叫 `MyBase.New` 提供必要的參數，或呼叫進行這類呼叫的對等函數。</span><span class="sxs-lookup"><span data-stu-id="78997-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="78997-111">例如，如果基類具有宣告為的函式，則衍生類別的函式 `Public Sub New(ByVal index as Integer)` 中的第一個語句可能是 `MyBase.New(100)` 。</span><span class="sxs-lookup"><span data-stu-id="78997-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78997-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78997-112">See also</span></span>

- [<span data-ttu-id="78997-113">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="78997-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
