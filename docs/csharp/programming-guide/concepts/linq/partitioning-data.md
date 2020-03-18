---
title: 分割資料 (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591587"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="bef60-102">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="bef60-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="bef60-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="bef60-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="bef60-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="bef60-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="bef60-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="bef60-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="bef60-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="bef60-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="bef60-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="bef60-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![顯示三個 LINQ 分割作業的圖例。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="bef60-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="bef60-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="bef60-110">操作員</span><span class="sxs-lookup"><span data-stu-id="bef60-110">Operators</span></span>  
  
|<span data-ttu-id="bef60-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="bef60-111">Operator Name</span></span>|<span data-ttu-id="bef60-112">描述</span><span class="sxs-lookup"><span data-stu-id="bef60-112">Description</span></span>|<span data-ttu-id="bef60-113">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="bef60-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="bef60-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="bef60-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="bef60-115">Skip</span><span class="sxs-lookup"><span data-stu-id="bef60-115">Skip</span></span>|<span data-ttu-id="bef60-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="bef60-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="bef60-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="bef60-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bef60-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="bef60-118">SkipWhile</span></span>|<span data-ttu-id="bef60-119">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="bef60-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="bef60-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="bef60-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bef60-121">Take</span><span class="sxs-lookup"><span data-stu-id="bef60-121">Take</span></span>|<span data-ttu-id="bef60-122">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="bef60-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="bef60-123">不適用。</span><span class="sxs-lookup"><span data-stu-id="bef60-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bef60-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="bef60-124">TakeWhile</span></span>|<span data-ttu-id="bef60-125">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="bef60-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="bef60-126">不適用。</span><span class="sxs-lookup"><span data-stu-id="bef60-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="bef60-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bef60-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="bef60-128">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="bef60-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
