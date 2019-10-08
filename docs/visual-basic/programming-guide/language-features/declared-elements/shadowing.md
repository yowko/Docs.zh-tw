---
title: Visual Basic 中的遮蔽功能
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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004862"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="b1bc0-102">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="b1bc0-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="b1bc0-103">當兩個程式設計項目共用相同名稱時，其中一個專案可以隱藏或*遮蔽*另一個。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="b1bc0-104">在這種情況下，陰影元素無法供參考;相反地，當您的程式碼使用元素名稱時，Visual Basic 編譯器會將它解析成遮蔽專案。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="b1bc0-105">用途</span><span class="sxs-lookup"><span data-stu-id="b1bc0-105">Purpose</span></span>  
 <span data-ttu-id="b1bc0-106">遮蔽的主要目的是保護類別成員的定義。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="b1bc0-107">基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="b1bc0-108">如果發生這種情況，`Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="b1bc0-109">遮蔽的類型</span><span class="sxs-lookup"><span data-stu-id="b1bc0-109">Types of Shadowing</span></span>  
 <span data-ttu-id="b1bc0-110">元素可以用兩種不同的方式來遮蔽另一個專案。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="b1bc0-111">遮蔽專案可以在包含陰影專案之區域的子領域內宣告，在此情況下，遮蔽會*透過範圍*來完成。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="b1bc0-112">或者，衍生類別可以重新定義基類的成員，在這種情況下，會*透過繼承*來完成遮蔽。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="b1bc0-113">透過範圍遮蔽</span><span class="sxs-lookup"><span data-stu-id="b1bc0-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="b1bc0-114">相同模組、類別或結構中的程式設計專案可能具有相同的名稱，但範圍不同。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="b1bc0-115">當以這種方式宣告兩個專案，且程式碼參考其共用的名稱時，具有較窄範圍的元素會遮蔽另一個元素（區塊範圍是最小的）。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="b1bc0-116">例如，模組可以定義名為 `temp` 的 @no__t 0 變數，而模組內的程式可以宣告名為 `temp` 的本機變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="b1bc0-117">從程式內對 `temp` 的參考會存取本機變數，而從程式外部對 `temp` 的參考則會存取 `Public` 變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="b1bc0-118">在此情況下，程式變數 `temp` 會將模組變數遮蔽 `temp`。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="b1bc0-119">下圖顯示兩個名為 `temp` 的變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="b1bc0-120">本機變數 `temp` 會在從本身的程式中存取時，將成員變數從 `temp` 遮蔽 `p`。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="b1bc0-121">不過，`MyClass` 關鍵字會略過遮蔽並存取成員變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![顯示透過範圍遮蔽的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="b1bc0-123">如需透過範圍進行遮蔽的範例，請參閱 [How 至：隱藏名稱與變數 @ no__t-0 相同的變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="b1bc0-124">透過繼承進行遮蔽</span><span class="sxs-lookup"><span data-stu-id="b1bc0-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="b1bc0-125">如果衍生類別重新定義繼承自基類的程式設計專案，重新定義元素會遮蔽原始專案。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="b1bc0-126">您可以使用任何其他類型來遮蔽任何類型的已宣告元素或多載專案集。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="b1bc0-127">例如，@no__t 0 變數可以遮蔽 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="b1bc0-128">如果您使用另一個程式來遮蔽程式，則可以使用不同的參數清單和不同的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="b1bc0-129">下圖顯示基類 `b`，以及繼承自 `b` 的衍生類別 `d`。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="b1bc0-130">基類會定義名為 `proc` 的程式，而衍生的類別會使用相同名稱的另一個程式來遮蔽它。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="b1bc0-131">第一個 `Call` 語句會存取衍生類別中的遮蔽 `proc`。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="b1bc0-132">不過，`MyBase` 關鍵字會略過遮蔽，並存取基類中的陰影程式。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="b1bc0-134">如需透過繼承進行遮蔽的範例，請參閱 [How to：隱藏與您的變數 @ no__t-0 相同的變數，並 @no__t 1How 至：隱藏繼承的變數 @ no__t-0。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="b1bc0-135">遮蔽和存取層級</span><span class="sxs-lookup"><span data-stu-id="b1bc0-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="b1bc0-136">使用衍生類別時，程式碼不一定可以存取遮蔽元素。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="b1bc0-137">例如，它可能會宣告 `Private`。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="b1bc0-138">在這種情況下，遮蔽會失效，而編譯器會解析任何對相同專案的參考（如果沒有任何遮蔽）。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="b1bc0-139">此元素是可存取的元素，這是從遮蔽類別回溯的最少 derivational 步驟。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="b1bc0-140">如果遮蔽的專案是程式，則解決方式會是具有相同名稱、參數清單和傳回類型的最接近可存取版本。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="b1bc0-141">下列範例顯示三個類別的繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="b1bc0-142">每個類別都會定義 `Sub` 程式 `display`，而每個衍生類別都會將 @no__t 2 程式遮蔽在其基類中。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="b1bc0-143">在上述範例中，衍生類別 `secondClass` 陰影 `display` 與 @no__t 2 程式。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="b1bc0-144">當模組 `callDisplay` 在 `secondClass` 中呼叫 `display` 時，呼叫端程式碼會超出 `secondClass`，因此無法存取私用的 `display` 程式。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="b1bc0-145">遮蔽會失效，而編譯器會解析基類的參考 `display` 程式。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="b1bc0-146">不過，進一步衍生的類別 `thirdClass` 會將 `display` 宣告為 `Public`，讓 `callDisplay` 中的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="b1bc0-147">遮蔽和覆寫</span><span class="sxs-lookup"><span data-stu-id="b1bc0-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="b1bc0-148">請勿將遮蔽與覆寫混淆。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="b1bc0-149">當衍生類別繼承自基類時，會使用這兩個專案，而且這兩個專案都是以另一個宣告的元素重新定義。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="b1bc0-150">但是兩者之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-150">But there are significant differences between the two.</span></span> <span data-ttu-id="b1bc0-151">如需比較，請參閱[遮蔽和覆寫之間的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="b1bc0-152">遮蔽和多載</span><span class="sxs-lookup"><span data-stu-id="b1bc0-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="b1bc0-153">如果您在衍生類別中遮蔽具有多個專案的相同基類元素，則遮蔽專案會變成該元素的多載版本。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="b1bc0-154">如需詳細資訊，請參閱 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="b1bc0-155">存取陰影元素</span><span class="sxs-lookup"><span data-stu-id="b1bc0-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="b1bc0-156">當您從衍生類別存取專案時，通常會透過使用 `Me` 關鍵字來限定專案名稱，藉此在該衍生類別的目前實例中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="b1bc0-157">如果您的衍生類別會遮蔽基類中的專案，您可以使用 `MyBase` 關鍵字來限定基類專案，藉以存取該元素。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="b1bc0-158">如需存取遮蔽專案的範例，請參閱 [How to：存取衍生類別 @ no__t-0 所隱藏的變數。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="b1bc0-159">物件變數的宣告</span><span class="sxs-lookup"><span data-stu-id="b1bc0-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="b1bc0-160">您建立物件變數的方式也會影響衍生類別是要存取遮蔽專案還是陰影元素。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="b1bc0-161">下列範例會從衍生類別建立兩個物件，但是一個物件宣告為基類，另一個則做為衍生類別。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="b1bc0-162">在上述範例中，`basObj` 的變數會宣告為基類。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="b1bc0-163">將 @no__t 0 物件指派給它會構成擴輾轉換，因此是有效的。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="b1bc0-164">不過，基類無法存取衍生類別中變數 `z` 的遮蔽版本，因此編譯器會將 `basObj.z` 解析為原始的基類值。</span><span class="sxs-lookup"><span data-stu-id="b1bc0-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bc0-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1bc0-165">See also</span></span>

- [<span data-ttu-id="b1bc0-166">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="b1bc0-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="b1bc0-167">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="b1bc0-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="b1bc0-168">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="b1bc0-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b1bc0-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="b1bc0-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="b1bc0-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="b1bc0-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="b1bc0-171">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b1bc0-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="b1bc0-172">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="b1bc0-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
