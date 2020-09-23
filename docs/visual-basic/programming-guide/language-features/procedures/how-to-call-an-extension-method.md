---
title: 如何：呼叫擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 38d6e8534283f475be2409f4b7c74ef48f1f248b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91074988"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>如何：呼叫擴充方法 (Visual Basic)

擴充方法可讓您將方法加入至現有的類別。 在宣告擴充方法並進入範圍之後，您可以呼叫它，就像它所擴充之類型的實例方法一樣。 如需如何撰寫擴充方法的詳細資訊，請參閱 how [to：撰寫擴充方法](./how-to-write-an-extension-method.md)。

 下列指示參考擴充方法，此方法 `PrintAndPunctuate` 會顯示叫用它的字串實例，然後在中傳送任何值給第二個參數 `punc` 。

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

呼叫方法時，該方法必須在範圍內。

### <a name="to-call-an-extension-method"></a>呼叫擴充方法

1. 宣告具有擴充方法第一個參數之資料類型的變數。 針對 `PrintAndPunctuate` ，您需要 <xref:System.String> 變數：

    ```vb
    Dim example = "Ready"
    ```

2. 該變數將會叫用擴充方法，且其值會系結至第一個參數 `aString` 。 將會顯示下列呼叫語句 `Ready?` 。

    ```vb
    example.PrintAndPunctuate("?")
    ```

     請注意，對此擴充方法的呼叫看起來就像呼叫任何一個 <xref:System.String> 需要一個參數的實例方法一樣：

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. 宣告另一個字串變數，並再次呼叫方法，以查看它是否可搭配任何字串使用。

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     這次的結果為： `or not!!!` 。

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
- [Visual Basic 中的範圍](../declared-elements/scope.md)
