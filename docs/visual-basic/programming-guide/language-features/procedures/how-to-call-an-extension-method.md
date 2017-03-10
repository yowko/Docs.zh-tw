---
title: "How to: Call an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "calling extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Call an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

擴充方法讓您能夠將方法加入至現有的類別。  宣告擴充方法並將其帶入範圍之後，您就可以呼叫該擴充方法，如同所擴充之型別的執行個體方法一樣。  如需如何撰寫擴充方法的詳細資訊，請參閱 [How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md)。  
  
 下列指示會參考擴充方法 `PrintAndPunctuate`，而這會顯示用來叫用此方法的字串執行個體，後面跟著針對第二個參數 `punc` 所傳送的值。  
  
```vb#  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
  
```  
  
 呼叫該方法時，該方法必須是在範圍內。  
  
### 若要呼叫擴充方法  
  
1.  宣告變數，這個變數具有擴充方法之第一個參數的資料型別。  如果是 `PrintAndPunctuate`，您就需要 <xref:System.String> 變數：  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  該變數會叫用擴充方法，而其值會繫結至第一個參數 `aString`。  下列呼叫陳述式將顯示 `Ready?`。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     請注意，這個擴充方法的呼叫就像其中一個需要一個參數之 <xref:System.String> 執行個體方法的呼叫一樣：  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  宣告其他字串變數並再次呼叫方法，以查看它是否可搭配任何字串來運作。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     這次的結果為：`or not!!!`。  
  
## 範例  
 下列程式碼是建立和使用簡單擴充方法的完整範例。  
  
```vb#  
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
  
## 請參閱  
 [How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md)   
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)