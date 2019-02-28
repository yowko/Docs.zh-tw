---
title: Friend (Visual Basic)
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
ms.openlocfilehash: 52fdbfa3b0cd79cc9714a13a75716829163e45f6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967369"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="cf6cb-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf6cb-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="cf6cb-103">指定一或多個宣告的程式設計元素，只能從包含其宣告的組件內加以存取。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf6cb-104">備註</span><span class="sxs-lookup"><span data-stu-id="cf6cb-104">Remarks</span></span>  
 <span data-ttu-id="cf6cb-105">在許多情況下，您想要的程式設計項目，例如類別和結構，以供整個組件中，不只是由其宣告的元件。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="cf6cb-106">不過，您可能不想要存取組件外部的程式碼 （例如，如果應用程式專屬）。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="cf6cb-107">如果您想要限制存取的項目，如此一來，您就可以將它宣告使用`Friend`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="cf6cb-108">其他類別、 結構和編譯成相同的模組中的程式碼組件可以存取所有`Friend`該組件中的項目。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="cf6cb-109">`Friend` 存取通常是慣用的應用程式的程式設計項目層級和`Friend`是預設存取層級的介面、 模組、 類別或結構。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="cf6cb-110">您可以使用`Friend`只能在模組、 介面或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="cf6cb-111">因此，宣告內容`Friend`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，不能在程序。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="cf6cb-112">您也可以使用[Protected Friend](protected-friend.md)讓從該類別中，從衍生的類別，以及從相同的組件中定義類別中存取類別成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="cf6cb-113">若要限制存取的成員在其類別內，以及從衍生類別中相同的組件，您使用[Private Protected](private-protected.md)存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="cf6cb-114">如需的比較`Friend`和其他存取修飾詞，請參閱 <<c2> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf6cb-115">您可以指定另一個組件是 friend 組件，可讓它以存取所有類型和成員標記為`Friend`。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="cf6cb-116">如需詳細資訊，請參閱 [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf6cb-117">範例</span><span class="sxs-lookup"><span data-stu-id="cf6cb-117">Example</span></span>  
 <span data-ttu-id="cf6cb-118">下列類別使用`Friend`修飾詞，以允許存取特定成員相同的組件中的其他程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="cf6cb-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="cf6cb-119">使用量</span><span class="sxs-lookup"><span data-stu-id="cf6cb-119">Usage</span></span>  
 <span data-ttu-id="cf6cb-120">您可以使用`Friend`修飾詞，在這些內容中：</span><span class="sxs-lookup"><span data-stu-id="cf6cb-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="cf6cb-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="cf6cb-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="cf6cb-123">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="cf6cb-124">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="cf6cb-125">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="cf6cb-126">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="cf6cb-127">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="cf6cb-128">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="cf6cb-129">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="cf6cb-130">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="cf6cb-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="cf6cb-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="cf6cb-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf6cb-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf6cb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf6cb-134">See also</span></span>
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="cf6cb-135">Public</span><span class="sxs-lookup"><span data-stu-id="cf6cb-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="cf6cb-136">Protected</span><span class="sxs-lookup"><span data-stu-id="cf6cb-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="cf6cb-137">Private</span><span class="sxs-lookup"><span data-stu-id="cf6cb-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="cf6cb-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="cf6cb-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="cf6cb-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="cf6cb-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="cf6cb-140">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="cf6cb-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cf6cb-141">程序</span><span class="sxs-lookup"><span data-stu-id="cf6cb-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cf6cb-142">結構</span><span class="sxs-lookup"><span data-stu-id="cf6cb-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cf6cb-143">物件和類別</span><span class="sxs-lookup"><span data-stu-id="cf6cb-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
