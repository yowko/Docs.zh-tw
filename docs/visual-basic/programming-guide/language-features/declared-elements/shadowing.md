---
title: 遮蔽
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266881"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="cf946-102">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="cf946-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="cf946-103">當兩個程式設計元素共用相同的名稱時，其中一個元素可以隱藏或*隱藏*另一個。</span><span class="sxs-lookup"><span data-stu-id="cf946-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="cf946-104">在這種情況下，陰影元素不能供參考;相反，當代碼使用元素名稱時，Visual Basic 編譯器會將其解析為隱藏元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="cf946-105">目的</span><span class="sxs-lookup"><span data-stu-id="cf946-105">Purpose</span></span>  
 <span data-ttu-id="cf946-106">陰影的主要目的是保護類成員的定義。</span><span class="sxs-lookup"><span data-stu-id="cf946-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="cf946-107">基類可能會經歷一個更改，該更改創建與已定義的元素同名的元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="cf946-108">如果發生這種情況，`Shadows`修改器將強制通過類的引用解析為您定義的成員，而不是新的基類元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="cf946-109">陰影類型</span><span class="sxs-lookup"><span data-stu-id="cf946-109">Types of Shadowing</span></span>  
 <span data-ttu-id="cf946-110">元素可以通過兩種不同的方式隱藏另一個元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="cf946-111">陰影元素可以在包含陰影元素的區域的次區域內聲明，在這種情況下，陰影*是通過作用域*完成的。</span><span class="sxs-lookup"><span data-stu-id="cf946-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="cf946-112">或者派生類可以重新定義基類的成員，在這種情況下，陰影*是通過繼承*來完成的。</span><span class="sxs-lookup"><span data-stu-id="cf946-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="cf946-113">陰影範圍</span><span class="sxs-lookup"><span data-stu-id="cf946-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="cf946-114">同一模組、類或結構中的程式設計元素可以具有相同的名稱但範圍不同。</span><span class="sxs-lookup"><span data-stu-id="cf946-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="cf946-115">以這種方式聲明兩個元素並且代碼引用它們共用的名稱時，具有較窄範圍的元素會陰影另一個元素（塊作用域是最窄的）。</span><span class="sxs-lookup"><span data-stu-id="cf946-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="cf946-116">例如，模組可以定義名為 的`Public``temp`變數，模組中的過程可以聲明也命名為 的`temp`區域變數。</span><span class="sxs-lookup"><span data-stu-id="cf946-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="cf946-117">從過程`temp`內部對的引用訪問區域變數，而從過程外部`temp`的引用訪問`Public`該變數。</span><span class="sxs-lookup"><span data-stu-id="cf946-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="cf946-118">在這種情況下，過程變數`temp`對模組變數`temp`進行陰影。</span><span class="sxs-lookup"><span data-stu-id="cf946-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="cf946-119">下圖顯示了兩個變數，這兩個變數`temp`都命名為 。</span><span class="sxs-lookup"><span data-stu-id="cf946-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="cf946-120">當從其`temp`自己的過程中`p`訪問成員`temp`變數時，區域變數將隱藏成員變數。</span><span class="sxs-lookup"><span data-stu-id="cf946-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="cf946-121">但是，`MyClass`關鍵字繞過陰影並訪問成員變數。</span><span class="sxs-lookup"><span data-stu-id="cf946-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![顯示陰影範圍的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="cf946-123">有關在作用域中隱藏的示例，請參閱[如何：隱藏與變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="cf946-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="cf946-124">通過繼承進行陰影</span><span class="sxs-lookup"><span data-stu-id="cf946-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="cf946-125">如果派生類重新定義從基類繼承的程式設計元素，則重新定義元素將隱藏原始元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="cf946-126">可以使用任何其他類型隱藏任何類型的聲明元素或一組重載元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="cf946-127">例如，`Integer`變數可以隱藏`Function`過程。</span><span class="sxs-lookup"><span data-stu-id="cf946-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="cf946-128">如果使用另一個過程對過程進行陰影，則可以使用不同的參數清單和不同的返回類型。</span><span class="sxs-lookup"><span data-stu-id="cf946-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="cf946-129">下圖顯示了從`b``b`繼承的基類和派生類`d`。</span><span class="sxs-lookup"><span data-stu-id="cf946-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="cf946-130">基類定義名為 的過程`proc`，派生類使用另一個同名過程來隱藏它。</span><span class="sxs-lookup"><span data-stu-id="cf946-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="cf946-131">第一`Call`個語句訪問派生類中的`proc`陰影。</span><span class="sxs-lookup"><span data-stu-id="cf946-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="cf946-132">但是，`MyBase`關鍵字繞過陰影並訪問基類中的隱藏過程。</span><span class="sxs-lookup"><span data-stu-id="cf946-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="cf946-134">有關通過繼承進行陰影的示例，請參閱[如何：隱藏與變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)以及如何[：隱藏繼承變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="cf946-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="cf946-135">陰影和存取層級</span><span class="sxs-lookup"><span data-stu-id="cf946-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="cf946-136">使用派生類的代碼並不總是可以訪問陰影元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="cf946-137">例如，它可能聲明`Private`。</span><span class="sxs-lookup"><span data-stu-id="cf946-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="cf946-138">在這種情況下，陰影將失敗，編譯器解析對如果沒有陰影時的相同元素的任何引用。</span><span class="sxs-lookup"><span data-stu-id="cf946-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="cf946-139">此元素是從陰影類向後派生最少的可訪問元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="cf946-140">如果隱藏元素是過程，則解析度是最接近的可訪問版本，具有相同的名稱、參數清單和返回類型。</span><span class="sxs-lookup"><span data-stu-id="cf946-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="cf946-141">下面的示例顯示了三個類的繼承層次結構。</span><span class="sxs-lookup"><span data-stu-id="cf946-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="cf946-142">每個類定義一個`Sub`過程`display`，每個派生類在其基類`display`中隱藏該過程。</span><span class="sxs-lookup"><span data-stu-id="cf946-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="cf946-143">在前面的示例中，派生類`secondClass`陰影`display`帶有一個`Private`過程。</span><span class="sxs-lookup"><span data-stu-id="cf946-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="cf946-144">當模組`callDisplay`調用`display``secondClass`時，調用代碼位於外部`secondClass`，因此無法訪問私有`display`過程。</span><span class="sxs-lookup"><span data-stu-id="cf946-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="cf946-145">隱藏將失敗，編譯器解析對基類`display`過程的引用。</span><span class="sxs-lookup"><span data-stu-id="cf946-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="cf946-146">但是，進一步的派生`thirdClass`類聲明`display`為`Public`，因此 中`callDisplay`的代碼可以訪問它。</span><span class="sxs-lookup"><span data-stu-id="cf946-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="cf946-147">陰影和覆蓋</span><span class="sxs-lookup"><span data-stu-id="cf946-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="cf946-148">不要混淆陰影和重寫。</span><span class="sxs-lookup"><span data-stu-id="cf946-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="cf946-149">當派生類從基類繼承時，兩者都使用，並且都與另一個類重新定義一個聲明的元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="cf946-150">但兩者之間存在顯著差異。</span><span class="sxs-lookup"><span data-stu-id="cf946-150">But there are significant differences between the two.</span></span> <span data-ttu-id="cf946-151">有關比較，請參閱[陰影和覆蓋之間的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。</span><span class="sxs-lookup"><span data-stu-id="cf946-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="cf946-152">陰影和重載</span><span class="sxs-lookup"><span data-stu-id="cf946-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="cf946-153">如果對派生類中具有多個元素的同一基類元素進行陰影，則陰影元素將成為該元素的重載版本。</span><span class="sxs-lookup"><span data-stu-id="cf946-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="cf946-154">如需詳細資訊，請參閱 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="cf946-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="cf946-155">訪問隱藏元素</span><span class="sxs-lookup"><span data-stu-id="cf946-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="cf946-156">當您從派生類訪問元素時，通常通過派生類的當前實例，通過`Me`用 關鍵字限定元素名稱來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="cf946-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="cf946-157">如果派生類對基類中的元素造成陰影，則可以通過使用`MyBase`關鍵字限定基類元素來訪問該元素元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="cf946-158">有關訪問隱藏元素的示例，請參閱[如何：訪問派生類隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="cf946-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="cf946-159">物件變數的聲明</span><span class="sxs-lookup"><span data-stu-id="cf946-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="cf946-160">創建物件變數的方式還可以影響派生類是訪問陰影元素還是隱影元素。</span><span class="sxs-lookup"><span data-stu-id="cf946-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="cf946-161">下面的示例從派生類創建兩個物件，但一個物件聲明為基類，另一個物件聲明為派生類。</span><span class="sxs-lookup"><span data-stu-id="cf946-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="cf946-162">在前面的示例中，變數`basObj`聲明為基類。</span><span class="sxs-lookup"><span data-stu-id="cf946-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="cf946-163">向其分配`dervCls`物件構成擴大轉換，因此有效。</span><span class="sxs-lookup"><span data-stu-id="cf946-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="cf946-164">但是，基類無法訪問派生類中變數`z`的隱藏版本，因此編譯器解析`basObj.z`為原始基類值。</span><span class="sxs-lookup"><span data-stu-id="cf946-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf946-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf946-165">See also</span></span>

- [<span data-ttu-id="cf946-166">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="cf946-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="cf946-167">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="cf946-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="cf946-168">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="cf946-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="cf946-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="cf946-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="cf946-170">重寫</span><span class="sxs-lookup"><span data-stu-id="cf946-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="cf946-171">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="cf946-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="cf946-172">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="cf946-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
