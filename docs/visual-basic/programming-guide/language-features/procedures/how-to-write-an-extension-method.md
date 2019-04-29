---
title: HOW TO：撰寫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665997"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>HOW TO：撰寫擴充方法 (Visual Basic)
擴充方法可讓您將方法加入至現有的類別。 可以呼叫擴充方法，如同它是該類別的執行個體。  
  
### <a name="to-define-an-extension-method"></a>若要定義擴充方法  
  
1. Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。  
  
2. 在您要在其中定義擴充方法的檔案頂端，加入下列 import 陳述式：  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. 在新的或現有應用程式中的模組，開始以擴充屬性的方法定義：  
  
    ```  
    <Extension()>  
    ```  
  
4. 不同之處在於第一個參數的型別必須是您想要擴充的資料類型，請以一般方式，宣告您的方法。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>範例  
 下列範例會宣告模組中的擴充方法`StringExtensions`。 第二個模組中， `Module1`，匯入`StringExtensions`並呼叫方法。 當呼叫它時，擴充方法必須在範圍內。 擴充方法`PrintAndPunctuate`擴充<xref:System.String>類別的方法，顯示的字串執行個體後面的標點符號中做為參數傳送的文字字串。  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
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
  
 請注意此方法時，定義具有兩個參數，而且呼叫只會與一個。 第一個參數， `aString`，在方法中定義繫結至`example`，執行個體`String`所呼叫的方法。 此範例的輸出如下：  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [擴充方法](./extension-methods.md)
- [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
