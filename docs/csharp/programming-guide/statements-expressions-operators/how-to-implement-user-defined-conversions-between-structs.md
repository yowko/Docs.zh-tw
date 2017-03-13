---
title: "如何：在結構之間實作使用者定義的轉換 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "使用者定義的轉換範例 [C#]"
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# 如何：在結構之間實作使用者定義的轉換 (C# 程式設計手冊)
本範例定義兩個結構：`RomanNumeral` 和 `BinaryNumeral`，並說明它們之間的轉換。  
  
## 範例  
 [!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## 穩固程式設計  
  
-   在前面的範例中，陳述式：  
  
     [!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     會執行轉換，從 `RomanNumeral` 轉換為 `BinaryNumeral`。  因為 `RomanNumeral` 和 `BinaryNumeral` 之間並沒有直接轉換，所以使用型別轉換以將 `RomanNumeral` 轉換成 `int`，並且使用另一個型別轉換以將 `int` 轉換成 `BinaryNumeral`。  
  
-   同時，陳述式  
  
     [!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     會執行轉換，從 `BinaryNumeral` 轉換為 `RomanNumeral`。  因為 `RomanNumeral` 定義了一個從 `BinaryNumeral` 轉換的隱含轉換，所以不需要轉換。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)