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
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400880"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="94e31-102">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94e31-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="94e31-103">該`Inherits`語句用於根據稱為*基類*的新類（稱為*派生類*）聲明新類。</span><span class="sxs-lookup"><span data-stu-id="94e31-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="94e31-104">派生類繼承並可以擴展基類中定義的屬性、方法、事件、欄位和常量。</span><span class="sxs-lookup"><span data-stu-id="94e31-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="94e31-105">以下部分介紹繼承的一些規則，以及可用於更改類繼承或繼承方式的修改器：</span><span class="sxs-lookup"><span data-stu-id="94e31-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="94e31-106">預設情況下，除非用 關鍵字標記，否則所有類都是`NotInheritable`可繼承的。</span><span class="sxs-lookup"><span data-stu-id="94e31-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="94e31-107">類可以從專案中的其他類或專案引用的其他程式集中的類繼承。</span><span class="sxs-lookup"><span data-stu-id="94e31-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="94e31-108">與允許多重繼承的語言不同，Visual Basic 只允許在類中進行單個繼承;也就是說，派生類只能有一個基類。</span><span class="sxs-lookup"><span data-stu-id="94e31-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="94e31-109">儘管類中不允許多次繼承，但類可以實現多個介面，從而有效地實現相同的目的。</span><span class="sxs-lookup"><span data-stu-id="94e31-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="94e31-110">為了防止在基類中公開受限制項，派生類的訪問類型必須等於或比其基類更具限制性。</span><span class="sxs-lookup"><span data-stu-id="94e31-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="94e31-111">`Public`例如，類不能繼承 或`Friend``Private`類，並且`Friend`類不能繼承類。 `Private`</span><span class="sxs-lookup"><span data-stu-id="94e31-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="94e31-112">繼承修改器</span><span class="sxs-lookup"><span data-stu-id="94e31-112">Inheritance Modifiers</span></span>

<span data-ttu-id="94e31-113">Visual Basic 引入了以下類級語句和修改器來支援繼承：</span><span class="sxs-lookup"><span data-stu-id="94e31-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="94e31-114">`Inherits`語句 = 指定基類。</span><span class="sxs-lookup"><span data-stu-id="94e31-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="94e31-115">`NotInheritable`修改器 = 防止程式師將類用作基類。</span><span class="sxs-lookup"><span data-stu-id="94e31-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="94e31-116">`MustInherit`修改器 = 指定類僅用於基類。</span><span class="sxs-lookup"><span data-stu-id="94e31-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="94e31-117">不能直接創建`MustInherit`類的實例;因此，無法直接創建類的實例。它們只能創建為派生類的基類實例。</span><span class="sxs-lookup"><span data-stu-id="94e31-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="94e31-118">（其他程式設計語言（如C++和 C#）使用術語*抽象類別*來描述此類。</span><span class="sxs-lookup"><span data-stu-id="94e31-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="94e31-119">派生類中的重寫屬性和方法</span><span class="sxs-lookup"><span data-stu-id="94e31-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="94e31-120">預設情況下，派生類繼承其基類的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="94e31-121">如果繼承的屬性或方法在派生類中的行為不同，則可以*重寫*它。</span><span class="sxs-lookup"><span data-stu-id="94e31-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="94e31-122">也就是說，您可以在派生類中定義方法的新實現。</span><span class="sxs-lookup"><span data-stu-id="94e31-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="94e31-123">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="94e31-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="94e31-124">`Overridable`• 允許在派生類中重寫類中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="94e31-125">`Overrides`• 重寫基`Overridable`類中定義的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="94e31-126">`NotOverridable`• 防止在繼承類中重寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="94e31-127">預設情況下，`Public`方法為`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="94e31-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="94e31-128">`MustOverride`• 要求派生類重寫屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="94e31-129">使用`MustOverride`關鍵字時，方法定義僅包含`Sub`。 `Function`。 `Property`</span><span class="sxs-lookup"><span data-stu-id="94e31-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="94e31-130">不允許任何其他語句，特別是沒有`End Sub`或`End Function`語句。</span><span class="sxs-lookup"><span data-stu-id="94e31-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="94e31-131">`MustOverride`方法必須在類中`MustInherit`聲明。</span><span class="sxs-lookup"><span data-stu-id="94e31-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="94e31-132">假設您要定義要處理工資單的類。</span><span class="sxs-lookup"><span data-stu-id="94e31-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="94e31-133">您可以定義一個泛`Payroll`型類，其中包含計算`RunPayroll`典型星期的工資單的方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="94e31-134">然後，您可以將用作`Payroll`更專業`BonusPayroll`類的基類，該類可用於分發員工獎金。</span><span class="sxs-lookup"><span data-stu-id="94e31-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="94e31-135">類`BonusPayroll`可以繼承和重寫基`PayEmployee``Payroll`類中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="94e31-136">下面的示例定義基類`Payroll,`和派生類 ，`BonusPayroll`它重寫繼承的方法 。 `PayEmployee`</span><span class="sxs-lookup"><span data-stu-id="94e31-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="94e31-137">過程 ，`RunPayroll``Payroll`創建，然後將物件和`BonusPayroll`物件傳遞給一個函數 ，`Pay`執行兩個物件`PayEmployee`的方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="94e31-138">MyBase 關鍵字</span><span class="sxs-lookup"><span data-stu-id="94e31-138">The MyBase Keyword</span></span>

<span data-ttu-id="94e31-139">關鍵字`MyBase`的作用類似于引用類當前實例的基類的物件變數。</span><span class="sxs-lookup"><span data-stu-id="94e31-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="94e31-140">`MyBase`通常用於訪問派生類中重寫或隱藏基類成員。</span><span class="sxs-lookup"><span data-stu-id="94e31-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="94e31-141">特別是，`MyBase.New`用於從派生類建構函式顯式調用基類建構函式。</span><span class="sxs-lookup"><span data-stu-id="94e31-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="94e31-142">例如，假設您正在設計一個派生類，該類重寫從基類繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="94e31-143">重寫方法可以在基類中調用 方法並修改傳回值，如以下代碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="94e31-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="94e31-144">下面的清單描述了對 使用`MyBase`的限制：</span><span class="sxs-lookup"><span data-stu-id="94e31-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="94e31-145">`MyBase`指直接基類及其繼承成員。</span><span class="sxs-lookup"><span data-stu-id="94e31-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="94e31-146">它不能用於訪問`Private`類中的成員。</span><span class="sxs-lookup"><span data-stu-id="94e31-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="94e31-147">`MyBase`是關鍵字，而不是真實物件。</span><span class="sxs-lookup"><span data-stu-id="94e31-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="94e31-148">`MyBase`不能分配給變數、傳遞給過程或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="94e31-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="94e31-149">`MyBase`限定的方法不必在直接基類中定義;它可以在間接繼承的基類中定義。</span><span class="sxs-lookup"><span data-stu-id="94e31-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="94e31-150">為了使 引用`MyBase`具有正確的編譯，某些基類必須包含一個方法，匹配調用中顯示的參數的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="94e31-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="94e31-151">不能使用`MyBase`調用`MustOverride`基類方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="94e31-152">`MyBase`不能用來限定自己。</span><span class="sxs-lookup"><span data-stu-id="94e31-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="94e31-153">因此，以下代碼無效：</span><span class="sxs-lookup"><span data-stu-id="94e31-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="94e31-154">`MyBase`不能在模組中使用。</span><span class="sxs-lookup"><span data-stu-id="94e31-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="94e31-155">`MyBase`不能用於訪問標記為`Friend`基類的基類成員，因為基類位於其他程式集中。</span><span class="sxs-lookup"><span data-stu-id="94e31-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="94e31-156">有關詳細資訊和另一個示例，請參閱[如何：訪問派生類隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。</span><span class="sxs-lookup"><span data-stu-id="94e31-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="94e31-157">MyClass 關鍵字</span><span class="sxs-lookup"><span data-stu-id="94e31-157">The MyClass Keyword</span></span>

<span data-ttu-id="94e31-158">關鍵字`MyClass`的作用類似于物件變數，該變數引用最初實現的類的當前實例。</span><span class="sxs-lookup"><span data-stu-id="94e31-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="94e31-159">`MyClass`類似于`Me`，但每個方法和屬性調用`MyClass`都被視為方法或屬性[不是可重寫的](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。</span><span class="sxs-lookup"><span data-stu-id="94e31-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="94e31-160">因此，方法或屬性不受派生類中重寫的影響。</span><span class="sxs-lookup"><span data-stu-id="94e31-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="94e31-161">`MyClass`是關鍵字，而不是真實物件。</span><span class="sxs-lookup"><span data-stu-id="94e31-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="94e31-162">`MyClass`不能分配給變數、傳遞給過程或用於`Is`比較。</span><span class="sxs-lookup"><span data-stu-id="94e31-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="94e31-163">`MyClass`引用包含類及其繼承成員。</span><span class="sxs-lookup"><span data-stu-id="94e31-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="94e31-164">`MyClass`可用作成員的`Shared`限定詞。</span><span class="sxs-lookup"><span data-stu-id="94e31-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="94e31-165">`MyClass`不能在`Shared`方法內使用，但可以在實例方法內訪問類的共用成員。</span><span class="sxs-lookup"><span data-stu-id="94e31-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="94e31-166">`MyClass`不能在標準模組中使用。</span><span class="sxs-lookup"><span data-stu-id="94e31-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="94e31-167">`MyClass`可用於限定在基類中定義且沒有該類中提供的方法的實現的方法。</span><span class="sxs-lookup"><span data-stu-id="94e31-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="94e31-168">這種引用與`MyBase.`*方法*的含義相同。</span><span class="sxs-lookup"><span data-stu-id="94e31-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="94e31-169">下面的示例比較`Me`和`MyClass`。</span><span class="sxs-lookup"><span data-stu-id="94e31-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="94e31-170">`derivedClass`即使重寫`testMethod`，`MyClass`中的`useMyClass`關鍵字將取消重寫的效果，編譯器解析對 基類版本的`testMethod`調用。</span><span class="sxs-lookup"><span data-stu-id="94e31-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="94e31-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94e31-171">See also</span></span>

- [<span data-ttu-id="94e31-172">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="94e31-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="94e31-173">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="94e31-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
