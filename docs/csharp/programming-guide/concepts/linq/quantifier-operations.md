---
title: 數量詞作業 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423355"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="fc08e-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="fc08e-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="fc08e-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="fc08e-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="fc08e-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="fc08e-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="fc08e-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fc08e-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="fc08e-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fc08e-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="fc08e-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="fc08e-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc08e-109">方法</span><span class="sxs-lookup"><span data-stu-id="fc08e-109">Methods</span></span>  
  
|<span data-ttu-id="fc08e-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="fc08e-110">Method Name</span></span>|<span data-ttu-id="fc08e-111">描述</span><span class="sxs-lookup"><span data-stu-id="fc08e-111">Description</span></span>|<span data-ttu-id="fc08e-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="fc08e-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="fc08e-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="fc08e-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fc08e-114">All</span><span class="sxs-lookup"><span data-stu-id="fc08e-114">All</span></span>|<span data-ttu-id="fc08e-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="fc08e-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="fc08e-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="fc08e-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fc08e-117">Any</span><span class="sxs-lookup"><span data-stu-id="fc08e-117">Any</span></span>|<span data-ttu-id="fc08e-118">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="fc08e-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="fc08e-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="fc08e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fc08e-120">包含</span><span class="sxs-lookup"><span data-stu-id="fc08e-120">Contains</span></span>|<span data-ttu-id="fc08e-121">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="fc08e-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="fc08e-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="fc08e-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="fc08e-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc08e-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fc08e-124">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="fc08e-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="fc08e-125">如何：在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="fc08e-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="fc08e-126">如何：查詢包含指定字組的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc08e-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
