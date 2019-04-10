---
title: HOW TO：呼叫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 5cb0684637a716dfec947740ba345c62eaabddd7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313797"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>HOW TO：呼叫擴充方法 (Visual Basic)
擴充方法可讓您將方法加入至現有的類別。 擴充方法宣告，然後帶入範圍之後，您可以呼叫它，如擴充類型的執行個體方法。 如需如何撰寫擴充方法的詳細資訊，請參閱[How to:撰寫擴充方法](./how-to-write-an-extension-method.md)。  
  
 下列指示，請參閱擴充方法`PrintAndPunctuate`，將會顯示叫用它後面的任何值的字串執行個體中的第二個參數，傳送`punc`。  
  
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
  
 呼叫時，此方法必須在範圍內。  
  
### <a name="to-call-an-extension-method"></a>若要呼叫擴充方法  
  
1. 宣告具有將擴充方法的第一個參數的資料類型的變數。 針對`PrintAndPunctuate`，您需要<xref:System.String>變數：  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2. 變數將會叫用擴充方法，和其值會繫結至第一個參數， `aString`。 下列呼叫的陳述式將會顯示`Ready?`。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     請注意，這個擴充方法的呼叫看起來就像對任何一種<xref:System.String>執行個體需要一個參數的方法：  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3. 宣告另一個字串變數，並呼叫方法，再以查看其運作以任何字串。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     結果這次是： `or not!!!`。  
  
## <a name="example"></a>範例  
 下列程式碼會建立完整範例，並使用簡單的延伸模組方法。  
  
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

- [HOW TO：撰寫延伸模組](./how-to-write-an-extension-method.md)
- [擴充方法](./extension-methods.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
