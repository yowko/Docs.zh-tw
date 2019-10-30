---
title: NameOf 運算子-Visual Basic
description: 瞭解如何在 Visual Basic 中使用 NameOf 運算子
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041314"
---
# <a name="nameof-operator---visual-basic"></a>NameOf 運算子-Visual Basic

`NameOf` 運算子會以字串常值格式取得變數、型別或成員的名稱：

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。

`NameOf` 運算子會在編譯時間評估，在執行階段則不會有作用。

您可以使用 `NameOf` 運算子，讓檢查引數的程式碼更容易維護：

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

`NameOf` 運算子可在 Visual Basic 14 和更新版本中取得。

## <a name="see-also"></a>請參閱

- [Visual Basic 語言參考](../index.md)
- [運算子（Visual Basic）](index.md)
