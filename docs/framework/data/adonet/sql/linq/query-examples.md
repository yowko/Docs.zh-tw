---
title: 查詢範例
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: f3f135850fb5f40b3b8882f72f5cc24512f21084
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147550"
---
# <a name="query-examples"></a><span data-ttu-id="0d6b8-102">查詢範例</span><span class="sxs-lookup"><span data-stu-id="0d6b8-102">Query Examples</span></span>

<span data-ttu-id="0d6b8-103">本節提供一般查詢的 Visual Basic 和 c # 範例 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="0d6b8-104">使用 Visual Studio 的開發人員可以在範例一節所提供的範例解決方案中找到更多範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="0d6b8-105">如需詳細資訊，請參閱 [範例](samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-105">For more information, see [Samples](samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d6b8-106">*資料庫* 通常用於檔中的程式碼範例 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="0d6b8-107">*db* 假設為 *Northwind* 類別的實例，而該類別繼承自 <xref:System.Data.Linq.DataContext> 。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d6b8-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0d6b8-108">In This Section</span></span>  

 [<span data-ttu-id="0d6b8-109">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="0d6b8-109">Aggregate Queries</span></span>](aggregate-queries.md)  
 <span data-ttu-id="0d6b8-110">說明如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> 等。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="0d6b8-111">傳回序列的第一個項目</span><span class="sxs-lookup"><span data-stu-id="0d6b8-111">Return the First Element in a Sequence</span></span>](return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="0d6b8-112">提供 <xref:System.Linq.Enumerable.First%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-113">傳回或略過序列中的項目</span><span class="sxs-lookup"><span data-stu-id="0d6b8-113">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="0d6b8-114">提供 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-115">在序列中排序項目</span><span class="sxs-lookup"><span data-stu-id="0d6b8-115">Sort Elements in a Sequence</span></span>](sort-elements-in-a-sequence.md)  
 <span data-ttu-id="0d6b8-116">提供 <xref:System.Linq.Enumerable.OrderBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-117">在序列中群組項目</span><span class="sxs-lookup"><span data-stu-id="0d6b8-117">Group Elements in a Sequence</span></span>](group-elements-in-a-sequence.md)  
 <span data-ttu-id="0d6b8-118">提供 <xref:System.Linq.Enumerable.GroupBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-119">從序列排除重複項目</span><span class="sxs-lookup"><span data-stu-id="0d6b8-119">Eliminate Duplicate Elements from a Sequence</span></span>](eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="0d6b8-120">提供 <xref:System.Linq.Enumerable.Distinct%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-121">判斷序列中的任何或所有項目是否全都符合條件</span><span class="sxs-lookup"><span data-stu-id="0d6b8-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="0d6b8-122">提供 <xref:System.Linq.Enumerable.All%2A> 和 <xref:System.Linq.Enumerable.Any%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-123">串連兩個序列</span><span class="sxs-lookup"><span data-stu-id="0d6b8-123">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)  
 <span data-ttu-id="0d6b8-124">提供 <xref:System.Linq.Enumerable.Concat%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-125">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="0d6b8-125">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="0d6b8-126">提供 <xref:System.Linq.Enumerable.Except%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-127">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="0d6b8-127">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="0d6b8-128">提供 <xref:System.Linq.Enumerable.Intersect%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-129">傳回兩個序列的集合聯集</span><span class="sxs-lookup"><span data-stu-id="0d6b8-129">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="0d6b8-130">提供 <xref:System.Linq.Enumerable.Union%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-131">將序列轉換為陣列</span><span class="sxs-lookup"><span data-stu-id="0d6b8-131">Convert a Sequence to an Array</span></span>](convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="0d6b8-132">提供 <xref:System.Linq.Enumerable.ToArray%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-133">將序列轉換為泛型 List</span><span class="sxs-lookup"><span data-stu-id="0d6b8-133">Convert a Sequence to a Generic List</span></span>](convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="0d6b8-134">提供 <xref:System.Linq.Enumerable.ToList%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-135">將類型轉換為泛型 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="0d6b8-135">Convert a Type to a Generic IEnumerable</span></span>](convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="0d6b8-136">提供 <xref:System.Linq.Enumerable.AsEnumerable%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="0d6b8-137">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="0d6b8-137">Formulate Joins and Cross-Product Queries</span></span>](formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="0d6b8-138">提供在 `from`、`where` 和 `select` 子句中進行外部索引鍵巡覽的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="0d6b8-139">制定投影</span><span class="sxs-lookup"><span data-stu-id="0d6b8-139">Formulate Projections</span></span>](formulate-projections.md)  
 <span data-ttu-id="0d6b8-140">提供 `select` 與其他功能結合的範例 (例如， *匿名* 型別) 來形成查詢投射。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d6b8-141">相關章節</span><span class="sxs-lookup"><span data-stu-id="0d6b8-141">Related Sections</span></span>  

 [<span data-ttu-id="0d6b8-142">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="0d6b8-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="0d6b8-143">說明使用 c # 的標準查詢運算子概念。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="0d6b8-144">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d6b8-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="0d6b8-145">說明使用 Visual Basic 之標準查詢運算子的概念。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="0d6b8-146">查詢概念</span><span class="sxs-lookup"><span data-stu-id="0d6b8-146">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="0d6b8-147">說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何運用查詢的概念。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="0d6b8-148">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0d6b8-148">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="0d6b8-149">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相關程式設計概念說明主題的入口網站。</span><span class="sxs-lookup"><span data-stu-id="0d6b8-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
