---
title: Shadows
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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351268"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="f18c8-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f18c8-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="f18c8-103">指定宣告的程式設計專案會在基類中重新宣告並隱藏具有相同名稱的專案或多載元素的集合。</span><span class="sxs-lookup"><span data-stu-id="f18c8-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="f18c8-104">備註</span><span class="sxs-lookup"><span data-stu-id="f18c8-104">Remarks</span></span>

<span data-ttu-id="f18c8-105">遮蔽的主要目的（也稱為「*依名稱隱藏*」）是保留類別成員的定義。</span><span class="sxs-lookup"><span data-stu-id="f18c8-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="f18c8-106">基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。</span><span class="sxs-lookup"><span data-stu-id="f18c8-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="f18c8-107">如果發生這種情況，`Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。</span><span class="sxs-lookup"><span data-stu-id="f18c8-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="f18c8-108">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="f18c8-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="f18c8-109">如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="f18c8-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="f18c8-110">規則</span><span class="sxs-lookup"><span data-stu-id="f18c8-110">Rules</span></span>

- <span data-ttu-id="f18c8-111">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="f18c8-111">**Declaration Context.**</span></span> <span data-ttu-id="f18c8-112">您只能在類別層級使用 `Shadows`。</span><span class="sxs-lookup"><span data-stu-id="f18c8-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="f18c8-113">這表示 `Shadows` 元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。</span><span class="sxs-lookup"><span data-stu-id="f18c8-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="f18c8-114">您只能在單一宣告語句中宣告一個遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="f18c8-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="f18c8-115">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="f18c8-115">**Combined Modifiers.**</span></span> <span data-ttu-id="f18c8-116">您不能在相同的宣告中同時指定 `Shadows` 與 `Overloads`、`Overrides`或 `Static`。</span><span class="sxs-lookup"><span data-stu-id="f18c8-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="f18c8-117">**元素類型。**</span><span class="sxs-lookup"><span data-stu-id="f18c8-117">**Element Types.**</span></span> <span data-ttu-id="f18c8-118">您可以使用任何其他類型遮蔽任何一種已宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="f18c8-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="f18c8-119">如果您使用另一個屬性或程式來遮蔽屬性或程式，參數和傳回型別就不需要與基類屬性或程式中的相同。</span><span class="sxs-lookup"><span data-stu-id="f18c8-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="f18c8-120">**正在.**</span><span class="sxs-lookup"><span data-stu-id="f18c8-120">**Accessing.**</span></span> <span data-ttu-id="f18c8-121">基類中的陰影元素通常無法從遮蔽它的衍生類別中使用。</span><span class="sxs-lookup"><span data-stu-id="f18c8-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="f18c8-122">不過，下列考慮適用于。</span><span class="sxs-lookup"><span data-stu-id="f18c8-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="f18c8-123">如果無法從參考的程式碼存取遮蔽專案，則會將參考解析為陰影專案。</span><span class="sxs-lookup"><span data-stu-id="f18c8-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="f18c8-124">例如，如果 `Private` 專案遮蔽基類元素，則沒有許可權存取 `Private` 專案的程式碼會改為存取基類元素。</span><span class="sxs-lookup"><span data-stu-id="f18c8-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="f18c8-125">如果您遮蔽某個元素，仍然可以透過以基類類型宣告的物件來存取陰影元素。</span><span class="sxs-lookup"><span data-stu-id="f18c8-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="f18c8-126">您也可以透過 `MyBase`來存取它。</span><span class="sxs-lookup"><span data-stu-id="f18c8-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="f18c8-127">`Shadows` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="f18c8-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="f18c8-128">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="f18c8-129">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="f18c8-130">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="f18c8-131">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="f18c8-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="f18c8-133">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="f18c8-134">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="f18c8-135">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="f18c8-136">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="f18c8-137">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="f18c8-138">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="f18c8-139">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f18c8-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="f18c8-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f18c8-140">See also</span></span>

- [<span data-ttu-id="f18c8-141">共用</span><span class="sxs-lookup"><span data-stu-id="f18c8-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="f18c8-142">Static</span><span class="sxs-lookup"><span data-stu-id="f18c8-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="f18c8-143">Private</span><span class="sxs-lookup"><span data-stu-id="f18c8-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="f18c8-144">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="f18c8-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f18c8-145">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="f18c8-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="f18c8-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f18c8-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="f18c8-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f18c8-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="f18c8-148">多載</span><span class="sxs-lookup"><span data-stu-id="f18c8-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="f18c8-149">Overrides</span><span class="sxs-lookup"><span data-stu-id="f18c8-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="f18c8-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="f18c8-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f18c8-151">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="f18c8-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
