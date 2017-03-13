---
title: "orderby 子句 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "orderby"
  - "orderby_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "orderby 子句 [C#]"
  - "orderby 關鍵字 [C#]"
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# orderby 子句 (C# 參考)
在查詢運算式中，`orderby` 子句會使傳回的序列或子序列 \(群組\) 以遞增或遞減的順序排序。  可以指定多個索引鍵，以執行一個或多個次要排序作業。  排序是由項目型別的預設比較子 \(Comparer\) 執行。  預設的排序次序為遞增。  您還可以指定自訂比較子。  但是，只能使用方法架構的語法指定。  如需詳細資訊，請參閱 [Sorting Data](../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)。  
  
## 範例  
 在下列範例中，第一個查詢會從 A 開始以字母順序排序文字，第二個查詢會以遞減順序排序相同的文字   \(`ascending` 關鍵字是預設排序值，無法略過\)。  
  
 [!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## 範例  
 下列範例執行學生姓氏的主要排序，然後執行名字的次要排序。  
  
 [!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## 備註  
 在編譯時期，`orderby` 子句會轉譯成 <xref:System.Linq.Enumerable.OrderBy%2A> 方法的呼叫。  `orderby` 子句中的多個索引鍵會轉譯成 <xref:System.Linq.Enumerable.ThenBy%2A> 方法的呼叫。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)