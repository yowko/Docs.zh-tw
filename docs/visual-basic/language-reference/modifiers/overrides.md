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
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826583"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="8549d-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8549d-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="8549d-103">指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="8549d-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8549d-104">備註</span><span class="sxs-lookup"><span data-stu-id="8549d-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8549d-105">規則</span><span class="sxs-lookup"><span data-stu-id="8549d-105">Rules</span></span>  
  
-   <span data-ttu-id="8549d-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="8549d-106">**Declaration Context.**</span></span> <span data-ttu-id="8549d-107">您只能在屬性或程序宣告陳述式中使用 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="8549d-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="8549d-108">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="8549d-108">**Combined Modifiers.**</span></span> <span data-ttu-id="8549d-109">您不能相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="8549d-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="8549d-110">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="8549d-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="8549d-111">**相符簽章。**</span><span class="sxs-lookup"><span data-stu-id="8549d-111">**Matching Signatures.**</span></span> <span data-ttu-id="8549d-112">此宣告的簽章必須完全符合*簽章*屬性或程序，它會覆寫。</span><span class="sxs-lookup"><span data-stu-id="8549d-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="8549d-113">這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8549d-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="8549d-114">除了簽章，覆寫宣告也必須完全符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="8549d-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="8549d-115">存取層級</span><span class="sxs-lookup"><span data-stu-id="8549d-115">The access level</span></span>  
  
    -   <span data-ttu-id="8549d-116">傳回類型 (如果有的話)</span><span class="sxs-lookup"><span data-stu-id="8549d-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="8549d-117">**泛型簽章。**</span><span class="sxs-lookup"><span data-stu-id="8549d-117">**Generic Signatures.**</span></span> <span data-ttu-id="8549d-118">在泛型程序中，簽章包含類型參數的個數。</span><span class="sxs-lookup"><span data-stu-id="8549d-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="8549d-119">因此，覆寫宣告在這方面也必須符合基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="8549d-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="8549d-120">**其他符合。**</span><span class="sxs-lookup"><span data-stu-id="8549d-120">**Additional Matching.**</span></span> <span data-ttu-id="8549d-121">除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：</span><span class="sxs-lookup"><span data-stu-id="8549d-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="8549d-122">存取層級修飾詞 (例如[公開](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="8549d-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="8549d-123">傳遞機制，每個參數 ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="8549d-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="8549d-124">泛型程序的每個類型參數的條件約束清單</span><span class="sxs-lookup"><span data-stu-id="8549d-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="8549d-125">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="8549d-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="8549d-126">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="8549d-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="8549d-127">如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="8549d-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="8549d-128">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="8549d-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="8549d-129">`Overrides` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="8549d-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8549d-130">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="8549d-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8549d-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="8549d-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8549d-132">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="8549d-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8549d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8549d-133">See also</span></span>

- [<span data-ttu-id="8549d-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8549d-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="8549d-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="8549d-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="8549d-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="8549d-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="8549d-137">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8549d-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8549d-138">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="8549d-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="8549d-139">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8549d-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8549d-140">類型清單</span><span class="sxs-lookup"><span data-stu-id="8549d-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
