---
title: 以方法為基礎的查詢語法範例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 0700711ece5cd8dda4688862e0ff19a3a63effdf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765902"
---
# <a name="method-based-query-examples-linq-to-dataset"></a>以方法為基礎的查詢語法範例 (LINQ to DataSet)
本節將透過以方法為基礎的查詢語法，提供使用標準查詢運算子的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式設計範例。 <xref:System.Data.DataSet>這些範例中使用填入的方式是使用`FillDataSet`方法中所指定[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。 如需詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
## <a name="in-this-section"></a>本節內容  
 [投影](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
 [資料分割](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。  
  
 [排序](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。  
  
 [集合運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 運算子，針對資料列集合執行以值為基礎的比較作業。  
  
 [轉換運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。  
  
 [項目運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。  
  
 [彙總運算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。  
  
 [Join](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
## <a name="see-also"></a>另請參閱  
 [查詢運算式範例](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [資料集專屬運算子範例](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
