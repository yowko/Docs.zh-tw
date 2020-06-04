---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402768"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="fb55f-102">'\<typename>' 無法繼承自 \<type> '\<basetypename>'，因為它會在組件外展開基底 \<type> 的存取</span><span class="sxs-lookup"><span data-stu-id="fb55f-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="fb55f-103">類別或介面繼承自基類或介面，但具有較不嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="fb55f-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="fb55f-104">例如， `Public` 介面繼承自 `Friend` 介面，或 `Protected` 類別繼承自 `Private` 類別。</span><span class="sxs-lookup"><span data-stu-id="fb55f-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="fb55f-105">這會公開基類或介面，以存取超出預期的層級。</span><span class="sxs-lookup"><span data-stu-id="fb55f-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="fb55f-106">**錯誤識別碼：** BC30910</span><span class="sxs-lookup"><span data-stu-id="fb55f-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb55f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fb55f-107">To correct this error</span></span>  
  
- <span data-ttu-id="fb55f-108">將衍生類別或介面的存取層級變更為至少和基類或介面的限制。</span><span class="sxs-lookup"><span data-stu-id="fb55f-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="fb55f-109">-或-</span><span class="sxs-lookup"><span data-stu-id="fb55f-109">-or-</span></span>  
  
- <span data-ttu-id="fb55f-110">如果您需要較不嚴格的存取層級，請移除 `Inherits` 語句。</span><span class="sxs-lookup"><span data-stu-id="fb55f-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="fb55f-111">您無法從更受限制的基類或介面繼承。</span><span class="sxs-lookup"><span data-stu-id="fb55f-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb55f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb55f-112">See also</span></span>

- [<span data-ttu-id="fb55f-113">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="fb55f-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="fb55f-114">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="fb55f-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="fb55f-115">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="fb55f-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="fb55f-116">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="fb55f-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
