---
title: "Visual Basic 中的遮蔽功能"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbfce3edc122ca875552b2d41ba876fe5cfcfc4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="a41ce-102">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="a41ce-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="a41ce-103">當兩個的程式設計項目共用相同的名稱時，可以隱藏其中一個，或*陰影*，另一個。</span><span class="sxs-lookup"><span data-stu-id="a41ce-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="a41ce-104">在這種情況下，加上陰影的項目不是可參考。相反地，當您的程式碼使用的項目名稱，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器解析遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="a41ce-105">用途</span><span class="sxs-lookup"><span data-stu-id="a41ce-105">Purpose</span></span>  
 <span data-ttu-id="a41ce-106">遮蔽的主要目的是要保護的定義類別成員。</span><span class="sxs-lookup"><span data-stu-id="a41ce-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="a41ce-107">基底類別可能進行的變更，建立名稱與您已定義的名稱相同的項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="a41ce-108">如果發生這種情況，`Shadows`修飾詞強制參考您要解析為成員的類別透過您定義的而不是新的基底類別項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="a41ce-109">遮蔽的型別</span><span class="sxs-lookup"><span data-stu-id="a41ce-109">Types of Shadowing</span></span>  
 <span data-ttu-id="a41ce-110">項目可遮蔽另一個項目以兩個不同的方式。</span><span class="sxs-lookup"><span data-stu-id="a41ce-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="a41ce-111">遮蔽的項目可以包含陰影的項目，遮蔽的案例來達成區域的子區域內宣告*透過範圍*。</span><span class="sxs-lookup"><span data-stu-id="a41ce-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="a41ce-112">衍生的類別可以重新定義基底類別，是案例遮蔽的成員或者*透過繼承*。</span><span class="sxs-lookup"><span data-stu-id="a41ce-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="a41ce-113">透過範圍遮蔽</span><span class="sxs-lookup"><span data-stu-id="a41ce-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="a41ce-114">它是讓程式設計中相同的模組、 類別或結構有相同名稱但不同範圍的項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="a41ce-115">當以這種方式宣告兩個項目，程式碼參照到它們共用的名稱具有較小範圍的項目會遮蔽另一個項目 （區塊範圍最小）。</span><span class="sxs-lookup"><span data-stu-id="a41ce-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="a41ce-116">例如，可以定義模組`Public`名為變數`temp`，而且在模組中的程序可以宣告本機變數，也稱為`temp`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="a41ce-117">若要參考`temp`從程序存取的本機變數的參考時`temp`從外部程序存取`Public`變數。</span><span class="sxs-lookup"><span data-stu-id="a41ce-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="a41ce-118">在此情況下，程序變數`temp`遮蔽模組變數`temp`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="a41ce-119">下圖顯示兩個變數，名為`temp`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="a41ce-120">本機變數`temp`遮蔽的成員變數`temp`時從自己的程序內存取`p`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="a41ce-121">不過，`MyClass`關鍵字略過遮蔽和存取的成員變數。</span><span class="sxs-lookup"><span data-stu-id="a41ce-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="a41ce-122">![透過範圍遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="a41ce-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="a41ce-123">透過範圍遮蔽</span><span class="sxs-lookup"><span data-stu-id="a41ce-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="a41ce-124">如需透過範圍遮蔽的範例，請參閱[如何： 隱藏與您變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="a41ce-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="a41ce-125">透過繼承遮蔽</span><span class="sxs-lookup"><span data-stu-id="a41ce-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="a41ce-126">如果在衍生的類別重新定義繼承自基底類別的程式設計項目，則重新定義的項目會遮蔽原始項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="a41ce-127">您可以使用任何其他類型遮蔽任何一種宣告的項目或集合的多載的項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="a41ce-128">例如，`Integer`變數可以遮蔽`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="a41ce-129">如果您要遮蔽另一個程序的程序，您可以使用不同的參數清單和傳回類型不同。</span><span class="sxs-lookup"><span data-stu-id="a41ce-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="a41ce-130">下圖顯示基底類別`b`和衍生的類別`d`繼承自`b`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="a41ce-131">基底類別會定義名為程序`proc`，並在衍生的類別可遮蔽它具有相同名稱的另一個程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="a41ce-132">第一個`Call`陳述式可讓您存取遮蔽`proc`衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="a41ce-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="a41ce-133">不過，`MyBase`關鍵字略過遮蔽和存取基底類別中加上陰影的程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="a41ce-134">![透過繼承遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="a41ce-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="a41ce-135">透過繼承遮蔽</span><span class="sxs-lookup"><span data-stu-id="a41ce-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="a41ce-136">如需透過繼承遮蔽的範例，請參閱[如何： 隱藏與您變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)和[如何： 隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="a41ce-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="a41ce-137">遮蔽和存取層級</span><span class="sxs-lookup"><span data-stu-id="a41ce-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="a41ce-138">遮蔽的項目不一定可從使用衍生的類別的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="a41ce-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="a41ce-139">例如，可能會宣告`Private`。</span><span class="sxs-lookup"><span data-stu-id="a41ce-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="a41ce-140">在這種情況下，若要遮蔽會失敗，則編譯器會解析就會相同項目的任何參考如果有任何遮蔽。</span><span class="sxs-lookup"><span data-stu-id="a41ce-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="a41ce-141">此元素為可以存取最少衍生步驟向後從遮蔽類別的項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="a41ce-142">如果加上陰影的項目為程序，解析為最接近的可存取版本具有相同名稱，也就是參數清單和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="a41ce-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="a41ce-143">下列範例示範三個類別的繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="a41ce-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="a41ce-144">每個類別會定義`Sub`程序`display`，以及每個衍生類別陰影`display`其基底類別中的程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```  
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
  
 <span data-ttu-id="a41ce-145">在上述範例中，在衍生類別中`secondClass`陰影`display`與`Private`程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="a41ce-146">當模組`callDisplay`呼叫`display`中`secondClass`，呼叫程式碼超出`secondClass`因此無法存取私用`display`程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="a41ce-147">遮蔽會失敗，並編譯器解析參考的基底類別`display`程序。</span><span class="sxs-lookup"><span data-stu-id="a41ce-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="a41ce-148">不過，進一步衍生類別`thirdClass`宣告`display`為`Public`，因此中的程式碼`callDisplay`可以存取它。</span><span class="sxs-lookup"><span data-stu-id="a41ce-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="a41ce-149">遮蔽和覆寫</span><span class="sxs-lookup"><span data-stu-id="a41ce-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="a41ce-150">請勿混淆遮蔽和覆寫。</span><span class="sxs-lookup"><span data-stu-id="a41ce-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="a41ce-151">在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目時，會使用這兩項目。</span><span class="sxs-lookup"><span data-stu-id="a41ce-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="a41ce-152">但有兩個重大差異。</span><span class="sxs-lookup"><span data-stu-id="a41ce-152">But there are significant differences between the two.</span></span> <span data-ttu-id="a41ce-153">如需比較，請參閱[差異之間遮蔽和覆](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。</span><span class="sxs-lookup"><span data-stu-id="a41ce-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="a41ce-154">遮蔽和多載化</span><span class="sxs-lookup"><span data-stu-id="a41ce-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="a41ce-155">如果您在衍生類別中遮蔽具有多個項目相同的基底類別項目，遮蔽的項目會變成該元素的多載的版本。</span><span class="sxs-lookup"><span data-stu-id="a41ce-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="a41ce-156">如需詳細資訊，請參閱[程序多載](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="a41ce-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="a41ce-157">存取遮蔽的項目</span><span class="sxs-lookup"><span data-stu-id="a41ce-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="a41ce-158">當您從衍生類別中存取項目時，您通常要透過目前的執行個體的衍生類別，來限定項目名稱與`Me`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a41ce-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="a41ce-159">如果您在衍生的類別會遮蔽基底類別中的項目，您可以存取的基底類別項目來限定它與`MyBase`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a41ce-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="a41ce-160">如需的存取遮蔽的項目範例，請參閱[如何： 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="a41ce-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="a41ce-161">物件變數的宣告</span><span class="sxs-lookup"><span data-stu-id="a41ce-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="a41ce-162">在衍生的類別存取遮蔽項目或遮蔽的項目是否也會影響您建立的物件變數的方式。</span><span class="sxs-lookup"><span data-stu-id="a41ce-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="a41ce-163">下列範例會建立兩個物件從衍生類別，但一個物件宣告為基底類別和另一個則為衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="a41ce-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```  
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
  
 <span data-ttu-id="a41ce-164">在上述範例中，變數`basObj`宣告的基底類別。</span><span class="sxs-lookup"><span data-stu-id="a41ce-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="a41ce-165">指派`dervCls`物件傳送給它構成擴展轉換，因此無效。</span><span class="sxs-lookup"><span data-stu-id="a41ce-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="a41ce-166">不過，基底類別無法存取遮蔽版本的變數`z`在衍生類別中，因此編譯器會解析`basObj.z`原始基底類別值。</span><span class="sxs-lookup"><span data-stu-id="a41ce-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a41ce-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a41ce-167">See Also</span></span>  
 [<span data-ttu-id="a41ce-168">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="a41ce-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="a41ce-169">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="a41ce-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="a41ce-170">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="a41ce-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="a41ce-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="a41ce-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="a41ce-172">Overrides</span><span class="sxs-lookup"><span data-stu-id="a41ce-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="a41ce-173">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="a41ce-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="a41ce-174">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="a41ce-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
