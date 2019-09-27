---
title: HOW TO：撰寫擴充方法（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 31ccb18e0e6d1569764ec2a67201d7f758129425
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332764"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>HOW TO：撰寫擴充方法（Visual Basic）

擴充方法可讓您將方法加入至現有的類別。 您可以呼叫擴充方法，就像它是該類別的實例一樣。

### <a name="to-define-an-extension-method"></a>定義擴充方法

1. 在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。

2. 在您要定義擴充方法的檔案頂端，加入下列 import 語句：

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. 在新的或現有應用程式的模組內，使用擴充屬性來開始方法定義：

    ```vb
    <Extension()>
    ```

4. 以一般方式宣告方法，不同之處在于第一個參數的類型必須是您想要擴充的資料類型。

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>範例

 下列範例會在模組 `StringExtensions` 中宣告擴充方法。 第二個模組 `Module1`，會匯入 `StringExtensions`，並呼叫方法。 呼叫擴充方法時，它必須在範圍內。 擴充方法 `PrintAndPunctuate` 會使用方法來擴充 @no__t 1 類別，該方法會顯示字串實例，後面接著以參數的形式傳送的標點符號符號字串。
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 請注意，方法是使用兩個參數所定義，而且只會使用一個呼叫。 方法定義中的第一個參數（`aString`）系結至 `example`，也就是呼叫方法的 `String` 的實例。 此範例的輸出如下：
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [擴充方法](extension-methods.md)
- [Module 陳述式](../../../language-reference/statements/module-statement.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [Visual Basic 中的範圍](../declared-elements/scope.md)
