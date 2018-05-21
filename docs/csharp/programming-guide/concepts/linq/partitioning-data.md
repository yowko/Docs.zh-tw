---
title: 分割資料 (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 003e292979b1dc75baa298ea4bda7ef432d0f27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="partitioning-data-c"></a><span data-ttu-id="6f7f2-102">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="6f7f2-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="6f7f2-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="6f7f2-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="6f7f2-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="6f7f2-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="6f7f2-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="6f7f2-108">![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="6f7f2-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="6f7f2-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="6f7f2-110">運算子</span><span class="sxs-lookup"><span data-stu-id="6f7f2-110">Operators</span></span>  
  
|<span data-ttu-id="6f7f2-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="6f7f2-111">Operator Name</span></span>|<span data-ttu-id="6f7f2-112">描述</span><span class="sxs-lookup"><span data-stu-id="6f7f2-112">Description</span></span>|<span data-ttu-id="6f7f2-113">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="6f7f2-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="6f7f2-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="6f7f2-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6f7f2-115">Skip</span><span class="sxs-lookup"><span data-stu-id="6f7f2-115">Skip</span></span>|<span data-ttu-id="6f7f2-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="6f7f2-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6f7f2-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="6f7f2-118">SkipWhile</span></span>|<span data-ttu-id="6f7f2-119">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="6f7f2-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6f7f2-121">Take</span><span class="sxs-lookup"><span data-stu-id="6f7f2-121">Take</span></span>|<span data-ttu-id="6f7f2-122">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="6f7f2-123">不適用。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6f7f2-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="6f7f2-124">TakeWhile</span></span>|<span data-ttu-id="6f7f2-125">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="6f7f2-126">不適用。</span><span class="sxs-lookup"><span data-stu-id="6f7f2-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="6f7f2-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7f2-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6f7f2-128">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="6f7f2-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
