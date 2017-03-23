---
title: "Group Join Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryGroupJoinIn"
  - "vb.QueryGroupJoinOn"
  - "vb.QueryGroupJoin"
  - "vb.QueryGroupJoinInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Group Join clause"
  - "Group Join statement"
  - "queries [Visual Basic], Group Join"
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Group Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

可將兩個集合合併成單一階層式集合。  這項聯結 \(Join\) 作業是根據相符的索引鍵來進行。  
  
## 語法  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`element`|必要項。  代表要聯結之集合的控制項變數。|  
|`type`|選擇項。  `element` 的型別。  如果沒有指定 `type`，則會從 `collection` 推斷 `element` 的型別。|  
|`collection`|必要項。  要與 `Group Join` 運算子左邊的集合進行合併的集合。  `Group Join` 子句可以巢狀於另一個 `Join` 子句或 `Group Join` 子句中。|  
|`key1` `Equals` `key2`|必要項。  識別要聯結之集合的索引鍵。  您必須使用 `Equals` 運算子來比較要聯結之集合中的索引鍵。  您可以使用 `And` 運算子識別多個索引鍵，藉以合併聯結條件 \(Join Condition\)。  `key1` 參數必須來自 `Join` 運算子左邊的集合。  `key2` 參數必須來自 `Join` 運算子右邊的集合。<br /><br /> 聯結條件中使用的索引鍵，可以是包含集合中之多個項目的運算式。  不過，每個索引鍵運算式只能包含其針對之集合中的項目。|  
|`expressionList`|必要項。  一個或多個運算式，用於識別如何彙總 \(Aggregate\) 集合中的項目群組。  若要為群組結果指定一個成員名稱，請使用 `Group` 關鍵字 \(`<alias> = Group`\)。  您也可以加入彙總函式，以便套用至群組。|  
  
## 備註  
 `Group Join` 子句是根據要聯結之集合中的相符索引鍵值來合併兩個集合。  所產生的集合包含一個成員，這個成員參考第二個集合中所有與第一個集合中的索引鍵值相符合之項目的集合。  您也可以指定彙總函式，以套用至從第二個集合群組得來的項目。  如需彙總函式的詳細資訊，請參閱 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 例如，假設有一個經理集合、一個員工集合。  這兩個集合中的項目都有 ManagerID 屬性，用於識別員工的直級經理。  聯結作業的結果要包含每一位經理和具有相符 ManagerID 值的員工。  `Group Join` 作業的結果會包含經理的完整清單。  而列出的每個經理都有一個成員，這個成員參考所有直級上級是該經理之員工的清單。  
  
 `Group Join` 作業所產生的集合中，可以包含 `From` 子句所識別集合中以及 `Group Join` 子句的`Into` 子句所識別運算式中的任意值組合。  如需 `Into` 子句之有效運算式的詳細資訊，請參閱 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 `Group Join` 作業會傳回 `Group Join` 運算子左邊所識別之集合的所有結果。  即使要聯結的集合中沒有符合項目，也是一樣。  這和 SQL 中的 `LEFT OUTER JOIN` 相似。  
  
 您可以使用 `Join` 子句，將集合合併成單一集合。  這相當於 SQL 中的 `INNER JOIN`。  
  
## 範例  
 下列程式碼範例會使用 `Group Join` 子句聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)