---
title: 在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: d0deea94084565ea91debe2b6db30def4cd9e00e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161487"
---
# <a name="bc42324-using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>BC42324：在 lambda 運算式中使用反覆運算變數可能會產生非預期的結果

在 lambda 運算式中使用反覆運算變數可能會產生非預期的結果。 相反地，請在迴圈中建立區域變數，並為其指派反覆運算變數的值。

 當您在迴圈內部宣告的 lambda 運算式中使用迴圈反覆運算變數時，就會出現這個警告。 例如，下列範例會顯示警告。

```vb
For i As Integer = 1 To 10
    ' The warning is given for the use of i.
    Dim exampleFunc As Func(Of Integer) = Function() i
Next
```

 下列範例會顯示可能發生的非預期結果。

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            array1(i) = Function() i
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

 `For`迴圈會建立 lambda 運算式的陣列，每個運算式都會傳回迴圈反覆運算變數的值 `i` 。 在迴圈中評估 lambda 運算式時 `For Each` ，您可能預期會看到0、1、2、3和4顯示 `i` 在迴圈中的連續值 `For` 。 相反地，您會看到 `i` 顯示五次的最終值：

 `5`

 `5`

 `5`

 `5`

 `5`

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42324

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將反覆運算變數的值指派給區域變數，並使用 lambda 運算式中的本機變數。

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            Dim j = i
            array1(i) = Function() j
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
