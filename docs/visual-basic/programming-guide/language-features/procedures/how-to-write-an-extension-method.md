---
title: 如何：撰寫擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 697508f86ff4ff0a89150b65782121395d0fed12
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346009"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>如何：撰寫擴充方法 (Visual Basic)

擴充方法可讓您將方法加入至現有的類別。 您可以呼叫擴充方法，就像它是該類別的實例一樣。

### <a name="to-define-an-extension-method"></a>定義擴充方法

1. 在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。

2. 在您要定義擴充方法的檔案頂端，加入下列 import 語句：

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. 在新的或現有應用程式的模組內，使用[`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute)屬性來開始方法定義：

    ```vb
    <Extension()>
    ```

    請注意，`Extension` 屬性只能套用至 Visual Basic[模組](../../../language-reference/statements/module-statement.md)中的方法（`Sub` 或 `Function` 程式）。 如果您將它套用至 `Class` 或 `Structure`中的方法，Visual Basic 編譯器會產生錯誤[BC36551](../../../misc/bc36551.md)「擴充方法只能在模組中定義」。

4. 以一般方式宣告方法，不同之處在于第一個參數的類型必須是您想要擴充的資料類型。

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>範例

下列範例會在模組 `StringExtensions`中宣告擴充方法。 第二個模組 `Module1`，會匯入 `StringExtensions` 並呼叫方法。 呼叫擴充方法時，它必須在範圍內。 擴充方法 `PrintAndPunctuate` 使用方法來擴充 <xref:System.String> 類別，並在其中顯示字串實例，後面接著以參數的形式傳送之標點符號符號的字串。

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

請注意，方法是使用兩個參數所定義，而且只會使用一個呼叫。 方法定義中的第一個參數（`aString`）會系結至 `example`，這是呼叫方法的 `String` 實例。 此範例的輸出如下：

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a>請參閱

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [擴充方法](extension-methods.md)
- [Module 陳述式](../../../language-reference/statements/module-statement.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [Visual Basic 中的範圍](../declared-elements/scope.md)
