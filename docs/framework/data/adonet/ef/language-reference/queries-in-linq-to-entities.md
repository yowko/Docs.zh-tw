---
title: "LINQ to Entities 中的查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LINQ to Entities 中的查詢
查詢是指從資料來源中擷取資料的運算式。  查詢通常會以特定的查詢語言來表示，例如 SQL 用於關聯式資料庫，而 XQuery 用於 XML。  因此，開發人員必須針對他們所查詢的每種資料來源或資料格式，學習新的查詢語言。  Language\-Integrated Query \(LINQ\) 提供了一種較簡單且一致的模型，可處理各種資料來源和格式的資料。  在 LINQ 查詢中，您一定會使用程式設計物件。  
  
 LINQ 查詢作業由三個動作構成：取得資料來源、建立查詢和執行查詢。  
  
 實作 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面或 <xref:System.Linq.IQueryable%601> 泛型介面的資料來源可以透過 LINQ 進行查詢。  實作泛型 <xref:System.Data.Objects.ObjectQuery%601> 介面之泛型 <xref:System.Linq.IQueryable%601> 類別的執行個體會當做 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢的資料來源。  <xref:System.Data.Objects.ObjectQuery%601> 泛型類別表示傳回零個或多個具型別物件之集合的查詢。  使用 C\# 的 `var` 關鍵字 \(在 Visual Basic 中為 Dim\)，您也可以讓編譯器推斷實體類型。  
  
 在此查詢中，您可以精確地指定想要從資料來源中擷取的資訊。  此外，查詢也可以指定該項資訊傳回之前應該如何排序、分組和成形。  在 LINQ 中，查詢會儲存在變數內。  如果查詢傳回一連串值，查詢變數本身必須是可查詢型別。  這個查詢變數不會採取任何動作，也不會傳回任何資料。它只會儲存查詢資訊。  在您建立查詢之後，必須執行該查詢以便擷取任何資料。  
  
## 查詢語法  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢可以使用兩個不同的語法來撰寫：查詢運算式語法和以方法為基礎的查詢語法。  查詢運算式語法是 C\# 3.0 和 Visual Basic 9.0 中的新項目，是由類似 Transact\-SQL 或 XQuery 的宣告式語法撰寫的一組子句所構成。  不過，[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] Common Language Runtime \(CLR\) 無法讀取查詢運算式語法本身。  因此，在編譯期間，查詢運算式會轉譯為 CLR 可以了解的項目：即方法呼叫。  這些方法就是所謂的*「標準查詢運算子」*。  身為開發人員，您可以選擇使用方法語法來直接呼叫它們，而非使用查詢語法。如需詳細資訊，請參閱[Query Syntax and Method Syntax in LINQ](../Topic/Query%20Syntax%20and%20Method%20Syntax%20in%20LINQ%20\(C%23\).md)。  
  
### 查詢運算式語法  
 查詢運算式是宣告式查詢語法。  這些語法可以讓開發人員以類似 Transact\-SQL 格式的高階語言撰寫查詢。  透過使用查詢運算式語法，您就可以利用最少的程式碼，針對資料來源執行同樣複雜的篩選、排序和分組作業。  如需詳細資訊，請參閱[基本查詢作業 \(Visual Basic\)](../Topic/Basic%20Query%20Operations%20\(Visual%20Basic\).md)。  如需示範如何使用查詢運算式語法的範例，請參閱下列主題：  
  
-   [查詢運算式語法範例：投影](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [查詢運算式語法範例：篩選](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [查詢運算式語法範例：排序](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [查詢運算式語法範例：彙總運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [查詢運算式語法範例：分割](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [查詢運算式語法範例：聯結運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [查詢運算式語法範例：元素運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [查詢運算式語法範例：群組](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [查詢運算式語法範例：巡覽關聯性](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### 以方法為基礎的查詢語法  
 另一種撰寫 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢的方式是使用以方法為基礎的查詢。  以方法為基礎的查詢語法是對 LINQ 運算子方法之直接方法呼叫的序列，並傳遞 Lambda 運算式當做參數。  如需詳細資訊，請參閱 [Lambda 運算式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md)。  如需示範如何使用以方法為基礎的語法之範例，請參閱下列主題：  
  
-   [以方法為基礎的查詢語法範例：投影](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [以方法為基礎的查詢語法範例：篩選](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [以方法為基礎的查詢語法範例：排序](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [以方法為基礎的查詢語法範例：彙總運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [以方法為基礎的查詢語法範例：分割](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [以方法為基礎的查詢語法範例：轉換](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [以方法為基礎的查詢語法範例：聯結運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [以方法為基礎的查詢語法範例：元素運算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [以方法為基礎的查詢語法範例：群組](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [以方法為基礎的查詢語法範例：巡覽關聯性](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## 請參閱  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)   
 [Getting Started with LINQ in C\#](../Topic/Getting%20Started%20with%20LINQ%20in%20C%23.md)   
 [Getting Started with LINQ in Visual Basic](../Topic/Getting%20Started%20with%20LINQ%20in%20Visual%20Basic.md)   
 [Entity Framework 的合併選項和已編譯查詢](http://go.microsoft.com/fwlink/?LinkId=199591)