---
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351567"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="13618-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13618-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="13618-103">指定一或多個宣告的程式設計項目，只能從包含其宣告的元件中存取。</span><span class="sxs-lookup"><span data-stu-id="13618-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13618-104">備註</span><span class="sxs-lookup"><span data-stu-id="13618-104">Remarks</span></span>  
 <span data-ttu-id="13618-105">在許多情況下，您會想要讓整個元件使用程式設計專案（例如類別和結構），而不只是宣告它們的元件。</span><span class="sxs-lookup"><span data-stu-id="13618-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="13618-106">不過，您可能不想讓程式碼能夠透過元件外部的程式碼存取（例如，如果應用程式是專屬的）。</span><span class="sxs-lookup"><span data-stu-id="13618-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="13618-107">如果您想要以這種方式限制對專案的存取，您可以使用 `Friend` 修飾詞來宣告它。</span><span class="sxs-lookup"><span data-stu-id="13618-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="13618-108">其他類別、結構和模組中編譯成相同元件的程式碼，可以存取該元件中的所有 `Friend` 元素。</span><span class="sxs-lookup"><span data-stu-id="13618-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="13618-109">`Friend` 存取通常是應用程式設計項目的慣用層級，`Friend` 是介面、模組、類別或結構的預設存取層級。</span><span class="sxs-lookup"><span data-stu-id="13618-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="13618-110">您只能在模組、介面或命名空間層級使用 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="13618-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="13618-111">因此，`Friend` 元素的宣告內容必須是原始程式檔、命名空間、介面、模組、類別或結構;它不能是程式。</span><span class="sxs-lookup"><span data-stu-id="13618-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="13618-112">您也可以使用[受保護的 Friend](protected-friend.md)存取修飾詞，讓類別成員可從類別內、衍生類別，以及定義類別的相同元件中存取。</span><span class="sxs-lookup"><span data-stu-id="13618-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="13618-113">若要從相同元件中的類別和衍生類別限制成員的存取權，您可以使用私用[保護](private-protected.md)的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="13618-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="13618-114">如需 `Friend` 和其他存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="13618-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13618-115">您可以指定另一個元件是 friend 元件，讓它能夠存取標記為 `Friend`的所有類型和成員。</span><span class="sxs-lookup"><span data-stu-id="13618-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="13618-116">如需詳細資訊，請參閱 [Friend Assemblies](../../../standard/assembly/friend.md) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="13618-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="13618-117">範例</span><span class="sxs-lookup"><span data-stu-id="13618-117">Example</span></span>  
 <span data-ttu-id="13618-118">下列類別使用 `Friend` 修飾詞，允許相同元件中的其他程式設計項目存取特定成員。</span><span class="sxs-lookup"><span data-stu-id="13618-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="13618-119">使用方式</span><span class="sxs-lookup"><span data-stu-id="13618-119">Usage</span></span>  
 <span data-ttu-id="13618-120">您可以在這些內容中使用 `Friend` 修飾詞：</span><span class="sxs-lookup"><span data-stu-id="13618-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="13618-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="13618-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="13618-123">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="13618-124">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="13618-125">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="13618-126">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="13618-127">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="13618-128">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="13618-129">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="13618-130">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="13618-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="13618-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="13618-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="13618-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="13618-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13618-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="13618-135">Public</span><span class="sxs-lookup"><span data-stu-id="13618-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="13618-136">Protected</span><span class="sxs-lookup"><span data-stu-id="13618-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="13618-137">Private</span><span class="sxs-lookup"><span data-stu-id="13618-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="13618-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="13618-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="13618-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="13618-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="13618-140">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="13618-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="13618-141">程序</span><span class="sxs-lookup"><span data-stu-id="13618-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="13618-142">結構</span><span class="sxs-lookup"><span data-stu-id="13618-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="13618-143">物件和類別</span><span class="sxs-lookup"><span data-stu-id="13618-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
