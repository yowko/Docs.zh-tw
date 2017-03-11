---
title: "operator (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "operator_CSharpKeyword"
  - "operator"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "運算子關鍵字 [C#]"
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# operator (C# 參考)
使用 `operator` 關鍵字可在類別或結構 \(Struct\) 宣告內多載內建運算子或提供使用者定義的轉換。  
  
## 範例  
 以下是一個極為簡化的分數類別，  它會多載 \+ 和 \* 運算子，以便執行分數的加法和乘法運算，並提供一個可將分數 \(Fraction\) 型別轉換為雙精度浮點數 \(Double\) 型別的轉換運算子。  
  
 [!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/csharp/operator_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [隱含](../../../csharp/language-reference/keywords/implicit.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)