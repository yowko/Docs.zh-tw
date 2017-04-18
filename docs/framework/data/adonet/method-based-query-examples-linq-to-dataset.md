---
title: "以方法為基礎的查詢範例 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 以方法為基礎的查詢範例 (LINQ to DataSet)
本節將透過以方法為基礎的查詢語法，提供使用標準查詢運算子的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式設計範例。  這些範例中使用的 <xref:System.Data.DataSet> 是使用[將資料載入 DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) 中指定的 `FillDataSet` 方法填入 \(Populate\) 資料。  如需詳細資訊，請參閱[Standard Query Operators Overview](../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## 在本節中  
 [投影](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
 [分割](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。  
  
 [排序](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。  
  
 [設定運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 運算子，針對資料列集合執行以值為基礎的比較作業。  
  
 [轉換運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。  
  
 [項目運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataSet> 中的 <xref:System.Data.DataRow> 項目。  
  
 [彙總運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。  
  
 [聯結](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
## 請參閱  
 [查詢運算式範例](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)   
 [DataSet 專用的運算子範例](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)   
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)