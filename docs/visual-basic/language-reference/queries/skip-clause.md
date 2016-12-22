---
title: "Skip Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QuerySkip"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Skip"
  - "Skip statement"
  - "Skip clause"
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Skip Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

略過集合中指定的項目數，然後傳回其餘項目。  
  
## 語法  
  
```  
Skip count  
```  
  
## 組件  
 `count`  
 必要項。  數值或運算式，表示要連續略過的項目數。  
  
## 備註  
 `Skip` 子句會使查詢略過結果清單開頭的項目並傳回剩餘項目。  略過的項目數是由 `count` 參數識別。  
  
 您可以在查詢的任何區段搭配使用 `Skip` 子句和 `Take` 子句，以傳回某個範圍的資料。  若要這樣做，請傳遞所需範圍中第一個項目的索引給 `Skip` 子句，並傳遞範圍的大小給 `Take` 子句。  
  
 當您在查詢中使用 `Skip` 子句時，可能還需要確保結果的傳回順序可讓 `Skip` 子句略過所要的結果。  如需排序查詢結果的詳細資訊，請參閱 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用 `SkipWhile` 子句，指定只略過符合所指定條件的特定項目。  
  
## 範例  
 下列程式碼範例會搭配使用 `Skip` 子句和 `Take` 子句，以頁面為單位傳回查詢資料。  `GetCustomers` 函式會使用 `Skip` 子句一直略過清單中的客戶直到遇到所提供的起始索引值，然後使用 `Take` 子句自該索引值起傳回一頁的客戶。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)