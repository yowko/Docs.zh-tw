---
title: 以方法為基礎的查詢語法範例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 3cda55457df4157f1b0d2cdef1f857cfe6540c66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783729"
---
# <a name="method-based-query-examples-linq-to-dataset"></a>以方法為基礎的查詢語法範例 (LINQ to DataSet)
本節提供使用標準查詢運算子之以方法為基礎的查詢語法中 LINQ to DataSet 程式設計範例。 在<xref:System.Data.DataSet>這些範例中使用的會`FillDataSet`使用方法填入，這是在將[資料載入資料集](loading-data-into-a-dataset.md)中所指定。 如需詳細資訊，請參閱[標準查詢運算子C#總覽（）](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或[標準查詢運算子總覽（Visual Basic）](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [投影](method-based-query-syntax-examples-projection.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
 [資料分割](method-based-query-syntax-examples-partitioning-linq.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。  
  
 [排序](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。  
  
 [集合運算子](method-based-query-syntax-examples-set-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 運算子，針對資料列集合執行以值為基礎的比較作業。  
  
 [轉換運算子](method-based-query-syntax-examples-conversion-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。  
  
 [項目運算子](method-based-query-syntax-examples-element-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。  
  
 [彙總運算子](method-based-query-syntax-examples-aggregate-operators.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。  
  
 [Join](method-based-query-syntax-examples-join-linq-to-dataset.md)  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。  
  
## <a name="see-also"></a>另請參閱

- [查詢運算式範例](query-expression-examples-linq-to-dataset.md)
- [資料集專屬運算子範例](dataset-specific-operator-examples-linq-to-dataset.md)
- [LINQ to DataSet 範例](linq-to-dataset-examples.md)
