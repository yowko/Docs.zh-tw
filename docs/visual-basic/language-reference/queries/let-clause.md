---
title: "Let Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Let"
  - "Let clause"
  - "Let statement"
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Let Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

計算出一個值並將該值指派給查詢中的新變數。  
  
## 語法  
  
```  
Let variable = expression [, ...]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`variable`|必要項。  可用於參考所提供運算式之結果的別名 \(Alias\)。|  
|`expression`|必要項。  會進行評估並指派給指定變數的運算式。|  
  
## 備註  
 `Let` 子句可以讓您計算每個查詢結果的值並使用別名參考這些值。  別名可以用在其他子句中，例如 `Where` 子句。  `Let` 子句可以讓您建立較易讀取的查詢陳述式，因為您可以指定查詢中包含之運算式子句的別名，並且在每次使用運算式子句的時候取代此別名。  
  
 您可以在 `Let` 子句中包含任意數量的 `variable` 和 `expression` 指派。  請使用逗號 \(,\) 分隔每個指派。  
  
## 範例  
 下列程式碼範例使用 `Let` 子句計算產品的 10 % 折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#16)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)