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
ms.openlocfilehash: 88e13fcd03c6a10cf1450cec90f9ca60aedc3eb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778706"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="9c651-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c651-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="9c651-103">成員存取修飾詞，指定一或多個宣告的程式設計項目都可以存取只會從自己的類別或從衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="9c651-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c651-104">備註</span><span class="sxs-lookup"><span data-stu-id="9c651-104">Remarks</span></span>  
 <span data-ttu-id="9c651-105">有時在類別中宣告的程式設計項目包含敏感性資料或受限制的程式碼，以及您想要限制存取的項目。</span><span class="sxs-lookup"><span data-stu-id="9c651-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="9c651-106">不過，如果是繼承的類別，而且您預期的衍生類別階層架構，它可能需要針對這些衍生的類別，以存取資料或程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c651-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="9c651-107">在此情況下，您想要存取的基底類別和所有衍生類別的項目。</span><span class="sxs-lookup"><span data-stu-id="9c651-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="9c651-108">若要限制存取的項目，以這種方式，您可以將它與宣告`Protected`。</span><span class="sxs-lookup"><span data-stu-id="9c651-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="9c651-109">`Protected`存取修飾詞可以結合兩個其他修飾詞：</span><span class="sxs-lookup"><span data-stu-id="9c651-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="9c651-110">[Protected Friend](protected-friend.md)修飾詞讓從該類別中，從衍生的類別，以及從相同的組件中定義類別中存取類別成員。</span><span class="sxs-lookup"><span data-stu-id="9c651-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="9c651-111">[Private Protected](private-protected.md)修飾詞可讓類別成員可存取由衍生的型別，但只在其包含的組件。</span><span class="sxs-lookup"><span data-stu-id="9c651-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="9c651-112">規則</span><span class="sxs-lookup"><span data-stu-id="9c651-112">Rules</span></span>  
  
- <span data-ttu-id="9c651-113">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="9c651-113">**Declaration Context.**</span></span> <span data-ttu-id="9c651-114">您可以使用`Protected`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="9c651-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="9c651-115">這表示的宣告內容`Protected`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="9c651-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="9c651-116">行為</span><span class="sxs-lookup"><span data-stu-id="9c651-116">Behavior</span></span>  
  
- <span data-ttu-id="9c651-117">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="9c651-117">**Access Level.**</span></span> <span data-ttu-id="9c651-118">在類別中的所有程式碼可以存取其項目。</span><span class="sxs-lookup"><span data-stu-id="9c651-118">All code in a class can access its elements.</span></span> <span data-ttu-id="9c651-119">在任何衍生自基底類別的類別中的程式碼可以存取所有`Protected`基底類別的項目。</span><span class="sxs-lookup"><span data-stu-id="9c651-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="9c651-120">這是衍生的所有層代，則為 true。</span><span class="sxs-lookup"><span data-stu-id="9c651-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="9c651-121">這表示的類別可以存取`Protected`基底類別的基底類別等的項目。</span><span class="sxs-lookup"><span data-stu-id="9c651-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="9c651-122">受保護的存取不是超集或 friend 存取權限的子集。</span><span class="sxs-lookup"><span data-stu-id="9c651-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="9c651-123">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="9c651-123">**Access Modifiers.**</span></span> <span data-ttu-id="9c651-124">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="9c651-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="9c651-125">如需存取修飾詞的比較，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9c651-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9c651-126">`Protected` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="9c651-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9c651-127">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="9c651-128">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="9c651-129">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9c651-130">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="9c651-131">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9c651-132">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="9c651-133">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9c651-134">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9c651-135">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="9c651-136">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9c651-137">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="9c651-138">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c651-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c651-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c651-139">See also</span></span>

- [<span data-ttu-id="9c651-140">Public</span><span class="sxs-lookup"><span data-stu-id="9c651-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="9c651-141">Friend</span><span class="sxs-lookup"><span data-stu-id="9c651-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="9c651-142">Private</span><span class="sxs-lookup"><span data-stu-id="9c651-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="9c651-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="9c651-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="9c651-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="9c651-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="9c651-145">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="9c651-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="9c651-146">程序</span><span class="sxs-lookup"><span data-stu-id="9c651-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="9c651-147">結構</span><span class="sxs-lookup"><span data-stu-id="9c651-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9c651-148">物件和類別</span><span class="sxs-lookup"><span data-stu-id="9c651-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
