---
title: 設定作業 (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167929"
---
# <a name="set-operations-c"></a><span data-ttu-id="f510f-102">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="f510f-102">Set Operations (C#)</span></span>
<span data-ttu-id="f510f-103">LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。</span><span class="sxs-lookup"><span data-stu-id="f510f-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="f510f-104">下節列出執行設定作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="f510f-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f510f-105">方法</span><span class="sxs-lookup"><span data-stu-id="f510f-105">Methods</span></span>  
  
|<span data-ttu-id="f510f-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="f510f-106">Method Name</span></span>|<span data-ttu-id="f510f-107">描述</span><span class="sxs-lookup"><span data-stu-id="f510f-107">Description</span></span>|<span data-ttu-id="f510f-108">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="f510f-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="f510f-109">相關資訊</span><span class="sxs-lookup"><span data-stu-id="f510f-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f510f-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="f510f-110">Distinct</span></span>|<span data-ttu-id="f510f-111">移除集合中的重複值。</span><span class="sxs-lookup"><span data-stu-id="f510f-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="f510f-112">不適用。</span><span class="sxs-lookup"><span data-stu-id="f510f-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f510f-113">Except</span><span class="sxs-lookup"><span data-stu-id="f510f-113">Except</span></span>|<span data-ttu-id="f510f-114">傳回集差異，表示未出現在第二個集合中的某個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="f510f-115">不適用。</span><span class="sxs-lookup"><span data-stu-id="f510f-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f510f-116">Intersect</span><span class="sxs-lookup"><span data-stu-id="f510f-116">Intersect</span></span>|<span data-ttu-id="f510f-117">傳回集交集，表示出現在這兩個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="f510f-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="f510f-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f510f-119">Union</span><span class="sxs-lookup"><span data-stu-id="f510f-119">Union</span></span>|<span data-ttu-id="f510f-120">傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="f510f-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="f510f-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="f510f-122">比較設定作業</span><span class="sxs-lookup"><span data-stu-id="f510f-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="f510f-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="f510f-123">Distinct</span></span>  
 <span data-ttu-id="f510f-124">下面的示例描述了<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType>方法對字元序列的行為。</span><span class="sxs-lookup"><span data-stu-id="f510f-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="f510f-125">所傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="f510f-127">Except</span><span class="sxs-lookup"><span data-stu-id="f510f-127">Except</span></span>  
 <span data-ttu-id="f510f-128">下面的示例描述了 的行為<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f510f-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f510f-129">所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="f510f-130">![顯示"&#40;&#41;"操作的圖形。](./media/set-operations/except-behavior-graphic.png "顯示"例外"的行為。")</span><span class="sxs-lookup"><span data-stu-id="f510f-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="f510f-131">Intersect</span><span class="sxs-lookup"><span data-stu-id="f510f-131">Intersect</span></span>  
 <span data-ttu-id="f510f-132">下面的示例描述了 的行為<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f510f-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f510f-133">所傳回的序列包含兩個輸入序列共有的項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="f510f-135">Union</span><span class="sxs-lookup"><span data-stu-id="f510f-135">Union</span></span>  
 <span data-ttu-id="f510f-136">下面的示例描述了對兩個字元序列的聯合操作。</span><span class="sxs-lookup"><span data-stu-id="f510f-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="f510f-137">所傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="f510f-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="f510f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f510f-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f510f-140">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="f510f-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="f510f-141">如何組合和比較字串集合 （LINQ） （C#）</span><span class="sxs-lookup"><span data-stu-id="f510f-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="f510f-142">如何查找兩個清單 （LINQ） （C#） 之間的設置差異</span><span class="sxs-lookup"><span data-stu-id="f510f-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
