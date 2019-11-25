---
title: Overrides
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351393"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="d9834-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9834-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="d9834-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span><span class="sxs-lookup"><span data-stu-id="d9834-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9834-104">備註</span><span class="sxs-lookup"><span data-stu-id="d9834-104">Remarks</span></span>  
 <span data-ttu-id="d9834-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="d9834-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="d9834-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="d9834-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="d9834-107">如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="d9834-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="d9834-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span><span class="sxs-lookup"><span data-stu-id="d9834-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="d9834-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="d9834-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="d9834-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="d9834-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="d9834-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="d9834-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="d9834-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span><span class="sxs-lookup"><span data-stu-id="d9834-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="d9834-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span><span class="sxs-lookup"><span data-stu-id="d9834-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="d9834-114">You can use `Overridable` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="d9834-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="d9834-115">Combined Modifiers</span><span class="sxs-lookup"><span data-stu-id="d9834-115">Combined Modifiers</span></span>  
 <span data-ttu-id="d9834-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span><span class="sxs-lookup"><span data-stu-id="d9834-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="d9834-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="d9834-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="d9834-118">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="d9834-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="d9834-119">使用量</span><span class="sxs-lookup"><span data-stu-id="d9834-119">Usage</span></span>  
 <span data-ttu-id="d9834-120">`Overridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d9834-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d9834-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9834-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d9834-122">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9834-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d9834-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9834-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9834-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="d9834-124">See also</span></span>

- [<span data-ttu-id="d9834-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="d9834-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="d9834-126">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="d9834-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="d9834-127">New</span><span class="sxs-lookup"><span data-stu-id="d9834-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="d9834-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d9834-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="d9834-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="d9834-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="d9834-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d9834-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="d9834-131">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9834-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
