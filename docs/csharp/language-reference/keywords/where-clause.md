---
title: "where 子句 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "whereclause_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "where 子句 [C#]"
  - "where 關鍵字 [C#]"
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# where 子句 (C# 參考)
在查詢運算式中，`where` 子句是用來指定資料來源的哪個項目將會在查詢運算式中傳回。  它會將布林值 \(Boolean\) 條件 \(「*述詞*」\(Predicate\)\) 套用到每個來源項目 \(由範圍變數參考\)，並傳回指定條件為 True 的項目。  單一查詢運算式可能包含多個 `where` 子句，而且單一子句可能包含多個述詞子運算式 \(Subexpression\)。  
  
## 範例  
 在下列範例中，`where` 子句會篩選掉不小於 5 的所有數字。  如果您移除 `where` 子句，便會傳回資料來源的所有數字。  運算式 `num < 5` 就是套用至每個項目的述詞。  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#5)]  
  
## 範例  
 在單一 `where` 子句內，您可以使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 運算子，指定任何所需要的述詞。  在下列範例中，查詢會指定兩個述詞，以便只選取小於 5 的偶數。  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#6)]  
  
## 範例  
 `where` 子句可能包含一個或多個傳回布林值的方法。  在下列範例中，`where` 子句會使用一個方法來判斷範圍變數的目前值為偶數或奇數。  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#7)]  
  
## 備註  
 `where` 子句是一項篩選機制。  它可以放置在查詢運算式的絕大多數位置，除了不能放置在第一個或最後一個子句中。  `where` 子句會根據需要在來源項目完成分組之前或之後篩選來源項目，而出現在 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句的之前或之後。  
  
 如果指定的述詞對於資料來源中的項目無效，便會造成編譯時期錯誤。  這是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 所提供強型別檢查的其中一項優點。  
  
 在編譯時期，`where` 關鍵字便會轉換成對 <xref:System.Linq.Enumerable.Where%2A> 標準查詢運算子方法的呼叫。  
  
## 請參閱  
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 子句](../../../csharp/language-reference/keywords/from-clause.md)   
 [select 子句](../../../csharp/language-reference/keywords/select-clause.md)   
 [Filtering Data](../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)