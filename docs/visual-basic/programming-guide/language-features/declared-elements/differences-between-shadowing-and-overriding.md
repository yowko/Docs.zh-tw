---
title: 遮蔽和覆寫的差異 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 94ce3e7fe25b7942730e6e89a53654b03d91c42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649629"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="84919-102">遮蔽和覆寫的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84919-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="84919-103">當您定義類別繼承自基底類別時，您有時會想要重新定義一或多個衍生類別中的基底類別項目。</span><span class="sxs-lookup"><span data-stu-id="84919-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="84919-104">遮蔽和覆寫都可供此目的。</span><span class="sxs-lookup"><span data-stu-id="84919-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="84919-105">比較</span><span class="sxs-lookup"><span data-stu-id="84919-105">Comparison</span></span>  
 <span data-ttu-id="84919-106">遮蔽和覆寫同時使用當在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="84919-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="84919-107">但有兩個重大差異。</span><span class="sxs-lookup"><span data-stu-id="84919-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="84919-108">下表比較遮蔽和覆寫。</span><span class="sxs-lookup"><span data-stu-id="84919-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="84919-109">比較點</span><span class="sxs-lookup"><span data-stu-id="84919-109">Point of comparison</span></span>|<span data-ttu-id="84919-110">遮蔽</span><span class="sxs-lookup"><span data-stu-id="84919-110">Shadowing</span></span>|<span data-ttu-id="84919-111">覆寫</span><span class="sxs-lookup"><span data-stu-id="84919-111">Overriding</span></span>|  
|<span data-ttu-id="84919-112">用途</span><span class="sxs-lookup"><span data-stu-id="84919-112">Purpose</span></span>|<span data-ttu-id="84919-113">防止後續的基底類別修改引入您已定義在衍生類別中的成員</span><span class="sxs-lookup"><span data-stu-id="84919-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="84919-114">藉由定義不同的實作程序或屬性具有相同的呼叫順序達成多型<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="84919-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="84919-115">已重新定義的項目</span><span class="sxs-lookup"><span data-stu-id="84919-115">Redefined element</span></span>|<span data-ttu-id="84919-116">任何宣告項目類型</span><span class="sxs-lookup"><span data-stu-id="84919-116">Any declared element type</span></span>|<span data-ttu-id="84919-117">程序 (`Function`， `Sub`，或`Operator`) 或屬性</span><span class="sxs-lookup"><span data-stu-id="84919-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="84919-118">重新定義項目</span><span class="sxs-lookup"><span data-stu-id="84919-118">Redefining element</span></span>|<span data-ttu-id="84919-119">任何宣告項目類型</span><span class="sxs-lookup"><span data-stu-id="84919-119">Any declared element type</span></span>|<span data-ttu-id="84919-120">只有程序或屬性具有相同的呼叫順序<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="84919-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="84919-121">存取層級的重新定義項目</span><span class="sxs-lookup"><span data-stu-id="84919-121">Access level of redefining element</span></span>|<span data-ttu-id="84919-122">任何存取層級</span><span class="sxs-lookup"><span data-stu-id="84919-122">Any access level</span></span>|<span data-ttu-id="84919-123">無法變更存取層級覆寫的元素</span><span class="sxs-lookup"><span data-stu-id="84919-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="84919-124">閱讀，並重新定義項目的可寫性</span><span class="sxs-lookup"><span data-stu-id="84919-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="84919-125">任何組合</span><span class="sxs-lookup"><span data-stu-id="84919-125">Any combination</span></span>|<span data-ttu-id="84919-126">無法變更可讀性或可寫性的覆寫屬性</span><span class="sxs-lookup"><span data-stu-id="84919-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="84919-127">重新定義的控制</span><span class="sxs-lookup"><span data-stu-id="84919-127">Control over redefining</span></span>|<span data-ttu-id="84919-128">無法在強制執行或禁止遮蔽基底類別項目</span><span class="sxs-lookup"><span data-stu-id="84919-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="84919-129">可以指定基底類別項目`MustOverride`， `NotOverridable`，或 `Overridable`</span><span class="sxs-lookup"><span data-stu-id="84919-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="84919-130">關鍵字的使用方式</span><span class="sxs-lookup"><span data-stu-id="84919-130">Keyword usage</span></span>|<span data-ttu-id="84919-131">`Shadows` 衍生類別中的建議`Shadows`假設如果兩者皆非`Shadows`也`Overrides`指定<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="84919-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="84919-132">`Overridable` 或`MustOverride`所需要的基底類別; 事件類別`Overrides`衍生類別中所需</span><span class="sxs-lookup"><span data-stu-id="84919-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="84919-133">繼承的類別衍生自您的衍生類別重新定義項目</span><span class="sxs-lookup"><span data-stu-id="84919-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="84919-134">遮蔽項目繼承進一步衍生的類別。遮蔽的項目仍然隱藏<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="84919-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="84919-135">覆寫項目所繼承的進一步衍生的類別。覆寫的元素，還是覆寫</span><span class="sxs-lookup"><span data-stu-id="84919-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="84919-136"><sup>1</sup> *呼叫順序*組成的項目類型 (`Function`， `Sub`， `Operator`，或`Property`)、 名稱、 參數清單和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="84919-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="84919-137">您無法覆寫屬性或利用其他方式的程序。</span><span class="sxs-lookup"><span data-stu-id="84919-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="84919-138">您無法覆寫程序的一種 (`Function`， `Sub`，或`Operator`) 與另一種。</span><span class="sxs-lookup"><span data-stu-id="84919-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="84919-139"><sup>2</sup>如果您未指定`Shadows`或`Overrides`，編譯器會發出警告訊息，以協助您務必要使用哪種重複定義。</span><span class="sxs-lookup"><span data-stu-id="84919-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="84919-140">如果您忽略此警告，則會使用遮蔽的機制。</span><span class="sxs-lookup"><span data-stu-id="84919-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="84919-141"><sup>3</sup>進一步衍生類別中無法存取遮蔽項目是否不繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="84919-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="84919-142">例如，如果您宣告遮蔽的項目，做為`Private`，從您的衍生類別中衍生的類別會繼承原始項目，而不是遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="84919-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="84919-143">方針</span><span class="sxs-lookup"><span data-stu-id="84919-143">Guidelines</span></span>  
 <span data-ttu-id="84919-144">您通常用在下列情況下覆寫：</span><span class="sxs-lookup"><span data-stu-id="84919-144">You normally use overriding in the following cases:</span></span>  
  
-   <span data-ttu-id="84919-145">您正在定義多型的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="84919-145">You are defining polymorphic derived classes.</span></span>  
  
-   <span data-ttu-id="84919-146">您想讓編譯器強制執行相同的項目類型和呼叫順序的安全性。</span><span class="sxs-lookup"><span data-stu-id="84919-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="84919-147">您通常用在下列情況中的遮蔽功能：</span><span class="sxs-lookup"><span data-stu-id="84919-147">You normally use shadowing in the following cases:</span></span>  
  
-   <span data-ttu-id="84919-148">您預期基底類別可能會被修改，並定義為您使用相同名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="84919-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
-   <span data-ttu-id="84919-149">您想要變更的項目類型，或呼叫順序自由。</span><span class="sxs-lookup"><span data-stu-id="84919-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84919-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84919-150">See Also</span></span>  
 [<span data-ttu-id="84919-151">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="84919-151">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="84919-152">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="84919-152">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="84919-153">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="84919-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="84919-154">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="84919-154">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="84919-155">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="84919-155">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="84919-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="84919-156">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="84919-157">Overrides</span><span class="sxs-lookup"><span data-stu-id="84919-157">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
