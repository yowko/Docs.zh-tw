---
title: NameOf 運算子
description: 瞭解如何在 Visual Basic 中使用 NameOf 運算子
ms.date: 10/27/2019
f1_keywords:
- NameOf
- vb.NameOf
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 0e72c4cb0c10113e53067ea4a743ca5ee77bcc95
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828899"
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

`NameOf`操作員可在 Visual Basic 14 和更新版本中使用。

## <a name="see-also"></a>另請參閱

- [Visual Basic 語言參考](../index.md)
- [運算子 (Visual Basic)](index.md)
