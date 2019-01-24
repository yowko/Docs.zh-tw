---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: e879819d945f3e7256edd34e87b9cae4a04c0829
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512732"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="74ab4-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74ab4-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="74ab4-103">指定宣告的程式設計項目會重新宣告並隱藏同名的項目或一組多載的項目，基底類別中。</span><span class="sxs-lookup"><span data-stu-id="74ab4-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74ab4-104">備註</span><span class="sxs-lookup"><span data-stu-id="74ab4-104">Remarks</span></span>  
 <span data-ttu-id="74ab4-105">遮蔽的主要目的 (也稱為*依名稱隱藏*) 是保留您的類別成員的定義。</span><span class="sxs-lookup"><span data-stu-id="74ab4-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="74ab4-106">基底類別可能進行的變更，會建立具有相同名稱做為其中一個已定義的項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="74ab4-107">如果發生這種情況，`Shadows`修飾詞強制參考透過您的類別成員解析您定義的而不是新的基底類別項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="74ab4-108">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="74ab4-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="74ab4-109">如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="74ab4-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="74ab4-110">規則</span><span class="sxs-lookup"><span data-stu-id="74ab4-110">Rules</span></span>  
  
-   <span data-ttu-id="74ab4-111">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="74ab4-111">**Declaration Context.**</span></span> <span data-ttu-id="74ab4-112">您可以使用`Shadows`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="74ab4-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="74ab4-113">這表示的宣告內容`Shadows`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="74ab4-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="74ab4-114">您可以宣告一個宣告陳述式中只能有一個遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="74ab4-115">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="74ab4-115">**Combined Modifiers.**</span></span> <span data-ttu-id="74ab4-116">您無法指定`Shadows`連同`Overloads`， `Overrides`，或`Static`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="74ab4-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="74ab4-117">**項目型別。**</span><span class="sxs-lookup"><span data-stu-id="74ab4-117">**Element Types.**</span></span> <span data-ttu-id="74ab4-118">您可以使用任何其他類型遮蔽任何一種已宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="74ab4-119">如果您遮蔽的屬性或程序與另一個屬性或程序，參數和傳回型別沒有以符合那些在基底類別屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="74ab4-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="74ab4-120">**存取。**</span><span class="sxs-lookup"><span data-stu-id="74ab4-120">**Accessing.**</span></span> <span data-ttu-id="74ab4-121">無法從遮蔽的衍生類別內通常使用遮蔽基底類別中的項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="74ab4-122">不過，適用下列考量。</span><span class="sxs-lookup"><span data-stu-id="74ab4-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="74ab4-123">如果遮蔽的項目不能從參考它的程式碼存取，則參考會解析為遮蔽的項目中。</span><span class="sxs-lookup"><span data-stu-id="74ab4-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="74ab4-124">例如，如果`Private`項目會遮蔽基底類別的項目，並沒有存取權限的程式碼`Private`項目改為存取基底類別項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="74ab4-125">如果遮蔽的項目時，您仍然可以透過使用基底類別的型別宣告的物件存取遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="74ab4-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="74ab4-126">您也可以存取透過`MyBase`。</span><span class="sxs-lookup"><span data-stu-id="74ab4-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="74ab4-127">`Shadows` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="74ab4-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="74ab4-128">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="74ab4-129">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="74ab4-130">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="74ab4-131">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="74ab4-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="74ab4-133">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="74ab4-134">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="74ab4-135">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="74ab4-136">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="74ab4-137">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="74ab4-138">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="74ab4-139">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="74ab4-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="74ab4-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74ab4-140">See also</span></span>
- [<span data-ttu-id="74ab4-141">Shared</span><span class="sxs-lookup"><span data-stu-id="74ab4-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="74ab4-142">Static</span><span class="sxs-lookup"><span data-stu-id="74ab4-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="74ab4-143">Private</span><span class="sxs-lookup"><span data-stu-id="74ab4-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="74ab4-144">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="74ab4-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="74ab4-145">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="74ab4-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="74ab4-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="74ab4-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="74ab4-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="74ab4-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="74ab4-148">多載</span><span class="sxs-lookup"><span data-stu-id="74ab4-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="74ab4-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="74ab4-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="74ab4-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="74ab4-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="74ab4-151">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="74ab4-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
