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
ms.openlocfilehash: 81e54875a3c1a4bbc5f5631e7ebac649a2e5afaf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085889"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="8a203-102">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="8a203-102">Shadowing in Visual Basic</span></span>

<span data-ttu-id="8a203-103">當兩個程式設計專案共用相同的名稱時，其中一個元素可以隱藏或 *遮蔽*另一個。</span><span class="sxs-lookup"><span data-stu-id="8a203-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="8a203-104">在這種情況下，隱藏的元素無法供參考;相反地，當您的程式碼使用專案名稱時，Visual Basic 編譯器會將它解析成遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="8a203-105">目的</span><span class="sxs-lookup"><span data-stu-id="8a203-105">Purpose</span></span>  

 <span data-ttu-id="8a203-106">遮蔽的主要目的是保護您類別成員的定義。</span><span class="sxs-lookup"><span data-stu-id="8a203-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="8a203-107">基類可能會進行變更，以建立名稱與您已定義的專案相同的專案。</span><span class="sxs-lookup"><span data-stu-id="8a203-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="8a203-108">如果發生這種情況， `Shadows` 修飾詞會強制將透過您類別的參考解析為您定義的成員，而不是新的基類元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="8a203-109">遮蔽的類型</span><span class="sxs-lookup"><span data-stu-id="8a203-109">Types of Shadowing</span></span>  

 <span data-ttu-id="8a203-110">元素可以用兩種不同的方式來遮蔽另一個元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="8a203-111">您可以在包含已遮蔽元素之區域的子領域內宣告遮蔽元素，在此情況下，會 *透過範圍*來完成遮蔽。</span><span class="sxs-lookup"><span data-stu-id="8a203-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="8a203-112">或衍生類別可以重新定義基類的成員，在這種情況下，會 *透過繼承*來完成遮蔽。</span><span class="sxs-lookup"><span data-stu-id="8a203-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="8a203-113">透過範圍遮蔽</span><span class="sxs-lookup"><span data-stu-id="8a203-113">Shadowing Through Scope</span></span>  

 <span data-ttu-id="8a203-114">相同模組、類別或結構中的程式設計專案，有可能具有相同名稱但不同的範圍。</span><span class="sxs-lookup"><span data-stu-id="8a203-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="8a203-115">當以這種方式宣告兩個元素，且程式碼參考它們共用的名稱時，具有較窄範圍的專案會遮蔽其他元素 (區塊範圍是最小的) 。</span><span class="sxs-lookup"><span data-stu-id="8a203-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="8a203-116">例如，模組可以定義一個 `Public` 名為的變數 `temp` ，而模組內的程式可以宣告也名為的本機變數 `temp` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="8a203-117">從程式內部的參考會 `temp` 存取區域變數，而從程式外部的參考則會 `temp` 存取 `Public` 變數。</span><span class="sxs-lookup"><span data-stu-id="8a203-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="8a203-118">在此情況下，程式變數會 `temp` 遮蔽模組變數 `temp` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="8a203-119">下圖顯示兩個名為的變數 `temp` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="8a203-120">區域變數會在 `temp` `temp` 從其本身的程式中存取時，遮蔽成員變數 `p` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="8a203-121">不過， `MyClass` 關鍵字會略過遮蔽並存取成員變數。</span><span class="sxs-lookup"><span data-stu-id="8a203-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![透過範圍顯示遮蔽的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="8a203-123">如需透過範圍進行遮蔽的範例，請參閱 [如何：隱藏與您變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="8a203-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="8a203-124">透過繼承進行遮蔽</span><span class="sxs-lookup"><span data-stu-id="8a203-124">Shadowing Through Inheritance</span></span>  

 <span data-ttu-id="8a203-125">如果衍生類別重新定義繼承自基類的程式設計專案，重新定義的元素會遮蔽原始專案。</span><span class="sxs-lookup"><span data-stu-id="8a203-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="8a203-126">您可以使用任何其他類型來遮蔽任何類型的宣告專案或一組多載的元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="8a203-127">例如， `Integer` 變數可以遮蔽程式 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="8a203-128">如果您使用另一個程式來遮蔽程式，則可以使用不同的參數清單和不同的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="8a203-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="8a203-129">下圖顯示繼承自的基類 `b` 和衍生類別 `d` `b` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="8a203-130">基類會定義名為的程式 `proc` ，而衍生的類別會使用相同名稱的另一個程式來將它隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="8a203-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="8a203-131">第一個 `Call` 語句會存取 `proc` 衍生類別中的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="8a203-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="8a203-132">不過， `MyBase` 關鍵字會略過遮蔽並存取基類中的陰影程式。</span><span class="sxs-lookup"><span data-stu-id="8a203-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="8a203-134">如需透過繼承進行遮蔽的範例，請參閱 [如何：隱藏變數與您變數的名稱相同](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ，以及 [如何：隱藏繼承的變數](how-to-hide-an-inherited-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="8a203-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="8a203-135">遮蔽和存取層級</span><span class="sxs-lookup"><span data-stu-id="8a203-135">Shadowing and Access Level</span></span>  

 <span data-ttu-id="8a203-136">使用衍生類別的程式碼不一定可以存取遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="8a203-137">例如，可能會宣告它 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="8a203-138">在這種情況下，遮蔽會失效，而編譯器會在沒有任何遮蔽的情況下，解析對相同元素的任何參考。</span><span class="sxs-lookup"><span data-stu-id="8a203-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="8a203-139">這個元素是可存取的元素，最少的 derivational 步驟會從遮蔽類別回溯。</span><span class="sxs-lookup"><span data-stu-id="8a203-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="8a203-140">如果遮蔽的元素是程式，則解析度會是使用相同名稱、參數清單和傳回類型的最接近可存取版本。</span><span class="sxs-lookup"><span data-stu-id="8a203-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="8a203-141">下列範例顯示三個類別的繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="8a203-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="8a203-142">每個類別都會定義一個程式 `Sub` `display` ，而每個衍生的類別會將程式隱藏 `display` 在其基類中。</span><span class="sxs-lookup"><span data-stu-id="8a203-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="8a203-143">在上述範例中，衍生的類別 `secondClass` 會 `display` 以程式進行遮蔽 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="8a203-144">當模組 `callDisplay` `display` 在中呼叫時 `secondClass` ，呼叫程式碼會在外部， `secondClass` 因此無法存取私 `display` 用程式。</span><span class="sxs-lookup"><span data-stu-id="8a203-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="8a203-145">遮蔽會失效，而編譯器會解析基類程式的參考 `display` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="8a203-146">不過，進一步衍生的類別 `thirdClass` 會將宣告 `display` 為 `Public` ，讓中的程式碼 `callDisplay` 可以存取它。</span><span class="sxs-lookup"><span data-stu-id="8a203-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="8a203-147">遮蔽和覆寫</span><span class="sxs-lookup"><span data-stu-id="8a203-147">Shadowing and Overriding</span></span>  

 <span data-ttu-id="8a203-148">請勿將遮蔽與覆寫混淆。</span><span class="sxs-lookup"><span data-stu-id="8a203-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="8a203-149">當衍生類別繼承自基類時，會使用這兩種方式，而且這兩個專案都會以另一個宣告的專案來重新定義。</span><span class="sxs-lookup"><span data-stu-id="8a203-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="8a203-150">但是兩者之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="8a203-150">But there are significant differences between the two.</span></span> <span data-ttu-id="8a203-151">如需比較，請參閱 [遮蔽和覆寫之間的差異](differences-between-shadowing-and-overriding.md)。</span><span class="sxs-lookup"><span data-stu-id="8a203-151">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="8a203-152">遮蔽和多載</span><span class="sxs-lookup"><span data-stu-id="8a203-152">Shadowing and Overloading</span></span>  

 <span data-ttu-id="8a203-153">如果您使用衍生類別中的多個專案來遮蔽相同的基類元素，則遮蔽專案會成為該元素的多載版本。</span><span class="sxs-lookup"><span data-stu-id="8a203-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="8a203-154">如需詳細資訊，請參閱 [Procedure Overloading](../procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="8a203-154">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="8a203-155">存取已遮蔽的元素</span><span class="sxs-lookup"><span data-stu-id="8a203-155">Accessing a Shadowed Element</span></span>  

 <span data-ttu-id="8a203-156">當您從衍生類別存取專案時，通常是透過該衍生類別的目前實例來執行此作業，方法是使用關鍵字來限定元素名稱 `Me` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="8a203-157">如果您的衍生類別遮蔽基類中的專案，您可以藉由使用關鍵字來限定基類元素來存取它 `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="8a203-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="8a203-158">如需存取隱藏專案的範例，請參閱 [如何：存取衍生類別所隱藏的變數](how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="8a203-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="8a203-159">物件變數的宣告</span><span class="sxs-lookup"><span data-stu-id="8a203-159">Declaration of the Object Variable</span></span>  

 <span data-ttu-id="8a203-160">您建立物件變數的方式也會影響衍生的類別是否會存取遮蔽專案或遮蔽的元素。</span><span class="sxs-lookup"><span data-stu-id="8a203-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="8a203-161">下列範例會從衍生類別建立兩個物件，但一個物件宣告為基類，另一個則做為衍生類別。</span><span class="sxs-lookup"><span data-stu-id="8a203-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="8a203-162">在上述範例中，變數 `basObj` 會宣告為基類。</span><span class="sxs-lookup"><span data-stu-id="8a203-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="8a203-163">將 `dervCls` 物件指派給它會構成擴輾轉換，因此有效。</span><span class="sxs-lookup"><span data-stu-id="8a203-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="8a203-164">不過，基類無法存取衍生類別中之變數的遮蔽版本 `z` ，因此編譯器會解析 `basObj.z` 為原始基類值。</span><span class="sxs-lookup"><span data-stu-id="8a203-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a203-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a203-165">See also</span></span>

- [<span data-ttu-id="8a203-166">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="8a203-166">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="8a203-167">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="8a203-167">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="8a203-168">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="8a203-168">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8a203-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="8a203-169">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="8a203-170">覆寫</span><span class="sxs-lookup"><span data-stu-id="8a203-170">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="8a203-171">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="8a203-171">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="8a203-172">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="8a203-172">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
