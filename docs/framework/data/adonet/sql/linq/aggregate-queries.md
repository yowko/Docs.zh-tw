---
title: "彙總查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 彙總查詢
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援 `Average`、`Count`、`Max`、`Min` 和 `Sum` 彙總運算子。  請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總運算子有下列特性：  
  
-   彙總查詢會立即執行。  
  
     如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)。  
  
-   彙總查詢通常會傳回數字，而不是集合。  
  
     如需詳細資訊，請參閱[Aggregation Operations](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/aggregation-operations.md)。  
  
-   您不可以對匿名型別呼叫彙總。  
  
 下列主題中的範例衍生自 Northwind 範例資料庫。  如需詳細資訊，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
## 在本節中  
 [從數值序列傳回平均值](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Average%2A> 運算子。  
  
 [統計序列中的項目數](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Count%2A> 運算子。  
  
 [尋找數值序列中的最大值](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Max%2A> 運算子。  
  
 [尋找數值序列中的最小值](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Min%2A> 運算子。  
  
 [計算數值序列中值的總和](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Sum%2A> 運算子。  
  
## 相關章節  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 提供 Visual Basic 和 C\# 中之 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的連結。  
  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 提供在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中設計 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢之概念說明主題的連結。  
  
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)  
 說明查詢在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的運作方式。