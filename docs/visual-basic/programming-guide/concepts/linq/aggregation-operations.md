---
title: "彙總作業 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d4b07eeb1d09d7db0f75d96629c816f66dbb128
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="f4a1e-102">彙總作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4a1e-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="f4a1e-103">彙總運算會計算值集合中的單一值。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="f4a1e-104">彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="f4a1e-105">下圖顯示一系列數字之三個不同彙總作業的結果。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="f4a1e-106">第一項作業會加總這些數字。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-106">The first operation sums the numbers.</span></span> <span data-ttu-id="f4a1e-107">第二個作業會傳回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="f4a1e-108">![LINQ 彙總作業](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="f4a1e-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="f4a1e-109">下節列出執行彙總作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4a1e-110">方法</span><span class="sxs-lookup"><span data-stu-id="f4a1e-110">Methods</span></span>  
  
|<span data-ttu-id="f4a1e-111">方法名稱</span><span class="sxs-lookup"><span data-stu-id="f4a1e-111">Method Name</span></span>|<span data-ttu-id="f4a1e-112">說明</span><span class="sxs-lookup"><span data-stu-id="f4a1e-112">Description</span></span>|<span data-ttu-id="f4a1e-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="f4a1e-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f4a1e-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="f4a1e-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f4a1e-115">彙總</span><span class="sxs-lookup"><span data-stu-id="f4a1e-115">Aggregate</span></span>|<span data-ttu-id="f4a1e-116">對集合的值執行自訂彙總運算。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="f4a1e-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-118">平均</span><span class="sxs-lookup"><span data-stu-id="f4a1e-118">Average</span></span>|<span data-ttu-id="f4a1e-119">計算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-120">計數</span><span class="sxs-lookup"><span data-stu-id="f4a1e-120">Count</span></span>|<span data-ttu-id="f4a1e-121">計算集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="f4a1e-122">LongCount</span></span>|<span data-ttu-id="f4a1e-123">計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-124">最大</span><span class="sxs-lookup"><span data-stu-id="f4a1e-124">Max</span></span>|<span data-ttu-id="f4a1e-125">決定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-126">最小</span><span class="sxs-lookup"><span data-stu-id="f4a1e-126">Min</span></span>|<span data-ttu-id="f4a1e-127">決定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a1e-128">Sum</span><span class="sxs-lookup"><span data-stu-id="f4a1e-128">Sum</span></span>|<span data-ttu-id="f4a1e-129">計算集合中值的總和。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f4a1e-130">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="f4a1e-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="f4a1e-131">Average</span><span class="sxs-lookup"><span data-stu-id="f4a1e-131">Average</span></span>  
 <span data-ttu-id="f4a1e-132">下列程式碼範例使用`Aggregate Into Average`中的子句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]來計算陣列中的數字，代表溫度平均溫度。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-132">The following code example uses the `Aggregate Into Average` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="f4a1e-133">計數</span><span class="sxs-lookup"><span data-stu-id="f4a1e-133">Count</span></span>  
 <span data-ttu-id="f4a1e-134">下列程式碼範例使用`Aggregate Into Count`中的子句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]來計算陣列中的值大於或等於 80 的數目。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-134">The following code example uses the `Aggregate Into Count` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="f4a1e-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="f4a1e-135">LongCount</span></span>  
 <span data-ttu-id="f4a1e-136">下列程式碼範例使用`Aggregate Into LongCount`子句來計算陣列中的值數目。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="f4a1e-137">最大</span><span class="sxs-lookup"><span data-stu-id="f4a1e-137">Max</span></span>  
 <span data-ttu-id="f4a1e-138">下列程式碼範例使用`Aggregate Into Max`子句來計算陣列中的數字，代表溫度最大的溫度。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="f4a1e-139">最小</span><span class="sxs-lookup"><span data-stu-id="f4a1e-139">Min</span></span>  
 <span data-ttu-id="f4a1e-140">下列程式碼範例使用`Aggregate Into Min`子句來計算陣列中的數字，代表溫度最小的溫度。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="f4a1e-141">Sum</span><span class="sxs-lookup"><span data-stu-id="f4a1e-141">Sum</span></span>  
 <span data-ttu-id="f4a1e-142">下列程式碼範例使用`Aggregate Into Sum`子句來計算總計的支出金額從陣列的值，表示費用。</span><span class="sxs-lookup"><span data-stu-id="f4a1e-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f4a1e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4a1e-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="f4a1e-144">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4a1e-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="f4a1e-145">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="f4a1e-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="f4a1e-146">如何： 計算 CSV 文字檔案 (LINQ) (Visual Basic) 中的資料行值</span><span class="sxs-lookup"><span data-stu-id="f4a1e-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="f4a1e-147">如何：統計、加總或平均資料</span><span class="sxs-lookup"><span data-stu-id="f4a1e-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="f4a1e-148">如何：尋找查詢結果中的最小或最大值</span><span class="sxs-lookup"><span data-stu-id="f4a1e-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="f4a1e-149">如何： 查詢的最大檔案或目錄樹狀 (LINQ) (Visual Basic) 中的檔案</span><span class="sxs-lookup"><span data-stu-id="f4a1e-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="f4a1e-150">如何： 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數</span><span class="sxs-lookup"><span data-stu-id="f4a1e-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
