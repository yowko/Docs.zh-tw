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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392115"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="d8f19-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8f19-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="d8f19-103">指定屬性或程式可由衍生類別中名稱相同的屬性或程式覆寫。</span><span class="sxs-lookup"><span data-stu-id="d8f19-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8f19-104">備註</span><span class="sxs-lookup"><span data-stu-id="d8f19-104">Remarks</span></span>  
 <span data-ttu-id="d8f19-105">`Overridable`修飾詞允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="d8f19-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="d8f19-106">[NotOverridable](notoverridable.md)修飾詞可防止在衍生類別中覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="d8f19-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="d8f19-107">如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f19-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="d8f19-108">如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="d8f19-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="d8f19-109">如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="d8f19-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="d8f19-110">您可以遮蔽或覆寫以重新定義繼承的元素，但這兩種方法之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="d8f19-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="d8f19-111">如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f19-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="d8f19-112">可以覆寫的專案有時稱為*虛擬*元素。</span><span class="sxs-lookup"><span data-stu-id="d8f19-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="d8f19-113">如果可以覆寫它，但不一定要這麼做，有時也稱為*具體*元素。</span><span class="sxs-lookup"><span data-stu-id="d8f19-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="d8f19-114">您 `Overridable` 只能在屬性或程式宣告語句中使用。</span><span class="sxs-lookup"><span data-stu-id="d8f19-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="d8f19-115">合併的修飾詞</span><span class="sxs-lookup"><span data-stu-id="d8f19-115">Combined Modifiers</span></span>  
 <span data-ttu-id="d8f19-116">您不能 `Overridable` `NotOverridable` 為方法指定或 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="d8f19-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="d8f19-117">您不能 `Overridable` `MustOverride` `NotOverridable` 在相同的宣告中，搭配、或來指定 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="d8f19-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="d8f19-118">因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="d8f19-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="d8f19-119">使用方式</span><span class="sxs-lookup"><span data-stu-id="d8f19-119">Usage</span></span>  
 <span data-ttu-id="d8f19-120">`Overridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d8f19-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d8f19-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d8f19-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="d8f19-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d8f19-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="d8f19-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d8f19-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d8f19-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f19-124">See also</span></span>

- [<span data-ttu-id="d8f19-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="d8f19-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d8f19-126">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="d8f19-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="d8f19-127">New</span><span class="sxs-lookup"><span data-stu-id="d8f19-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="d8f19-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d8f19-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="d8f19-129">覆寫</span><span class="sxs-lookup"><span data-stu-id="d8f19-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="d8f19-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d8f19-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="d8f19-131">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="d8f19-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
