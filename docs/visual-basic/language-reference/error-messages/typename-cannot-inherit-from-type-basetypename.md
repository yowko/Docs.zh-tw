---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838946"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="7abbb-102">'\<類型名稱 >' 無法繼承自\<類型 >'\<基 >' 因為它會展開基底存取\<類型 > 外部組件</span><span class="sxs-lookup"><span data-stu-id="7abbb-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="7abbb-103">類別或介面繼承自基底類別或介面，但具有較不嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="7abbb-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="7abbb-104">例如，`Public`介面繼承自`Friend`介面，或有`Protected`類別繼承自`Private`類別。</span><span class="sxs-lookup"><span data-stu-id="7abbb-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="7abbb-105">這會公開基底類別或介面，以存取超過預期的層級。</span><span class="sxs-lookup"><span data-stu-id="7abbb-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="7abbb-106">**錯誤 ID:** BC30910</span><span class="sxs-lookup"><span data-stu-id="7abbb-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7abbb-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7abbb-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7abbb-108">變更衍生的類別或介面，以最少的基底類別或介面限制的存取層級。</span><span class="sxs-lookup"><span data-stu-id="7abbb-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="7abbb-109">-或-</span><span class="sxs-lookup"><span data-stu-id="7abbb-109">-or-</span></span>  
  
-   <span data-ttu-id="7abbb-110">如果您需要較不嚴格的存取層級時，移除`Inherits`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7abbb-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="7abbb-111">您無法繼承自更具限制性的基底類別或介面。</span><span class="sxs-lookup"><span data-stu-id="7abbb-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abbb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7abbb-112">See also</span></span>

- [<span data-ttu-id="7abbb-113">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="7abbb-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="7abbb-114">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="7abbb-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="7abbb-115">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="7abbb-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="7abbb-116">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="7abbb-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
