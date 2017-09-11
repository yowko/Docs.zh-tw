---
title: "項目作業 (C#)"
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
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: da747e884960c89fabc45d3761da92f913d66362
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="element-operations-c"></a><span data-ttu-id="d2ebe-102">項目作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ebe-102">Element Operations (C#)</span></span>
<span data-ttu-id="d2ebe-103">項目作業會從序列中傳回單一特定的項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-103">Element operations return a single, specific element from a sequence.</span></span>  
  
 <span data-ttu-id="d2ebe-104">下節列出執行項目作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-104">The standard query operator methods that perform element operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2ebe-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2ebe-105">Methods</span></span>  
  
|<span data-ttu-id="d2ebe-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="d2ebe-106">Method Name</span></span>|<span data-ttu-id="d2ebe-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2ebe-107">Description</span></span>|<span data-ttu-id="d2ebe-108">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="d2ebe-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="d2ebe-109">更多資訊</span><span class="sxs-lookup"><span data-stu-id="d2ebe-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d2ebe-110">ElementAt</span><span class="sxs-lookup"><span data-stu-id="d2ebe-110">ElementAt</span></span>|<span data-ttu-id="d2ebe-111">傳回位於集合中指定索引處的項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-111">Returns the element at a specified index in a collection.</span></span>|<span data-ttu-id="d2ebe-112">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-113">ElementAtOrDefault</span><span class="sxs-lookup"><span data-stu-id="d2ebe-113">ElementAtOrDefault</span></span>|<span data-ttu-id="d2ebe-114">傳回位於集合中指定索引處的項目；如果索引超出範圍，則傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-114">Returns the element at a specified index in a collection or a default value if the index is out of range.</span></span>|<span data-ttu-id="d2ebe-115">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-116">First</span><span class="sxs-lookup"><span data-stu-id="d2ebe-116">First</span></span>|<span data-ttu-id="d2ebe-117">傳回集合中的第一個項目或符合條件的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-117">Returns the first element of a collection, or the first element that satisfies a condition.</span></span>|<span data-ttu-id="d2ebe-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-119">FirstOrDefault</span><span class="sxs-lookup"><span data-stu-id="d2ebe-119">FirstOrDefault</span></span>|<span data-ttu-id="d2ebe-120">傳回集合中的第一個項目或符合條件的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-120">Returns the first element of a collection, or the first element that satisfies a condition.</span></span> <span data-ttu-id="d2ebe-121">如果沒有這類項目，則傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-121">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="d2ebe-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-123">最後一筆</span><span class="sxs-lookup"><span data-stu-id="d2ebe-123">Last</span></span>|<span data-ttu-id="d2ebe-124">傳回集合中的最後一個項目或符合條件的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-124">Returns the last element of a collection, or the last element that satisfies a condition.</span></span>|<span data-ttu-id="d2ebe-125">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-126">LastOrDefault</span><span class="sxs-lookup"><span data-stu-id="d2ebe-126">LastOrDefault</span></span>|<span data-ttu-id="d2ebe-127">傳回集合中的最後一個項目或符合條件的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-127">Returns the last element of a collection, or the last element that satisfies a condition.</span></span> <span data-ttu-id="d2ebe-128">如果沒有這類項目，則傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-128">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="d2ebe-129">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-130">Single</span><span class="sxs-lookup"><span data-stu-id="d2ebe-130">Single</span></span>|<span data-ttu-id="d2ebe-131">傳回集合中的唯一項目或符合條件的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-131">Returns the only element of a collection, or the only element that satisfies a condition.</span></span>|<span data-ttu-id="d2ebe-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|<span data-ttu-id="d2ebe-133">SingleOrDefault</span><span class="sxs-lookup"><span data-stu-id="d2ebe-133">SingleOrDefault</span></span>|<span data-ttu-id="d2ebe-134">傳回集合中的唯一項目或符合條件的唯一項目。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-134">Returns the only element of a collection, or the only element that satisfies a condition.</span></span> <span data-ttu-id="d2ebe-135">如果沒有這類項目或集合不僅僅包含一個項目，則傳回預設值。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-135">Returns a default value if no such element exists or the collection does not contain exactly one element.</span></span>|<span data-ttu-id="d2ebe-136">不適用。</span><span class="sxs-lookup"><span data-stu-id="d2ebe-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="d2ebe-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ebe-137">See Also</span></span>  
 <span data-ttu-id="d2ebe-138"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="d2ebe-138"><xref:System.Linq></span></span>   
 <span data-ttu-id="d2ebe-139">[標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d2ebe-139">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="d2ebe-140">如何：查詢目錄樹狀中的最大檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ebe-140">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

