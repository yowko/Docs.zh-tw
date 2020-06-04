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
# <a name="inheritance-basics-visual-basic"></a>繼承基本概念 (Visual Basic)

`Inherits`語句是用來根據現有的類別（稱為*基類*）來宣告新的類別，稱為*衍生類別*。 衍生類別會繼承和擴充、屬性、方法、事件、欄位，以及在基類中定義的常數。 下一節將描述繼承的一些規則，以及您可以用來變更類別繼承或繼承方式的修飾詞：

- 根據預設，所有類別都是可繼承的，除非以 `NotInheritable` 關鍵字標記。 類別可以繼承自您專案中的其他類別，或從您的專案所參考之其他元件中的類別。

- 不同于允許多個繼承的語言，Visual Basic 只允許類別中的單一繼承;也就是說，衍生的類別只能有一個基類。 雖然類別中不允許多個繼承，但類別可以實作用多個介面，這可以有效地完成相同的結束。

- 若要避免公開基類中受限制的專案，衍生類別的存取類型必須等於或大於其基類的限制。 例如， `Public` 類別無法繼承 `Friend` 或 `Private` 類別，而且 `Friend` 類別無法繼承 `Private` 類別。

## <a name="inheritance-modifiers"></a>繼承修飾詞

Visual Basic 引進下列類別層級語句和修飾詞，以支援繼承：

- `Inherits`語句-指定基類。

- `NotInheritable`修飾詞-防止程式設計人員使用類別做為基類。

- `MustInherit`修飾詞—指定類別僅供做為基類使用。 `MustInherit`無法直接建立類別的實例，它們只能建立為衍生類別的基類實例。 （其他程式設計語言，例如 c + + 和 c #，會使用「*抽象類別*」一詞來描述這類類別）。

## <a name="overriding-properties-and-methods-in-derived-classes"></a>覆寫衍生類別中的屬性和方法

根據預設，衍生類別會繼承其基類的屬性和方法。 如果繼承的屬性或方法在衍生類別中必須有不同的行為，則可以覆*寫*它。 也就是說，您可以在衍生類別中定義方法的新執行。 下列修飾詞是用來控制如何覆寫屬性及方法：

- `Overridable`-允許在衍生類別中覆寫類別中的屬性或方法。

- `Overrides`-覆寫 `Overridable` 在基類中定義的屬性或方法。

- `NotOverridable`-防止在繼承類別中覆寫屬性或方法。 根據預設， `Public` 方法是 `NotOverridable` 。

- `MustOverride`-需要衍生的類別覆寫屬性或方法。 `MustOverride`使用關鍵字時，方法定義只會包含 `Sub` 、 `Function` 或 `Property` 語句。 不允許其他語句，特別是沒有 `End Sub` 或 `End Function` 語句。 `MustOverride`方法必須在類別中宣告 `MustInherit` 。

假設您想要定義用來處理薪資的類別。 您可以定義泛型 `Payroll` 類別，其中包含的 `RunPayroll` 方法會計算一般周的薪資。 然後，您可以使用 `Payroll` 作為更特殊化類別的基類 `BonusPayroll` ，以便在散發員工獎金時使用。

`BonusPayroll`類別可以繼承和覆寫 `PayEmployee` 基類中定義的方法 `Payroll` 。

下列範例定義一個基類， `Payroll,` 以及一個衍生的類別， `BonusPayroll` 它會覆寫繼承的方法 `PayEmployee` 。 `RunPayroll`程式會建立物件和物件，然後將它傳遞至函式，而該函式 `Payroll` `BonusPayroll` `Pay` 會執行 `PayEmployee` 這兩個物件的方法。

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase 關鍵字

`MyBase`關鍵字的行為就像是參考類別目前實例之基類的物件變數。 `MyBase`經常用來存取衍生類別中覆寫或陰影的基類成員。 特別是， `MyBase.New` 是用來從衍生類別的函式明確呼叫基類的「函數」（base class）。

例如，假設您設計的衍生類別會覆寫繼承自基類的方法。 覆寫的方法可以呼叫基類中的方法，並修改傳回值，如下列程式碼片段所示：

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

下列清單描述使用的限制 `MyBase` ：

- `MyBase`參考直接基類及其繼承的成員。 它不能用來存取 `Private` 類別中的成員。

- `MyBase`是關鍵字，而不是真正的物件。 `MyBase`無法指派給變數、傳遞給程式或用於 `Is` 比較。

- 限定的方法 `MyBase` 不需要在直接基類中定義，而是可以在間接繼承的基類中定義。 為了讓限定的參考 `MyBase` 正確編譯，某些基類必須包含符合呼叫中所出現之參數名稱和類型的方法。

- 您不能使用 `MyBase` 呼叫 `MustOverride` 基類方法。

- `MyBase`不能用來限定自己。 因此，下列程式碼無效：

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`無法在模組中使用。

- `MyBase`無法用來存取已標記為的基類成員，因為 `Friend` 基類是在不同的元件中。

如需詳細資訊和另一個範例，請參閱[如何：存取衍生類別所隱藏的變數](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。

## <a name="the-myclass-keyword"></a>MyClass 關鍵字

`MyClass`關鍵字的行為就像物件變數，它會參考原本實作為之類別的目前實例。 `MyClass`類似于 `Me` ，但是上的每個方法和屬性呼叫 `MyClass` 都會被視為[NotOverridable](../../../language-reference/modifiers/notoverridable.md)方法或屬性。 因此，方法或屬性不會受到在衍生類別中覆寫的影響。

- `MyClass`是關鍵字，而不是真正的物件。 `MyClass`無法指派給變數、傳遞給程式或用於 `Is` 比較。

- `MyClass`參考包含類別及其繼承的成員。

- `MyClass`可用來做為成員的辨識符號 `Shared` 。

- `MyClass`無法在方法內部使用 `Shared` ，但可以在實例方法內用來存取類別的共用成員。

- `MyClass`不能用於標準模組。

- `MyClass`可以用來限定在基類中定義的方法，而且不會執行該類別中提供的方法。 這類參考與方法具有相同的意義 `MyBase.` * *。

下列範例會比較 `Me` 和 `MyClass` 。

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

雖然 `derivedClass` 覆寫 `testMethod` ， `MyClass` 中的關鍵字會 nullifies 覆寫的 `useMyClass` 效果，而編譯器會解析基類版本的呼叫 `testMethod` 。

## <a name="see-also"></a>另請參閱

- [Inherits Statement](../../../language-reference/statements/inherits-statement.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
