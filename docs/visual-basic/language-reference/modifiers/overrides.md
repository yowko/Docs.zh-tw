---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="0b1d6-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b1d6-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="0b1d6-103">指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b1d6-104">備註</span><span class="sxs-lookup"><span data-stu-id="0b1d6-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0b1d6-105">規則</span><span class="sxs-lookup"><span data-stu-id="0b1d6-105">Rules</span></span>  
  
-   <span data-ttu-id="0b1d6-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-106">**Declaration Context.**</span></span> <span data-ttu-id="0b1d6-107">您只能在屬性或程序宣告陳述式中使用 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="0b1d6-108">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-108">**Combined Modifiers.**</span></span> <span data-ttu-id="0b1d6-109">您不能相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="0b1d6-110">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="0b1d6-111">**相符簽章。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-111">**Matching Signatures.**</span></span> <span data-ttu-id="0b1d6-112">此宣告的簽章必須完全符合*簽章*屬性或程序，它會覆寫。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="0b1d6-113">這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="0b1d6-114">除了簽章，覆寫宣告也必須完全符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="0b1d6-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="0b1d6-115">存取層級</span><span class="sxs-lookup"><span data-stu-id="0b1d6-115">The access level</span></span>  
  
    -   <span data-ttu-id="0b1d6-116">傳回型別 (如果有的話)</span><span class="sxs-lookup"><span data-stu-id="0b1d6-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="0b1d6-117">**泛型簽章。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-117">**Generic Signatures.**</span></span> <span data-ttu-id="0b1d6-118">在泛型程序中，簽章包含型別參數的個數。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="0b1d6-119">因此，覆寫宣告在這方面也必須符合基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="0b1d6-120">**其他符合。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-120">**Additional Matching.**</span></span> <span data-ttu-id="0b1d6-121">除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：</span><span class="sxs-lookup"><span data-stu-id="0b1d6-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="0b1d6-122">存取層級修飾詞 (例如[公用](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="0b1d6-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="0b1d6-123">傳遞機制，每個參數 ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="0b1d6-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="0b1d6-124">泛型程序的每個型別參數的條件約束清單</span><span class="sxs-lookup"><span data-stu-id="0b1d6-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="0b1d6-125">**遮蔽和覆寫。**</span><span class="sxs-lookup"><span data-stu-id="0b1d6-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="0b1d6-126">遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="0b1d6-127">如需詳細資訊，請參閱[Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="0b1d6-128">如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。</span><span class="sxs-lookup"><span data-stu-id="0b1d6-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="0b1d6-129">`Overrides` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="0b1d6-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0b1d6-130">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b1d6-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="0b1d6-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b1d6-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="0b1d6-132">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b1d6-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b1d6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b1d6-133">See Also</span></span>  
 [<span data-ttu-id="0b1d6-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0b1d6-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="0b1d6-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0b1d6-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="0b1d6-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="0b1d6-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="0b1d6-137">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0b1d6-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="0b1d6-138">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="0b1d6-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="0b1d6-139">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="0b1d6-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="0b1d6-140">類型清單</span><span class="sxs-lookup"><span data-stu-id="0b1d6-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
