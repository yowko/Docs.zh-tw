---
title: 作法：呼叫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512665"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>作法：呼叫擴充方法 (Visual Basic)

擴充方法可讓您將方法加入至現有的類別。 在宣告擴充方法並將其納入範圍之後, 您就可以像它所擴充之類型的實例方法一樣呼叫它。 如需如何撰寫擴充方法的詳細資訊, 請參閱[如何:撰寫擴充方法](./how-to-write-an-extension-method.md)。

 下列指示會參考擴充方法`PrintAndPunctuate`, 它會顯示叫用它的字串實例, 後面接著針對第二個`punc`參數傳送的任何值。

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

方法在呼叫時必須在範圍內。

### <a name="to-call-an-extension-method"></a>呼叫擴充方法

1. 宣告具有擴充方法第一個參數之資料類型的變數。 針對`PrintAndPunctuate`, 您需要一個<xref:System.String>變數:

    ```vb
    Dim example = "Ready"
    ```

2. 該變數會叫用擴充方法, 而且其值會系結至第一個參數`aString`。 將會顯示`Ready?`下列呼叫語句。

    ```vb
    example.PrintAndPunctuate("?")
    ```

     請注意, 此擴充方法的呼叫看起來就像是呼叫任何一個<xref:System.String>需要一個參數的實例方法一樣:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. 請宣告另一個字串變數, 然後再次呼叫方法, 以查看它是否能與任何字串搭配使用。

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     這次的結果是: `or not!!!`。

## <a name="example"></a>範例
 下列程式碼是建立和使用簡單擴充方法的完整範例。

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a>另請參閱

- [如何：撰寫擴充方法](./how-to-write-an-extension-method.md)
- [擴充方法](./extension-methods.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
