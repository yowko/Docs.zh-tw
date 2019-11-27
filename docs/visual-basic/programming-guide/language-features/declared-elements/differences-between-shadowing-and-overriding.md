---
title: 遮蔽和覆寫的差異
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345422"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="14a04-102">遮蔽和覆寫的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14a04-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="14a04-103">當您定義繼承自基類的類別時，您有時會想要重新定義衍生類別中的一個或多個基類元素。</span><span class="sxs-lookup"><span data-stu-id="14a04-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="14a04-104">遮蔽和覆寫皆可用於此用途。</span><span class="sxs-lookup"><span data-stu-id="14a04-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="14a04-105">比較</span><span class="sxs-lookup"><span data-stu-id="14a04-105">Comparison</span></span>  
 <span data-ttu-id="14a04-106">當衍生類別繼承基類時，會使用遮蔽和覆寫，而這兩個專案都是以另一個宣告的專案重新定義。</span><span class="sxs-lookup"><span data-stu-id="14a04-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="14a04-107">但是兩者之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="14a04-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="14a04-108">下表會比較與覆寫的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="14a04-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="14a04-109">比較點</span><span class="sxs-lookup"><span data-stu-id="14a04-109">Point of comparison</span></span>|<span data-ttu-id="14a04-110">遮蔽</span><span class="sxs-lookup"><span data-stu-id="14a04-110">Shadowing</span></span>|<span data-ttu-id="14a04-111">覆寫</span><span class="sxs-lookup"><span data-stu-id="14a04-111">Overriding</span></span>|  
|<span data-ttu-id="14a04-112">目的</span><span class="sxs-lookup"><span data-stu-id="14a04-112">Purpose</span></span>|<span data-ttu-id="14a04-113">防止後續的基類修改，引進您已在衍生類別中定義的成員。</span><span class="sxs-lookup"><span data-stu-id="14a04-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="14a04-114">藉由定義具有相同呼叫順序<sup>1</sup>的程式或屬性的不同執行，來達到多型</span><span class="sxs-lookup"><span data-stu-id="14a04-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="14a04-115">已重新定義元素</span><span class="sxs-lookup"><span data-stu-id="14a04-115">Redefined element</span></span>|<span data-ttu-id="14a04-116">任何宣告的元素類型</span><span class="sxs-lookup"><span data-stu-id="14a04-116">Any declared element type</span></span>|<span data-ttu-id="14a04-117">只有程式（`Function`、`Sub`或 `Operator`）或屬性</span><span class="sxs-lookup"><span data-stu-id="14a04-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="14a04-118">重新定義元素</span><span class="sxs-lookup"><span data-stu-id="14a04-118">Redefining element</span></span>|<span data-ttu-id="14a04-119">任何宣告的元素類型</span><span class="sxs-lookup"><span data-stu-id="14a04-119">Any declared element type</span></span>|<span data-ttu-id="14a04-120">只有具有相同呼叫順序<sup>1</sup>的程式或屬性</span><span class="sxs-lookup"><span data-stu-id="14a04-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="14a04-121">重新定義元素的存取層級</span><span class="sxs-lookup"><span data-stu-id="14a04-121">Access level of redefining element</span></span>|<span data-ttu-id="14a04-122">任何存取層級</span><span class="sxs-lookup"><span data-stu-id="14a04-122">Any access level</span></span>|<span data-ttu-id="14a04-123">無法變更覆寫元素的存取層級</span><span class="sxs-lookup"><span data-stu-id="14a04-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="14a04-124">重新定義元素的可讀性和可寫性</span><span class="sxs-lookup"><span data-stu-id="14a04-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="14a04-125">任何組合</span><span class="sxs-lookup"><span data-stu-id="14a04-125">Any combination</span></span>|<span data-ttu-id="14a04-126">無法變更覆寫屬性的可讀性或可寫性</span><span class="sxs-lookup"><span data-stu-id="14a04-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="14a04-127">控制重新定義</span><span class="sxs-lookup"><span data-stu-id="14a04-127">Control over redefining</span></span>|<span data-ttu-id="14a04-128">基類元素無法強制或禁止遮蔽</span><span class="sxs-lookup"><span data-stu-id="14a04-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="14a04-129">基類元素可以指定 `MustOverride`、`NotOverridable`或 `Overridable`</span><span class="sxs-lookup"><span data-stu-id="14a04-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="14a04-130">關鍵字使用方式</span><span class="sxs-lookup"><span data-stu-id="14a04-130">Keyword usage</span></span>|<span data-ttu-id="14a04-131">建議在衍生類別中 `Shadows`;`Shadows` 假設 `Shadows` 或 `Overrides` 都未指定<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="14a04-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="14a04-132">在基類中需要 `Overridable` 或 `MustOverride`;衍生類別中需要 `Overrides`</span><span class="sxs-lookup"><span data-stu-id="14a04-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="14a04-133">繼承自衍生類別之類別的重新定義元素</span><span class="sxs-lookup"><span data-stu-id="14a04-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="14a04-134">其他衍生類別所繼承的遮蔽元素;陰影元素仍然隱藏<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="14a04-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="14a04-135">覆寫由進一步衍生類別繼承的元素;覆寫的元素仍然被覆寫</span><span class="sxs-lookup"><span data-stu-id="14a04-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="14a04-136"><sup>1</sup> *呼叫序列*是由元素類型（`Function`、`Sub`、`Operator`或 `Property`）、名稱、參數清單和傳回類型所組成。</span><span class="sxs-lookup"><span data-stu-id="14a04-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="14a04-137">您不能使用屬性來覆寫程式，也無法以另一種方式來覆寫。</span><span class="sxs-lookup"><span data-stu-id="14a04-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="14a04-138">您不能以另一種方法覆寫一種程式（`Function`、`Sub`或 `Operator`）。</span><span class="sxs-lookup"><span data-stu-id="14a04-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="14a04-139"><sup>2</sup>如果您未指定 `Shadows` 或 `Overrides`，則編譯器會發出警告訊息，協助您確定要使用哪種重新定義。</span><span class="sxs-lookup"><span data-stu-id="14a04-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="14a04-140">如果您忽略此警告，則會使用遮蔽機制。</span><span class="sxs-lookup"><span data-stu-id="14a04-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="14a04-141"><sup>3</sup>如果在進一步的衍生類別中無法存取遮蔽元素，則不會繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="14a04-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="14a04-142">例如，如果您將遮蔽專案宣告為 `Private`，衍生自衍生類別的類別會繼承原始專案，而不是遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="14a04-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="14a04-143">方針</span><span class="sxs-lookup"><span data-stu-id="14a04-143">Guidelines</span></span>  
 <span data-ttu-id="14a04-144">在下列情況下，您通常會使用覆寫：</span><span class="sxs-lookup"><span data-stu-id="14a04-144">You normally use overriding in the following cases:</span></span>  
  
- <span data-ttu-id="14a04-145">您正在定義多型的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="14a04-145">You are defining polymorphic derived classes.</span></span>  
  
- <span data-ttu-id="14a04-146">您想要讓編譯器強制執行完全相同的元素類型和呼叫順序的安全性。</span><span class="sxs-lookup"><span data-stu-id="14a04-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="14a04-147">在下列情況下，您通常會使用遮蔽：</span><span class="sxs-lookup"><span data-stu-id="14a04-147">You normally use shadowing in the following cases:</span></span>  
  
- <span data-ttu-id="14a04-148">您預期您的基類可能已修改，並使用與您相同的名稱來定義元素。</span><span class="sxs-lookup"><span data-stu-id="14a04-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
- <span data-ttu-id="14a04-149">您想要能夠自由變更元素類型或呼叫順序。</span><span class="sxs-lookup"><span data-stu-id="14a04-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a04-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="14a04-150">See also</span></span>

- [<span data-ttu-id="14a04-151">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="14a04-151">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="14a04-152">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="14a04-152">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="14a04-153">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="14a04-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="14a04-154">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="14a04-154">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="14a04-155">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="14a04-155">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="14a04-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="14a04-156">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="14a04-157">Overrides</span><span class="sxs-lookup"><span data-stu-id="14a04-157">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
