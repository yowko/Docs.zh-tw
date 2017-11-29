---
title: "如何：呼叫擴充方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>如何：呼叫擴充方法 (Visual Basic)
擴充方法可讓您將方法加入至現有的類別。 擴充方法宣告，然後帶入範圍之後，您可以像擴充類型的執行個體方法呼叫它。 如需如何撰寫擴充方法的詳細資訊，請參閱[How to： 撰寫擴充方法](./how-to-write-an-extension-method.md)。  
  
 擴充方法，請參閱下列指示`PrintAndPunctuate`，這會顯示叫用它，後面接著任何值的字串執行個體中的第二個參數，傳送`punc`。  
  
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
  
### <a name="to-call-an-extension-method"></a>呼叫擴充方法  
  
1.  宣告具有擴充方法的第一個參數的資料類型的變數。 如`PrintAndPunctuate`，您需要<xref:System.String>變數：  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  變數將會叫用擴充方法，和其值會繫結至第一個參數， `aString`。 下列呼叫的陳述式將會顯示`Ready?`。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     請注意，這個擴充方法的呼叫看起來就像呼叫任何一個<xref:System.String>執行個體需要一個參數的方法：  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  宣告另一個字串變數，並呼叫方法，一次，以查看其運作以任何字串。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     結果現在是： `or not!!!`。  
  
## <a name="example"></a>範例  
 下列程式碼是完整的範例，在建立和使用簡單的擴充方法。  
  
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
 [如何：撰寫擴充方法](./how-to-write-an-extension-method.md)  
 [擴充方法](./extension-methods.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
