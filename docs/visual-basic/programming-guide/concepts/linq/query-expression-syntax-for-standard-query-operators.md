---
title: 標準查詢運算子的查詢運算式語法
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: 57a08f6540cbf3e091ee1b2e202e0e181487e3be
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090244"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>標準查詢運算子的查詢運算式語法 (Visual Basic) 

某些更常用的標準查詢運算子具有專用的 Visual Basic 語言關鍵字語法，可讓它們當做 *查詢運算式*的一部分來呼叫。 相較於「方法」** 對等項目，查詢運算式是一個不同且更具可讀性的表示查詢形式。 查詢運算式子句會在編譯時期轉譯成查詢方法的呼叫。  
  
## <a name="query-expression-syntax-table"></a>查詢運算式語法表  

 下表列出具有對等查詢運算式子句的標準查詢運算子。  
  
|方法|Visual Basic 查詢運算式語法|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br />  (需詳細資訊，請參閱 [From 子句](../../../language-reference/queries/from-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br />  (需詳細資訊，請參閱 [Distinct 子句](../../../language-reference/queries/distinct-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br />  (需詳細資訊，請參閱 [Group By 子句](../../../language-reference/queries/group-by-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br />  (需詳細資訊，請參閱 [Group Join 子句](../../../language-reference/queries/group-join-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> -或-<br /><br /> `Join … [As …]In … On …`<br /><br />  (需詳細資訊，請參閱 [Join 子句](../../../language-reference/queries/join-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br />  (需詳細資訊，請參閱 [Order By 子句](../../../language-reference/queries/order-by-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br />  (需詳細資訊，請參閱 [Order By 子句](../../../language-reference/queries/order-by-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br />  (需詳細資訊，請參閱 [Select 子句](../../../language-reference/queries/select-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.SelectMany%2A>|多個 `From` 子句<br /><br />  (需詳細資訊，請參閱 [From 子句](../../../language-reference/queries/from-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br />  (需詳細資訊，請參閱 [Skip 子句](../../../language-reference/queries/skip-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br />  (如需詳細資訊，請參閱 [Skip While 子句](../../../language-reference/queries/skip-while-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br />  (需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br />  (需詳細資訊，請參閱 [Take 子句](../../../language-reference/queries/take-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br />  (如需詳細資訊，請參閱 [Take While 子句](../../../language-reference/queries/take-while-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br />  (需詳細資訊，請參閱 [Order By 子句](../../../language-reference/queries/order-by-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br />  (需詳細資訊，請參閱 [Order By 子句](../../../language-reference/queries/order-by-clause.md)。 ) |  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br />  (需詳細資訊，請參閱 [Where 子句](../../../language-reference/queries/where-clause.md)。 ) |  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [以執行 (Visual Basic 的方式分類標準查詢運算子) ](classification-of-standard-query-operators-by-manner-of-execution.md)
