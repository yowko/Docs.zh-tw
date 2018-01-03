---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="9a53c-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a53c-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="9a53c-103">指定一或多個宣告的程式設計項目只能從包含其宣告的組件內存取。</span><span class="sxs-lookup"><span data-stu-id="9a53c-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a53c-104">備註</span><span class="sxs-lookup"><span data-stu-id="9a53c-104">Remarks</span></span>  
 <span data-ttu-id="9a53c-105">在許多情況下，您會想程式設計元素，例如類別和結構，以供整個組件，只要其宣告的元件。</span><span class="sxs-lookup"><span data-stu-id="9a53c-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="9a53c-106">不過，您可能不想要讓他們存取組件之外的程式碼 （例如，如果應用程式是專屬的）。</span><span class="sxs-lookup"><span data-stu-id="9a53c-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="9a53c-107">如果您想要限制存取的項目，如此一來，您就可以將它宣告使用`Friend`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9a53c-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="9a53c-108">其他的類別、 結構和編譯成相同的模組中的程式碼組件可以存取所有`Friend`該組件中的項目。</span><span class="sxs-lookup"><span data-stu-id="9a53c-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="9a53c-109">`Friend`存取通常是慣用的應用程式的程式設計項目層級和`Friend`是介面、 模組、 類別或結構的層級的預設存取權。</span><span class="sxs-lookup"><span data-stu-id="9a53c-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="9a53c-110">您可以使用`Friend`只在模組、 介面或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="9a53c-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="9a53c-111">因此，宣告內容`Friend`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，不能在程序。</span><span class="sxs-lookup"><span data-stu-id="9a53c-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="9a53c-112">您可以使用`Friend`修飾詞搭配[保護](../../../visual-basic/language-reference/modifiers/protected.md)相同宣告中的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9a53c-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="9a53c-113">這個組合會授與兩者`Friend`存取，以及上宣告的項目，這樣就可從相同組件，從其自己的類別和衍生類別中的任何位置存取受保護的存取。</span><span class="sxs-lookup"><span data-stu-id="9a53c-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="9a53c-114">您可以指定`Protected Friend`只能在類別成員上。</span><span class="sxs-lookup"><span data-stu-id="9a53c-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="9a53c-115">如需的比較`Friend`和其他存取修飾詞，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9a53c-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a53c-116">您可以指定另一個組件是 friend 組件，使其可以存取所有類型和成員標記為`Friend`。</span><span class="sxs-lookup"><span data-stu-id="9a53c-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="9a53c-117">如需詳細資訊，請參閱 [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md) (Friend 組件)。</span><span class="sxs-lookup"><span data-stu-id="9a53c-117">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a53c-118">範例</span><span class="sxs-lookup"><span data-stu-id="9a53c-118">Example</span></span>  
 <span data-ttu-id="9a53c-119">下列類別使用`Friend`修飾詞，以允許存取特定成員相同的組件中的其他程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="9a53c-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="9a53c-120">使用量</span><span class="sxs-lookup"><span data-stu-id="9a53c-120">Usage</span></span>  
 <span data-ttu-id="9a53c-121">您可以使用`Friend`修飾詞在這些內容中：</span><span class="sxs-lookup"><span data-stu-id="9a53c-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="9a53c-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="9a53c-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="9a53c-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9a53c-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="9a53c-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9a53c-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="9a53c-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9a53c-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9a53c-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="9a53c-131">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="9a53c-132">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9a53c-133">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="9a53c-134">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a53c-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9a53c-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a53c-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="9a53c-136">Public</span><span class="sxs-lookup"><span data-stu-id="9a53c-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="9a53c-137">Protected</span><span class="sxs-lookup"><span data-stu-id="9a53c-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="9a53c-138">Private</span><span class="sxs-lookup"><span data-stu-id="9a53c-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="9a53c-139">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="9a53c-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="9a53c-140">程序</span><span class="sxs-lookup"><span data-stu-id="9a53c-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="9a53c-141">結構</span><span class="sxs-lookup"><span data-stu-id="9a53c-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="9a53c-142">物件和類別</span><span class="sxs-lookup"><span data-stu-id="9a53c-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
