---
title: Overrides (Visual Basic)
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
ms.openlocfilehash: 7fff91d993743574d13030aa3d5cc1e462e76838
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751023"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="ce838-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce838-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="ce838-103">指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="ce838-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="ce838-104">規則</span><span class="sxs-lookup"><span data-stu-id="ce838-104">Rules</span></span>

- <span data-ttu-id="ce838-105">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="ce838-105">**Declaration Context.**</span></span> <span data-ttu-id="ce838-106">您只能在屬性或程序宣告陳述式中使用 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="ce838-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="ce838-107">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="ce838-107">**Combined Modifiers.**</span></span> <span data-ttu-id="ce838-108">您不能相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="ce838-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="ce838-109">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="ce838-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="ce838-110">**相符簽章。**</span><span class="sxs-lookup"><span data-stu-id="ce838-110">**Matching Signatures.**</span></span> <span data-ttu-id="ce838-111">此宣告的簽章必須完全符合*簽章*屬性或程序，它會覆寫。</span><span class="sxs-lookup"><span data-stu-id="ce838-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="ce838-112">這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ce838-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="ce838-113">除了簽章，覆寫宣告也必須完全符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="ce838-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="ce838-114">存取層級</span><span class="sxs-lookup"><span data-stu-id="ce838-114">The access level</span></span>

  - <span data-ttu-id="ce838-115">傳回類型 (如果有的話)</span><span class="sxs-lookup"><span data-stu-id="ce838-115">The return type, if any</span></span>

- <span data-ttu-id="ce838-116">**泛型簽章。**</span><span class="sxs-lookup"><span data-stu-id="ce838-116">**Generic Signatures.**</span></span> <span data-ttu-id="ce838-117">在泛型程序中，簽章包含類型參數的個數。</span><span class="sxs-lookup"><span data-stu-id="ce838-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="ce838-118">因此，覆寫宣告在這方面也必須符合基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="ce838-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="ce838-119">**其他符合。**</span><span class="sxs-lookup"><span data-stu-id="ce838-119">**Additional Matching.**</span></span> <span data-ttu-id="ce838-120">除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：</span><span class="sxs-lookup"><span data-stu-id="ce838-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="ce838-121">存取層級修飾詞 (例如[公開](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="ce838-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="ce838-122">傳遞機制，每個參數 ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="ce838-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="ce838-123">泛型程序的每個類型參數的條件約束清單</span><span class="sxs-lookup"><span data-stu-id="ce838-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="ce838-124">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="ce838-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="ce838-125">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="ce838-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="ce838-126">如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="ce838-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="ce838-127">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="ce838-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="ce838-128">`Overrides` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="ce838-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="ce838-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce838-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="ce838-130">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce838-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="ce838-131">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="ce838-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="ce838-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce838-132">See also</span></span>

- [<span data-ttu-id="ce838-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ce838-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="ce838-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ce838-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="ce838-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="ce838-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="ce838-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ce838-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="ce838-137">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="ce838-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="ce838-138">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce838-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ce838-139">類型清單</span><span class="sxs-lookup"><span data-stu-id="ce838-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
