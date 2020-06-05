---
title: 遮蔽和覆寫的差異
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: a6ea83fadf18ef3be778e6de31c0eb4e65e74824
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392866"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="93c67-102">遮蔽和覆寫的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93c67-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="93c67-103">當您定義繼承自基類的類別時，您有時會想要重新定義衍生類別中的一個或多個基類元素。</span><span class="sxs-lookup"><span data-stu-id="93c67-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="93c67-104">遮蔽和覆寫皆可用於此用途。</span><span class="sxs-lookup"><span data-stu-id="93c67-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="93c67-105">比較</span><span class="sxs-lookup"><span data-stu-id="93c67-105">Comparison</span></span>  
 <span data-ttu-id="93c67-106">當衍生類別繼承基類時，會使用遮蔽和覆寫，而這兩個專案都是以另一個宣告的專案重新定義。</span><span class="sxs-lookup"><span data-stu-id="93c67-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="93c67-107">但是兩者之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="93c67-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="93c67-108">下表會比較與覆寫的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="93c67-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="93c67-109">比較點</span><span class="sxs-lookup"><span data-stu-id="93c67-109">Point of comparison</span></span>|<span data-ttu-id="93c67-110">遮蔽</span><span class="sxs-lookup"><span data-stu-id="93c67-110">Shadowing</span></span>|<span data-ttu-id="93c67-111">覆寫</span><span class="sxs-lookup"><span data-stu-id="93c67-111">Overriding</span></span>|  
|<span data-ttu-id="93c67-112">目的</span><span class="sxs-lookup"><span data-stu-id="93c67-112">Purpose</span></span>|<span data-ttu-id="93c67-113">防止後續的基類修改，引進您已在衍生類別中定義的成員。</span><span class="sxs-lookup"><span data-stu-id="93c67-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="93c67-114">藉由定義具有相同呼叫順序<sup>1</sup>的程式或屬性的不同執行，來達到多型</span><span class="sxs-lookup"><span data-stu-id="93c67-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="93c67-115">已重新定義元素</span><span class="sxs-lookup"><span data-stu-id="93c67-115">Redefined element</span></span>|<span data-ttu-id="93c67-116">任何宣告的元素類型</span><span class="sxs-lookup"><span data-stu-id="93c67-116">Any declared element type</span></span>|<span data-ttu-id="93c67-117">只有程式（ `Function` 、 `Sub` 或 `Operator` ）或屬性</span><span class="sxs-lookup"><span data-stu-id="93c67-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="93c67-118">重新定義元素</span><span class="sxs-lookup"><span data-stu-id="93c67-118">Redefining element</span></span>|<span data-ttu-id="93c67-119">任何宣告的元素類型</span><span class="sxs-lookup"><span data-stu-id="93c67-119">Any declared element type</span></span>|<span data-ttu-id="93c67-120">只有具有相同呼叫順序<sup>1</sup>的程式或屬性</span><span class="sxs-lookup"><span data-stu-id="93c67-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="93c67-121">重新定義元素的存取層級</span><span class="sxs-lookup"><span data-stu-id="93c67-121">Access level of redefining element</span></span>|<span data-ttu-id="93c67-122">任何存取層級</span><span class="sxs-lookup"><span data-stu-id="93c67-122">Any access level</span></span>|<span data-ttu-id="93c67-123">無法變更覆寫元素的存取層級</span><span class="sxs-lookup"><span data-stu-id="93c67-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="93c67-124">重新定義元素的可讀性和可寫性</span><span class="sxs-lookup"><span data-stu-id="93c67-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="93c67-125">任何組合</span><span class="sxs-lookup"><span data-stu-id="93c67-125">Any combination</span></span>|<span data-ttu-id="93c67-126">無法變更覆寫屬性的可讀性或可寫性</span><span class="sxs-lookup"><span data-stu-id="93c67-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="93c67-127">控制重新定義</span><span class="sxs-lookup"><span data-stu-id="93c67-127">Control over redefining</span></span>|<span data-ttu-id="93c67-128">基類元素無法強制或禁止遮蔽</span><span class="sxs-lookup"><span data-stu-id="93c67-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="93c67-129">基類元素可以指定 `MustOverride` 、 `NotOverridable` 或`Overridable`</span><span class="sxs-lookup"><span data-stu-id="93c67-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="93c67-130">關鍵字使用方式</span><span class="sxs-lookup"><span data-stu-id="93c67-130">Keyword usage</span></span>|<span data-ttu-id="93c67-131">`Shadows`建議在衍生類別中使用;`Shadows`如果沒有 `Shadows` 或 `Overrides` 指定<sup>2</sup> ，則假設為</span><span class="sxs-lookup"><span data-stu-id="93c67-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="93c67-132">`Overridable`或 `MustOverride` 在基類中需要， `Overrides` 在衍生類別中為必要項</span><span class="sxs-lookup"><span data-stu-id="93c67-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="93c67-133">繼承自衍生類別之類別的重新定義元素</span><span class="sxs-lookup"><span data-stu-id="93c67-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="93c67-134">其他衍生類別所繼承的遮蔽元素;陰影元素仍然隱藏<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="93c67-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="93c67-135">覆寫由進一步衍生類別繼承的元素;覆寫的元素仍然被覆寫</span><span class="sxs-lookup"><span data-stu-id="93c67-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="93c67-136"><sup>1</sup> *呼叫序列*是由元素類型（ `Function` 、 `Sub` 、 `Operator` 或 `Property` ）、名稱、參數清單和傳回類型所組成。</span><span class="sxs-lookup"><span data-stu-id="93c67-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="93c67-137">您不能使用屬性來覆寫程式，也無法以另一種方式來覆寫。</span><span class="sxs-lookup"><span data-stu-id="93c67-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="93c67-138">您不能以另一種方法覆寫一種程式（ `Function` 、 `Sub` 或 `Operator` ）。</span><span class="sxs-lookup"><span data-stu-id="93c67-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="93c67-139"><sup>2</sup>如果您未指定 `Shadows` 或，則 `Overrides` 編譯器會發出警告訊息，協助您確定要使用哪種重新定義。</span><span class="sxs-lookup"><span data-stu-id="93c67-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="93c67-140">如果您忽略此警告，則會使用遮蔽機制。</span><span class="sxs-lookup"><span data-stu-id="93c67-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="93c67-141"><sup>3</sup>如果在進一步的衍生類別中無法存取遮蔽元素，則不會繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="93c67-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="93c67-142">例如，如果您將遮蔽專案宣告為 `Private` ，衍生自衍生類別的類別會繼承原始專案，而不是遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="93c67-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="93c67-143">指導方針</span><span class="sxs-lookup"><span data-stu-id="93c67-143">Guidelines</span></span>  
 <span data-ttu-id="93c67-144">在下列情況下，您通常會使用覆寫：</span><span class="sxs-lookup"><span data-stu-id="93c67-144">You normally use overriding in the following cases:</span></span>  
  
- <span data-ttu-id="93c67-145">您正在定義多型的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="93c67-145">You are defining polymorphic derived classes.</span></span>  
  
- <span data-ttu-id="93c67-146">您想要讓編譯器強制執行完全相同的元素類型和呼叫順序的安全性。</span><span class="sxs-lookup"><span data-stu-id="93c67-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="93c67-147">在下列情況下，您通常會使用遮蔽：</span><span class="sxs-lookup"><span data-stu-id="93c67-147">You normally use shadowing in the following cases:</span></span>  
  
- <span data-ttu-id="93c67-148">您預期您的基類可能已修改，並使用與您相同的名稱來定義元素。</span><span class="sxs-lookup"><span data-stu-id="93c67-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
- <span data-ttu-id="93c67-149">您想要能夠自由變更元素類型或呼叫順序。</span><span class="sxs-lookup"><span data-stu-id="93c67-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c67-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93c67-150">See also</span></span>

- [<span data-ttu-id="93c67-151">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="93c67-151">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="93c67-152">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="93c67-152">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="93c67-153">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="93c67-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="93c67-154">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="93c67-154">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="93c67-155">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="93c67-155">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="93c67-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="93c67-156">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="93c67-157">覆寫</span><span class="sxs-lookup"><span data-stu-id="93c67-157">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
