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
ms.openlocfilehash: d37a93343822d069295477958780c2b9c72043fa
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875455"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="cea2c-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cea2c-102">Friend (Visual Basic)</span></span>

<span data-ttu-id="cea2c-103">指定一或多個宣告的程式設計專案只能從包含其宣告的元件內進行存取。</span><span class="sxs-lookup"><span data-stu-id="cea2c-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cea2c-104">備註</span><span class="sxs-lookup"><span data-stu-id="cea2c-104">Remarks</span></span>  

 <span data-ttu-id="cea2c-105">在許多情況下，您會想要讓整個元件使用程式設計專案（例如類別和結構），而不只是由宣告它們的元件使用。</span><span class="sxs-lookup"><span data-stu-id="cea2c-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="cea2c-106">不過，您可能不想讓元件之外的程式碼能夠存取它們 (例如，如果應用程式是專屬的) 。</span><span class="sxs-lookup"><span data-stu-id="cea2c-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="cea2c-107">如果您想要以這種方式限制對專案的存取，可以使用修飾詞來宣告 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="cea2c-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="cea2c-108">其他類別、結構以及編譯成相同元件的模組中的程式碼，都可以存取 `Friend` 該元件中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="cea2c-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="cea2c-109">`Friend` 存取通常是應用程式程式設計項目的慣用層級，而且 `Friend` 是介面、模組、類別或結構的預設存取層級。</span><span class="sxs-lookup"><span data-stu-id="cea2c-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="cea2c-110">您 `Friend` 只能在模組、介面或命名空間層級使用。</span><span class="sxs-lookup"><span data-stu-id="cea2c-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="cea2c-111">因此，元素的宣告內容 `Friend` 必須是原始程式檔、命名空間、介面、模組、類別或結構，但不能是程式。</span><span class="sxs-lookup"><span data-stu-id="cea2c-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="cea2c-112">您也可以使用 [受保護的 Friend](protected-friend.md) 存取修飾詞，讓類別成員可以從該類別、衍生類別，以及定義類別的相同元件中存取。</span><span class="sxs-lookup"><span data-stu-id="cea2c-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="cea2c-113">若要在其類別中以及從相同元件中的衍生類別，限制成員的存取權，您可以使用 [私用受保護](private-protected.md) 的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="cea2c-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="cea2c-114">如需和其他存取修飾詞的比較 `Friend` ，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="cea2c-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea2c-115">您可以指定另一個元件是 friend 元件，讓它能夠存取標記為的所有類型和成員 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="cea2c-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="cea2c-116">如需詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="cea2c-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="cea2c-117">範例</span><span class="sxs-lookup"><span data-stu-id="cea2c-117">Example</span></span>  

 <span data-ttu-id="cea2c-118">下列類別會使用 `Friend` 修飾詞，以允許相同元件中的其他程式設計專案存取某些成員。</span><span class="sxs-lookup"><span data-stu-id="cea2c-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="cea2c-119">使用方式</span><span class="sxs-lookup"><span data-stu-id="cea2c-119">Usage</span></span>  

 <span data-ttu-id="cea2c-120">您可以 `Friend` 在這些內容中使用修飾詞：</span><span class="sxs-lookup"><span data-stu-id="cea2c-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="cea2c-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-121">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="cea2c-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-122">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="cea2c-123">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="cea2c-123">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="cea2c-124">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-124">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="cea2c-125">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-125">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="cea2c-126">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-126">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="cea2c-127">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-127">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="cea2c-128">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-128">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="cea2c-129">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-129">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="cea2c-130">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-130">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="cea2c-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="cea2c-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="cea2c-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="cea2c-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="cea2c-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cea2c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea2c-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="cea2c-135">公開</span><span class="sxs-lookup"><span data-stu-id="cea2c-135">Public</span></span>](public.md)
- [<span data-ttu-id="cea2c-136">保護</span><span class="sxs-lookup"><span data-stu-id="cea2c-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="cea2c-137">私人</span><span class="sxs-lookup"><span data-stu-id="cea2c-137">Private</span></span>](private.md)
- [<span data-ttu-id="cea2c-138">私用保護</span><span class="sxs-lookup"><span data-stu-id="cea2c-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="cea2c-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="cea2c-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="cea2c-140">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="cea2c-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cea2c-141">程序</span><span class="sxs-lookup"><span data-stu-id="cea2c-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cea2c-142">結構</span><span class="sxs-lookup"><span data-stu-id="cea2c-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cea2c-143">物件和類別</span><span class="sxs-lookup"><span data-stu-id="cea2c-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
