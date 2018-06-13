---
title: 如何：撰寫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648729"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>如何：撰寫擴充方法 (Visual Basic)
擴充方法可讓您將方法加入至現有的類別。 可以呼叫擴充方法，就好像該類別的執行個體。  
  
### <a name="to-define-an-extension-method"></a>若要定義的擴充方法  
  
1.  Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。  
  
2.  在您要定義的擴充方法的檔案頂端，加入下列 import 陳述式：  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  在新的或現有應用程式中的模組，開始使用擴充屬性和方法定義：  
  
    ```  
    <Extension()>  
    ```  
  
4.  第一個參數的型別必須是您想要擴充的資料類型，請以一般方式，宣告您的方法。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>範例  
 下列範例宣告模組中的擴充方法`StringExtensions`。 第二個模組， `Module1`，匯入`StringExtensions`呼叫的方法。 擴充方法必須在範圍內呼叫它。 擴充方法`PrintAndPunctuate`擴充<xref:System.String>類別顯示的字串執行個體的方法後面的標點符號中傳送做為參數的字串。  
  
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
  
 請注意，方法是使用兩個參數定義只有一個呼叫。 第一個參數， `aString`，方法中定義為繫結至`example`，執行個體`String`用來呼叫方法。 範例的輸出如下所示：  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [擴充方法](./extension-methods.md)  
 [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
