---
title: "Select Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySelect"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Select clause"
  - "queries [Visual Basic], Select"
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Select Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義查詢的結果。  
  
## 語法  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## 組件  
 `var1`  
 選擇項。  可用於參考資料行運算式之結果的別名 \(Alias\)。  
  
 `fieldName1`  
 必要項。  在查詢結果中傳回的欄位名稱。  
  
## 備註  
 您可以使用 `Select` 子句定義查詢傳回的結果。  這可讓您定義查詢建立之新匿名型別的成員，或鎖定查詢傳回之具名型別的成員。  查詢不需要 `Select` 子句。  如果未指定 `Select` 子句，查詢會依據目前範圍所識別之範圍變數的所有成員傳回型別。  如需詳細資訊，請參閱[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  查詢建立具名型別時，會傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的結果，其中 `T` 是建立的型別。  
  
 `Select` 子句可以參考目前範圍中的任何變數。  這包含 `From` 子句 \(或 `From` 子句\) 中識別的範圍變數。  這也包含由 `Aggregate`、`Let`、`Group By` 或 `Group Join` 子句之別名所建立的新變數，或由查詢運算式中先前 `Select` 子句所決定的變數。  `Select` 子句也可以包含靜態值。  例如，下列程式碼範例會顯示查詢運算式，其中 `Select` 子句會將查詢結果定義為匿名型別並具有四個成員：`ProductName`、`Price`、`Discount` 及 `DiscountedPrice`。  `ProductName` 和 `Price` 成員值是取自 `From` 子句中定義的產品範圍變數。  `DiscountedPrice` 成員值是在 `Let` 子句中計算。  `Discount` 成員是靜態值。  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select` 子句會引入新的範圍變數集供後續查詢子句使用，範圍中不再有先前的範圍變數。  查詢運算式中最後一個 `Select` 子句會決定查詢的傳回值。  例如，下列查詢會傳回總值超過 500 的每份客戶訂單的公司名稱和訂單 ID。  第一個 `Select` 子句識別 `Where` 子句和第二個 `Select` 子句的範圍變數。  第二個 `Select` 子句識別查詢傳回的值，做為新匿名型別。  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 如果 `Select` 子句識別單一項目以傳回，則查詢運算式會傳回該單一項目之型別的集合。  如果 `Select` 子句識別多個項目以傳回，則查詢運算式會依據選取的項目傳回新匿名型別的集合。  例如，下列兩個查詢會依據 `Select` 子句傳回兩個不同型別的集合。  第一個查詢會以字串傳回公司名稱集合。  第二個查詢會傳回以公司名稱和地址資訊填入 \(Populate\) 之 `Customer` 物件的集合。  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## 範例  
 下列查詢運算式使用 `From` 子句宣告 `customers` 集合的範圍變數 `cust`。  `Select` 子句會選取客戶名稱和 ID 值，並填入新範圍變數的 `CompanyName` 和 `CustomerID` 資料行。  `For Each` 陳述式 \(Statement\) 會對每個傳回的物件執行迴圈，並顯示每個記錄的 `CompanyName` 和 `CustomerID` 資料行。  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)