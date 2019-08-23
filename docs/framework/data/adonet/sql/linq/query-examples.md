---
title: 查詢範例
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: 7be01abf568ed089089b1bc25d2a175f78ae7f7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962748"
---
# <a name="query-examples"></a><span data-ttu-id="5efd1-102">查詢範例</span><span class="sxs-lookup"><span data-stu-id="5efd1-102">Query Examples</span></span>
<span data-ttu-id="5efd1-103">本節提供一般[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢的C# Visual Basic 和範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="5efd1-104">使用 Visual Studio 的開發人員可以在範例一節中提供的範例解決方案中找到更多範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="5efd1-105">如需詳細資訊, 請參閱[範例](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5efd1-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5efd1-106">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔的程式碼範例中, 通常會使用 db。</span><span class="sxs-lookup"><span data-stu-id="5efd1-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="5efd1-107">假設*db*是*Northwind*類別的實例, 它會繼承自<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="5efd1-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5efd1-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="5efd1-108">In This Section</span></span>  
 [<span data-ttu-id="5efd1-109">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="5efd1-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="5efd1-110">說明如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> 等。</span><span class="sxs-lookup"><span data-stu-id="5efd1-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="5efd1-111">傳回序列的第一個項目</span><span class="sxs-lookup"><span data-stu-id="5efd1-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="5efd1-112">提供 <xref:System.Linq.Enumerable.First%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-113">傳回或略過序列中的項目</span><span class="sxs-lookup"><span data-stu-id="5efd1-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="5efd1-114">提供 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-115">排序序列中的項目</span><span class="sxs-lookup"><span data-stu-id="5efd1-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="5efd1-116">提供 <xref:System.Linq.Enumerable.OrderBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-117">群組序列中的項目</span><span class="sxs-lookup"><span data-stu-id="5efd1-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="5efd1-118">提供 <xref:System.Linq.Enumerable.GroupBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-119">從序列排除重複項目</span><span class="sxs-lookup"><span data-stu-id="5efd1-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="5efd1-120">提供 <xref:System.Linq.Enumerable.Distinct%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-121">判斷序列中的任何或所有項目是否全都符合條件</span><span class="sxs-lookup"><span data-stu-id="5efd1-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="5efd1-122">提供 <xref:System.Linq.Enumerable.All%2A> 和 <xref:System.Linq.Enumerable.Any%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-123">串連兩個序列</span><span class="sxs-lookup"><span data-stu-id="5efd1-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="5efd1-124">提供 <xref:System.Linq.Enumerable.Concat%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-125">傳回兩個序列之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="5efd1-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="5efd1-126">提供 <xref:System.Linq.Enumerable.Except%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-127">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="5efd1-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="5efd1-128">提供 <xref:System.Linq.Enumerable.Intersect%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-129">傳回兩個序列的集合聯集</span><span class="sxs-lookup"><span data-stu-id="5efd1-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="5efd1-130">提供 <xref:System.Linq.Enumerable.Union%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-131">將序列轉換為陣列</span><span class="sxs-lookup"><span data-stu-id="5efd1-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="5efd1-132">提供 <xref:System.Linq.Enumerable.ToArray%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-133">將序列轉換為泛型 List</span><span class="sxs-lookup"><span data-stu-id="5efd1-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="5efd1-134">提供 <xref:System.Linq.Enumerable.ToList%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-135">將類型轉換為泛型 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="5efd1-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="5efd1-136">提供 <xref:System.Linq.Enumerable.AsEnumerable%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="5efd1-137">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="5efd1-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="5efd1-138">提供在 `from`、`where` 和 `select` 子句中進行外部索引鍵巡覽的使用範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="5efd1-139">制定投影</span><span class="sxs-lookup"><span data-stu-id="5efd1-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="5efd1-140">提供與其他功能`select` (例如*匿名型別*) 結合以形成查詢投影的範例。</span><span class="sxs-lookup"><span data-stu-id="5efd1-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5efd1-141">相關章節</span><span class="sxs-lookup"><span data-stu-id="5efd1-141">Related Sections</span></span>  
 [<span data-ttu-id="5efd1-142">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="5efd1-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="5efd1-143">說明使用C#之標準查詢運算子的概念。</span><span class="sxs-lookup"><span data-stu-id="5efd1-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="5efd1-144">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5efd1-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="5efd1-145">說明使用 Visual Basic 之標準查詢運算子的概念。</span><span class="sxs-lookup"><span data-stu-id="5efd1-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="5efd1-146">查詢概念</span><span class="sxs-lookup"><span data-stu-id="5efd1-146">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="5efd1-147">說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何運用查詢的概念。</span><span class="sxs-lookup"><span data-stu-id="5efd1-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="5efd1-148">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="5efd1-148">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="5efd1-149">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相關程式設計概念說明主題的入口網站。</span><span class="sxs-lookup"><span data-stu-id="5efd1-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
