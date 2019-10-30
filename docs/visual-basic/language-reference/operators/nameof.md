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
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="85fc3-103">NameOf 運算子-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85fc3-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="85fc3-104">`NameOf` 運算子會以字串常值格式取得變數、型別或成員的名稱：</span><span class="sxs-lookup"><span data-stu-id="85fc3-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

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

<span data-ttu-id="85fc3-105">如上述範例所示，在型別與命名空間的情況下，產生的名稱通常不是[完整](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)的。</span><span class="sxs-lookup"><span data-stu-id="85fc3-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="85fc3-106">`NameOf` 運算子會在編譯時間評估，在執行階段則不會有作用。</span><span class="sxs-lookup"><span data-stu-id="85fc3-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="85fc3-107">您可以使用 `NameOf` 運算子，讓檢查引數的程式碼更容易維護：</span><span class="sxs-lookup"><span data-stu-id="85fc3-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

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

<span data-ttu-id="85fc3-108">`NameOf` 運算子可在 Visual Basic 14 和更新版本中取得。</span><span class="sxs-lookup"><span data-stu-id="85fc3-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="85fc3-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="85fc3-109">See also</span></span>

- [<span data-ttu-id="85fc3-110">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="85fc3-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="85fc3-111">運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="85fc3-111">Operators (Visual Basic)</span></span>](index.md)
