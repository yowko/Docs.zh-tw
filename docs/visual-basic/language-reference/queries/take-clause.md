---
title: "Take Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTake"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Take statement"
  - "queries [Visual Basic], Take"
  - "Take clause"
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Take Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

從集合開頭傳回指定的連續項目數。  
  
## 語法  
  
```  
Take count  
```  
  
## 組件  
 `count`  
 必要項。  數值或運算式，表示要連續傳回的項目數。  
  
## 備註  
 `Take` 子句會使查詢自結果清單開頭起，連續加入所指定數目的項目。  要加入的項目數是由 `count` 參數指定。  
  
 您可以在查詢的任何區段搭配使用 `Take` 子句和 `Skip` 子句，以傳回某個範圍的資料。  若要這樣做，請傳遞所需範圍中第一個項目的索引給 `Skip` 子句，並傳遞範圍的大小給 `Take` 子句。  在此情況下，`Take` 子句必須指定在 `Skip` 子句之後。  
  
 當您在查詢中使用 `Take` 子句時，可能還需要確保結果的傳回順序可讓 `Take` 子句加入所要的結果。  如需排序查詢結果的詳細資訊，請參閱 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用 `TakeWhile` 子句，指定只傳回符合所指定條件的特定項目。  
  
## 範例  
 下列程式碼範例會搭配使用 `Take` 子句和 `Skip` 子句，以頁面為單位傳回查詢資料。  GetCustomers 函式會使用 `Skip` 子句一直略過清單中的客戶直到遇到所提供的起始索引值，然後使用 `Take` 子句自該索引值起傳回一頁的客戶。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#1)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)