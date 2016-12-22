---
title: "Join Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryJoinIn"
  - "vb.QueryJoin"
  - "vb.QueryJoinOn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Join"
  - "Join statement"
  - "Join clause"
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將兩個集合合併成單一集合。  這項聯結 \(Join\) 作業是根據相符的索引鍵，使用的是 `Equals` 運算子。  
  
## 語法  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## 組件  
 `element`  
 必要項。  代表要聯結之集合的控制項變數。  
  
 `collection`  
 必要項。  要與 `Join` 運算子左邊定義的集合進行合併的集合。  `Join` 子句可以巢狀於另一個 `Join` 子句或 `Group Join` 子句中。  
  
 `joinClause`  
 選擇項。  一個或多個用來進一步限定查詢的其他 `Join` 子句。  
  
 `groupJoinClause`  
 選擇項。  一個或多個用來進一步限定查詢的其他 `Group Join` 子句。  
  
 `key1` `Equals` `key2`  
 必要項。  識別要聯結之集合的索引鍵。  您必須使用 `Equals` 運算子來比較要聯結之集合中的索引鍵。  您可以使用 `And` 運算子識別多個索引鍵，藉以合併聯結條件 \(Join Condition\)。  `key1` 必須來自 `Join` 運算子左邊的集合。  `key2` 必須來自 `Join` 運算子右邊的集合。  
  
 聯結條件中使用的索引鍵，可以是包含集合中之多個項目的運算式。  不過，每個索引鍵運算式只能包含其針對之集合中的項目。  
  
## 備註  
 `Join` 子句會根據要聯結之集合中的相符索引鍵值來合併兩個集合。  所產生的集合中，可以包含 `Join` 運算子左邊所識別集合中的值和 `Join` 子句所識別集合中的值的任意組合。  查詢只會傳回符合 `Equals` 運算子所指定之條件的結果。  這相當於 SQL 中的 `INNER JOIN`。  
  
 您可以在查詢中使用多個 `Join` 子句，將兩個以上的集合聯結成單一集合。  
  
 您可以執行隱含聯結 \(Implicit Join\) 來合併集合，而不需要使用 `Join` 子句。  其做法是在 `From` 子句中加入多個 `In` 子句，然後指定 `Where` 子句以識別要使用的聯結索引鍵。  
  
 您可以使用 `Group Join` 子句將集合合併成單一階層式集合。  這和 SQL 中的 `LEFT OUTER JOIN` 相似。  
  
## 範例  
 下列程式碼範例會執行隱含聯結以將客戶清單及其訂單合併。  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## 範例  
 下列程式碼範例會使用 `Join` 子句聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 這個範例會產生類似如下的輸出：  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## 範例  
 下列程式碼範例會使用 `Join` 子句並搭配兩個索引鍵資料行聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 這個範例會產生類似如下的輸出：  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)