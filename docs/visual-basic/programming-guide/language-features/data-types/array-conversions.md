---
title: "Array Conversions (Visual Basic) | Microsoft Docs"
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
  - "arrays [Visual Basic], converting type"
  - "type conversion, arrays"
  - "conversions, type"
  - "arrays [Visual Basic], data types"
  - "conversions, data type"
  - "object arrays, converting type"
  - "data type conversion, array conversions"
  - "conversions, array types"
  - "object arrays"
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Array Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以將一種陣列型別 \(Array Type\) 轉換為不同的陣列型別，但必須先符合以下條件：  
  
-   **相等陣序**： 兩陣列的陣序規範必須相同，也就是必須有相同的維度數目。  不過各自維度的長度不一定要相同。  
  
-   **元素資料型別**： 兩陣列元素的資料型別必須是參考型別 \(Reference Type\)。  您無法將 `Integer` 陣列轉換為 `Long` 陣列，甚或是 `Object` 陣列，這是因為其中都至少有一實值型別。  如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
-   **轉換能力**： 兩陣列的元素型別之間必須能夠進行擴大或縮小轉換。  `String` 陣列與衍生自 <xref:System.Attribute?displayProperty=fullName> 類別的陣列間無法進行擴大或縮小轉換的範例即為嘗試轉換。  這兩種型別完全不同，它們之間也不存在任何種類的轉換。  
  
 從一陣列型別轉換為另一陣列型別是屬於擴大或縮小，這要根據各自元素的轉換是擴大或縮小而定。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## 轉換為 Object 陣列  
 若您在宣告 `Object` 陣列之前未先初始化，則在尚未初始化之前，陣列的元素型別都是 `Object`。  若您將它設定為特定類別的陣列，它會使用這個類別的型別。  不過它的基礎型別仍然是 `Object`，接下來您可以將它設定為不相關類別的其他陣列。  由於所有的類別都衍生自 `Object`，您可以將任何類別的陣列元素型別改變成任何其他類別。  
  
 在下列範例中，`student` 型別和 `String` 之間沒有轉換，但型別都衍生自 `Object`，所以所有的指派都有效。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### 陣列的基礎型別  
 如果您原本宣告特定類別的陣列，則它的基礎元素型別是這個類別。  如果您隨後將它設定為其他類別的陣列，則在兩個類別之間必須有轉換。  
  
 在下列範列中，`students` 是 `student` 陣列。  由於 `String` 與 `student` 之間未進行轉換，最後的陳述式並未成功。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## 請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)