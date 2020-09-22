---
title: Class 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 3b64597fcd7453c20ed295fe263eeaa8783b20ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866035"
---
# <a name="class-statement-visual-basic"></a><span data-ttu-id="3fec7-102">Class 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fec7-102">Class Statement (Visual Basic)</span></span>

<span data-ttu-id="3fec7-103">宣告類別的名稱，並引進類別所組成之變數、屬性、事件和程式的定義。</span><span class="sxs-lookup"><span data-stu-id="3fec7-103">Declares the name of a class and introduces the definition of the variables, properties, events, and procedures that the class comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fec7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3fec7-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a><span data-ttu-id="3fec7-105">組件</span><span class="sxs-lookup"><span data-stu-id="3fec7-105">Parts</span></span>  
  
|<span data-ttu-id="3fec7-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3fec7-106">Term</span></span>|<span data-ttu-id="3fec7-107">定義</span><span class="sxs-lookup"><span data-stu-id="3fec7-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="3fec7-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-108">Optional.</span></span> <span data-ttu-id="3fec7-109">請參閱 [屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="3fec7-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-110">Optional.</span></span> <span data-ttu-id="3fec7-111">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3fec7-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="3fec7-112">-   [公共](../modifiers/public.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-112">-   [Public](../modifiers/public.md)</span></span><br /><span data-ttu-id="3fec7-113">-   [保護](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-113">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="3fec7-114">-   [朋友](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-114">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="3fec7-115">-   [私人](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-115">-   [Private](../modifiers/private.md)</span></span><br /><span data-ttu-id="3fec7-116">-   [受保護的 Friend](../modifiers/protected-friend.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-116">-   [Protected Friend](../modifiers/protected-friend.md)</span></span><br /><span data-ttu-id="3fec7-117">- [私用保護](../modifiers/private-protected.md)</span><span class="sxs-lookup"><span data-stu-id="3fec7-117">- [Private Protected](../modifiers/private-protected.md)</span></span><br/><br/> <span data-ttu-id="3fec7-118">請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-118">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="3fec7-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-119">Optional.</span></span> <span data-ttu-id="3fec7-120">請參閱 [陰影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-120">See [Shadows](../modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="3fec7-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-121">Optional.</span></span> <span data-ttu-id="3fec7-122">請參閱 [MustInherit](../modifiers/mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-122">See [MustInherit](../modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="3fec7-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-123">Optional.</span></span> <span data-ttu-id="3fec7-124">請參閱 [NotInheritable](../modifiers/notinheritable.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-124">See [NotInheritable](../modifiers/notinheritable.md).</span></span>|  
|`Partial`|<span data-ttu-id="3fec7-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-125">Optional.</span></span> <span data-ttu-id="3fec7-126">指出類別的部分定義。</span><span class="sxs-lookup"><span data-stu-id="3fec7-126">Indicates a partial definition of the class.</span></span> <span data-ttu-id="3fec7-127">請參閱 [部分](../modifiers/partial.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-127">See [Partial](../modifiers/partial.md).</span></span>|  
|`name`|<span data-ttu-id="3fec7-128">必要。</span><span class="sxs-lookup"><span data-stu-id="3fec7-128">Required.</span></span> <span data-ttu-id="3fec7-129">此類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fec7-129">Name of this class.</span></span> <span data-ttu-id="3fec7-130">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-130">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`Of`|<span data-ttu-id="3fec7-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-131">Optional.</span></span> <span data-ttu-id="3fec7-132">指定這是泛型類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-132">Specifies that this is a generic class.</span></span>|  
|`typelist`|<span data-ttu-id="3fec7-133">如果您使用 of 關鍵字，則 [為必要項](of-clause.md) 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-133">Required if you use the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="3fec7-134">此類別的型別參數清單。</span><span class="sxs-lookup"><span data-stu-id="3fec7-134">List of type parameters for this class.</span></span> <span data-ttu-id="3fec7-135">請參閱 [類型清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-135">See [Type List](type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="3fec7-136">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-136">Optional.</span></span> <span data-ttu-id="3fec7-137">指出這個類別會繼承另一個類別的成員。</span><span class="sxs-lookup"><span data-stu-id="3fec7-137">Indicates that this class inherits the members of another class.</span></span> <span data-ttu-id="3fec7-138">請參閱 [繼承語句](inherits-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-138">See [Inherits Statement](inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="3fec7-139">如果您使用語句，則為必要 `Inherits` 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-139">Required if you use the `Inherits` statement.</span></span> <span data-ttu-id="3fec7-140">這個類別所衍生的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="3fec7-140">The name of the class from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="3fec7-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-141">Optional.</span></span> <span data-ttu-id="3fec7-142">指出這個類別會執行一個或多個介面的成員。</span><span class="sxs-lookup"><span data-stu-id="3fec7-142">Indicates that this class implements the members of one or more interfaces.</span></span> <span data-ttu-id="3fec7-143">請參閱 [Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-143">See [Implements Statement](implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="3fec7-144">如果您使用語句，則為必要 `Implements` 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-144">Required if you use the `Implements` statement.</span></span> <span data-ttu-id="3fec7-145">這個類別所執行的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="3fec7-145">The names of the interfaces this class implements.</span></span>|  
|`statements`|<span data-ttu-id="3fec7-146">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3fec7-146">Optional.</span></span> <span data-ttu-id="3fec7-147">定義這個類別成員的語句。</span><span class="sxs-lookup"><span data-stu-id="3fec7-147">Statements which define the members of this class.</span></span>|  
|`End Class`|<span data-ttu-id="3fec7-148">必要。</span><span class="sxs-lookup"><span data-stu-id="3fec7-148">Required.</span></span> <span data-ttu-id="3fec7-149">結束 `Class` 定義。</span><span class="sxs-lookup"><span data-stu-id="3fec7-149">Terminates the `Class` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fec7-150">備註</span><span class="sxs-lookup"><span data-stu-id="3fec7-150">Remarks</span></span>  

 <span data-ttu-id="3fec7-151">`Class`語句會定義新的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3fec7-151">A `Class` statement defines a new data type.</span></span> <span data-ttu-id="3fec7-152">*類別*是物件導向程式設計的基本組建區塊， (OOP) 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-152">A *class* is a fundamental building block of object-oriented programming (OOP).</span></span> <span data-ttu-id="3fec7-153">如需詳細資訊，請參閱 [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-153">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
 <span data-ttu-id="3fec7-154">您 `Class` 只能在命名空間或模組層級使用。</span><span class="sxs-lookup"><span data-stu-id="3fec7-154">You can use `Class` only at namespace or module level.</span></span> <span data-ttu-id="3fec7-155">這表示類別的宣告 *內容* 必須是原始程式檔、命名空間、類別、結構、模組或介面，且不能是程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="3fec7-155">This means the *declaration context* for a class must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure or block.</span></span> <span data-ttu-id="3fec7-156">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-156">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3fec7-157">類別的每個實例都有與其他所有實例無關的存留期。</span><span class="sxs-lookup"><span data-stu-id="3fec7-157">Each instance of a class has a lifetime independent of all other instances.</span></span> <span data-ttu-id="3fec7-158">當這個存留期是由 [新的 Operator](../operators/new-operator.md) 子句或像這樣的函式建立時，就會開始 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-158">This lifetime begins when it is created by a [New Operator](../operators/new-operator.md) clause or by a function such as <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>.</span></span> <span data-ttu-id="3fec7-159">當所有指向實例的變數都已設定為 [Nothing](../nothing.md) 或其他類別的實例時，就會結束。</span><span class="sxs-lookup"><span data-stu-id="3fec7-159">It ends when all variables pointing to the instance have been set to [Nothing](../nothing.md) or to instances of other classes.</span></span>  
  
 <span data-ttu-id="3fec7-160">類別預設為 [Friend](../modifiers/friend.md) 存取。</span><span class="sxs-lookup"><span data-stu-id="3fec7-160">Classes default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="3fec7-161">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="3fec7-161">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="3fec7-162">如需詳細資訊，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-162">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3fec7-163">規則</span><span class="sxs-lookup"><span data-stu-id="3fec7-163">Rules</span></span>  
  
- <span data-ttu-id="3fec7-164">**嵌 套。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-164">**Nesting.**</span></span> <span data-ttu-id="3fec7-165">您可以在另一個類別中定義一個類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-165">You can define one class within another.</span></span> <span data-ttu-id="3fec7-166">外部類別稱為「包含」 *類別*，而內部類別稱為「 *嵌套類別」（nested class*）。</span><span class="sxs-lookup"><span data-stu-id="3fec7-166">The outer class is called the *containing class*, and the inner class is called a *nested class*.</span></span>  
  
- <span data-ttu-id="3fec7-167">**繼承。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-167">**Inheritance.**</span></span> <span data-ttu-id="3fec7-168">如果類別使用 [Inherits 語句](inherits-statement.md)，您只能指定一個基類或介面。</span><span class="sxs-lookup"><span data-stu-id="3fec7-168">If the class uses the [Inherits Statement](inherits-statement.md), you can specify only one base class or interface.</span></span> <span data-ttu-id="3fec7-169">類別不能繼承自一個以上的元素。</span><span class="sxs-lookup"><span data-stu-id="3fec7-169">A class cannot inherit from more than one element.</span></span>  
  
     <span data-ttu-id="3fec7-170">類別無法繼承自另一個具有較嚴格存取層級的類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-170">A class cannot inherit from another class with a more restrictive access level.</span></span> <span data-ttu-id="3fec7-171">例如， `Public` 類別無法繼承自 `Friend` 類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-171">For example, a `Public` class cannot inherit from a `Friend` class.</span></span>  
  
     <span data-ttu-id="3fec7-172">類別無法繼承自其內嵌套的類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-172">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="3fec7-173">**實現。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-173">**Implementation.**</span></span> <span data-ttu-id="3fec7-174">如果類別使用 [Implements 語句](implements-statement.md)，則您必須執行您在中指定的每個介面所定義的每個成員 `interfacenames` 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-174">If the class uses the [Implements Statement](implements-statement.md), you must implement every member defined by every interface you specify in `interfacenames`.</span></span> <span data-ttu-id="3fec7-175">例外狀況是基類成員的重新實作。</span><span class="sxs-lookup"><span data-stu-id="3fec7-175">An exception to this is reimplementation of a base class member.</span></span> <span data-ttu-id="3fec7-176">如需詳細資訊，請參閱 [Implements](implements-clause.md)中的 "重新實作"。</span><span class="sxs-lookup"><span data-stu-id="3fec7-176">For more information, see "Reimplementation" in [Implements](implements-clause.md).</span></span>  
  
- <span data-ttu-id="3fec7-177">**Default 屬性。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-177">**Default Property.**</span></span> <span data-ttu-id="3fec7-178">類別可以指定最多一個屬性做為其 *預設屬性*。</span><span class="sxs-lookup"><span data-stu-id="3fec7-178">A class can specify at most one property as its *default property*.</span></span> <span data-ttu-id="3fec7-179">如需詳細資訊，請參閱 [Default](../modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-179">For more information, see [Default](../modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3fec7-180">行為</span><span class="sxs-lookup"><span data-stu-id="3fec7-180">Behavior</span></span>  
  
- <span data-ttu-id="3fec7-181">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-181">**Access Level.**</span></span> <span data-ttu-id="3fec7-182">在類別內，您可以使用自己的存取層級來宣告每個成員。</span><span class="sxs-lookup"><span data-stu-id="3fec7-182">Within a class, you can declare each member with its own access level.</span></span> <span data-ttu-id="3fec7-183">類別成員預設為 [公用](../modifiers/public.md) 存取，但變數和常數除外，預設為 [私](../modifiers/private.md) 用存取。</span><span class="sxs-lookup"><span data-stu-id="3fec7-183">Class members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="3fec7-184">當類別的存取權多於其其中一個成員時，就會優先使用類別存取層級。</span><span class="sxs-lookup"><span data-stu-id="3fec7-184">When a class has more restricted access than one of its members, the class access level takes precedence.</span></span>  
  
- <span data-ttu-id="3fec7-185">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-185">**Scope.**</span></span> <span data-ttu-id="3fec7-186">類別在其內含命名空間、類別、結構或模組的範圍內。</span><span class="sxs-lookup"><span data-stu-id="3fec7-186">A class is in scope throughout its containing namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="3fec7-187">每個類別成員的範圍都是整個類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-187">The scope of every class member is the entire class.</span></span>  
  
     <span data-ttu-id="3fec7-188">**一生。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-188">**Lifetime.**</span></span> <span data-ttu-id="3fec7-189">Visual Basic 不支援靜態類別。</span><span class="sxs-lookup"><span data-stu-id="3fec7-189">Visual Basic does not support static classes.</span></span> <span data-ttu-id="3fec7-190">靜態類別的功能對等專案是由模組所提供。</span><span class="sxs-lookup"><span data-stu-id="3fec7-190">The functional equivalent of a static class is provided by a module.</span></span> <span data-ttu-id="3fec7-191">如需詳細資訊，請參閱 [Module 語句](module-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-191">For more information, see [Module Statement](module-statement.md).</span></span>  
  
     <span data-ttu-id="3fec7-192">類別成員有存留期，視其宣告的方式和位置而定。</span><span class="sxs-lookup"><span data-stu-id="3fec7-192">Class members have lifetimes depending on how and where they are declared.</span></span> <span data-ttu-id="3fec7-193">如需詳細資訊，請參閱 [Visual Basic 中的存留期](../../programming-guide/language-features/declared-elements/lifetime.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-193">For more information, see [Lifetime in Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
- <span data-ttu-id="3fec7-194">**資格。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-194">**Qualification.**</span></span> <span data-ttu-id="3fec7-195">類別外部的程式碼必須以該類別的名稱來限定成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fec7-195">Code outside a class must qualify a member's name with the name of that class.</span></span>  
  
     <span data-ttu-id="3fec7-196">如果嵌套類別內的程式碼會對程式設計專案進行不合格的參考，Visual Basic 會先在嵌套類別中搜尋專案，然後在其包含類別中搜尋專案，依此類推到最外層的包含元素。</span><span class="sxs-lookup"><span data-stu-id="3fec7-196">If code inside a nested class makes an unqualified reference to a programming element, Visual Basic searches for the element first in the nested class, then in its containing class, and so on out to the outermost containing element.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="3fec7-197">類別和模組</span><span class="sxs-lookup"><span data-stu-id="3fec7-197">Classes and Modules</span></span>  

 <span data-ttu-id="3fec7-198">這些元素有許多相似之處，但也有一些重要的差異。</span><span class="sxs-lookup"><span data-stu-id="3fec7-198">These elements have many similarities, but there are some important differences as well.</span></span>  
  
- <span data-ttu-id="3fec7-199">**術語：**</span><span class="sxs-lookup"><span data-stu-id="3fec7-199">**Terminology.**</span></span> <span data-ttu-id="3fec7-200">舊版的 Visual Basic 會辨識兩種類型的模組： *類別模組* ( 的 cls 檔) 和 *標準模組* ( bas 檔案) 。</span><span class="sxs-lookup"><span data-stu-id="3fec7-200">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="3fec7-201">目前版本會分別呼叫這些 *類別* 和 *模組*。</span><span class="sxs-lookup"><span data-stu-id="3fec7-201">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
- <span data-ttu-id="3fec7-202">**共用成員。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-202">**Shared Members.**</span></span> <span data-ttu-id="3fec7-203">您可以控制類別的成員是否為共用成員或實例成員。</span><span class="sxs-lookup"><span data-stu-id="3fec7-203">You can control whether a member of a class is a shared or instance member.</span></span>  
  
- <span data-ttu-id="3fec7-204">**物件方向。**</span><span class="sxs-lookup"><span data-stu-id="3fec7-204">**Object Orientation.**</span></span> <span data-ttu-id="3fec7-205">類別是物件導向，但模組則不是。</span><span class="sxs-lookup"><span data-stu-id="3fec7-205">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="3fec7-206">您可以建立一個或多個類別的實例。</span><span class="sxs-lookup"><span data-stu-id="3fec7-206">You can create one or more instances of a class.</span></span> <span data-ttu-id="3fec7-207">如需詳細資訊，請參閱 [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec7-207">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fec7-208">範例</span><span class="sxs-lookup"><span data-stu-id="3fec7-208">Example</span></span>  

 <span data-ttu-id="3fec7-209">下列範例會使用 `Class` 語句來定義類別和數個成員。</span><span class="sxs-lookup"><span data-stu-id="3fec7-209">The following example uses a `Class` statement to define a class and several members.</span></span>  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a><span data-ttu-id="3fec7-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fec7-210">See also</span></span>

- [<span data-ttu-id="3fec7-211">物件和類別</span><span class="sxs-lookup"><span data-stu-id="3fec7-211">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3fec7-212">結構與類別</span><span class="sxs-lookup"><span data-stu-id="3fec7-212">Structures and Classes</span></span>](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="3fec7-213">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="3fec7-213">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="3fec7-214">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="3fec7-214">Module Statement</span></span>](module-statement.md)
- [<span data-ttu-id="3fec7-215">Property Statement</span><span class="sxs-lookup"><span data-stu-id="3fec7-215">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="3fec7-216">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="3fec7-216">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="3fec7-217">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fec7-217">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="3fec7-218">作法：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="3fec7-218">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
