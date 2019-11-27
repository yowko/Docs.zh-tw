---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351450"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="e01ca-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e01ca-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="e01ca-103">指定無法在衍生類別中覆寫屬性或程式。</span><span class="sxs-lookup"><span data-stu-id="e01ca-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e01ca-104">備註</span><span class="sxs-lookup"><span data-stu-id="e01ca-104">Remarks</span></span>  
 <span data-ttu-id="e01ca-105">`NotOverridable` 修飾詞可防止在衍生類別中覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="e01ca-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="e01ca-106">可覆[寫](../../../visual-basic/language-reference/modifiers/overridable.md)的修飾詞允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="e01ca-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="e01ca-107">如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="e01ca-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="e01ca-108">如果未指定 `Overridable` 或 `NotOverridable` 修飾詞，則預設值取決於屬性或方法是否會覆寫基類屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="e01ca-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="e01ca-109">如果屬性或方法會覆寫基類屬性或方法，則預設設定為 `Overridable`。否則，它會 `NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="e01ca-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="e01ca-110">無法覆寫的專案有時稱為*密封*元素。</span><span class="sxs-lookup"><span data-stu-id="e01ca-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="e01ca-111">您只能在屬性或程式宣告語句中使用 `NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="e01ca-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="e01ca-112">您只能在覆寫另一個屬性或程式的屬性或程式上指定 `NotOverridable`，也就是只與 `Overrides`組合。</span><span class="sxs-lookup"><span data-stu-id="e01ca-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="e01ca-113">合併的修飾詞</span><span class="sxs-lookup"><span data-stu-id="e01ca-113">Combined Modifiers</span></span>  
 <span data-ttu-id="e01ca-114">您不能為 `Private` 方法指定 `Overridable` 或 `NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="e01ca-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="e01ca-115">您不能在相同的宣告中同時指定 `NotOverridable` 與 `MustOverride`、`Overridable`或 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="e01ca-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e01ca-116">使用方式</span><span class="sxs-lookup"><span data-stu-id="e01ca-116">Usage</span></span>  
 <span data-ttu-id="e01ca-117">`NotOverridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="e01ca-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e01ca-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e01ca-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e01ca-119">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="e01ca-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e01ca-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e01ca-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e01ca-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e01ca-121">See also</span></span>

- [<span data-ttu-id="e01ca-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="e01ca-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="e01ca-123">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="e01ca-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="e01ca-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e01ca-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="e01ca-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="e01ca-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="e01ca-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="e01ca-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="e01ca-127">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e01ca-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="e01ca-128">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="e01ca-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
