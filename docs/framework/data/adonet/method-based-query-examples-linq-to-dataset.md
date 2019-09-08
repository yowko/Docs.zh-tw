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
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="bcae2-102">以方法為基礎的查詢語法範例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bcae2-102">Method-Based Query Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="bcae2-103">本節提供使用標準查詢運算子之以方法為基礎的查詢語法中 LINQ to DataSet 程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="bcae2-103">This section provides LINQ to DataSet programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="bcae2-104">在<xref:System.Data.DataSet>這些範例中使用的會`FillDataSet`使用方法填入，這是在將[資料載入資料集](loading-data-into-a-dataset.md)中所指定。</span><span class="sxs-lookup"><span data-stu-id="bcae2-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="bcae2-105">如需詳細資訊，請參閱[標準查詢運算子C#總覽（）](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或[標準查詢運算子總覽（Visual Basic）](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bcae2-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcae2-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="bcae2-106">In This Section</span></span>  
 [<span data-ttu-id="bcae2-107">投影</span><span class="sxs-lookup"><span data-stu-id="bcae2-107">Projection</span></span>](method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="bcae2-108">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="bcae2-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="bcae2-109">資料分割</span><span class="sxs-lookup"><span data-stu-id="bcae2-109">Partitioning</span></span>](method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="bcae2-110">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法來查詢 <xref:System.Data.DataSet> 並分割結果。</span><span class="sxs-lookup"><span data-stu-id="bcae2-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="bcae2-111">排序</span><span class="sxs-lookup"><span data-stu-id="bcae2-111">Ordering</span></span>](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="bcae2-112">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法來查詢 <xref:System.Data.DataSet> 並排序結果。</span><span class="sxs-lookup"><span data-stu-id="bcae2-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="bcae2-113">集合運算子</span><span class="sxs-lookup"><span data-stu-id="bcae2-113">Set Operators</span></span>](method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="bcae2-114">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 運算子，針對資料列集合執行以值為基礎的比較作業。</span><span class="sxs-lookup"><span data-stu-id="bcae2-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="bcae2-115">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="bcae2-115">Conversion Operators</span></span>](method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="bcae2-116">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="bcae2-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="bcae2-117">項目運算子</span><span class="sxs-lookup"><span data-stu-id="bcae2-117">Element Operators</span></span>](method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="bcae2-118">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。</span><span class="sxs-lookup"><span data-stu-id="bcae2-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="bcae2-119">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="bcae2-119">Aggregate Operators</span></span>](method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="bcae2-120">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法來查詢 <xref:System.Data.DataSet> 並彙總資料。</span><span class="sxs-lookup"><span data-stu-id="bcae2-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="bcae2-121">Join</span><span class="sxs-lookup"><span data-stu-id="bcae2-121">Join</span></span>](method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="bcae2-122">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="bcae2-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcae2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcae2-123">See also</span></span>

- [<span data-ttu-id="bcae2-124">查詢運算式範例</span><span class="sxs-lookup"><span data-stu-id="bcae2-124">Query Expression Examples</span></span>](query-expression-examples-linq-to-dataset.md)
- [<span data-ttu-id="bcae2-125">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="bcae2-125">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="bcae2-126">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="bcae2-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
