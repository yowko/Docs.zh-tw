---
title: "設定作業 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 37841cde3aa5e4aaa6545b3a160422d024be5842
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="set-operations-c"></a><span data-ttu-id="2d734-102">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d734-102">Set Operations (C#)</span></span>
<span data-ttu-id="2d734-103">LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。</span><span class="sxs-lookup"><span data-stu-id="2d734-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="2d734-104">下節列出執行設定作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="2d734-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d734-105">方法</span><span class="sxs-lookup"><span data-stu-id="2d734-105">Methods</span></span>  
  
|<span data-ttu-id="2d734-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="2d734-106">Method Name</span></span>|<span data-ttu-id="2d734-107">描述</span><span class="sxs-lookup"><span data-stu-id="2d734-107">Description</span></span>|<span data-ttu-id="2d734-108">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="2d734-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="2d734-109">更多資訊</span><span class="sxs-lookup"><span data-stu-id="2d734-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="2d734-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="2d734-110">Distinct</span></span>|<span data-ttu-id="2d734-111">移除集合中的重複值。</span><span class="sxs-lookup"><span data-stu-id="2d734-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="2d734-112">不適用。</span><span class="sxs-lookup"><span data-stu-id="2d734-112">Not applicable.</span></span>|<span data-ttu-id="2d734-113"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-113"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2d734-114"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-114"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="2d734-115">例外</span><span class="sxs-lookup"><span data-stu-id="2d734-115">Except</span></span>|<span data-ttu-id="2d734-116">傳回集差異，表示未出現在第二個集合中的某個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-116">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="2d734-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="2d734-117">Not applicable.</span></span>|<span data-ttu-id="2d734-118"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-118"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2d734-119"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-119"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="2d734-120">交集</span><span class="sxs-lookup"><span data-stu-id="2d734-120">Intersect</span></span>|<span data-ttu-id="2d734-121">傳回集交集，表示出現在這兩個集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-121">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="2d734-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="2d734-122">Not applicable.</span></span>|<span data-ttu-id="2d734-123"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-123"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2d734-124"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-124"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="2d734-125">聯集</span><span class="sxs-lookup"><span data-stu-id="2d734-125">Union</span></span>|<span data-ttu-id="2d734-126">傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-126">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="2d734-127">不適用。</span><span class="sxs-lookup"><span data-stu-id="2d734-127">Not applicable.</span></span>|<span data-ttu-id="2d734-128"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-128"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2d734-129"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2d734-129"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span></span>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="2d734-130">比較設定作業</span><span class="sxs-lookup"><span data-stu-id="2d734-130">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="2d734-131">Distinct</span><span class="sxs-lookup"><span data-stu-id="2d734-131">Distinct</span></span>  
 <span data-ttu-id="2d734-132">下圖說明 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> 方法對一系列字元的行為。</span><span class="sxs-lookup"><span data-stu-id="2d734-132">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> method on a sequence of characters.</span></span> <span data-ttu-id="2d734-133">所傳回的序列包含輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-133">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="2d734-134">![顯示 Distinct&#40;&#41; 行為的圖形。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="2d734-134">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="2d734-135">例外</span><span class="sxs-lookup"><span data-stu-id="2d734-135">Except</span></span>  
 <span data-ttu-id="2d734-136">下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName> 的行為。</span><span class="sxs-lookup"><span data-stu-id="2d734-136">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="2d734-137">所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-137">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="2d734-138">![顯示 Except&#40;&#41; 動作的圖形。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="2d734-138">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="2d734-139">交集</span><span class="sxs-lookup"><span data-stu-id="2d734-139">Intersect</span></span>  
 <span data-ttu-id="2d734-140">下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName> 的行為。</span><span class="sxs-lookup"><span data-stu-id="2d734-140">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="2d734-141">所傳回的序列包含兩個輸入序列共有的項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-141">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="2d734-142">![顯示兩種序列交集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="2d734-142">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="2d734-143">聯集</span><span class="sxs-lookup"><span data-stu-id="2d734-143">Union</span></span>  
 <span data-ttu-id="2d734-144">下圖說明兩個字元序列的聯合作業。</span><span class="sxs-lookup"><span data-stu-id="2d734-144">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="2d734-145">所傳回的序列包含兩個輸入序列中的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="2d734-145">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="2d734-146">![顯示兩個序列聯集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="2d734-146">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d734-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d734-147">See Also</span></span>  
 <span data-ttu-id="2d734-148"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="2d734-148"><xref:System.Linq></span></span>   
<span data-ttu-id="2d734-149"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2d734-149"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="2d734-150"> [如何：合併和比較字串集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span><span class="sxs-lookup"><span data-stu-id="2d734-150"> [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span></span>  
<span data-ttu-id="2d734-151"> [如何：尋找兩個清單之間的集合差異 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span><span class="sxs-lookup"><span data-stu-id="2d734-151"> [How to: Find the Set Difference Between Two Lists (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span></span>
