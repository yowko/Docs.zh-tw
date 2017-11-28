---
title: "數量詞作業 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d6152cbbd390508a8ffce732f6cbdf1f2e1aa0f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="b2bfb-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="b2bfb-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="b2bfb-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="b2bfb-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="b2bfb-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="b2bfb-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="b2bfb-107">![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="b2bfb-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="b2bfb-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2bfb-109">方法</span><span class="sxs-lookup"><span data-stu-id="b2bfb-109">Methods</span></span>  
  
|<span data-ttu-id="b2bfb-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="b2bfb-110">Method Name</span></span>|<span data-ttu-id="b2bfb-111">描述</span><span class="sxs-lookup"><span data-stu-id="b2bfb-111">Description</span></span>|<span data-ttu-id="b2bfb-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="b2bfb-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="b2bfb-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="b2bfb-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b2bfb-114">全部</span><span class="sxs-lookup"><span data-stu-id="b2bfb-114">All</span></span>|<span data-ttu-id="b2bfb-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b2bfb-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b2bfb-117">任何</span><span class="sxs-lookup"><span data-stu-id="b2bfb-117">Any</span></span>|<span data-ttu-id="b2bfb-118">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b2bfb-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b2bfb-120">包含</span><span class="sxs-lookup"><span data-stu-id="b2bfb-120">Contains</span></span>|<span data-ttu-id="b2bfb-121">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="b2bfb-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="b2bfb-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="b2bfb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2bfb-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="b2bfb-124">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="b2bfb-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="b2bfb-125">如何：在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="b2bfb-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="b2bfb-126">如何：查詢包含指定字組的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b2bfb-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
