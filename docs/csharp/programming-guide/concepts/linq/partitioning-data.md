---
title: 分割資料 (C#)
description: 瞭解如何在 LINQ 中分割資料。 觀看顯示分割作業結果的圖例。
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 31beacd672addb3eb38ade8f2bf9cfae25f4d27a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176262"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="9eda6-104">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="9eda6-104">Partitioning Data (C#)</span></span>

<span data-ttu-id="9eda6-105">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="9eda6-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="9eda6-106">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="9eda6-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="9eda6-107">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="9eda6-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="9eda6-108">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="9eda6-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="9eda6-109">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="9eda6-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![顯示三個 LINQ 分割作業的圖例。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="9eda6-111">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="9eda6-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="9eda6-112">運算子</span><span class="sxs-lookup"><span data-stu-id="9eda6-112">Operators</span></span>  
  
|<span data-ttu-id="9eda6-113">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="9eda6-113">Operator Name</span></span>|<span data-ttu-id="9eda6-114">描述</span><span class="sxs-lookup"><span data-stu-id="9eda6-114">Description</span></span>|<span data-ttu-id="9eda6-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="9eda6-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="9eda6-116">相關資訊</span><span class="sxs-lookup"><span data-stu-id="9eda6-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9eda6-117">跳過</span><span class="sxs-lookup"><span data-stu-id="9eda6-117">Skip</span></span>|<span data-ttu-id="9eda6-118">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="9eda6-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="9eda6-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="9eda6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9eda6-120">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="9eda6-120">SkipWhile</span></span>|<span data-ttu-id="9eda6-121">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="9eda6-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="9eda6-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="9eda6-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9eda6-123">Take</span><span class="sxs-lookup"><span data-stu-id="9eda6-123">Take</span></span>|<span data-ttu-id="9eda6-124">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="9eda6-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="9eda6-125">不適用。</span><span class="sxs-lookup"><span data-stu-id="9eda6-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9eda6-126">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="9eda6-126">TakeWhile</span></span>|<span data-ttu-id="9eda6-127">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="9eda6-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="9eda6-128">不適用。</span><span class="sxs-lookup"><span data-stu-id="9eda6-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="9eda6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eda6-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9eda6-130">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="9eda6-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
