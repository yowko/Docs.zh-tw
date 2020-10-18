---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f5b8b226d46afa0555559de0930f20025ba27f2b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162761"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a>BC42026：運算式以遞迴方式呼叫包含的屬性 ' \<propertyname> '

屬性定義的程式中的語句會將 `Set` 值儲存到屬性的名稱。

 保留屬性值的建議方法是在 `Private` 屬性的容器中定義變數，並在和程式中使用它 `Get` `Set` 。 然後，程式 `Set` 應該將傳入值儲存在此 `Private` 變數中。

 `Get`程式的行為就像程式一樣 `Function` ，因此它可以將值指派給屬性名稱，並藉由遇到語句來傳回控制項 `End Get` 。 不過，建議的方法是 `Private` 在 [Return 語句](../statements/return-statement.md)中包含變數作為值。

 程式的 `Set` 行為就像是 `Sub` 不會傳回值的程式。 因此，程式或屬性名稱在程式內沒有特殊意義 `Set` ，而且您無法將值儲存到其中。

 下列範例說明可能會導致此錯誤的方法，後面接著建議的方法。

```vb
Public Class illustrateProperties
' The code in the following property causes this error.
    Public Property badProp() As Char
        Get
            Dim charValue As Char
            ' Insert code to update charValue.
            badProp = charValue
        End Get
        Set(ByVal Value As Char)
            ' The following statement causes this error.
            badProp = Value
            ' The value stored in the local variable badProp
            ' is not used by the Get procedure in this property.
        End Set
    End Property
' The following code uses the recommended approach.
    Private propValue As Char
    Public Property goodProp() As Char
        Get
            ' Insert code to update propValue.
            Return propValue
        End Get
        Set(ByVal Value As Char)
            propValue = Value
        End Set
    End Property
End Class
```

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱設定 [Visual Basic 中的警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42026

## <a name="to-correct-this-error"></a>更正這個錯誤

- 重寫屬性定義以使用建議的方法，如上述範例所示。

## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Set 語句](../statements/set-statement.md)
