---
title: "繼承基本概念 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4892ed6dcfb3843bd6cb2de2d3e032bfeb1efdf9
ms.openlocfilehash: 43b6505634b12f7f8353866e938151f1e00fb073
ms.contentlocale: zh-tw
ms.lasthandoff: 05/16/2017

---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="8ee63-102">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ee63-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="8ee63-103">`Inherits`陳述式用來宣告新的類別，稱為*衍生的類別*、 根據現有的類別，稱為*基底類別*。</span><span class="sxs-lookup"><span data-stu-id="8ee63-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="8ee63-104">在衍生的類別繼承，並擴充屬性、 方法、 事件、 欄位和基底類別中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="8ee63-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="8ee63-105">下節說明一些繼承的規則和修飾詞可用來變更方式類別繼承，或是會繼承︰</span><span class="sxs-lookup"><span data-stu-id="8ee63-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="8ee63-106">根據預設，所有類別都都會繼承除非標`NotInheritable`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8ee63-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="8ee63-107">類別可以繼承自其他類別，在您的專案，或從您的專案參考其他組件中的類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="8ee63-108">不同於語言可讓多重繼承，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許只有單一繼承類別; 也就是說，衍生的類別可以有只有一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-108">Unlike languages that allow multiple inheritance, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="8ee63-109">雖然類別中不允許多重繼承，類別可以實作多個介面，可以達到相同目的。</span><span class="sxs-lookup"><span data-stu-id="8ee63-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="8ee63-110">若要避免公開受限制的項目與基底類別，衍生類別的存取類型必須相等或更具限制性其基底類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="8ee63-111">例如，`Public`類別無法繼承`Friend`或`Private`類別，和`Friend`類別無法繼承`Private`類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="8ee63-112">繼承修飾詞</span><span class="sxs-lookup"><span data-stu-id="8ee63-112">Inheritance Modifiers</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8ee63-113">導入了下列類別層級的陳述式和修飾詞來支援繼承︰</span><span class="sxs-lookup"><span data-stu-id="8ee63-113"> introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="8ee63-114">`Inherits`陳述式，指定基底類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="8ee63-115">`NotInheritable`修飾詞，可讓程式設計人員使用類別當做基底類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="8ee63-116">`MustInherit`修飾詞，指定類別，適用於做為基底類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="8ee63-117">執行個體`MustInherit`類別不能直接建立; 他們只能建立為基底的類別執行個體的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="8ee63-118">(其他程式設計語言，例如 c + + 和 C# 中，使用詞彙*抽象類別*來說明這類的類別。)</span><span class="sxs-lookup"><span data-stu-id="8ee63-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="8ee63-119">屬性和方法在衍生類別中的覆寫</span><span class="sxs-lookup"><span data-stu-id="8ee63-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="8ee63-120">根據預設，在衍生的類別會從其基底類別繼承屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="8ee63-121">在衍生類別中有不同的行為繼承的屬性或方法有很*覆寫*。</span><span class="sxs-lookup"><span data-stu-id="8ee63-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="8ee63-122">也就是說，您可以定義新的實作方法的衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="8ee63-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="8ee63-123">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="8ee63-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="8ee63-124">`Overridable`— 可讓衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="8ee63-125">`Overrides`-覆寫`Overridable`屬性或方法的基底類別中定義。</span><span class="sxs-lookup"><span data-stu-id="8ee63-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="8ee63-126">`NotOverridable`可防止遭到覆寫繼承的類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="8ee63-127">根據預設，`Public`方法都是`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="8ee63-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="8ee63-128">`MustOverride`-需要在衍生的類別覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="8ee63-129">當`MustOverride`關鍵字時，方法定義都包含只`Sub`， `Function`，或`Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ee63-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="8ee63-130">允許其他陳述式，以及特別是沒有任何`End Sub`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ee63-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="8ee63-131">`MustOverride`方法必須宣告中`MustInherit`類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="8ee63-132">假設您想要定義類別處理薪資。</span><span class="sxs-lookup"><span data-stu-id="8ee63-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="8ee63-133">您可以定義泛型`Payroll`類別，其中包含`RunPayroll`計算薪資典型的一週的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="8ee63-134">您接著可以使用`Payroll`更特殊的基底類別為`BonusPayroll`分配員工加分時可用的類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="8ee63-135">`BonusPayroll`類別可以繼承，並覆寫，`PayEmployee`定義基底方法`Payroll`類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="8ee63-136">下列範例會定義基底類別，`Payroll,`和衍生的類別， `BonusPayroll`，因而覆寫繼承的方法， `PayEmployee`。</span><span class="sxs-lookup"><span data-stu-id="8ee63-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="8ee63-137">程序， `RunPayroll`、 建立和傳送`Payroll`物件和`BonusPayroll`函式物件`Pay`，執行`PayEmployee`兩個物件的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 <span data-ttu-id="8ee63-138">[!code-vb[VbVbalrOOP #&28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ee63-138">[!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span></span>  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="8ee63-139">MyBase 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8ee63-139">The MyBase Keyword</span></span>  
 <span data-ttu-id="8ee63-140">`MyBase`關鍵字的行為就像指的是類別的目前執行個體的基底類別的物件變數。</span><span class="sxs-lookup"><span data-stu-id="8ee63-140">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="8ee63-141">`MyBase`經常用來存取基底類別成員會覆寫或遮蔽衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="8ee63-141">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="8ee63-142">特別是，`MyBase.New`用來明確地從衍生的類別建構函式呼叫基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="8ee63-142">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="8ee63-143">例如，假設您正在設計衍生的類別中覆寫繼承自基底類別的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-143">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="8ee63-144">覆寫的方法可以呼叫基底類別中的方法，並修改的傳回值，如下列程式碼片段所示︰</span><span class="sxs-lookup"><span data-stu-id="8ee63-144">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="8ee63-145">[!code-vb[VbVbalrOOP #&109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ee63-145">[!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="8ee63-146">下列清單說明限制使用`MyBase`:</span><span class="sxs-lookup"><span data-stu-id="8ee63-146">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="8ee63-147">`MyBase`是指直接基底類別和繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="8ee63-147">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="8ee63-148">它不能用來存取`Private`類別中的成員。</span><span class="sxs-lookup"><span data-stu-id="8ee63-148">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="8ee63-149">`MyBase`是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="8ee63-149">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="8ee63-150">`MyBase`無法指派給變數，傳遞至程序，或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="8ee63-150">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="8ee63-151">此方法，`MyBase`限定並沒有定義中直接基底類別; 它可能會改為在間接繼承的基底類別中定義。</span><span class="sxs-lookup"><span data-stu-id="8ee63-151">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="8ee63-152">為了讓所限定的參考`MyBase`才能正確編譯，某些基底類別必須包含符合的名稱和類型的參數，會出現在呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-152">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="8ee63-153">您不能使用`MyBase`呼叫`MustOverride`基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-153">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="8ee63-154">`MyBase`不能用來限定本身。</span><span class="sxs-lookup"><span data-stu-id="8ee63-154">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="8ee63-155">因此，下列程式碼不正確︰</span><span class="sxs-lookup"><span data-stu-id="8ee63-155">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="8ee63-156">`MyBase`不能在模組中。</span><span class="sxs-lookup"><span data-stu-id="8ee63-156">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="8ee63-157">`MyBase`無法用來存取基底類別成員標記為`Friend`基底類別位於不同的組件中。</span><span class="sxs-lookup"><span data-stu-id="8ee63-157">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="8ee63-158">如需詳細資訊和另一個範例，請參閱[How to︰ 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee63-158">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="8ee63-159">MyClass 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8ee63-159">The MyClass Keyword</span></span>  
 <span data-ttu-id="8ee63-160">`MyClass`關鍵字的行為就像適用於目前的執行個體的類別，為原始實作的物件變數。</span><span class="sxs-lookup"><span data-stu-id="8ee63-160">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="8ee63-161">`MyClass`類似於`Me`，但每個方法和屬性上呼叫`MyClass`一樣的方法或屬性會被視為[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee63-161">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="8ee63-162">因此，不會影響方法或屬性藉由衍生類別中覆寫。</span><span class="sxs-lookup"><span data-stu-id="8ee63-162">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="8ee63-163">`MyClass`是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="8ee63-163">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="8ee63-164">`MyClass`無法指派給變數，傳遞至程序，或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="8ee63-164">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="8ee63-165">`MyClass`是指包含類別和繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="8ee63-165">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="8ee63-166">`MyClass`可用來當做限定詞`Shared`成員。</span><span class="sxs-lookup"><span data-stu-id="8ee63-166">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="8ee63-167">`MyClass`不在內部使用`Shared`方法，但可以在執行個體方法內用來存取共用的成員的類別。</span><span class="sxs-lookup"><span data-stu-id="8ee63-167">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="8ee63-168">`MyClass`不能在標準模組。</span><span class="sxs-lookup"><span data-stu-id="8ee63-168">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="8ee63-169">`MyClass`可用來限定基底類別中定義，而該類別中所提供的方法沒有實作的方法。</span><span class="sxs-lookup"><span data-stu-id="8ee63-169">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="8ee63-170">這類的參考具有相同的意義`MyBase.`*方法*。</span><span class="sxs-lookup"><span data-stu-id="8ee63-170">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="8ee63-171">下列範例會比較`Me`和`MyClass`。</span><span class="sxs-lookup"><span data-stu-id="8ee63-171">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="8ee63-172">即使`derivedClass`覆寫`testMethod`、`MyClass`關鍵字`useMyClass`nullifies 的覆寫和編譯器解析效果的基底類別版本來呼叫`testMethod`。</span><span class="sxs-lookup"><span data-stu-id="8ee63-172">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee63-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ee63-173">See Also</span></span>  
 <span data-ttu-id="8ee63-174">[Inherits 陳述式](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8ee63-174">[Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="8ee63-175"> [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="8ee63-175"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

