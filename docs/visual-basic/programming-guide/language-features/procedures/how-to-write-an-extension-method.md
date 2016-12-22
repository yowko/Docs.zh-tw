---
title: "How to: Write an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "extending data types"
  - "writing extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

擴充方法讓您能夠將方法加入至現有的類別。  可以將擴充方法當做該類別的執行個體來呼叫。  
  
### 若要定義擴充方法  
  
1.  在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。  
  
2.  在您要定義擴充方法的檔案頂端，加入下列匯入陳述式：  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  在新的或現有應用程式的模組內，使用擴充屬性開始方法定義：  
  
    ```  
    <Extension()>  
    ```  
  
4.  以一般方式宣告方法，不過第一個參數的型別必須是您要擴充的資料型別。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## 範例  
 下列範例會在 `StringExtensions` 模組中宣告擴充方法。  第二個模組 `Module1` 會匯入 `StringExtensions` 並呼叫該方法。  呼叫時，該擴充方法必須在範圍內。  擴充方法 `PrintAndPunctuate` 會使用方法擴充 <xref:System.String> 類別，而這個方法會顯示字串執行個體，後面接著當做參數傳送的標點符號字串。  
  
```vb#  
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
  
```vb#  
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
  
 請注意，定義方法時會搭配兩個參數，但只會搭配一個參數來呼叫方法。  方法定義中的第一個參數 `aString` 會繫結至 `example`，這是呼叫方法的 `String` 執行個體。  範例的輸出如下：  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)