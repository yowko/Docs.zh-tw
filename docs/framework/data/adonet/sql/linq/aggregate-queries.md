---
title: "彙總查詢"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb1f26ec1fb8e5344946938206bb2418eeb6cd2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="aggregate-queries"></a><span data-ttu-id="24fb7-102">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="24fb7-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="24fb7-103"> 支援 `Average`、`Count`、`Max`、`Min` 和 `Sum` 彙總運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="24fb7-104">請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總運算子有下列特性：</span><span class="sxs-lookup"><span data-stu-id="24fb7-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="24fb7-105">彙總查詢會立即執行。</span><span class="sxs-lookup"><span data-stu-id="24fb7-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="24fb7-106">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="24fb7-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="24fb7-107">彙總查詢通常會傳回數字，而不是集合。</span><span class="sxs-lookup"><span data-stu-id="24fb7-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="24fb7-108">如需詳細資訊，請參閱[彙總作業](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4)。</span><span class="sxs-lookup"><span data-stu-id="24fb7-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="24fb7-109">您不可以對匿名型別呼叫彙總。</span><span class="sxs-lookup"><span data-stu-id="24fb7-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="24fb7-110">下列主題中的範例衍生自 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="24fb7-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="24fb7-111">如需詳細資訊，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="24fb7-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24fb7-112">本章節內容</span><span class="sxs-lookup"><span data-stu-id="24fb7-112">In This Section</span></span>  
 [<span data-ttu-id="24fb7-113">傳回數值序列的平均值</span><span class="sxs-lookup"><span data-stu-id="24fb7-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="24fb7-114">示範如何使用 <xref:System.Linq.Enumerable.Average%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="24fb7-115">計算序列中的項目數</span><span class="sxs-lookup"><span data-stu-id="24fb7-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="24fb7-116">示範如何使用 <xref:System.Linq.Enumerable.Count%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="24fb7-117">尋找數值序列中的最大值</span><span class="sxs-lookup"><span data-stu-id="24fb7-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="24fb7-118">示範如何使用 <xref:System.Linq.Enumerable.Max%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="24fb7-119">尋找數值序列中的最小值</span><span class="sxs-lookup"><span data-stu-id="24fb7-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="24fb7-120">示範如何使用 <xref:System.Linq.Enumerable.Min%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="24fb7-121">計算數值序列中值的總和</span><span class="sxs-lookup"><span data-stu-id="24fb7-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="24fb7-122">示範如何使用 <xref:System.Linq.Enumerable.Sum%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="24fb7-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="24fb7-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="24fb7-123">Related Sections</span></span>  
 [<span data-ttu-id="24fb7-124">查詢範例</span><span class="sxs-lookup"><span data-stu-id="24fb7-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="24fb7-125">提供 Visual Basic 和 C# 中之 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的連結。</span><span class="sxs-lookup"><span data-stu-id="24fb7-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="24fb7-126">查詢概念</span><span class="sxs-lookup"><span data-stu-id="24fb7-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="24fb7-127">提供在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中設計 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢之概念說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="24fb7-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="24fb7-128">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="24fb7-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="24fb7-129">說明查詢在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="24fb7-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
