---
title: 設定作業 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 2620fa02c8f1f07edbf149c3202af8ab1decc072
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652522"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="7b35b-102">設定作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b35b-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="7b35b-103">LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。</span><span class="sxs-lookup"><span data-stu-id="7b35b-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="7b35b-104">下節列出執行設定作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="7b35b-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b35b-105">方法</span><span class="sxs-lookup"><span data-stu-id="7b35b-105">Methods</span></span>  
  
|<span data-ttu-id="7b35b-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="7b35b-106">Method Name</span></span>|<span data-ttu-id="7b35b-107">描述</span><span class="sxs-lookup"><span data-stu-id="7b35b-107">Description</span></span>|<span data-ttu-id="7b35b-108">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="7b35b-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="7b35b-109">更多資訊</span><span class="sxs-lookup"><span data-stu-id="7b35b-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="7b35b-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="7b35b-110">Distinct</span></span>|<span data-ttu-id="7b35b-111">移除集合中的重複值。</span><span class="sxs-lookup"><span data-stu-id="7b35b-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7b35b-112">例外</span><span class="sxs-lookup"><span data-stu-id="7b35b-112">Except</span></span>|<span data-ttu-id="7b35b-113">傳回集差異，表示未出現在第二個集合中的某個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="7b35b-114">不適用。</span><span class="sxs-lookup"><span data-stu-id="7b35b-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7b35b-115">交集</span><span class="sxs-lookup"><span data-stu-id="7b35b-115">Intersect</span></span>|<span data-ttu-id="7b35b-116">傳回集交集，表示出現在這兩個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="7b35b-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="7b35b-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7b35b-118">聯集</span><span class="sxs-lookup"><span data-stu-id="7b35b-118">Union</span></span>|<span data-ttu-id="7b35b-119">傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="7b35b-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="7b35b-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="7b35b-121">比較設定作業</span><span class="sxs-lookup"><span data-stu-id="7b35b-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="7b35b-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="7b35b-122">Distinct</span></span>  
 <span data-ttu-id="7b35b-123">下圖說明一連串字元的 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法行為。</span><span class="sxs-lookup"><span data-stu-id="7b35b-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="7b35b-124">所傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="7b35b-125">![顯示 Distinct&#40;&#41; 行為的圖形。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="7b35b-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="7b35b-126">例外</span><span class="sxs-lookup"><span data-stu-id="7b35b-126">Except</span></span>  
 <span data-ttu-id="7b35b-127">下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行為。</span><span class="sxs-lookup"><span data-stu-id="7b35b-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7b35b-128">所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="7b35b-129">![顯示 Except&#40;&#41; 動作的圖形。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="7b35b-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="7b35b-130">交集</span><span class="sxs-lookup"><span data-stu-id="7b35b-130">Intersect</span></span>  
 <span data-ttu-id="7b35b-131">下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行為。</span><span class="sxs-lookup"><span data-stu-id="7b35b-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7b35b-132">所傳回的序列包含兩個輸入序列共有的項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="7b35b-133">![顯示兩種序列交集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="7b35b-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="7b35b-134">聯集</span><span class="sxs-lookup"><span data-stu-id="7b35b-134">Union</span></span>  
 <span data-ttu-id="7b35b-135">下圖說明兩個字元序列的聯合作業。</span><span class="sxs-lookup"><span data-stu-id="7b35b-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="7b35b-136">所傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="7b35b-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="7b35b-137">![顯示兩個序列聯集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="7b35b-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="7b35b-138">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="7b35b-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="7b35b-139">下列範例會使用`Distinct`LINQ 查詢來傳回唯一的數字從整數的清單中的子句。</span><span class="sxs-lookup"><span data-stu-id="7b35b-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b35b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b35b-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="7b35b-141">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b35b-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="7b35b-142">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="7b35b-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="7b35b-143">如何： 合併和比較字串集合 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b35b-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="7b35b-144">如何： 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異</span><span class="sxs-lookup"><span data-stu-id="7b35b-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
