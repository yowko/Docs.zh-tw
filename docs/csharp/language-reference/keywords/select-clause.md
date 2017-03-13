---
title: "select 子句 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "select_CSharpKeyword"
  - "select"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "select 子句 [C#]"
  - "select 關鍵字 [C#]"
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# select 子句 (C# 參考)
在查詢運算式中，`select` 子句會指定執行查詢時，將產生的實值型別。  結果是根據所有先前子句的評估和 `select` 子句本身的任何運算式而得。  查詢運算式必須終止 `select` 子句或 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句。  
  
 下列範例顯示查詢運算式中簡單的 `select` 子句。  
  
 [!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 `select` 子句產生的序列型別會決定查詢變數 `queryHighScores` 的型別。  在最簡單的情況下，`select` 子句只要指定範圍變數。  這會使傳回的序列包含與資料來源相同型別的項目。  如需詳細資訊，請參閱[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  但是，`select` 子句也提供功能強大的機制，可將來源資料轉換 \(或「*投影*」\(Projecting\)\) 為新型別。  如需詳細資訊，請參閱 [使用 LINQ 轉換資料 \(C\#\)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)。  
  
## 範例  
 下列範例顯示 `select` 子句可能會採用的不同格式。  在每個查詢中，請注意 `select` 子句與「*查詢變數*」\(Query Variable\) \(`studentQuery1`、`studentQuery2` 等等\) 之型別之間的關係。  
  
 [!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 如同前述範例中的 `studentQuery8` 所示，有時您可能想要傳回之序列的項目只包含來源項目之屬性的子集。  盡可能使傳回的序列越小，您就可以減少記憶體需求，並且增加執行查詢的速度。  您可以藉由在 `select` 子句中建立匿名型別，以及使用物件初始設定式以來源項目的適當屬性進行初始化，達成這個目的。  如需如何進行的範例，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## 備註  
 在編譯時期，`select` 子句會轉譯成對 <xref:System.Linq.Enumerable.Select%2A> 標準查詢運算子的方法呼叫。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 子句](../../../csharp/language-reference/keywords/from-clause.md)   
 [partial \(方法\) \(C\# 參考\)](../../../csharp/language-reference/keywords/partial-method.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)