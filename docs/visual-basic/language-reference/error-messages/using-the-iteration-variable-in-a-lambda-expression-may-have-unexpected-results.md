---
title: 在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 7144a5fd4a197fddaf1ac4132df0ff70995ad067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>在 Lambda 運算式中使用反覆運算變數可能會產生非預期的結果
Lambda 運算式中使用反覆運算變數可能會產生非預期的結果。 相反地，建立在迴圈內的區域變數，並將它指派反覆項目變數的值。  
  
 當您使用迴圈反覆項目變數的宣告在迴圈內部的 lambda 運算式中，會出現這個警告。 例如，下列範例會顯示警告。  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 下列範例顯示可能會發生非預期的結果。  
  
```vb  
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
  
 `For`迴圈建立其中每個迴圈反覆項目變數的值會傳回 lambda 運算式的陣列`i`。 Lambda 運算式中的評估時`For Each`迴圈中，您可能會看到 0、 1、 2、 3 和 4 顯示，後續的值`i`中`For`迴圈。 相反地，您會看到的最終值`i`顯示五次：  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42324  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將反覆運算變數的值指派給區域變數，並在 lambda 運算式中使用此區域變數。  
  
```vb  
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
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
