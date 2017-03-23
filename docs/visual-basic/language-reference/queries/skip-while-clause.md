---
title: "Skip While Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySkipWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Skip While statement"
  - "Skip While clause"
  - "queries [Visual Basic], Skip While"
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Skip While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

一直略過集合中的項目，直到指定的條件不為 `true`，然後傳回剩餘項目。  
  
## 語法  
  
```  
Skip While expression  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`expression`|必要項。  運算式，表示要對項目測試的條件。  這個運算式必須傳回 `Boolean` 值或功能上的對等用法，例如待評估為 `Boolean` 的 `Integer`。|  
  
## 備註  
 `Skip While` 子句會自查詢結果開頭起一直略過項目，直到提供的 `expression` 傳回 `false` 為止。  在 `expression` 傳回 `false` 之後，查詢會傳回所有剩餘項目。  傳回剩餘結果時會略過 `expression`。  
  
 `Skip While` 子句跟`Where` 子句有個不同點，即 `Where` 子句可用來排除查詢中所有不符合特定條件的項目。  `Skip While` 子句則只會排除在第一次不符合條件之前遇到的項目。  當您使用已排序的查詢結果時，`Skip While` 子句會很有幫助。  
  
 您可以使用 `Skip` 子句，略過查詢結果的前幾筆結果。  
  
## 範例  
 下列程式碼範例會使用 `Skip While` 子句一直略過結果，直到找到第一個美國客戶為止。  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)