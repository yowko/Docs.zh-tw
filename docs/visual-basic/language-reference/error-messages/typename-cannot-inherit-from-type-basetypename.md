---
title: '&#39;&lt;typename&gt; &#39;無法繼承自&lt;類型&gt; &#39;&lt;產生&gt;&#39;因為它會展開基底存取&lt;類型&gt;外部組件'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="fa620-102">&#39;&lt;typename&gt; &#39;無法繼承自&lt;類型&gt; &#39;&lt;產生&gt;&#39;因為它會展開基底存取&lt;類型&gt;外部組件</span><span class="sxs-lookup"><span data-stu-id="fa620-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="fa620-103">類別或介面繼承自基底類別或介面，但具有較不嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="fa620-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="fa620-104">例如，`Public`介面繼承自`Friend`介面，或`Protected`類別繼承自`Private`類別。</span><span class="sxs-lookup"><span data-stu-id="fa620-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="fa620-105">這樣會公開基底類別或介面，以存取超過預期的層級。</span><span class="sxs-lookup"><span data-stu-id="fa620-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="fa620-106">**錯誤 ID:** BC30910</span><span class="sxs-lookup"><span data-stu-id="fa620-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa620-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fa620-107">To correct this error</span></span>  
  
-   <span data-ttu-id="fa620-108">變更衍生的類別或介面若要在至少相同嚴格度的基底類別或介面的存取層級。</span><span class="sxs-lookup"><span data-stu-id="fa620-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="fa620-109">-或-</span><span class="sxs-lookup"><span data-stu-id="fa620-109">-or-</span></span>  
  
-   <span data-ttu-id="fa620-110">如果您需要較不嚴格的存取層級，移除`Inherits`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fa620-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="fa620-111">您無法繼承自更具限制性的基底類別或介面。</span><span class="sxs-lookup"><span data-stu-id="fa620-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa620-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa620-112">See Also</span></span>  
 [<span data-ttu-id="fa620-113">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="fa620-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="fa620-114">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="fa620-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="fa620-115">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="fa620-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="fa620-116">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="fa620-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
