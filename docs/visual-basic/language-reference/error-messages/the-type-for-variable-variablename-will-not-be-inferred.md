---
title: 不會推斷變數 '<variablename>' 的類型，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363042"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>不會推斷變數 '\<variablename>' 的類型，因為它繫結至封閉範圍中的欄位

\<variablename>將不會推斷變數 ' ' 的類型，因為它已系結至封閉範圍中的欄位。 請變更 ' ' 的名稱 \<variablename> ，或使用完整名稱（例如 ' variablename ' 或 ' MyBase. variablename '）。

程式碼中的迴圈控制變數與類別或其他封閉範圍的欄位名稱相同。 因為在沒有子句的情況下使用控制變數 `As` ，所以它會系結至封閉範圍中的欄位，而編譯器不會為它建立新的變數或推斷其型別。

在下列範例中， `Index` 語句中的控制項變數會系結 `For` 至 `Index` 類別中的欄位 `Customer` 。 編譯器不會為控制項變數建立新的變數 `Index` 或推斷其型別。

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

根據預設，這個訊息是一個警告。 如需如何隱藏警告或如何將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

**錯誤識別碼：** BC42110

### <a name="to-address-this-warning"></a>解決這個警告

- 將迴圈控制變數的名稱變更為不是該類別的欄位名稱的識別碼，以將它設為區域變數。

  ```vb
  For I = 1 To 10
  ```

- 澄清迴圈控制變數會藉由在變數名稱前面加上來系結至類別欄位 `Me.` 。

  ```vb
  For Me.Index = 1 To 10
  ```

- 使用 `As` 子句來指定迴圈控制變數的類型，而不是依賴區欄位型別推斷。

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>範例
 下列程式碼顯示先前的範例，其中包含了第一個更正的位置。

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>另請參閱

- [Option Infer 陳述式](../statements/option-infer-statement.md)
- [For Each...Next 陳述式](../statements/for-each-next-statement.md)
- [For...Next 陳述式](../statements/for-next-statement.md)
- [如何：參考物件目前的執行個體](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
- [Me、My、MyBase 及 MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
