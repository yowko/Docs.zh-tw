---
title: 設定作業 (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591125"
---
# <a name="set-operations-c"></a><span data-ttu-id="0f31e-102">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f31e-102">Set Operations (C#)</span></span>
<span data-ttu-id="0f31e-103">LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。</span><span class="sxs-lookup"><span data-stu-id="0f31e-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="0f31e-104">下節列出執行設定作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="0f31e-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f31e-105">方法</span><span class="sxs-lookup"><span data-stu-id="0f31e-105">Methods</span></span>  
  
|<span data-ttu-id="0f31e-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="0f31e-106">Method Name</span></span>|<span data-ttu-id="0f31e-107">說明</span><span class="sxs-lookup"><span data-stu-id="0f31e-107">Description</span></span>|<span data-ttu-id="0f31e-108">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="0f31e-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="0f31e-109">更多資訊</span><span class="sxs-lookup"><span data-stu-id="0f31e-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0f31e-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="0f31e-110">Distinct</span></span>|<span data-ttu-id="0f31e-111">移除集合中的重複值。</span><span class="sxs-lookup"><span data-stu-id="0f31e-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="0f31e-112">不適用。</span><span class="sxs-lookup"><span data-stu-id="0f31e-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f31e-113">Except</span><span class="sxs-lookup"><span data-stu-id="0f31e-113">Except</span></span>|<span data-ttu-id="0f31e-114">傳回集差異，表示未出現在第二個集合中的某個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="0f31e-115">不適用。</span><span class="sxs-lookup"><span data-stu-id="0f31e-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f31e-116">Intersect</span><span class="sxs-lookup"><span data-stu-id="0f31e-116">Intersect</span></span>|<span data-ttu-id="0f31e-117">傳回集交集，表示出現在這兩個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="0f31e-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="0f31e-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f31e-119">Union</span><span class="sxs-lookup"><span data-stu-id="0f31e-119">Union</span></span>|<span data-ttu-id="0f31e-120">傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="0f31e-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="0f31e-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="0f31e-122">比較設定作業</span><span class="sxs-lookup"><span data-stu-id="0f31e-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="0f31e-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="0f31e-123">Distinct</span></span>  
 <span data-ttu-id="0f31e-124">下圖說明一連串字元的 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法行為。</span><span class="sxs-lookup"><span data-stu-id="0f31e-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="0f31e-125">所傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="0f31e-127">Except</span><span class="sxs-lookup"><span data-stu-id="0f31e-127">Except</span></span>  
 <span data-ttu-id="0f31e-128">下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行為。</span><span class="sxs-lookup"><span data-stu-id="0f31e-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f31e-129">所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="0f31e-130">![顯示 Except&#40;&#41; 動作的圖形。](./media/set-operations/except-behavior-graphic.png "顯示 Except 的行為。")</span><span class="sxs-lookup"><span data-stu-id="0f31e-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="0f31e-131">Intersect</span><span class="sxs-lookup"><span data-stu-id="0f31e-131">Intersect</span></span>  
 <span data-ttu-id="0f31e-132">下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行為。</span><span class="sxs-lookup"><span data-stu-id="0f31e-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f31e-133">所傳回的序列包含兩個輸入序列共有的項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="0f31e-135">Union</span><span class="sxs-lookup"><span data-stu-id="0f31e-135">Union</span></span>  
 <span data-ttu-id="0f31e-136">下圖說明兩個字元序列的聯合作業。</span><span class="sxs-lookup"><span data-stu-id="0f31e-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="0f31e-137">所傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="0f31e-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="0f31e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f31e-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0f31e-140">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f31e-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0f31e-141">如何：合併和比較字串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f31e-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="0f31e-142">如何：尋找兩個清單之間的集合差異 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f31e-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
