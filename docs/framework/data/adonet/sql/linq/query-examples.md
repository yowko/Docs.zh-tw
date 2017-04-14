---
title: "查詢範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 查詢範例
本節提供典型 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 和 C\# 範例。  使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員，可以在＜範例＞一節提供的範例方案中找到更多的範例。  如需詳細資訊，請參閱[範例](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 文件的程式碼範例中，經常會使用 *db*。  *db* 是假設為 *Northwind* 類別的執行個體，而這個類別是繼承自 <xref:System.Data.Linq.DataContext>。  
  
## 在本節中  
 [彙總查詢](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 說明如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> 等。  
  
 [傳回序列中的第一個項目](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 提供 <xref:System.Linq.Enumerable.First%2A> 的使用範例。  
  
 [傳回或略過序列中的項目](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 提供 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 的使用範例。  
  
 [排序序列中的項目](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 提供 <xref:System.Linq.Enumerable.OrderBy%2A> 的使用範例。  
  
 [分組序列中的項目](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 提供 <xref:System.Linq.Enumerable.GroupBy%2A> 的使用範例。  
  
 [從序列去除重複的項目](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 提供 <xref:System.Linq.Enumerable.Distinct%2A> 的使用範例。  
  
 [判斷序列中的任何或所有項目是否符合條件](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 提供 <xref:System.Linq.Enumerable.All%2A> 和 <xref:System.Linq.Enumerable.Any%2A> 的使用範例。  
  
 [串連兩個序列](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 提供 <xref:System.Linq.Enumerable.Concat%2A> 的使用範例。  
  
 [傳回兩個序列之間的差異](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 提供 <xref:System.Linq.Enumerable.Except%2A> 的使用範例。  
  
 [傳回兩個序列的交集](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 提供 <xref:System.Linq.Enumerable.Intersect%2A> 的使用範例。  
  
 [傳回兩個序列的聯集](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 提供 <xref:System.Linq.Enumerable.Union%2A> 的使用範例。  
  
 [將序列轉換為陣列](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 提供 <xref:System.Linq.Enumerable.ToArray%2A> 的使用範例。  
  
 [將序列轉換為泛型清單](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 提供 <xref:System.Linq.Enumerable.ToList%2A> 的使用範例。  
  
 [將型別轉換為泛型 IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 提供 <xref:System.Linq.Enumerable.AsEnumerable%2A> 的使用範例。  
  
 [制定聯結和叉積查詢](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 提供在 `from`、`where` 和 `select` 子句中進行外部索引鍵巡覽的使用範例。  
  
 [制定投影](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 提供合併使用 `select` 與其他功能 \(例如，「*匿名型別*」\(Anonymous Type\)\) 以形成查詢投影 \(Projection\) 的範例。  
  
## 相關章節  
 [Standard Query Operators Overview](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 說明標準查詢運算子的概念。  
  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何運用查詢的概念。  
  
 [程式設計手冊](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相關程式設計概念說明主題的入口網站。