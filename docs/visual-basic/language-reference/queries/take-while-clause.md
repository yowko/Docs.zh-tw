---
title: "Take While Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTakeWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Take While"
  - "Take While clause"
  - "Take While statement"
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Take While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

一直包含集合中的項目，直到指定的條件不為 `true`，然後略過剩餘項目。  
  
## 語法  
  
```  
Take While expression  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`expression`|必要項。  運算式，表示要對項目測試的條件。  這個運算式必須傳回 `Boolean` 值或功能上的對等用法，例如待評估為 `Boolean` 的 `Integer`。|  
  
## 備註  
 `Take While` 子句會自查詢結果開頭起一直包含項目，直到提供的 `expression` 傳回 `false` 為止。  在 `expression` 傳回 `false` 之後，查詢會略過所有剩餘項目。  傳回剩餘結果時會略過 `expression`。  
  
 `Take While` 子句跟`Where` 子句有個不同點，即 `Where` 子句可用來包含查詢中所有符合特定條件的項目。  `Take While` 子句則只會包含在第一次不合條件之前遇到的項目。  當您使用已排序的查詢結果時，`Take While` 子句會很有幫助。  
  
## 範例  
 下列程式碼範例會使用 `Take While` 子句擷取結果，直到找到第一個沒有任何訂單的客戶為止。  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)