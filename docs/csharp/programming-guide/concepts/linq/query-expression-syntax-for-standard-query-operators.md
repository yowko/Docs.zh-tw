---
title: "標準查詢運算子的查詢運算式語法 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 30e994329234b8bd455f739694e50121bac63d5d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a><span data-ttu-id="071c4-102">標準查詢運算子的查詢運算式語法 (C#)</span><span class="sxs-lookup"><span data-stu-id="071c4-102">Query Expression Syntax for Standard Query Operators (C#)</span></span>
<span data-ttu-id="071c4-103">某些更常用的標準查詢運算子具有專用 C# 語言關鍵字語法，可將它們呼叫為「查詢運算式」的一部分。</span><span class="sxs-lookup"><span data-stu-id="071c4-103">Some of the more frequently used standard query operators have dedicated C# language keyword syntax that enables them to be called as part of a *query expression*.</span></span> <span data-ttu-id="071c4-104">相較於「方法」對等項目，查詢運算式是一個不同且更具可讀性的表示查詢形式。</span><span class="sxs-lookup"><span data-stu-id="071c4-104">A query expression is a different, more readable form of expressing a query than its *method-based*  equivalent.</span></span> <span data-ttu-id="071c4-105">查詢運算式子句會在編譯時期轉譯成查詢方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="071c4-105">Query expression clauses are translated into calls to the query methods at compile time.</span></span>  
  
## <a name="query-expression-syntax-table"></a><span data-ttu-id="071c4-106">查詢運算式語法表</span><span class="sxs-lookup"><span data-stu-id="071c4-106">Query Expression Syntax Table</span></span>  
 <span data-ttu-id="071c4-107">下表列出具有對等查詢運算式子句的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="071c4-107">The following table lists the standard query operators that have equivalent query expression clauses.</span></span>  
  
|<span data-ttu-id="071c4-108">方法</span><span class="sxs-lookup"><span data-stu-id="071c4-108">Method</span></span>|<span data-ttu-id="071c4-109">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="071c4-109">C# Query Expression Syntax</span></span>|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|<span data-ttu-id="071c4-110">使用明確類型範圍變數，例如：</span><span class="sxs-lookup"><span data-stu-id="071c4-110">Use an explicitly typed range variable, for example:</span></span><br /><br /> `from int i in numbers`<br /><br /> <span data-ttu-id="071c4-111">(如需詳細資訊，請參閱 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-111">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> <span data-ttu-id="071c4-112">-或-</span><span class="sxs-lookup"><span data-stu-id="071c4-112">-or-</span></span><br /><br /> `group … by … into …`<br /><br /> <span data-ttu-id="071c4-113">(如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-113">(For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> <span data-ttu-id="071c4-114">(如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-114">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> <span data-ttu-id="071c4-115">(如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-115">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> <span data-ttu-id="071c4-116">(如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-116">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> <span data-ttu-id="071c4-117">(如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-117">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> <span data-ttu-id="071c4-118">(如需詳細資訊，請參閱 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-118">(For more information, see [select clause](../../../../csharp/language-reference/keywords/select-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<span data-ttu-id="071c4-119">多個 `from` 子句。</span><span class="sxs-lookup"><span data-stu-id="071c4-119">Multiple `from` clauses.</span></span><br /><br /> <span data-ttu-id="071c4-120">(如需詳細資訊，請參閱 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-120">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> <span data-ttu-id="071c4-121">(如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-121">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> <span data-ttu-id="071c4-122">(如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-122">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> <span data-ttu-id="071c4-123">(如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md))。</span><span class="sxs-lookup"><span data-stu-id="071c4-123">(For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="071c4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="071c4-124">See Also</span></span>  
 <span data-ttu-id="071c4-125"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="071c4-125"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="071c4-126"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="071c4-126"><xref:System.Linq.Queryable></span></span>   
 <span data-ttu-id="071c4-127">[標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="071c4-127">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="071c4-128">依據執行方式將標準查詢運算子分類 (C#)</span><span class="sxs-lookup"><span data-stu-id="071c4-128">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)

