---
title: 查詢運算式範例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1671769871d8c224391a34f5a6294bb6015cafdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177367"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="deff1-102">查詢運算式範例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="deff1-102">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="deff1-103">本節提供使用標準查詢運算子的查詢運算式語法 LINQ to DataSet 程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="deff1-103">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="deff1-104"><xref:System.Data.DataSet>這些範例中使用的會使用方法來填入 `FillDataSet` ，而此方法是在將[資料載入資料集](loading-data-into-a-dataset.md)時指定。</span><span class="sxs-lookup"><span data-stu-id="deff1-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="deff1-105">如需詳細資訊，請參閱 [標準查詢運算子總覽 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [標準查詢運算子總覽 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="deff1-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="deff1-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="deff1-106">In This Section</span></span>  

 [<span data-ttu-id="deff1-107">Projection</span><span class="sxs-lookup"><span data-stu-id="deff1-107">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="deff1-108">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="deff1-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="deff1-109">限制</span><span class="sxs-lookup"><span data-stu-id="deff1-109">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="deff1-110">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Where%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="deff1-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="deff1-111">資料分割</span><span class="sxs-lookup"><span data-stu-id="deff1-111">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="deff1-112">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。</span><span class="sxs-lookup"><span data-stu-id="deff1-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="deff1-113">排序</span><span class="sxs-lookup"><span data-stu-id="deff1-113">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="deff1-114">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。</span><span class="sxs-lookup"><span data-stu-id="deff1-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="deff1-115">Element 運算子</span><span class="sxs-lookup"><span data-stu-id="deff1-115">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="deff1-116">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。</span><span class="sxs-lookup"><span data-stu-id="deff1-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="deff1-117">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="deff1-117">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="deff1-118">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。</span><span class="sxs-lookup"><span data-stu-id="deff1-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="deff1-119">聯結運算子</span><span class="sxs-lookup"><span data-stu-id="deff1-119">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="deff1-120">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="deff1-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deff1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deff1-121">See also</span></span>

- [<span data-ttu-id="deff1-122">以方法為基礎的查詢範例</span><span class="sxs-lookup"><span data-stu-id="deff1-122">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="deff1-123">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="deff1-123">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="deff1-124">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="deff1-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
