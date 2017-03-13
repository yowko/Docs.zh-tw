---
title: "partial (方法) (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "partialmethod_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "部分方法 [C#]"
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# partial (方法) (C# 參考)
部分方法的簽章是在部分型別的一部分中定義，而其實作是在型別的另一部分中定義。  部分方法可以讓類別設計工具提供方法連結，類似開發人員可能會決定是否實作的事件處理常式。  如果開發人員未提供實作，編譯器會在編譯時期移除簽章。  下列條件適用於部分方法：  
  
-   部分型別兩個部分中的簽章必須相符。  
  
-   方法必須傳回 void。  
  
-   沒有存取修飾詞是被允許的。  部分方法都是隱含的私用方法。  
  
 下列範例顯示部分類別兩個部分中定義的部分方法：  
  
 [!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [partial \(類型\)](../../../csharp/language-reference/keywords/partial-type.md)