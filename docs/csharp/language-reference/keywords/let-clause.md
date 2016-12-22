---
title: "let 子句 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "let_CSharpKeyword"
  - "let"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "let 子句 [C#]"
  - "let 關鍵字 [C#]"
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# let 子句 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在查詢運算式中，若要將子運算式的結果用於後續子句，則儲存子運算式的結果有時會十分有用。  做法是使用 `let` 關鍵字，這個關鍵字會建立新的範圍變數，並利用提供的運算式結果來初始化這個範圍變數。  使用值進行初始化之後，就不可以再使用範圍變數來儲存另一個值。  不過，如果範圍變數保留的是可查詢的型別，則還是可以對它進行查詢。  
  
## 範例  
 在下列範例中，`let` 有兩種使用方式：  
  
1.  建立本身可以進行查詢的可列舉型別。  
  
2.  讓查詢只在範圍變數 `word` 上呼叫一次 `ToLower`。  如果未使用 `let`，就需要在 `where` 子句的每個述詞 \(Predicate\) 中呼叫 `ToLower`。  
  
 [!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [如何：處理查詢運算式中的例外狀況](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)