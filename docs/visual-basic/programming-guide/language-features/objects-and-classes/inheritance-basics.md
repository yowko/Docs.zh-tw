---
title: 繼承基本概念
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
ms.openlocfilehash: 3bf1847f618a642d26df4aa1c5247a4ba2bd3b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411775"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="01f77-102">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01f77-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="01f77-103">`Inherits`語句是用來根據現有的類別（稱為*基類*）來宣告新的類別，稱為*衍生類別*。</span><span class="sxs-lookup"><span data-stu-id="01f77-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="01f77-104">衍生類別會繼承和擴充、屬性、方法、事件、欄位，以及在基類中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="01f77-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="01f77-105">下一節將描述繼承的一些規則，以及您可以用來變更類別繼承或繼承方式的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="01f77-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="01f77-106">根據預設，所有類別都是可繼承的，除非以 `NotInheritable` 關鍵字標記。</span><span class="sxs-lookup"><span data-stu-id="01f77-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="01f77-107">類別可以繼承自您專案中的其他類別，或從您的專案所參考之其他元件中的類別。</span><span class="sxs-lookup"><span data-stu-id="01f77-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="01f77-108">不同于允許多個繼承的語言，Visual Basic 只允許類別中的單一繼承;也就是說，衍生的類別只能有一個基類。</span><span class="sxs-lookup"><span data-stu-id="01f77-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="01f77-109">雖然類別中不允許多個繼承，但類別可以實作用多個介面，這可以有效地完成相同的結束。</span><span class="sxs-lookup"><span data-stu-id="01f77-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="01f77-110">若要避免公開基類中受限制的專案，衍生類別的存取類型必須等於或大於其基類的限制。</span><span class="sxs-lookup"><span data-stu-id="01f77-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="01f77-111">例如， `Public` 類別無法繼承 `Friend` 或 `Private` 類別，而且 `Friend` 類別無法繼承 `Private` 類別。</span><span class="sxs-lookup"><span data-stu-id="01f77-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="01f77-112">繼承修飾詞</span><span class="sxs-lookup"><span data-stu-id="01f77-112">Inheritance Modifiers</span></span>

<span data-ttu-id="01f77-113">Visual Basic 引進下列類別層級語句和修飾詞，以支援繼承：</span><span class="sxs-lookup"><span data-stu-id="01f77-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="01f77-114">`Inherits`語句-指定基類。</span><span class="sxs-lookup"><span data-stu-id="01f77-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="01f77-115">`NotInheritable`修飾詞-防止程式設計人員使用類別做為基類。</span><span class="sxs-lookup"><span data-stu-id="01f77-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="01f77-116">`MustInherit`修飾詞—指定類別僅供做為基類使用。</span><span class="sxs-lookup"><span data-stu-id="01f77-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="01f77-117">`MustInherit`無法直接建立類別的實例，它們只能建立為衍生類別的基類實例。</span><span class="sxs-lookup"><span data-stu-id="01f77-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="01f77-118">（其他程式設計語言，例如 c + + 和 c #，會使用「*抽象類別*」一詞來描述這類類別）。</span><span class="sxs-lookup"><span data-stu-id="01f77-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="01f77-119">覆寫衍生類別中的屬性和方法</span><span class="sxs-lookup"><span data-stu-id="01f77-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="01f77-120">根據預設，衍生類別會繼承其基類的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="01f77-121">如果繼承的屬性或方法在衍生類別中必須有不同的行為，則可以覆*寫*它。</span><span class="sxs-lookup"><span data-stu-id="01f77-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="01f77-122">也就是說，您可以在衍生類別中定義方法的新執行。</span><span class="sxs-lookup"><span data-stu-id="01f77-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="01f77-123">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="01f77-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="01f77-124">`Overridable`-允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="01f77-125">`Overrides`-覆寫 `Overridable` 在基類中定義的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="01f77-126">`NotOverridable`-防止在繼承類別中覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="01f77-127">根據預設， `Public` 方法是 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="01f77-128">`MustOverride`-需要衍生的類別覆寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="01f77-129">`MustOverride`使用關鍵字時，方法定義只會包含 `Sub` 、 `Function` 或 `Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="01f77-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="01f77-130">不允許其他語句，特別是沒有 `End Sub` 或 `End Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="01f77-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="01f77-131">`MustOverride`方法必須在類別中宣告 `MustInherit` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="01f77-132">假設您想要定義用來處理薪資的類別。</span><span class="sxs-lookup"><span data-stu-id="01f77-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="01f77-133">您可以定義泛型 `Payroll` 類別，其中包含的 `RunPayroll` 方法會計算一般周的薪資。</span><span class="sxs-lookup"><span data-stu-id="01f77-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="01f77-134">然後，您可以使用 `Payroll` 作為更特殊化類別的基類 `BonusPayroll` ，以便在散發員工獎金時使用。</span><span class="sxs-lookup"><span data-stu-id="01f77-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="01f77-135">`BonusPayroll`類別可以繼承和覆寫 `PayEmployee` 基類中定義的方法 `Payroll` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="01f77-136">下列範例定義一個基類， `Payroll,` 以及一個衍生的類別， `BonusPayroll` 它會覆寫繼承的方法 `PayEmployee` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="01f77-137">`RunPayroll`程式會建立物件和物件，然後將它傳遞至函式，而該函式 `Payroll` `BonusPayroll` `Pay` 會執行 `PayEmployee` 這兩個物件的方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="01f77-138">MyBase 關鍵字</span><span class="sxs-lookup"><span data-stu-id="01f77-138">The MyBase Keyword</span></span>

<span data-ttu-id="01f77-139">`MyBase`關鍵字的行為就像是參考類別目前實例之基類的物件變數。</span><span class="sxs-lookup"><span data-stu-id="01f77-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="01f77-140">`MyBase`經常用來存取衍生類別中覆寫或陰影的基類成員。</span><span class="sxs-lookup"><span data-stu-id="01f77-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="01f77-141">特別是， `MyBase.New` 是用來從衍生類別的函式明確呼叫基類的「函數」（base class）。</span><span class="sxs-lookup"><span data-stu-id="01f77-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="01f77-142">例如，假設您設計的衍生類別會覆寫繼承自基類的方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="01f77-143">覆寫的方法可以呼叫基類中的方法，並修改傳回值，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="01f77-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="01f77-144">下列清單描述使用的限制 `MyBase` ：</span><span class="sxs-lookup"><span data-stu-id="01f77-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="01f77-145">`MyBase`參考直接基類及其繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="01f77-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="01f77-146">它不能用來存取 `Private` 類別中的成員。</span><span class="sxs-lookup"><span data-stu-id="01f77-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="01f77-147">`MyBase`是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="01f77-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="01f77-148">`MyBase`無法指派給變數、傳遞給程式或用於 `Is` 比較。</span><span class="sxs-lookup"><span data-stu-id="01f77-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="01f77-149">限定的方法 `MyBase` 不需要在直接基類中定義，而是可以在間接繼承的基類中定義。</span><span class="sxs-lookup"><span data-stu-id="01f77-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="01f77-150">為了讓限定的參考 `MyBase` 正確編譯，某些基類必須包含符合呼叫中所出現之參數名稱和類型的方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="01f77-151">您不能使用 `MyBase` 呼叫 `MustOverride` 基類方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="01f77-152">`MyBase`不能用來限定自己。</span><span class="sxs-lookup"><span data-stu-id="01f77-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="01f77-153">因此，下列程式碼無效：</span><span class="sxs-lookup"><span data-stu-id="01f77-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="01f77-154">`MyBase`無法在模組中使用。</span><span class="sxs-lookup"><span data-stu-id="01f77-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="01f77-155">`MyBase`無法用來存取已標記為的基類成員，因為 `Friend` 基類是在不同的元件中。</span><span class="sxs-lookup"><span data-stu-id="01f77-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="01f77-156">如需詳細資訊和另一個範例，請參閱[如何：存取衍生類別所隱藏的變數](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="01f77-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="01f77-157">MyClass 關鍵字</span><span class="sxs-lookup"><span data-stu-id="01f77-157">The MyClass Keyword</span></span>

<span data-ttu-id="01f77-158">`MyClass`關鍵字的行為就像物件變數，它會參考原本實作為之類別的目前實例。</span><span class="sxs-lookup"><span data-stu-id="01f77-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="01f77-159">`MyClass`類似于 `Me` ，但是上的每個方法和屬性呼叫 `MyClass` 都會被視為[NotOverridable](../../../language-reference/modifiers/notoverridable.md)方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="01f77-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="01f77-160">因此，方法或屬性不會受到在衍生類別中覆寫的影響。</span><span class="sxs-lookup"><span data-stu-id="01f77-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="01f77-161">`MyClass`是關鍵字，而不是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="01f77-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="01f77-162">`MyClass`無法指派給變數、傳遞給程式或用於 `Is` 比較。</span><span class="sxs-lookup"><span data-stu-id="01f77-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="01f77-163">`MyClass`參考包含類別及其繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="01f77-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="01f77-164">`MyClass`可用來做為成員的辨識符號 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="01f77-165">`MyClass`無法在方法內部使用 `Shared` ，但可以在實例方法內用來存取類別的共用成員。</span><span class="sxs-lookup"><span data-stu-id="01f77-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="01f77-166">`MyClass`不能用於標準模組。</span><span class="sxs-lookup"><span data-stu-id="01f77-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="01f77-167">`MyClass`可以用來限定在基類中定義的方法，而且不會執行該類別中提供的方法。</span><span class="sxs-lookup"><span data-stu-id="01f77-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="01f77-168">這類參考與方法具有相同的意義 `MyBase.` \* \*。</span><span class="sxs-lookup"><span data-stu-id="01f77-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="01f77-169">下列範例會比較 `Me` 和 `MyClass` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="01f77-170">雖然 `derivedClass` 覆寫 `testMethod` ， `MyClass` 中的關鍵字會 nullifies 覆寫的 `useMyClass` 效果，而編譯器會解析基類版本的呼叫 `testMethod` 。</span><span class="sxs-lookup"><span data-stu-id="01f77-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="01f77-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f77-171">See also</span></span>

- [<span data-ttu-id="01f77-172">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="01f77-172">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="01f77-173">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="01f77-173">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
