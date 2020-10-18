---
title: 不會推斷變數 '<variablename>' 的類型，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 3e76ffea283de2843fc5586179074c01a053ece8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161279"
---
# <a name="bc42110-the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>BC42110：將不會推斷變數 ' ' 的類型， \<variablename> 因為它已系結至封閉範圍內的欄位

\<variablename>將不會推斷變數 ' ' 的類型，因為它已系結至封閉範圍內的欄位。 請變更 ' ' 的名稱 \<variablename> ，或使用完整名稱 (例如 ' variablename ' 或 ' MyBase. variablename ' ) 。

您程式碼中的迴圈控制變數與類別或其他封閉範圍的欄位有相同的名稱。 因為在沒有子句的情況下使用控制項變數 `As` ，所以它會系結至封閉範圍內的欄位，而編譯器不會為它建立新的變數或推斷其型別。

在下列範例中， `Index` 語句中的控制項變數系結 `For` 至 `Index` 類別中的欄位 `Customer` 。 編譯器不會為控制項變數建立新的變數 `Index` 或推斷其型別。

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

## <a name="to-address-this-warning"></a>解決這個警告

- 將迴圈控制變數的名稱變更為不是類別之功能變數名稱的識別碼，以使其變成本機。

  ```vb
  For I = 1 To 10
  ```

- 請注意，迴圈控制變數會藉由在變數名稱前面加上系結至類別欄位 `Me.` 。

  ```vb
  For Me.Index = 1 To 10
  ```

- 您 `As` 可以使用子句來指定迴圈控制變數的類型，而不需要依賴區欄位型別推斷。

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>範例

 下列程式碼顯示先前的範例，其中的第一個更正已備妥。

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
