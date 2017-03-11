---
title: "as (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "as_CSharpKeyword"
  - "as"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "as 關鍵字 [C#]"
  - "類型轉換 [C#], as 關鍵字"
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# as (C# 參考)
您可以使用 `as` 運算子執行轉換的某些型別在相容的參考型別或 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)的。  下列程式碼示範一個範例。  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#1)]  
  
## 備註  
 `as` 運算子就像是轉型作業。  不過，，如果無法轉換的 `as` 傳回 `null` ，而不會引發例外狀況。  參考下列範例：  
  
```  
expression as type  
```  
  
 程式碼與下列運算式相同，除了 `expression` 變數只會評估一次。  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 請注意 `as` 運算子執行只參考轉換、可轉換及 Boxing 轉換。  `as` 運算子無法執行其他轉換方式，例如使用者定義的轉換，應該執行使用 cast 運算式。  
  
## 範例  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#2)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?: 運算子](../../../csharp/language-reference/operators/conditional-operator.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)