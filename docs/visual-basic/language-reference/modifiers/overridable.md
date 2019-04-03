---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816873"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="b0e17-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0e17-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="b0e17-103">指定的屬性或程序可覆寫同名的屬性或衍生類別中的程序。</span><span class="sxs-lookup"><span data-stu-id="b0e17-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0e17-104">備註</span><span class="sxs-lookup"><span data-stu-id="b0e17-104">Remarks</span></span>  
 <span data-ttu-id="b0e17-105">`Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="b0e17-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="b0e17-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾詞可防止屬性或方法覆寫衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="b0e17-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="b0e17-107">如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e17-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="b0e17-108">如果`Overridable`或`NotOverridable`修飾詞未指定，預設值取決於是否屬性或方法會覆寫基底類別屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="b0e17-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="b0e17-109">如果屬性或方法覆寫基底類別屬性或方法，預設值是`Overridable`; 否則它是`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="b0e17-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="b0e17-110">您可以遮蔽或覆寫，以重新定義繼承的項目，但有兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="b0e17-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="b0e17-111">如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e17-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="b0e17-112">可以覆寫的項目有時稱為*虛擬*項目。</span><span class="sxs-lookup"><span data-stu-id="b0e17-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="b0e17-113">如果它可以覆寫，但不一定要時，有時也稱為*具體*項目。</span><span class="sxs-lookup"><span data-stu-id="b0e17-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="b0e17-114">您只能在屬性或程序宣告陳述式中使用 `Overridable`。</span><span class="sxs-lookup"><span data-stu-id="b0e17-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="b0e17-115">結合的修飾詞</span><span class="sxs-lookup"><span data-stu-id="b0e17-115">Combined Modifiers</span></span>  
 <span data-ttu-id="b0e17-116">您無法指定`Overridable`或是`NotOverridable`如`Private`方法。</span><span class="sxs-lookup"><span data-stu-id="b0e17-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="b0e17-117">您無法指定`Overridable`連同`MustOverride`， `NotOverridable`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="b0e17-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="b0e17-118">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="b0e17-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b0e17-119">使用量</span><span class="sxs-lookup"><span data-stu-id="b0e17-119">Usage</span></span>  
 <span data-ttu-id="b0e17-120">`Overridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="b0e17-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b0e17-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0e17-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b0e17-122">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0e17-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b0e17-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0e17-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b0e17-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e17-124">See also</span></span>

- [<span data-ttu-id="b0e17-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="b0e17-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="b0e17-126">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="b0e17-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="b0e17-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b0e17-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="b0e17-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b0e17-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="b0e17-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="b0e17-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="b0e17-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b0e17-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="b0e17-131">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="b0e17-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
