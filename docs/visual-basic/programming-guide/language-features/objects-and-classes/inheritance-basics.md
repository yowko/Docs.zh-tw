---
title: 繼承基本概念 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 5e4b8511145e758bf3d6328141be0e526965dccf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826570"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="4fd90-102">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fd90-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="4fd90-103">`Inherits`陳述式用來宣告新的類別，叫做*衍生類別*根據現有的類別，稱為*基底類別*。</span><span class="sxs-lookup"><span data-stu-id="4fd90-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="4fd90-104">在衍生的類別繼承，且可以擴充，屬性、 方法、 事件、 欄位和基底類別中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="4fd90-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="4fd90-105">下節描述一些繼承規則，以及修飾詞，可用來變更方法的類別繼承，或會繼承：</span><span class="sxs-lookup"><span data-stu-id="4fd90-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="4fd90-106">根據預設，除非標記為可繼承的所有類別都都會`NotInheritable`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4fd90-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="4fd90-107">類別可以繼承自其他類別，在您的專案，或從您的專案參考其他組件中的類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="4fd90-108">不同於允許多個繼承的語言，Visual Basic，請允許類別; 中的只有單一繼承也就是在衍生的類別可以有只有一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="4fd90-109">雖然在類別中不允許多重繼承，類別可以實作多個介面，可以有效地達成相同的目的。</span><span class="sxs-lookup"><span data-stu-id="4fd90-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="4fd90-110">若要避免公開受限制的項目中的基底類別，衍生類別的存取類型必須等於或限制性大於其基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="4fd90-111">例如，`Public`類別無法繼承`Friend`或`Private`類別，和`Friend`類別無法繼承`Private`類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="4fd90-112">繼承修飾詞</span><span class="sxs-lookup"><span data-stu-id="4fd90-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="4fd90-113">下列類別層級的陳述式和修飾詞，以支援繼承，導入了 Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="4fd90-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="4fd90-114">`Inherits` 陳述式，指定基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="4fd90-115">`NotInheritable` 修飾詞，可讓程式設計人員使用類別作為基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="4fd90-116">`MustInherit` 修飾詞，指定類別，適用於做為基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="4fd90-117">執行個體`MustInherit`類別不能直接建立; 他們只能建立衍生的類別為基底類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4fd90-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="4fd90-118">(其他程式設計語言，例如C++和C#，使用詞彙*抽象類別*來說明這種類別。)</span><span class="sxs-lookup"><span data-stu-id="4fd90-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="4fd90-119">屬性和方法在衍生類別中的覆寫</span><span class="sxs-lookup"><span data-stu-id="4fd90-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="4fd90-120">根據預設，在衍生的類別會從其基底類別繼承屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="4fd90-121">如果繼承的屬性或方法的衍生類別中有不同的行為很*覆寫*。</span><span class="sxs-lookup"><span data-stu-id="4fd90-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="4fd90-122">也就是說，您可以定義新的實作方法的衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="4fd90-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="4fd90-123">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="4fd90-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="4fd90-124">`Overridable` — 可讓衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="4fd90-125">`Overrides` -覆寫`Overridable`屬性或方法的基底類別中定義。</span><span class="sxs-lookup"><span data-stu-id="4fd90-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="4fd90-126">`NotOverridable` 可防止遭到覆寫繼承的類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="4fd90-127">根據預設，`Public`方法都是`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="4fd90-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="4fd90-128">`MustOverride` -需要在衍生的類別覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="4fd90-129">當`MustOverride`關鍵字時，包含方法定義只`Sub`， `Function`，或`Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fd90-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="4fd90-130">不允許使用任何其他陳述式，而且特別是沒有任何`End Sub`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fd90-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="4fd90-131">`MustOverride` 方法必須宣告在`MustInherit`類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="4fd90-132">假設您想要定義類別，來處理薪資。</span><span class="sxs-lookup"><span data-stu-id="4fd90-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="4fd90-133">您可以定義為泛型`Payroll`類別，其中包含`RunPayroll`計算薪資典型的一週的方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="4fd90-134">您接著可以使用`Payroll`更具特製化的基底類別為`BonusPayroll`散發員工加分時可以使用的類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="4fd90-135">`BonusPayroll`類別可以繼承並覆寫，請`PayEmployee`定義在基底方法`Payroll`類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="4fd90-136">下列範例會定義基底類別`Payroll,`和衍生的類別中， `BonusPayroll`，這會覆寫繼承的方法， `PayEmployee`。</span><span class="sxs-lookup"><span data-stu-id="4fd90-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="4fd90-137">程序中， `RunPayroll`、 建立，並接著傳遞`Payroll`物件並`BonusPayroll`函式物件`Pay`，執行`PayEmployee`這兩個物件的方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="4fd90-138">MyBase 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4fd90-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="4fd90-139">`MyBase`關鍵字的行為就像類別的目前執行個體的基底類別是指的物件變數。</span><span class="sxs-lookup"><span data-stu-id="4fd90-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="4fd90-140">`MyBase` 經常用來存取所覆寫或遮蔽衍生類別中的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="4fd90-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="4fd90-141">特別是，`MyBase.New`用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="4fd90-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="4fd90-142">例如，假設您正在設計衍生的類別會覆寫繼承自基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="4fd90-143">覆寫的方法可以呼叫基底類別中的方法，並修改的傳回值，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="4fd90-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 <span data-ttu-id="4fd90-144">下列清單描述限制使用`MyBase`:</span><span class="sxs-lookup"><span data-stu-id="4fd90-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="4fd90-145">`MyBase` 是指直接基底類別和其繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="4fd90-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="4fd90-146">它不能用來存取`Private`類別中的成員。</span><span class="sxs-lookup"><span data-stu-id="4fd90-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="4fd90-147">`MyBase` 是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="4fd90-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="4fd90-148">`MyBase` 無法指派給變數，傳遞至程序，或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="4fd90-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="4fd90-149">此方法，`MyBase`限定並沒有直接的基底類別; 中定義它可能會改為在間接繼承的基底類別中定義。</span><span class="sxs-lookup"><span data-stu-id="4fd90-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="4fd90-150">為了讓所限定的參考`MyBase`正確編譯，某些基底類別必須包含比對出現在呼叫的參數類型與名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="4fd90-151">您無法使用`MyBase`呼叫`MustOverride`基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="4fd90-152">`MyBase` 不用來限定本身。</span><span class="sxs-lookup"><span data-stu-id="4fd90-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="4fd90-153">因此，下列程式碼不是有效的：</span><span class="sxs-lookup"><span data-stu-id="4fd90-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="4fd90-154">`MyBase` 不能在模組中。</span><span class="sxs-lookup"><span data-stu-id="4fd90-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="4fd90-155">`MyBase` 不能用來存取基底類別成員標記為`Friend`如果基底類別位於不同的組件。</span><span class="sxs-lookup"><span data-stu-id="4fd90-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="4fd90-156">如需詳細資訊和另一個範例，請參閱[How to:存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="4fd90-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="4fd90-157">MyClass 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4fd90-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="4fd90-158">`MyClass`關鍵字的行為就像以原始實作類別的目前執行個體是指的物件變數。</span><span class="sxs-lookup"><span data-stu-id="4fd90-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="4fd90-159">`MyClass` 類似於`Me`，但每個方法和屬性上呼叫`MyClass`會被視為方法或屬性所[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。</span><span class="sxs-lookup"><span data-stu-id="4fd90-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="4fd90-160">因此，不會影響方法或屬性藉由衍生類別中覆寫。</span><span class="sxs-lookup"><span data-stu-id="4fd90-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="4fd90-161">`MyClass` 是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="4fd90-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="4fd90-162">`MyClass` 無法指派給變數，傳遞至程序，或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="4fd90-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="4fd90-163">`MyClass` 是指包含類別和其繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="4fd90-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="4fd90-164">`MyClass` 可用來當做限定詞`Shared`成員。</span><span class="sxs-lookup"><span data-stu-id="4fd90-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="4fd90-165">`MyClass` 不能在`Shared`方法，但是可以在執行個體方法內用來存取共用的成員的類別。</span><span class="sxs-lookup"><span data-stu-id="4fd90-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="4fd90-166">`MyClass` 不能在標準模組。</span><span class="sxs-lookup"><span data-stu-id="4fd90-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="4fd90-167">`MyClass` 可用來限定，定義於基底類別，而該類別中提供的方法沒有實作的方法。</span><span class="sxs-lookup"><span data-stu-id="4fd90-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="4fd90-168">這類參考具有相同的意義`MyBase.`*方法*。</span><span class="sxs-lookup"><span data-stu-id="4fd90-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="4fd90-169">下列範例會比較`Me`和`MyClass`。</span><span class="sxs-lookup"><span data-stu-id="4fd90-169">The following example compares `Me` and `MyClass`.</span></span>  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="4fd90-170">即使`derivedClass`會覆寫`testMethod`，則`MyClass`中的關鍵字`useMyClass`nullifies 的覆寫，且編譯器會解析效果的基底類別版本呼叫`testMethod`。</span><span class="sxs-lookup"><span data-stu-id="4fd90-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd90-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fd90-171">See also</span></span>

- [<span data-ttu-id="4fd90-172">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="4fd90-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="4fd90-173">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="4fd90-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
