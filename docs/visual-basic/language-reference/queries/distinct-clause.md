---
title: "Distinct Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryDistinct"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Distinct clause"
  - "Distinct statement"
  - "queries [Visual Basic], Distinct"
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Distinct Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

限制目前範圍變數的值，以免後續查詢子句中出現重複的值。  
  
## 語法  
  
```  
Distinct  
```  
  
## 備註  
 您可以使用 `Distinct` 子句傳回只含唯一項目的清單。  `Distinct` 子句會使查詢忽略重複的查詢結果。  `Distinct` 子句會套用至 `Select` 子句所指定之所有傳回欄位中的重複值。  如果未指定 `Select` 子句，則 `Distinct` 子句會套用至 `From` 子句中所識別查詢的範圍變數。  如果範圍變數並非不變的型別，則只有當型別的所有成員都符合現有的查詢結果時，查詢才會忽略查詢結果。  
  
## 範例  
 下列查詢運算式會將客戶清單和客戶訂單清單建立聯結 \(Join\)。  其中加入 `Distinct` 子句，只傳回唯一客戶名稱和訂單日期的清單。  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)