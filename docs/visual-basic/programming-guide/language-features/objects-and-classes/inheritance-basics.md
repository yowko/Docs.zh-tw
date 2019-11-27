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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350826"
---
# <a name="inheritance-basics-visual-basic"></a>繼承基本概念 (Visual Basic)

`Inherits` 語句是用來根據現有的類別（稱為「*基類*」）來宣告新的類別，稱為「*衍生類別*」。 衍生類別會繼承和擴充、屬性、方法、事件、欄位，以及在基類中定義的常數。 下一節將描述繼承的一些規則，以及您可以用來變更類別繼承或繼承方式的修飾詞：

- 根據預設，所有類別都是可繼承的，除非以 `NotInheritable` 關鍵字標記。 類別可以繼承自您專案中的其他類別，或從您的專案所參考之其他元件中的類別。

- 不同于允許多個繼承的語言，Visual Basic 只允許類別中的單一繼承;也就是說，衍生的類別只能有一個基類。 雖然類別中不允許多個繼承，但類別可以實作用多個介面，這可以有效地完成相同的結束。

- 若要避免公開基類中受限制的專案，衍生類別的存取類型必須等於或大於其基類的限制。 例如，`Public` 類別無法繼承 `Friend` 或 `Private` 類別，而且 `Friend` 類別無法繼承 `Private` 類別。

## <a name="inheritance-modifiers"></a>繼承修飾詞

Visual Basic 引進下列類別層級語句和修飾詞，以支援繼承：

- `Inherits` 語句-指定基類。

- `NotInheritable` 修飾詞-防止程式設計人員使用類別做為基類。

- `MustInherit` 修飾詞-指定類別僅供做為基類使用。 無法直接建立 `MustInherit` 類別的實例;它們只能建立為衍生類別的基類實例。 （其他程式設計語言（例如C++和C#）會使用「*抽象類別*」一詞來描述這類類別）。

## <a name="overriding-properties-and-methods-in-derived-classes"></a>覆寫衍生類別中的屬性和方法

根據預設，衍生類別會繼承其基類的屬性和方法。 如果繼承的屬性或方法在衍生類別中必須有不同的行為，則可以覆*寫*它。 也就是說，您可以在衍生類別中定義方法的新執行。 下列修飾詞是用來控制如何覆寫屬性及方法：

- `Overridable`-允許在衍生類別中覆寫類別中的屬性或方法。

- `Overrides`-覆寫在基類中定義的 `Overridable` 屬性或方法。

- `NotOverridable`-防止在繼承類別中覆寫屬性或方法。 根據預設，會 `NotOverridable``Public` 方法。

- `MustOverride`-需要衍生類別覆寫屬性或方法。 使用 `MustOverride` 關鍵字時，方法定義只會包含 `Sub`、`Function`或 `Property` 語句。 不允許其他語句，特別是沒有 `End Sub` 或 `End Function` 的語句。 `MustOverride` 的方法必須在 `MustInherit` 類別中宣告。

假設您想要定義用來處理薪資的類別。 您可以定義泛型 `Payroll` 類別，其中包含的 `RunPayroll` 方法會計算一般周的薪資。 接著，您可以使用 `Payroll` 做為更特殊化 `BonusPayroll` 類別的基類，以便在散發員工獎金時使用。

`BonusPayroll` 類別可以繼承和覆寫在基底 `Payroll` 類別中定義的 `PayEmployee` 方法。

下列範例會定義基類、`Payroll,` 和衍生類別，`BonusPayroll`，它會覆寫繼承的方法，`PayEmployee`。 程式 `RunPayroll`，會建立 `Payroll` 物件，然後將 `BonusPayroll` 物件傳遞至函式 `Pay`，以執行這兩個物件的 `PayEmployee` 方法。

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase 關鍵字

`MyBase` 關鍵字的行為就像是參考類別目前實例之基類的物件變數。 `MyBase` 經常用來存取在衍生類別中覆寫或遮蔽的基類成員。 特別是，`MyBase.New` 是用來從衍生類別的「函式」明確呼叫基類的「函數」（base class）。

例如，假設您設計的衍生類別會覆寫繼承自基類的方法。 覆寫的方法可以呼叫基類中的方法，並修改傳回值，如下列程式碼片段所示：

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

下列清單描述使用 `MyBase`的限制：

- `MyBase` 指的是直接基類及其繼承的成員。 它不能用來存取類別中 `Private` 成員。

- `MyBase` 是關鍵字，而不是真正的物件。 `MyBase` 無法指派給變數、傳遞至程式，或用於 `Is` 比較。

- `MyBase` 限定的方法不需要在直接基類中定義;它可以改為在間接繼承的基類中定義。 為了讓 `MyBase` 限定的參考正確編譯，某些基類必須包含符合呼叫中所出現之參數名稱和類型的方法。

- 您無法使用 `MyBase` 來呼叫 `MustOverride` 基類方法。

- `MyBase` 不能用來限定自己。 因此，下列程式碼無效：

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase` 不能用在模組中。

- 如果基類位於不同的元件中，`MyBase` 不能用來存取標示為 `Friend` 的基類成員。

如需詳細資訊和另一個範例，請參閱[如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。

## <a name="the-myclass-keyword"></a>MyClass 關鍵字

`MyClass` 關鍵字的行為就像是物件變數，它會參考原本實作為之類別的目前實例。 `MyClass` 類似 `Me`，但 `MyClass` 上的每個方法和屬性呼叫都會被視為[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)方法或屬性。 因此，方法或屬性不會受到在衍生類別中覆寫的影響。

- `MyClass` 是關鍵字，而不是真正的物件。 `MyClass` 無法指派給變數、傳遞至程式，或用於 `Is` 比較。

- `MyClass` 是指包含的類別及其繼承的成員。

- `MyClass` 可用來做為 `Shared` 成員的限定詞。

- `MyClass` 不能用在 `Shared` 方法內，但是可以在實例方法內用來存取類別的共用成員。

- `MyClass` 不能用於標準模組。

- `MyClass` 可用來限定在基類中定義的方法，而且不會執行該類別中提供的方法。 這類參考與 `MyBase.`*方法*具有相同的意義。

下列範例會比較 `Me` 和 `MyClass`。

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

雖然 `derivedClass` 覆寫 `testMethod`，`useMyClass` 中的 `MyClass` 關鍵字會 nullifies 覆寫的效果，而編譯器會解析基類版本 `testMethod`的呼叫。

## <a name="see-also"></a>請參閱

- [Inherits 陳述式](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
