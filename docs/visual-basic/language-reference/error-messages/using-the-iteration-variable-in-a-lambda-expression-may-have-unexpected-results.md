---
title: "Using the iteration variable in a lambda expression may have unexpected results | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42324"
  - "bc42324"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42324"
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Using the iteration variable in a lambda expression may have unexpected results
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果。請改為在迴圈內建立區域變數，並指派它反覆運算變數的值。  
  
 當您在迴圈內宣告的 Lambda 運算式中使用迴圈反覆運算變數時，會出現此警告。  例如，下列範例會導致警告出現。  
  
```vb#  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 下列範例顯示可能發生的未預期結果。  
  
```vb#  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For` 迴圈會建立 Lambda 運算式陣列，每個運算式會傳回迴圈反覆運算變數 `i` 的值。  當 Lambda 運算式在 `For Each` 迴圈中評估時，您可能會預期看到 0、1、2、3 和 4 顯示，也就是 `For` 迴圈中 `i` 的連續值。  但是，您看到的卻會是 `i` 的最後一個值顯示五次：  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**：BC42324  
  
### 若要更正這個錯誤  
  
-   將反覆運算變數的值指派給區域變數，然後在 Lambda 運算式中使用該區域變數。  
  
    ```vb#  
    Module Module1  
        Sub Main()  
            Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
            For i As Integer = 0 To 4  
                Dim j = i  
                array1(i) = Function() j  
            Next  
  
            For Each funcElement In array1  
                System.Console.WriteLine(funcElement())  
            Next  
  
        End Sub  
    End Module  
    ```  
  
## 請參閱  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)