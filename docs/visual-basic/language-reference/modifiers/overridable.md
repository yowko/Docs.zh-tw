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
ms.openlocfilehash: 8506aba7e64f2dbd975cc275cefb7b5bb1aefda5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875005"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="e0132-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0132-102">Overridable (Visual Basic)</span></span>

<span data-ttu-id="e0132-103">指定屬性或程式可由衍生類別中的相同命名屬性或程式覆寫。</span><span class="sxs-lookup"><span data-stu-id="e0132-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0132-104">備註</span><span class="sxs-lookup"><span data-stu-id="e0132-104">Remarks</span></span>  

 <span data-ttu-id="e0132-105">`Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="e0132-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="e0132-106">[NotOverridable](notoverridable.md)修飾詞可防止屬性或方法在衍生類別中遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="e0132-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="e0132-107">如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="e0132-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="e0132-108">如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="e0132-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="e0132-109">如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="e0132-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="e0132-110">您可以使用陰影或覆寫來重新定義繼承的元素，但是這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="e0132-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e0132-111">如需詳細資訊，請參閱 [Visual Basic 中的遮蔽](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="e0132-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="e0132-112">可以覆寫的元素有時稱為 *虛擬* 元素。</span><span class="sxs-lookup"><span data-stu-id="e0132-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="e0132-113">如果可以覆寫，但不一定要這樣做，有時也稱為 *實體* 元素。</span><span class="sxs-lookup"><span data-stu-id="e0132-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="e0132-114">您 `Overridable` 只能在屬性或程式聲明語句中使用。</span><span class="sxs-lookup"><span data-stu-id="e0132-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="e0132-115">合併的修飾詞</span><span class="sxs-lookup"><span data-stu-id="e0132-115">Combined Modifiers</span></span>  

 <span data-ttu-id="e0132-116">您無法 `Overridable` `NotOverridable` 為方法指定或 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="e0132-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="e0132-117">您無法 `Overridable` 在相同的宣告中同時指定和 `MustOverride` 、 `NotOverridable` 或 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="e0132-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="e0132-118">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="e0132-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e0132-119">使用方式</span><span class="sxs-lookup"><span data-stu-id="e0132-119">Usage</span></span>  

 <span data-ttu-id="e0132-120">`Overridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="e0132-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e0132-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0132-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="e0132-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e0132-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="e0132-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0132-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0132-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0132-124">See also</span></span>

- [<span data-ttu-id="e0132-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="e0132-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e0132-126">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="e0132-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="e0132-127">New</span><span class="sxs-lookup"><span data-stu-id="e0132-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="e0132-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e0132-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="e0132-129">覆寫</span><span class="sxs-lookup"><span data-stu-id="e0132-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="e0132-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e0132-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e0132-131">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="e0132-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
