---
title: "數量詞作業 (C#) | Microsoft Docs"
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
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
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
ms.openlocfilehash: 0e4265f08f1fbe540885e1c9de28c5054f2f33a7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="quantifier-operations-c"></a><span data-ttu-id="7e38a-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e38a-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="7e38a-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="7e38a-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="7e38a-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="7e38a-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="7e38a-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7e38a-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="7e38a-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7e38a-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="7e38a-107">![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="7e38a-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="7e38a-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="7e38a-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e38a-109">方法</span><span class="sxs-lookup"><span data-stu-id="7e38a-109">Methods</span></span>  
  
|<span data-ttu-id="7e38a-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="7e38a-110">Method Name</span></span>|<span data-ttu-id="7e38a-111">描述</span><span class="sxs-lookup"><span data-stu-id="7e38a-111">Description</span></span>|<span data-ttu-id="7e38a-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="7e38a-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="7e38a-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="7e38a-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7e38a-114">全部</span><span class="sxs-lookup"><span data-stu-id="7e38a-114">All</span></span>|<span data-ttu-id="7e38a-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="7e38a-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7e38a-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="7e38a-116">Not applicable.</span></span>|<span data-ttu-id="7e38a-117"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-117"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="7e38a-118"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-118"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="7e38a-119">任何</span><span class="sxs-lookup"><span data-stu-id="7e38a-119">Any</span></span>|<span data-ttu-id="7e38a-120">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="7e38a-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7e38a-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="7e38a-121">Not applicable.</span></span>|<span data-ttu-id="7e38a-122"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-122"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="7e38a-123"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-123"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="7e38a-124">包含</span><span class="sxs-lookup"><span data-stu-id="7e38a-124">Contains</span></span>|<span data-ttu-id="7e38a-125">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="7e38a-125">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="7e38a-126">不適用。</span><span class="sxs-lookup"><span data-stu-id="7e38a-126">Not applicable.</span></span>|<span data-ttu-id="7e38a-127"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-127"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="7e38a-128"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7e38a-128"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e38a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e38a-129">See Also</span></span>  
 <span data-ttu-id="7e38a-130"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="7e38a-130"><xref:System.Linq></span></span>   
<span data-ttu-id="7e38a-131"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7e38a-131"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="7e38a-132"> [如何：在執行階段動態指定述詞篩選](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="7e38a-132"> [How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
<span data-ttu-id="7e38a-133"> [如何：查詢包含指定字組的句子 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)</span><span class="sxs-lookup"><span data-stu-id="7e38a-133"> [How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)</span></span>
