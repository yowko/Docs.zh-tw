---
title: 設定作業 (C#)
description: '深入瞭解設定作業，以及在 c # 中以 LINQ 執行設定作業的標準查詢運算子方法。'
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 8679f804adaaeada390206e3e1dd2a0711a2cbf6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195606"
---
# <a name="set-operations-c"></a><span data-ttu-id="05bd9-103">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="05bd9-103">Set Operations (C#)</span></span>

<span data-ttu-id="05bd9-104">LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。</span><span class="sxs-lookup"><span data-stu-id="05bd9-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="05bd9-105">下節列出執行設定作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="05bd9-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05bd9-106">方法</span><span class="sxs-lookup"><span data-stu-id="05bd9-106">Methods</span></span>  
  
|<span data-ttu-id="05bd9-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="05bd9-107">Method Name</span></span>|<span data-ttu-id="05bd9-108">描述</span><span class="sxs-lookup"><span data-stu-id="05bd9-108">Description</span></span>|<span data-ttu-id="05bd9-109">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="05bd9-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="05bd9-110">相關資訊</span><span class="sxs-lookup"><span data-stu-id="05bd9-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="05bd9-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="05bd9-111">Distinct</span></span>|<span data-ttu-id="05bd9-112">移除集合中的重複值。</span><span class="sxs-lookup"><span data-stu-id="05bd9-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="05bd9-113">不適用。</span><span class="sxs-lookup"><span data-stu-id="05bd9-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="05bd9-114">Except</span><span class="sxs-lookup"><span data-stu-id="05bd9-114">Except</span></span>|<span data-ttu-id="05bd9-115">傳回集差異，表示未出現在第二個集合中的某個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="05bd9-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="05bd9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="05bd9-117">Intersect</span><span class="sxs-lookup"><span data-stu-id="05bd9-117">Intersect</span></span>|<span data-ttu-id="05bd9-118">傳回集交集，表示出現在這兩個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="05bd9-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="05bd9-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="05bd9-120">Union</span><span class="sxs-lookup"><span data-stu-id="05bd9-120">Union</span></span>|<span data-ttu-id="05bd9-121">傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="05bd9-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="05bd9-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="05bd9-123">比較設定作業</span><span class="sxs-lookup"><span data-stu-id="05bd9-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="05bd9-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="05bd9-124">Distinct</span></span>  

 <span data-ttu-id="05bd9-125">下列範例描述 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 字元序列上方法的行為。</span><span class="sxs-lookup"><span data-stu-id="05bd9-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="05bd9-126">所傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="05bd9-128">Except</span><span class="sxs-lookup"><span data-stu-id="05bd9-128">Except</span></span>  

 <span data-ttu-id="05bd9-129">下列範例描述的行為 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="05bd9-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="05bd9-130">所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="05bd9-131">![顯示&#40;&#41; 以外之動作的圖形。](./media/set-operations/except-behavior-graphic.png "顯示 Except 的行為。")</span><span class="sxs-lookup"><span data-stu-id="05bd9-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="05bd9-132">Intersect</span><span class="sxs-lookup"><span data-stu-id="05bd9-132">Intersect</span></span>  

 <span data-ttu-id="05bd9-133">下列範例描述的行為 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="05bd9-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="05bd9-134">所傳回的序列包含兩個輸入序列共有的項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="05bd9-136">Union</span><span class="sxs-lookup"><span data-stu-id="05bd9-136">Union</span></span>  

 <span data-ttu-id="05bd9-137">下列範例描述兩個字元序列的聯集運算。</span><span class="sxs-lookup"><span data-stu-id="05bd9-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="05bd9-138">所傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="05bd9-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="05bd9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05bd9-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="05bd9-141">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="05bd9-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="05bd9-142">如何結合和比較字串集合 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="05bd9-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="05bd9-143">如何尋找兩個清單之間的集合差異 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="05bd9-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
