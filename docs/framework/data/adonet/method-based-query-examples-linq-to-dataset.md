---
title: 以方法為基礎的查詢語法範例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 1c1ef8f1b6c05415ac6f5ee59d9a415bfab2c410
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175378"
---
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="c9686-102">以方法為基礎的查詢語法範例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c9686-102">Method-Based Query Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="c9686-103">本節提供以方法為基礎的查詢語法中使用標準查詢運算子的 LINQ to DataSet 程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="c9686-103">This section provides LINQ to DataSet programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="c9686-104"><xref:System.Data.DataSet>這些範例中使用的會使用方法來填入 `FillDataSet` ，而此方法是在將[資料載入資料集](loading-data-into-a-dataset.md)時指定。</span><span class="sxs-lookup"><span data-stu-id="c9686-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="c9686-105">如需詳細資訊，請參閱 [標準查詢運算子總覽 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [標準查詢運算子總覽 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c9686-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9686-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c9686-106">In This Section</span></span>  

 [<span data-ttu-id="c9686-107">Projection</span><span class="sxs-lookup"><span data-stu-id="c9686-107">Projection</span></span>](method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="c9686-108">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="c9686-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="c9686-109">資料分割</span><span class="sxs-lookup"><span data-stu-id="c9686-109">Partitioning</span></span>](method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="c9686-110">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。</span><span class="sxs-lookup"><span data-stu-id="c9686-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="c9686-111">排序</span><span class="sxs-lookup"><span data-stu-id="c9686-111">Ordering</span></span>](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="c9686-112">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。</span><span class="sxs-lookup"><span data-stu-id="c9686-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="c9686-113">設定運算子</span><span class="sxs-lookup"><span data-stu-id="c9686-113">Set Operators</span></span>](method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="c9686-114">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 運算子，針對資料列集合執行以值為基礎的比較作業。</span><span class="sxs-lookup"><span data-stu-id="c9686-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="c9686-115">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="c9686-115">Conversion Operators</span></span>](method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="c9686-116">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="c9686-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="c9686-117">Element 運算子</span><span class="sxs-lookup"><span data-stu-id="c9686-117">Element Operators</span></span>](method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="c9686-118">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。</span><span class="sxs-lookup"><span data-stu-id="c9686-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="c9686-119">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="c9686-119">Aggregate Operators</span></span>](method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="c9686-120">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。</span><span class="sxs-lookup"><span data-stu-id="c9686-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="c9686-121">聯結</span><span class="sxs-lookup"><span data-stu-id="c9686-121">Join</span></span>](method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="c9686-122">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="c9686-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9686-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9686-123">See also</span></span>

- [<span data-ttu-id="c9686-124">查詢運算式範例</span><span class="sxs-lookup"><span data-stu-id="c9686-124">Query Expression Examples</span></span>](query-expression-examples-linq-to-dataset.md)
- [<span data-ttu-id="c9686-125">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="c9686-125">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="c9686-126">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="c9686-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
