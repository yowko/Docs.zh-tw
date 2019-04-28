---
title: 遮蔽和覆寫的差異 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61827940"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="0731a-102">遮蔽和覆寫的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0731a-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="0731a-103">當您定義繼承自基底類別的類別時，您有時會想要重新定義一或多個基底類別中的項目衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0731a-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="0731a-104">遮蔽和覆寫都可針對此目的。</span><span class="sxs-lookup"><span data-stu-id="0731a-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="0731a-105">邏輯比對</span><span class="sxs-lookup"><span data-stu-id="0731a-105">Comparison</span></span>  
 <span data-ttu-id="0731a-106">遮蔽和覆寫同時使用當在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="0731a-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="0731a-107">但兩者之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="0731a-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="0731a-108">下表比較遮蔽和覆寫。</span><span class="sxs-lookup"><span data-stu-id="0731a-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="0731a-109">相較之下</span><span class="sxs-lookup"><span data-stu-id="0731a-109">Point of comparison</span></span>|<span data-ttu-id="0731a-110">遮蔽</span><span class="sxs-lookup"><span data-stu-id="0731a-110">Shadowing</span></span>|<span data-ttu-id="0731a-111">覆寫</span><span class="sxs-lookup"><span data-stu-id="0731a-111">Overriding</span></span>|  
|<span data-ttu-id="0731a-112">用途</span><span class="sxs-lookup"><span data-stu-id="0731a-112">Purpose</span></span>|<span data-ttu-id="0731a-113">防止後續的基底類別修改，將會介紹您已定義在衍生類別中的成員</span><span class="sxs-lookup"><span data-stu-id="0731a-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="0731a-114">藉由定義的程序或屬性具有相同的呼叫順序的不同實作，達到多型<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0731a-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="0731a-115">已重新定義的項目</span><span class="sxs-lookup"><span data-stu-id="0731a-115">Redefined element</span></span>|<span data-ttu-id="0731a-116">任何宣告項目類型</span><span class="sxs-lookup"><span data-stu-id="0731a-116">Any declared element type</span></span>|<span data-ttu-id="0731a-117">程序 (`Function`， `Sub`，或`Operator`) 或屬性</span><span class="sxs-lookup"><span data-stu-id="0731a-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="0731a-118">重新定義的項目</span><span class="sxs-lookup"><span data-stu-id="0731a-118">Redefining element</span></span>|<span data-ttu-id="0731a-119">任何宣告項目類型</span><span class="sxs-lookup"><span data-stu-id="0731a-119">Any declared element type</span></span>|<span data-ttu-id="0731a-120">只有程序或屬性具有相同的呼叫順序<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0731a-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="0731a-121">存取層級的重新定義項目</span><span class="sxs-lookup"><span data-stu-id="0731a-121">Access level of redefining element</span></span>|<span data-ttu-id="0731a-122">任何存取層級</span><span class="sxs-lookup"><span data-stu-id="0731a-122">Any access level</span></span>|<span data-ttu-id="0731a-123">無法變更存取層級覆寫的項目</span><span class="sxs-lookup"><span data-stu-id="0731a-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="0731a-124">可讀性和可寫性的重新定義項目</span><span class="sxs-lookup"><span data-stu-id="0731a-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="0731a-125">任何組合</span><span class="sxs-lookup"><span data-stu-id="0731a-125">Any combination</span></span>|<span data-ttu-id="0731a-126">無法變更可讀性或可寫性的覆寫的屬性</span><span class="sxs-lookup"><span data-stu-id="0731a-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="0731a-127">重新定義的控制</span><span class="sxs-lookup"><span data-stu-id="0731a-127">Control over redefining</span></span>|<span data-ttu-id="0731a-128">基底類別項目無法強制執行，或禁止的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="0731a-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="0731a-129">基底類別項目可以指定`MustOverride`， `NotOverridable`，或 `Overridable`</span><span class="sxs-lookup"><span data-stu-id="0731a-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="0731a-130">關鍵字的使用方式</span><span class="sxs-lookup"><span data-stu-id="0731a-130">Keyword usage</span></span>|<span data-ttu-id="0731a-131">`Shadows` 在衍生類別中的建議`Shadows`假設如果都不`Shadows`也不`Overrides`指定<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0731a-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="0731a-132">`Overridable` 或`MustOverride`所需要的基底類別;`Overrides`衍生類別中所需</span><span class="sxs-lookup"><span data-stu-id="0731a-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="0731a-133">繼承的類別衍生自您的衍生類別中重新定義項目</span><span class="sxs-lookup"><span data-stu-id="0731a-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="0731a-134">遮蔽項目繼承進一步衍生的類別;遮蔽的項目仍然隱藏<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0731a-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="0731a-135">覆寫項目繼承進一步衍生的類別;覆寫的元素，還是覆寫</span><span class="sxs-lookup"><span data-stu-id="0731a-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="0731a-136"><sup>1</sup> *呼叫順序*項目類型所組成 (`Function`， `Sub`， `Operator`，或`Property`)、 名稱、 參數 清單中，並傳回型別。</span><span class="sxs-lookup"><span data-stu-id="0731a-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="0731a-137">您無法覆寫屬性或利用其他方式的程序。</span><span class="sxs-lookup"><span data-stu-id="0731a-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="0731a-138">您無法覆寫程序的一種 (`Function`， `Sub`，或`Operator`) 與另一種。</span><span class="sxs-lookup"><span data-stu-id="0731a-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="0731a-139"><sup>2</sup>如果您未指定其中一個`Shadows`或`Overrides`，編譯器會發出一則警告訊息可協助您確定要使用哪一種重複定義。</span><span class="sxs-lookup"><span data-stu-id="0731a-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="0731a-140">如果您忽略此警告，則會使用遮蔽的機制。</span><span class="sxs-lookup"><span data-stu-id="0731a-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="0731a-141"><sup>3</sup>進一步衍生類別中無法存取遮蔽項目時，無法繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="0731a-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="0731a-142">例如，如果您宣告遮蔽的項目，做為`Private`，衍生自您的衍生類別繼承原始的項目，而非遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="0731a-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="0731a-143">方針</span><span class="sxs-lookup"><span data-stu-id="0731a-143">Guidelines</span></span>  
 <span data-ttu-id="0731a-144">您通常會使用覆寫在下列情況：</span><span class="sxs-lookup"><span data-stu-id="0731a-144">You normally use overriding in the following cases:</span></span>  
  
- <span data-ttu-id="0731a-145">您會定義多型的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0731a-145">You are defining polymorphic derived classes.</span></span>  
  
- <span data-ttu-id="0731a-146">您想讓編譯器強制的完全相同的項目類型和呼叫順序的安全。</span><span class="sxs-lookup"><span data-stu-id="0731a-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="0731a-147">您通常會使用下列案例中的遮蔽功能：</span><span class="sxs-lookup"><span data-stu-id="0731a-147">You normally use shadowing in the following cases:</span></span>  
  
- <span data-ttu-id="0731a-148">您預期可能會修改基底類別，並定義為您使用相同名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="0731a-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
- <span data-ttu-id="0731a-149">您想要能夠變更的項目類型，或呼叫順序。</span><span class="sxs-lookup"><span data-stu-id="0731a-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0731a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0731a-150">See also</span></span>

- [<span data-ttu-id="0731a-151">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="0731a-151">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="0731a-152">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="0731a-152">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="0731a-153">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="0731a-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="0731a-154">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="0731a-154">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="0731a-155">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="0731a-155">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="0731a-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="0731a-156">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="0731a-157">Overrides</span><span class="sxs-lookup"><span data-stu-id="0731a-157">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
