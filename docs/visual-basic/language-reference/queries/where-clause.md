---
title: "Where Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryWhere"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Where statement"
  - "queries [Visual Basic], Where"
  - "Where clause"
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Where Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定查詢的篩選條件。  
  
## 語法  
  
```  
Where condition  
```  
  
## 組件  
 `condition`  
 必要項。  運算式，用於判斷集合中目前項目的值是否要納入輸出集合。  此運算式必須評估為 `Boolean` 值或 `Boolean` 值的對等用法。  如果條件評估為 `True`，則會將項目納入查詢結果中，否則會將項目排除在查詢結果之外。  
  
## 備註  
 `Where` 子句可讓您只選取符合特定準則的項目，因此可以用來篩選查詢資料。  會使 `Where` 子句評估為 `True` 的項目都會併入查詢結果中，其他項目則會被排除。  `Where` 子句中的運算式必須評估為 `Boolean` 或 `Boolean` 的對等用法，例如當值為零時會評估為 `False` 的 Integer。  您可以使用 `And`、`Or`、`AndAlso`、`OrElse`、`Is` 和 `IsNot` 之類的邏輯運算子 \(Logical Operator\)，在 `Where` 子句中合併多個運算式。  
  
 根據預設，查詢運算式需有存取活動才會受到評估，例如，查詢運算式為資料繫結或在 `For` 迴圈 \(Loop\) 中逐一查看時。  因此，除非存取查詢，否則都不會評估 `Where` 子句。  如果您在 `Where` 子句中用到查詢以外的值，請確定在執行查詢時，`Where` 子句中使用的值是適當的。  如需查詢執行的詳細資訊，請參閱[撰寫第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 您可以在 `Where` 子句中呼叫函式，以對集合中目前項目的值執行計算或作業。  在 `Where` 子句中呼叫函式會使查詢在進行定義時就立即執行，而不是等到進行存取時才執行。  如需查詢執行的詳細資訊，請參閱[撰寫第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## 範例  
 下列查詢運算式使用 `From` 子句，為 `customers` 集合中每個 `Customer` 物件宣告範圍變數 `cust`。  接著 `Where` 子句使用範圍變數，將輸出限制在所指定區域的客戶。  `For Each` 迴圈則會顯示查詢結果中每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#23)]  
  
## 範例  
 下列範例會使用`And`和`Or`中的邏輯運算子`Where`子句。  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#31)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)