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
ms.openlocfilehash: 8eec54a12c7fb748df46e8c48a8b07eab983cc72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867861"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="bbb38-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbb38-102">NotOverridable (Visual Basic)</span></span>

<span data-ttu-id="bbb38-103">指定無法在衍生類別中覆寫屬性或程式。</span><span class="sxs-lookup"><span data-stu-id="bbb38-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbb38-104">備註</span><span class="sxs-lookup"><span data-stu-id="bbb38-104">Remarks</span></span>  

 <span data-ttu-id="bbb38-105">`NotOverridable`修飾詞可防止屬性或方法在衍生類別中遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="bbb38-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="bbb38-106">可 [覆寫的修飾詞](overridable.md) 允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="bbb38-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="bbb38-107">如需詳細資訊，請參閱[繼承的基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="bbb38-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="bbb38-108">如果 `Overridable` `NotOverridable` 未指定或修飾詞，預設值會取決於屬性或方法是否會覆寫基類屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="bbb38-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="bbb38-109">如果屬性或方法會覆寫基類屬性或方法，則預設設定為， `Overridable` 否則為 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="bbb38-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="bbb38-110">無法覆寫的元素有時也稱為 *密封* 元素。</span><span class="sxs-lookup"><span data-stu-id="bbb38-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="bbb38-111">您 `NotOverridable` 只能在屬性或程式聲明語句中使用。</span><span class="sxs-lookup"><span data-stu-id="bbb38-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="bbb38-112">您只能在 `NotOverridable` 覆寫另一個屬性或程式的屬性或程式上指定，也就是只與一起使用 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="bbb38-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="bbb38-113">合併的修飾詞</span><span class="sxs-lookup"><span data-stu-id="bbb38-113">Combined Modifiers</span></span>  

 <span data-ttu-id="bbb38-114">您無法 `Overridable` `NotOverridable` 為方法指定或 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="bbb38-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="bbb38-115">您無法 `NotOverridable` 在相同的宣告中同時指定和 `MustOverride` 、 `Overridable` 或 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="bbb38-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="bbb38-116">使用方式</span><span class="sxs-lookup"><span data-stu-id="bbb38-116">Usage</span></span>  

 <span data-ttu-id="bbb38-117">`NotOverridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="bbb38-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bbb38-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbb38-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="bbb38-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="bbb38-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="bbb38-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbb38-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bbb38-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbb38-121">See also</span></span>

- [<span data-ttu-id="bbb38-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="bbb38-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="bbb38-123">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="bbb38-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="bbb38-124">New</span><span class="sxs-lookup"><span data-stu-id="bbb38-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="bbb38-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="bbb38-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="bbb38-126">覆寫</span><span class="sxs-lookup"><span data-stu-id="bbb38-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="bbb38-127">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bbb38-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="bbb38-128">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="bbb38-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
