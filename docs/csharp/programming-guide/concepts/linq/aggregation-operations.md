---
title: 彙總作業 (C#)
description: 瞭解執行匯總作業的方法。 彙總運算會計算值集合中的單一值。
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: c302667ec7f1d4ed5acb98439ea9f8f80250077d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159380"
---
# <a name="aggregation-operations-c"></a><span data-ttu-id="da7ba-104">彙總作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="da7ba-104">Aggregation Operations (C#)</span></span>

<span data-ttu-id="da7ba-105">彙總運算會計算值集合中的單一值。</span><span class="sxs-lookup"><span data-stu-id="da7ba-105">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="da7ba-106">彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。</span><span class="sxs-lookup"><span data-stu-id="da7ba-106">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="da7ba-107">下圖顯示一系列數字之三個不同彙總作業的結果。</span><span class="sxs-lookup"><span data-stu-id="da7ba-107">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="da7ba-108">第一項作業會加總這些數字。</span><span class="sxs-lookup"><span data-stu-id="da7ba-108">The first operation sums the numbers.</span></span> <span data-ttu-id="da7ba-109">第二個作業會傳回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="da7ba-109">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![顯示 LINQ 彙總作業的圖例。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="da7ba-111">下節列出執行彙總作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="da7ba-111">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da7ba-112">方法</span><span class="sxs-lookup"><span data-stu-id="da7ba-112">Methods</span></span>  
  
|<span data-ttu-id="da7ba-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="da7ba-113">Method Name</span></span>|<span data-ttu-id="da7ba-114">描述</span><span class="sxs-lookup"><span data-stu-id="da7ba-114">Description</span></span>|<span data-ttu-id="da7ba-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="da7ba-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="da7ba-116">相關資訊</span><span class="sxs-lookup"><span data-stu-id="da7ba-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="da7ba-117">Aggregate</span><span class="sxs-lookup"><span data-stu-id="da7ba-117">Aggregate</span></span>|<span data-ttu-id="da7ba-118">對集合的值執行自訂彙總運算。</span><span class="sxs-lookup"><span data-stu-id="da7ba-118">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="da7ba-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-120">Average</span><span class="sxs-lookup"><span data-stu-id="da7ba-120">Average</span></span>|<span data-ttu-id="da7ba-121">計算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="da7ba-121">Calculates the average value of a collection of values.</span></span>|<span data-ttu-id="da7ba-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-123">計數</span><span class="sxs-lookup"><span data-stu-id="da7ba-123">Count</span></span>|<span data-ttu-id="da7ba-124">計算集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="da7ba-124">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="da7ba-125">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-126">LongCount</span><span class="sxs-lookup"><span data-stu-id="da7ba-126">LongCount</span></span>|<span data-ttu-id="da7ba-127">計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="da7ba-127">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="da7ba-128">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-129">最大值</span><span class="sxs-lookup"><span data-stu-id="da7ba-129">Max</span></span>|<span data-ttu-id="da7ba-130">決定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="da7ba-130">Determines the maximum value in a collection.</span></span>|<span data-ttu-id="da7ba-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-132">最小值</span><span class="sxs-lookup"><span data-stu-id="da7ba-132">Min</span></span>|<span data-ttu-id="da7ba-133">決定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="da7ba-133">Determines the minimum value in a collection.</span></span>|<span data-ttu-id="da7ba-134">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-134">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da7ba-135">Sum</span><span class="sxs-lookup"><span data-stu-id="da7ba-135">Sum</span></span>|<span data-ttu-id="da7ba-136">計算集合中值的總和。</span><span class="sxs-lookup"><span data-stu-id="da7ba-136">Calculates the sum of the values in a collection.</span></span>|<span data-ttu-id="da7ba-137">不適用。</span><span class="sxs-lookup"><span data-stu-id="da7ba-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="da7ba-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da7ba-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="da7ba-139">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="da7ba-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="da7ba-140">如何計算 CSV 文字檔中的資料行值 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="da7ba-140">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="da7ba-141">如何查詢目錄樹狀結構中的最大檔案 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="da7ba-141">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [<span data-ttu-id="da7ba-142">如何查詢一組資料夾中的總位元組數 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="da7ba-142">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
