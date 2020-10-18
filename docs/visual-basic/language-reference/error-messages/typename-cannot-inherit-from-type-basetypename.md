---
title: "'<typename>' 無法繼承自 <type> '<basetypename>'，因為它會在組件外展開基底 <type> 的存取"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5c019f9d74b11e48aa05a1480b9449fa28488b43
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161838"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="0688c-102">BC30910： ' \<typename> ' 無法繼承自 \<type> ' '， \<basetypename> 因為它會展開元件外部的基底存取 \<type></span><span class="sxs-lookup"><span data-stu-id="0688c-102">BC30910: '\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="0688c-103">類別或介面繼承自基底類別或介面，但存取層級較不嚴格。</span><span class="sxs-lookup"><span data-stu-id="0688c-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>

 <span data-ttu-id="0688c-104">例如， `Public` 介面繼承自 `Friend` 介面，或類別繼承自類別 `Protected` `Private` 。</span><span class="sxs-lookup"><span data-stu-id="0688c-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="0688c-105">這會公開基底類別或介面，以存取超出預期的層級。</span><span class="sxs-lookup"><span data-stu-id="0688c-105">This exposes the base class or interface to access beyond the intended level.</span></span>

 <span data-ttu-id="0688c-106">**錯誤識別碼：** BC30910</span><span class="sxs-lookup"><span data-stu-id="0688c-106">**Error ID:** BC30910</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0688c-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0688c-107">To correct this error</span></span>

- <span data-ttu-id="0688c-108">將衍生類別或介面的存取層級變更為至少與基類或介面的限制相同。</span><span class="sxs-lookup"><span data-stu-id="0688c-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>

     <span data-ttu-id="0688c-109">-或-</span><span class="sxs-lookup"><span data-stu-id="0688c-109">-or-</span></span>

- <span data-ttu-id="0688c-110">如果您需要較不嚴格的存取層級，請移除該 `Inherits` 語句。</span><span class="sxs-lookup"><span data-stu-id="0688c-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="0688c-111">您無法繼承更受限制的基類或介面。</span><span class="sxs-lookup"><span data-stu-id="0688c-111">You cannot inherit from a more restricted base class or interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="0688c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0688c-112">See also</span></span>

- [<span data-ttu-id="0688c-113">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="0688c-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="0688c-114">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="0688c-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="0688c-115">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="0688c-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="0688c-116">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="0688c-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
