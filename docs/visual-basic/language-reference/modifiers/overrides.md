---
title: '[覆寫]'
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351377"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="ce1e3-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce1e3-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="ce1e3-103">指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="ce1e3-104">規則</span><span class="sxs-lookup"><span data-stu-id="ce1e3-104">Rules</span></span>

- <span data-ttu-id="ce1e3-105">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-105">**Declaration Context.**</span></span> <span data-ttu-id="ce1e3-106">您只能在屬性或程式宣告語句中使用 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="ce1e3-107">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-107">**Combined Modifiers.**</span></span> <span data-ttu-id="ce1e3-108">您不能在相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="ce1e3-109">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="ce1e3-110">**符合的簽章。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-110">**Matching Signatures.**</span></span> <span data-ttu-id="ce1e3-111">這個宣告的簽章必須與它所覆寫之屬性或*程式的簽*章完全相符。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="ce1e3-112">這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="ce1e3-113">除了簽章，覆寫宣告也必須完全符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="ce1e3-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="ce1e3-114">存取層級</span><span class="sxs-lookup"><span data-stu-id="ce1e3-114">The access level</span></span>

  - <span data-ttu-id="ce1e3-115">傳回類型 (如果有的話)</span><span class="sxs-lookup"><span data-stu-id="ce1e3-115">The return type, if any</span></span>

- <span data-ttu-id="ce1e3-116">**一般簽章。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-116">**Generic Signatures.**</span></span> <span data-ttu-id="ce1e3-117">在泛型程序中，簽章包含類型參數的個數。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="ce1e3-118">因此，覆寫宣告在這方面也必須符合基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="ce1e3-119">**其他相符的。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-119">**Additional Matching.**</span></span> <span data-ttu-id="ce1e3-120">除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：</span><span class="sxs-lookup"><span data-stu-id="ce1e3-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="ce1e3-121">存取層級修飾詞（例如[Public](../../../visual-basic/language-reference/modifiers/public.md)）</span><span class="sxs-lookup"><span data-stu-id="ce1e3-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="ce1e3-122">每個參數的傳遞機制（[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)）</span><span class="sxs-lookup"><span data-stu-id="ce1e3-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="ce1e3-123">泛型程序的每個類型參數的條件約束清單</span><span class="sxs-lookup"><span data-stu-id="ce1e3-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="ce1e3-124">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="ce1e3-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="ce1e3-125">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="ce1e3-126">如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="ce1e3-127">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="ce1e3-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="ce1e3-128">`Overrides` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="ce1e3-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="ce1e3-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce1e3-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="ce1e3-130">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce1e3-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="ce1e3-131">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce1e3-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="ce1e3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1e3-132">See also</span></span>

- [<span data-ttu-id="ce1e3-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ce1e3-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="ce1e3-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ce1e3-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="ce1e3-135">Overrides</span><span class="sxs-lookup"><span data-stu-id="ce1e3-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="ce1e3-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ce1e3-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="ce1e3-137">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="ce1e3-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="ce1e3-138">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="ce1e3-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ce1e3-139">類型清單</span><span class="sxs-lookup"><span data-stu-id="ce1e3-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
