---
title: "使用轉換運算子 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "轉換運算子 [C#]"
  - "轉換 [C#], 運算子"
  - "明確轉換運算子 [C#]"
  - "隱含轉換運算子 [C#]"
  - "運算子 [C#], 轉換"
  - "使用者定義的轉換範例 [C#]"
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# 使用轉換運算子 (C# 程式設計手冊)
您可以使用比較容易上手的 `implicit` 轉換運算子，或者用可以向任何人清楚表達你所轉換的程式碼的 `explicit` 轉換運算子。  這個主題示範轉換運算子的兩個型別。  
  
> [!NOTE]
>  如需簡單型別轉換子的資訊，請參閱 [如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)，[如何：將位元組陣列轉換成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)或<xref:System.Convert>。  
  
## 範例  
 下面示範如何使用明確轉換運算子。  此運算子會從 <xref:System.Byte> 型別轉換至名為 `Digit` 的數值型別。  因為並非所有的位元都可以轉換成數字，所以轉換是明確的，意思就是必須使用轉型 \(Cast\)，如 `Main` 方法中所示。  
  
 [!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## 範例  
 此範例示範隱含轉換運算子，方法為定義會復原先前範例所執行作業的轉換運算子：它會從名為 `Digit` 的數值類別轉換成整數 <xref:System.Byte> 型別。  因為任何數字都可轉換成 <xref:System.Byte>，所以不需要強制使用者明確轉換。  
  
 [!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [is](../../../csharp/language-reference/keywords/is.md)