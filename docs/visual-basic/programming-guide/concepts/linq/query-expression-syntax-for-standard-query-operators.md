---
title: "標準查詢運算子 (Visual Basic) 的查詢運算式語法"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c68e924b88b312ef17b8bb83de0def21ea621824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>標準查詢運算子 (Visual Basic) 的查詢運算式語法
某些較常使用的標準查詢運算子具有專用的 Visual Basic 語言關鍵字語法可讓它們的一部分呼叫*查詢運算式*。 相較於「方法」對等項目，查詢運算式是一個不同且更具可讀性的表示查詢形式。 查詢運算式子句會在編譯時期轉譯成查詢方法的呼叫。  
  
## <a name="query-expression-syntax-table"></a>查詢運算式語法表  
 下表列出具有對等查詢運算式子句的標準查詢運算子。  
  
|方法|Visual Basic 查詢運算式語法|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (如需詳細資訊，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (如需詳細資訊，請參閱[Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md)。)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (如需詳細資訊，請參閱[群組 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (如需詳細資訊，請參閱[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> -或-<br /><br /> `Join … [As …]In … On …`<br /><br /> (如需詳細資訊，請參閱[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)。)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (如需詳細資訊，請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|多個`From`子句<br /><br /> (如需詳細資訊，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (如需詳細資訊，請參閱[Skip 子句](../../../../visual-basic/language-reference/queries/skip-clause.md)。)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (如需詳細資訊，請參閱[Skip While 子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)。)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)。)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (如需詳細資訊，請參閱[Take 子句](../../../../visual-basic/language-reference/queries/take-clause.md)。)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (如需詳細資訊，請參閱[採取 While 子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)。)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (如需詳細資訊，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。)|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [分類的標準查詢運算子的方式執行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
