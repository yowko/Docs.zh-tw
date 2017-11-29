---
title: "查詢範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e7d7a0a1f641603887675ed0c1faebd5c06b273
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="query-examples"></a><span data-ttu-id="0d390-102">查詢範例</span><span class="sxs-lookup"><span data-stu-id="0d390-102">Query Examples</span></span>
<span data-ttu-id="0d390-103">本節提供典型 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 查詢的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 和 C# 範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-103">This section provides [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="0d390-104">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員，可以在＜範例＞一節提供的範例方案中找到更多的範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="0d390-105">如需詳細資訊，請參閱[範例](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d390-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d390-106">*db*常用程式碼範例中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="0d390-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="0d390-107">*db*假設為執行個體*Northwind*類別，繼承自<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="0d390-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d390-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="0d390-108">In This Section</span></span>  
 [<span data-ttu-id="0d390-109">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="0d390-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="0d390-110">說明如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> 等。</span><span class="sxs-lookup"><span data-stu-id="0d390-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="0d390-111">傳回序列中的第一個項目</span><span class="sxs-lookup"><span data-stu-id="0d390-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="0d390-112">提供 <xref:System.Linq.Enumerable.First%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-113">傳回或略過序列中的項目</span><span class="sxs-lookup"><span data-stu-id="0d390-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="0d390-114">提供 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-115">排序順序中的項目</span><span class="sxs-lookup"><span data-stu-id="0d390-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="0d390-116">提供 <xref:System.Linq.Enumerable.OrderBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-117">序列中的群組項目</span><span class="sxs-lookup"><span data-stu-id="0d390-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="0d390-118">提供 <xref:System.Linq.Enumerable.GroupBy%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-119">排除重複的項目，從序列</span><span class="sxs-lookup"><span data-stu-id="0d390-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="0d390-120">提供 <xref:System.Linq.Enumerable.Distinct%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-121">決定是否序列中的任何或所有項目滿足條件</span><span class="sxs-lookup"><span data-stu-id="0d390-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="0d390-122">提供 <xref:System.Linq.Enumerable.All%2A> 和 <xref:System.Linq.Enumerable.Any%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-123">串連兩個序列</span><span class="sxs-lookup"><span data-stu-id="0d390-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="0d390-124">提供 <xref:System.Linq.Enumerable.Concat%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-125">傳回兩個序列之間的差異</span><span class="sxs-lookup"><span data-stu-id="0d390-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="0d390-126">提供 <xref:System.Linq.Enumerable.Except%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-127">傳回兩個序列的集合交集</span><span class="sxs-lookup"><span data-stu-id="0d390-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="0d390-128">提供 <xref:System.Linq.Enumerable.Intersect%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-129">傳回兩個序列的聯集</span><span class="sxs-lookup"><span data-stu-id="0d390-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="0d390-130">提供 <xref:System.Linq.Enumerable.Union%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-131">將序列轉換為陣列</span><span class="sxs-lookup"><span data-stu-id="0d390-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="0d390-132">提供 <xref:System.Linq.Enumerable.ToArray%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-133">將序列轉換為一般清單</span><span class="sxs-lookup"><span data-stu-id="0d390-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="0d390-134">提供 <xref:System.Linq.Enumerable.ToList%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-135">將類型轉換成泛型 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="0d390-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="0d390-136">提供 <xref:System.Linq.Enumerable.AsEnumerable%2A> 的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="0d390-137">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="0d390-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="0d390-138">提供在 `from`、`where` 和 `select` 子句中進行外部索引鍵巡覽的使用範例。</span><span class="sxs-lookup"><span data-stu-id="0d390-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="0d390-139">制定投影</span><span class="sxs-lookup"><span data-stu-id="0d390-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="0d390-140">提供的合併範例`select`與其他功能 (例如，*匿名型別*) 以構成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="0d390-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d390-141">相關章節</span><span class="sxs-lookup"><span data-stu-id="0d390-141">Related Sections</span></span>  
 [<span data-ttu-id="0d390-142">標準查詢運算子概觀</span><span class="sxs-lookup"><span data-stu-id="0d390-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="0d390-143">說明標準查詢運算子的概念。</span><span class="sxs-lookup"><span data-stu-id="0d390-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="0d390-144">查詢概念</span><span class="sxs-lookup"><span data-stu-id="0d390-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="0d390-145">說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何運用查詢的概念。</span><span class="sxs-lookup"><span data-stu-id="0d390-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="0d390-146">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="0d390-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="0d390-147">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 相關程式設計概念說明主題的入口網站。</span><span class="sxs-lookup"><span data-stu-id="0d390-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
