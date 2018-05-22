---
title: 依據執行方式將標準查詢運算子分類 (C#)
ms.date: 07/20/2015
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
ms.openlocfilehash: 40b5859631b37f8d5e810de3c999742bafe9f6ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>依據執行方式將標準查詢運算子分類 (C#)
會使用兩種主要方式之一執行標準查詢運算子方法的 LINQ to Objects 實作：立即或延後。 使用延後執行的查詢運算子可以另外細分成兩個分類︰資料流和非資料流。 如果您知道如何執行不同的查詢運算子，則可以協助您了解透過給定查詢所取得的結果。 如果資料來源變更，或您所建置的查詢是根據另一個查詢，則這特別有用。 本主題會根據執行方式來分類標準查詢運算子。  
  
## <a name="manners-of-execution"></a>執行方式  
  
### <a name="immediate"></a>即時運算  
 立即執行表示讀取資料來源，並且在程式碼中宣告查詢的位置執行作業。 會立即執行傳回單一非可列舉結果的所有標準查詢運算子。  
  
### <a name="deferred"></a>已延期  
 延後執行表示未在程式碼中宣告查詢的位置執行作業。 只有在列舉查詢變數時，才會執行這項作業，例如，透過使用 `foreach` 陳述式。 這表示執行查詢的結果取決於執行查詢時的資料來源內容，而不是定義查詢時的資料來源內容。 如果多次列舉查詢變數，則每次都可能會有不同的結果。 幾乎傳回型別為 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IOrderedEnumerable%601> 的所有標準查詢運算子都會以延遲方式執行。  
  
 使用延後執行的查詢運算子可以另外分類為資料流和非資料流。  
  
#### <a name="streaming"></a>資料流  
 資料流運算子在產生項目之前不需要讀取所有來源資料。 執行時，資料流運算子會在讀取並產生項目時 (適用時) 於每個來源項目上執行其運算。 除非產生結果項目，否則資料流運算子會繼續讀取來源項目。 這表示可能會讀取多個來源項目，以產生一個結果項目。  
  
#### <a name="non-streaming"></a>非資料流  
 非資料流運算子在產生結果項目之前必須讀取所有來源資料。 排序或分組這類作業會歸到此分類。 執行時，非資料流查詢運算子會讀取所有來源資料、將其放入資料結構中、執行作業，並產生結果項目。  
  
## <a name="classification-table"></a>分類表  
 下表會根據執行方法來分類每個標準查詢運算子方法。  
  
> [!NOTE]
>  如果在兩個資料行中標記運算子，則作業包含兩個輸入序列，而且會以不同的方式評估每個序列。 在這些情況下，它一律是參數清單中以延後資料流方式評估的第一個序列。  
  
|標準查詢運算子|傳回型別|立即執行|延後資料流執行|延後非資料流執行|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|單一數值|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|單一數值、TSource 或 TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|單一數值、TSource 或 TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|單一數值|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|TSource 陣列|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Linq.Enumerable>  
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [標準查詢運算子的查詢運算式語法 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
