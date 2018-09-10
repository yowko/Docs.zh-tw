---
title: 標準查詢運算子的查詢運算式語法 (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: 46923b34fce08a9ddb8152e51a5308aa7d557ca3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514457"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>標準查詢運算子的查詢運算式語法 (C#)
某些更常用的標準查詢運算子具有專用 C# 語言關鍵字語法，可將它們呼叫為「查詢運算式」的一部分。 相較於「方法」對等項目，查詢運算式是一個不同且更具可讀性的表示查詢形式。 查詢運算式子句會在編譯時期轉譯成查詢方法的呼叫。  
  
## <a name="query-expression-syntax-table"></a>查詢運算式語法表  
 下表列出具有對等查詢運算式子句的標準查詢運算子。  
  
|方法|C# 查詢運算式語法|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|使用明確類型範圍變數，例如：<br /><br /> `from int i in numbers`<br /><br /> (如需詳細資訊，請參閱 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md))。|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -或-<br /><br /> `group … by … into …`<br /><br /> (如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md))。|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md))。|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md))。|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (如需詳細資訊，請參閱 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md))。|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|多個 `from` 子句。<br /><br /> (如需詳細資訊，請參閱 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md))。|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md))。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Linq.Enumerable>  
- <xref:System.Linq.Queryable>  
- [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [依據執行方式將標準查詢運算子分類 (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
