---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="79561-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79561-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="79561-103">指定的一或多個宣告的程式設計項目都可以存取只會從他們自己的類別或從衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="79561-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79561-104">備註</span><span class="sxs-lookup"><span data-stu-id="79561-104">Remarks</span></span>  
 <span data-ttu-id="79561-105">有時類別中宣告的程式設計項目包含機密資料或受限制的程式碼，而且您想要限制存取的項目。</span><span class="sxs-lookup"><span data-stu-id="79561-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="79561-106">不過，如果是繼承的類別，而您預期的衍生類別階層架構，它可能需要針對這些衍生的類別，以存取資料或程式碼。</span><span class="sxs-lookup"><span data-stu-id="79561-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="79561-107">在這種情況下，您會想要存取的基底類別和所有衍生類別的項目。</span><span class="sxs-lookup"><span data-stu-id="79561-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="79561-108">若要限制存取，這種方式中的項目，您可以將它與宣告`Protected`。</span><span class="sxs-lookup"><span data-stu-id="79561-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="79561-109">規則</span><span class="sxs-lookup"><span data-stu-id="79561-109">Rules</span></span>  
  
-   <span data-ttu-id="79561-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="79561-110">**Declaration Context.**</span></span> <span data-ttu-id="79561-111">您可以使用`Protected`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="79561-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="79561-112">這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="79561-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="79561-113">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="79561-113">**Combined Modifiers.**</span></span> <span data-ttu-id="79561-114">您可以使用`Protected`修飾詞搭配[Friend](../../../visual-basic/language-reference/modifiers/friend.md)相同宣告中的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="79561-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="79561-115">這種組合可讓您可以從相同組件，從其自己的類別和衍生類別的任何位置存取宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="79561-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="79561-116">您可以指定`Protected Friend`只能在類別成員上。</span><span class="sxs-lookup"><span data-stu-id="79561-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="79561-117">行為</span><span class="sxs-lookup"><span data-stu-id="79561-117">Behavior</span></span>  
  
-   <span data-ttu-id="79561-118">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="79561-118">**Access Level.**</span></span> <span data-ttu-id="79561-119">類別中的所有程式碼可以存取其項目。</span><span class="sxs-lookup"><span data-stu-id="79561-119">All code in a class can access its elements.</span></span> <span data-ttu-id="79561-120">任何衍生自基底類別的類別中的程式碼可以存取所有`Protected`基底類別的項目。</span><span class="sxs-lookup"><span data-stu-id="79561-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="79561-121">這是衍生的所有層代，則為 true。</span><span class="sxs-lookup"><span data-stu-id="79561-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="79561-122">這表示類別可以存取`Protected`基底類別的基底類別等的項目。</span><span class="sxs-lookup"><span data-stu-id="79561-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="79561-123">受保護的存取不是超集或 friend 存取權限的子集。</span><span class="sxs-lookup"><span data-stu-id="79561-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="79561-124">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="79561-124">**Access Modifiers.**</span></span> <span data-ttu-id="79561-125">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="79561-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="79561-126">如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="79561-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="79561-127">`Protected` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="79561-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="79561-128">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="79561-129">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="79561-130">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="79561-131">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="79561-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="79561-133">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="79561-134">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="79561-135">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="79561-136">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="79561-137">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="79561-138">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="79561-139">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="79561-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="79561-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79561-140">See Also</span></span>  
 [<span data-ttu-id="79561-141">Public</span><span class="sxs-lookup"><span data-stu-id="79561-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="79561-142">Friend</span><span class="sxs-lookup"><span data-stu-id="79561-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="79561-143">Private</span><span class="sxs-lookup"><span data-stu-id="79561-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="79561-144">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="79561-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="79561-145">程序</span><span class="sxs-lookup"><span data-stu-id="79561-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="79561-146">結構</span><span class="sxs-lookup"><span data-stu-id="79561-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="79561-147">物件和類別</span><span class="sxs-lookup"><span data-stu-id="79561-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
