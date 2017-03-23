---
title: "From Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryFrom"
  - "vb.QueryFromIn"
  - "vb.QueryFromLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], From"
  - "From clause"
  - "From statement"
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# From Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一個或多個範圍變數以及要查詢的集合。  
  
## 語法  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`element`|必要項。  用於逐一查看集合中項目的「*範圍變數*」\(Range Variable\)。  在查詢逐一查看 `collection` 時，範圍變數可用以參考 `collection` 的每個成員。  必須是可列舉的型別。|  
|`type`|選擇項。  `element` 的型別。  如果沒有指定 `type`，則會從 `collection` 推斷 `element` 的型別。|  
|`collection`|必要項。  參考要查詢的集合。  必須是可列舉的型別。|  
  
## 備註  
 `From` 子句可用來識別查詢的來源資料，以及用以參考來源集合中的某個項目的變數。  這些變數稱為「*範圍變數*」。  除非在查詢中使用 `Aggregate` 子句表示只傳回彙總結果，否則查詢中一定要使用 `From` 子句。  如需詳細資訊，請參閱 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 您可以在查詢中指定多個 `From` 子句，以識別要聯結 \(Join\) 的多個集合。  指定多個集合時，這些集合會個別受到反覆查看，如果這些集合互相關聯，您也可以將它們聯結再反覆查看。  您可以使用 `Select` 子句隱含聯結集合，也可以使用 `Join` 或 `Group Join` 子句明確聯結集合。  或者，還可以在單一 `From` 子句中將每個相關的範圍變數和集合以逗號隔開，藉以指定多個範圍變數和集合。  下列程式碼範例顯示 `From` 子句的這兩種語法選項。  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` 子句會定義查詢的範圍，類似於 `For` 迴圈 \(Loop\) 的範圍。  因此，查詢的範圍中每個 `element` 範圍變數都必須具有唯一的名稱。  因為查詢中可以指定多個 `From` 子句，所以後續 `From` 子句可以參考該 `From` 子句中的範圍變數，也可以參考上一個 `From` 子句中的範圍變數。  例如，下列範例顯示一個巢狀 `From` 子句，其中第二個子句中的集合是根據第一個子句中的範圍變數屬性。  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 每個 `From` 子句後面都可以接其他查詢子句的任意組合，以進一步限定查詢。  您可以利用下列方式限定查詢：  
  
-   使用 `From` 和 `Select` 子句可以隱含合併多個集合，使用 `Join` 或 `Group Join` 子句則可明確合併多個集合。  
  
-   使用 `Where` 子句可以篩選查詢結果。  
  
-   使用 `Order By` 子句可將結果排序。  
  
-   使用 `Group By` 子句可將類似的結果放在一起形成群組。  
  
-   使用 `Aggregate` 子句可以識別要針對整個查詢結果進行評估的彙總函式 \(Aggregate Function\)。  
  
-   使用 `Let` 子句可引進反覆運算變數，這個變數的值是由運算式而不是集合所決定。  
  
-   使用 `Distinct` 子句可忽略重複的查詢結果。  
  
-   使用 `Skip`、`Take`、`Skip While` 和 `Take While` 子句可以識別要傳回的結果部分。  
  
## 範例  
 下列查詢運算式使用 `From` 子句，為 `customers` 集合中每個 `Customer` 物件宣告範圍變數 `cust`。  接著 `Where` 子句使用範圍變數，將輸出限制在所指定區域的客戶。  `For Each` 迴圈則會顯示查詢結果中每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## 請參閱  
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Distinct Clause](../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)