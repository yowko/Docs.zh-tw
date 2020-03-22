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
# <a name="inheritance-basics-visual-basic"></a>繼承基本概念 (Visual Basic)

該`Inherits`語句用於根據稱為*基類*的新類（稱為*派生類*）聲明新類。 派生類繼承並可以擴展基類中定義的屬性、方法、事件、欄位和常量。 以下部分介紹繼承的一些規則，以及可用於更改類繼承或繼承方式的修改器：

- 預設情況下，除非用 關鍵字標記，否則所有類都是`NotInheritable`可繼承的。 類可以從專案中的其他類或專案引用的其他程式集中的類繼承。

- 與允許多重繼承的語言不同，Visual Basic 只允許在類中進行單個繼承;也就是說，派生類只能有一個基類。 儘管類中不允許多次繼承，但類可以實現多個介面，從而有效地實現相同的目的。

- 為了防止在基類中公開受限制項，派生類的訪問類型必須等於或比其基類更具限制性。 `Public`例如，類不能繼承 或`Friend``Private`類，並且`Friend`類不能繼承類。 `Private`

## <a name="inheritance-modifiers"></a>繼承修改器

Visual Basic 引入了以下類級語句和修改器來支援繼承：

- `Inherits`語句 = 指定基類。

- `NotInheritable`修改器 = 防止程式師將類用作基類。

- `MustInherit`修改器 = 指定類僅用於基類。 不能直接創建`MustInherit`類的實例;因此，無法直接創建類的實例。它們只能創建為派生類的基類實例。 （其他程式設計語言（如C++和 C#）使用術語*抽象類別*來描述此類。

## <a name="overriding-properties-and-methods-in-derived-classes"></a>派生類中的重寫屬性和方法

預設情況下，派生類繼承其基類的屬性和方法。 如果繼承的屬性或方法在派生類中的行為不同，則可以*重寫*它。 也就是說，您可以在派生類中定義方法的新實現。 下列修飾詞是用來控制如何覆寫屬性及方法：

- `Overridable`• 允許在派生類中重寫類中的屬性或方法。

- `Overrides`• 重寫基`Overridable`類中定義的屬性或方法。

- `NotOverridable`• 防止在繼承類中重寫屬性或方法。 預設情況下，`Public`方法為`NotOverridable`。

- `MustOverride`• 要求派生類重寫屬性或方法。 使用`MustOverride`關鍵字時，方法定義僅包含`Sub`。 `Function`。 `Property` 不允許任何其他語句，特別是沒有`End Sub`或`End Function`語句。 `MustOverride`方法必須在類中`MustInherit`聲明。

假設您要定義要處理工資單的類。 您可以定義一個泛`Payroll`型類，其中包含計算`RunPayroll`典型星期的工資單的方法。 然後，您可以將用作`Payroll`更專業`BonusPayroll`類的基類，該類可用於分發員工獎金。

類`BonusPayroll`可以繼承和重寫基`PayEmployee``Payroll`類中定義的方法。

下面的示例定義基類`Payroll,`和派生類 ，`BonusPayroll`它重寫繼承的方法 。 `PayEmployee` 過程 ，`RunPayroll``Payroll`創建，然後將物件和`BonusPayroll`物件傳遞給一個函數 ，`Pay`執行兩個物件`PayEmployee`的方法。

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase 關鍵字

關鍵字`MyBase`的作用類似于引用類當前實例的基類的物件變數。 `MyBase`通常用於訪問派生類中重寫或隱藏基類成員。 特別是，`MyBase.New`用於從派生類建構函式顯式調用基類建構函式。

例如，假設您正在設計一個派生類，該類重寫從基類繼承的方法。 重寫方法可以在基類中調用 方法並修改傳回值，如以下代碼片段所示：

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

下面的清單描述了對 使用`MyBase`的限制：

- `MyBase`指直接基類及其繼承成員。 它不能用於訪問`Private`類中的成員。

- `MyBase`是關鍵字，而不是真實物件。 `MyBase`不能分配給變數、傳遞給過程或用於`Is`比較。

- `MyBase`限定的方法不必在直接基類中定義;它可以在間接繼承的基類中定義。 為了使 引用`MyBase`具有正確的編譯，某些基類必須包含一個方法，匹配調用中顯示的參數的名稱和類型。

- 不能使用`MyBase`調用`MustOverride`基類方法。

- `MyBase`不能用來限定自己。 因此，以下代碼無效：

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`不能在模組中使用。

- `MyBase`不能用於訪問標記為`Friend`基類的基類成員，因為基類位於其他程式集中。

有關詳細資訊和另一個示例，請參閱[如何：訪問派生類隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。

## <a name="the-myclass-keyword"></a>MyClass 關鍵字

關鍵字`MyClass`的作用類似于物件變數，該變數引用最初實現的類的當前實例。 `MyClass`類似于`Me`，但每個方法和屬性調用`MyClass`都被視為方法或屬性[不是可重寫的](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。 因此，方法或屬性不受派生類中重寫的影響。

- `MyClass`是關鍵字，而不是真實物件。 `MyClass`不能分配給變數、傳遞給過程或用於`Is`比較。

- `MyClass`引用包含類及其繼承成員。

- `MyClass`可用作成員的`Shared`限定詞。

- `MyClass`不能在`Shared`方法內使用，但可以在實例方法內訪問類的共用成員。

- `MyClass`不能在標準模組中使用。

- `MyClass`可用於限定在基類中定義且沒有該類中提供的方法的實現的方法。 這種引用與`MyBase.`*方法*的含義相同。

下面的示例比較`Me`和`MyClass`。

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

`derivedClass`即使重寫`testMethod`，`MyClass`中的`useMyClass`關鍵字將取消重寫的效果，編譯器解析對 基類版本的`testMethod`調用。

## <a name="see-also"></a>另請參閱

- [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
