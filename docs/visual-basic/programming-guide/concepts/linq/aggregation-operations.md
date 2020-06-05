---
title: 彙總作業
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 8e2c9698de67dc4def348a03c9d69713a6130f31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383789"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="c74bd-102">匯總作業（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c74bd-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="c74bd-103">彙總運算會計算值集合中的單一值。</span><span class="sxs-lookup"><span data-stu-id="c74bd-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="c74bd-104">彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。</span><span class="sxs-lookup"><span data-stu-id="c74bd-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="c74bd-105">下圖顯示一系列數字之三個不同彙總作業的結果。</span><span class="sxs-lookup"><span data-stu-id="c74bd-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="c74bd-106">第一項作業會加總這些數字。</span><span class="sxs-lookup"><span data-stu-id="c74bd-106">The first operation sums the numbers.</span></span> <span data-ttu-id="c74bd-107">第二個作業會傳回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="c74bd-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![顯示 LINQ 彙總作業的圖例。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="c74bd-109">下節列出執行彙總作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="c74bd-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c74bd-110">方法</span><span class="sxs-lookup"><span data-stu-id="c74bd-110">Methods</span></span>  
  
|<span data-ttu-id="c74bd-111">方法名稱</span><span class="sxs-lookup"><span data-stu-id="c74bd-111">Method Name</span></span>|<span data-ttu-id="c74bd-112">Description</span><span class="sxs-lookup"><span data-stu-id="c74bd-112">Description</span></span>|<span data-ttu-id="c74bd-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="c74bd-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c74bd-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="c74bd-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c74bd-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="c74bd-115">Aggregate</span></span>|<span data-ttu-id="c74bd-116">對集合的值執行自訂彙總運算。</span><span class="sxs-lookup"><span data-stu-id="c74bd-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="c74bd-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="c74bd-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-118">Average</span><span class="sxs-lookup"><span data-stu-id="c74bd-118">Average</span></span>|<span data-ttu-id="c74bd-119">計算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="c74bd-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-120">Count</span><span class="sxs-lookup"><span data-stu-id="c74bd-120">Count</span></span>|<span data-ttu-id="c74bd-121">計算集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="c74bd-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="c74bd-122">LongCount</span></span>|<span data-ttu-id="c74bd-123">計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="c74bd-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-124">最大值</span><span class="sxs-lookup"><span data-stu-id="c74bd-124">Max</span></span>|<span data-ttu-id="c74bd-125">決定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="c74bd-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-126">最小值</span><span class="sxs-lookup"><span data-stu-id="c74bd-126">Min</span></span>|<span data-ttu-id="c74bd-127">決定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="c74bd-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c74bd-128">Sum</span><span class="sxs-lookup"><span data-stu-id="c74bd-128">Sum</span></span>|<span data-ttu-id="c74bd-129">計算集合中值的總和。</span><span class="sxs-lookup"><span data-stu-id="c74bd-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c74bd-130">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="c74bd-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="c74bd-131">Average</span><span class="sxs-lookup"><span data-stu-id="c74bd-131">Average</span></span>  
 <span data-ttu-id="c74bd-132">下列程式碼範例會使用 `Aggregate Into Average` Visual Basic 中的子句，來計算代表溫度的數位陣列中的平均溫度。</span><span class="sxs-lookup"><span data-stu-id="c74bd-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="c74bd-133">Count</span><span class="sxs-lookup"><span data-stu-id="c74bd-133">Count</span></span>  
 <span data-ttu-id="c74bd-134">下列程式碼範例會使用 `Aggregate Into Count` Visual Basic 中的子句，來計算陣列中大於或等於80的值數目。</span><span class="sxs-lookup"><span data-stu-id="c74bd-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="c74bd-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="c74bd-135">LongCount</span></span>  
 <span data-ttu-id="c74bd-136">下列程式碼範例會使用 `Aggregate Into LongCount` 子句來計算陣列中的值數目。</span><span class="sxs-lookup"><span data-stu-id="c74bd-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="c74bd-137">最大值</span><span class="sxs-lookup"><span data-stu-id="c74bd-137">Max</span></span>  
 <span data-ttu-id="c74bd-138">下列程式碼範例會使用 `Aggregate Into Max` 子句來計算代表溫度之數位陣列中的最大溫度。</span><span class="sxs-lookup"><span data-stu-id="c74bd-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="c74bd-139">最小值</span><span class="sxs-lookup"><span data-stu-id="c74bd-139">Min</span></span>  
 <span data-ttu-id="c74bd-140">下列程式碼範例會使用 `Aggregate Into Min` 子句，來計算代表溫度的數位陣列中的最小溫度。</span><span class="sxs-lookup"><span data-stu-id="c74bd-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="c74bd-141">Sum</span><span class="sxs-lookup"><span data-stu-id="c74bd-141">Sum</span></span>  
 <span data-ttu-id="c74bd-142">下列程式碼範例會使用 `Aggregate Into Sum` 子句來計算代表費用之值陣列中的總支出金額。</span><span class="sxs-lookup"><span data-stu-id="c74bd-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c74bd-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74bd-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c74bd-144">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74bd-144">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="c74bd-145">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="c74bd-145">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="c74bd-146">如何：計算 CSV 文字檔中的資料行值（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c74bd-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="c74bd-147">如何：統計、加總或平均資料</span><span class="sxs-lookup"><span data-stu-id="c74bd-147">How to: Count, Sum, or Average Data</span></span>](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="c74bd-148">如何：尋找查詢結果中的最小或最大值</span><span class="sxs-lookup"><span data-stu-id="c74bd-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="c74bd-149">如何：查詢目錄樹狀中的最大檔案 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74bd-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="c74bd-150">如何：查詢一組資料夾中的總位元組數（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c74bd-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
