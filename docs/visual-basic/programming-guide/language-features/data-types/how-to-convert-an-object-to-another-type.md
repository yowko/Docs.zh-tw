---
title: "How to: Convert an Object to Another Type in Visual Basic | Microsoft Docs"
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
  - "objects [Visual Basic], converting"
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Convert an Object to Another Type in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

使用 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md) 這類的轉換關鍵字，即可以將 `Object` 變數轉換成其他資料型別。  
  
## 範例  
 下列範例會將 `Object` 變數轉換成 `Integer` 或 `String`。  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 如果已知 `Object` 變數的內容是屬於某特定資料型別，最好將變數轉換成該資料型別。  如果持續使用 `Object` 變數，可能會導致 *Boxing* 和 *Unboxing* \(針對實值型別\) 或「*晚期繫結*」\(Late binding\) \(針對參考型別\)。  而這些作業都會花費額外的執行時間，導致效能減低。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   對 <xref:System?displayProperty=fullName> 命名空間的參考。  
  
## 請參閱  
 <xref:System.Object>   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)