---
title: "設定作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2b9fd7ec122fff2601296ae3a46bb7607b2b32ef
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="077dd-102">設定作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="077dd-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="077dd-103">產生的結果集根據相同或不同的集合 （或集合） 內的對等項目存在的查詢作業，請參閱 LINQ 中的 set 作業。</span><span class="sxs-lookup"><span data-stu-id="077dd-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="077dd-104">執行設定作業的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="077dd-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="077dd-105">方法</span><span class="sxs-lookup"><span data-stu-id="077dd-105">Methods</span></span>  
  
|<span data-ttu-id="077dd-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="077dd-106">Method Name</span></span>|<span data-ttu-id="077dd-107">描述</span><span class="sxs-lookup"><span data-stu-id="077dd-107">Description</span></span>|<span data-ttu-id="077dd-108">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="077dd-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="077dd-109">更多資訊</span><span class="sxs-lookup"><span data-stu-id="077dd-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="077dd-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="077dd-110">Distinct</span></span>|<span data-ttu-id="077dd-111">移除重複值的集合。</span><span class="sxs-lookup"><span data-stu-id="077dd-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<span data-ttu-id="077dd-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="077dd-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="077dd-114">例外</span><span class="sxs-lookup"><span data-stu-id="077dd-114">Except</span></span>|<span data-ttu-id="077dd-115">傳回的集合差異，這表示不會出現在第二個集合的一個集合中項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="077dd-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="077dd-116">Not applicable.</span></span>|<span data-ttu-id="077dd-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="077dd-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="077dd-119">交集</span><span class="sxs-lookup"><span data-stu-id="077dd-119">Intersect</span></span>|<span data-ttu-id="077dd-120">傳回集合的交集，這表示會出現在兩個集合的項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-120">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="077dd-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="077dd-121">Not applicable.</span></span>|<span data-ttu-id="077dd-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="077dd-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="077dd-124">聯集</span><span class="sxs-lookup"><span data-stu-id="077dd-124">Union</span></span>|<span data-ttu-id="077dd-125">傳回的集合聯集，這表示會出現在兩個集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-125">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="077dd-126">不適用。</span><span class="sxs-lookup"><span data-stu-id="077dd-126">Not applicable.</span></span>|<span data-ttu-id="077dd-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="077dd-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span></span>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="077dd-129">設定作業的比較</span><span class="sxs-lookup"><span data-stu-id="077dd-129">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="077dd-130">Distinct</span><span class="sxs-lookup"><span data-stu-id="077dd-130">Distinct</span></span>  
 <span data-ttu-id="077dd-131">下圖說明的行為<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>方法的一連串字元。</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="077dd-131">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> method on a sequence of characters.</span></span> <span data-ttu-id="077dd-132">傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-132">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="077dd-133">![顯示 distinct （） 的行為的圖形。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "相異")</span><span class="sxs-lookup"><span data-stu-id="077dd-133">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="077dd-134">例外</span><span class="sxs-lookup"><span data-stu-id="077dd-134">Except</span></span>  
 <span data-ttu-id="077dd-135">下圖說明<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>行為</span><span class="sxs-lookup"><span data-stu-id="077dd-135">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="077dd-136">傳回的序列包含只從第一個輸入序列中的項目不第二個輸入序列。</span><span class="sxs-lookup"><span data-stu-id="077dd-136">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="077dd-137">![顯示 except （） 的動作圖形。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="077dd-137">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="077dd-138">交集</span><span class="sxs-lookup"><span data-stu-id="077dd-138">Intersect</span></span>  
 <span data-ttu-id="077dd-139">下圖說明<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>行為</span><span class="sxs-lookup"><span data-stu-id="077dd-139">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="077dd-140">傳回的序列中沒有包含通用於這兩個輸入序列的項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-140">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="077dd-141">![顯示兩個序列的交集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "交集")</span><span class="sxs-lookup"><span data-stu-id="077dd-141">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="077dd-142">聯集</span><span class="sxs-lookup"><span data-stu-id="077dd-142">Union</span></span>  
 <span data-ttu-id="077dd-143">下圖說明兩個序列的字元聯集作業。</span><span class="sxs-lookup"><span data-stu-id="077dd-143">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="077dd-144">傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="077dd-144">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="077dd-145">![顯示兩個序列的聯集圖形。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="077dd-145">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="077dd-146">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="077dd-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="077dd-147">下列範例會使用`Distinct`子句在 LINQ 查詢中傳回唯一的數字從整數的清單。</span><span class="sxs-lookup"><span data-stu-id="077dd-147">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 <span data-ttu-id="077dd-148">[!code-vb[CsLINQSetOps #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="077dd-148">[!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077dd-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="077dd-149">See Also</span></span>  
 <span data-ttu-id="077dd-150"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="077dd-150"><xref:System.Linq></span></span>   
<span data-ttu-id="077dd-151"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="077dd-151"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="077dd-152"> [Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span><span class="sxs-lookup"><span data-stu-id="077dd-152"> [Distinct Clause](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span></span>  
<span data-ttu-id="077dd-153"> [如何︰ 合併和比較字串集合 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span><span class="sxs-lookup"><span data-stu-id="077dd-153"> [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span></span>  
<span data-ttu-id="077dd-154"> [如何︰ 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span><span class="sxs-lookup"><span data-stu-id="077dd-154"> [How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span></span>
