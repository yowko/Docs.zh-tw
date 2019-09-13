---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929462"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="18a4d-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a4d-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="18a4d-103">成員存取修飾詞，指定一或多個宣告的程式設計項目，只能從其本身的類別或衍生類別中存取。</span><span class="sxs-lookup"><span data-stu-id="18a4d-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18a4d-104">備註</span><span class="sxs-lookup"><span data-stu-id="18a4d-104">Remarks</span></span>  
 <span data-ttu-id="18a4d-105">有時候，在類別中宣告的程式設計專案包含敏感性資料或受限制的程式碼，而您想要限制對專案的存取。</span><span class="sxs-lookup"><span data-stu-id="18a4d-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="18a4d-106">不過，如果類別是可繼承的，而且您預期衍生類別的階層，則這些衍生類別可能需要存取資料或程式碼。</span><span class="sxs-lookup"><span data-stu-id="18a4d-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="18a4d-107">在這種情況下，您會想要從基類和所有衍生類別來存取元素。</span><span class="sxs-lookup"><span data-stu-id="18a4d-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="18a4d-108">若要以這種方式限制對專案的存取，您可以使用`Protected`來宣告該元素。</span><span class="sxs-lookup"><span data-stu-id="18a4d-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="18a4d-109">`Protected`存取修飾詞可以與兩個其他修改者結合：</span><span class="sxs-lookup"><span data-stu-id="18a4d-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="18a4d-110">[受保護的 Friend](protected-friend.md)修飾詞可讓類別成員從該類別、衍生類別，以及定義類別的相同元件中存取。</span><span class="sxs-lookup"><span data-stu-id="18a4d-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="18a4d-111">[私用保護](private-protected.md)的修飾詞可讓衍生類型存取類別成員，但只能在其包含的元件內使用。</span><span class="sxs-lookup"><span data-stu-id="18a4d-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="18a4d-112">規則</span><span class="sxs-lookup"><span data-stu-id="18a4d-112">Rules</span></span>  
  
- <span data-ttu-id="18a4d-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="18a4d-113">**Declaration Context.**</span></span> <span data-ttu-id="18a4d-114">您只能在`Protected`類別層級使用。</span><span class="sxs-lookup"><span data-stu-id="18a4d-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="18a4d-115">這表示`Protected`元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。</span><span class="sxs-lookup"><span data-stu-id="18a4d-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="18a4d-116">行為</span><span class="sxs-lookup"><span data-stu-id="18a4d-116">Behavior</span></span>  
  
- <span data-ttu-id="18a4d-117">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="18a4d-117">**Access Level.**</span></span> <span data-ttu-id="18a4d-118">類別中的所有程式碼都可以存取其元素。</span><span class="sxs-lookup"><span data-stu-id="18a4d-118">All code in a class can access its elements.</span></span> <span data-ttu-id="18a4d-119">任何衍生自基類的類別中的程式碼，都可以存取`Protected`基類的所有元素。</span><span class="sxs-lookup"><span data-stu-id="18a4d-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="18a4d-120">這適用于所有的衍生層代。</span><span class="sxs-lookup"><span data-stu-id="18a4d-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="18a4d-121">這表示，類別可以存取`Protected`基類基類的元素，依此類推。</span><span class="sxs-lookup"><span data-stu-id="18a4d-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="18a4d-122">受保護的存取不是 friend 存取的超集合或子集。</span><span class="sxs-lookup"><span data-stu-id="18a4d-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="18a4d-123">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="18a4d-123">**Access Modifiers.**</span></span> <span data-ttu-id="18a4d-124">指定存取層級的關鍵字稱為*存取*修飾詞。</span><span class="sxs-lookup"><span data-stu-id="18a4d-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="18a4d-125">如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="18a4d-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="18a4d-126">`Protected` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="18a4d-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="18a4d-127">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="18a4d-128">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="18a4d-129">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="18a4d-130">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="18a4d-131">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="18a4d-132">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="18a4d-133">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="18a4d-134">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="18a4d-135">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="18a4d-136">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="18a4d-137">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="18a4d-138">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="18a4d-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="18a4d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a4d-139">See also</span></span>

- [<span data-ttu-id="18a4d-140">Public</span><span class="sxs-lookup"><span data-stu-id="18a4d-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="18a4d-141">Friend</span><span class="sxs-lookup"><span data-stu-id="18a4d-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="18a4d-142">Private</span><span class="sxs-lookup"><span data-stu-id="18a4d-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="18a4d-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="18a4d-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="18a4d-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="18a4d-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="18a4d-145">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="18a4d-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="18a4d-146">程序</span><span class="sxs-lookup"><span data-stu-id="18a4d-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="18a4d-147">結構</span><span class="sxs-lookup"><span data-stu-id="18a4d-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="18a4d-148">物件和類別</span><span class="sxs-lookup"><span data-stu-id="18a4d-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
