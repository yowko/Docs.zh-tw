---
title: 數量詞作業 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 24c8f9a6b589592c26c8a514bc44ff9623a82d2f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523101"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="485f5-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="485f5-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="485f5-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="485f5-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="485f5-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="485f5-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="485f5-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="485f5-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="485f5-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="485f5-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="485f5-107">![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="485f5-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="485f5-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="485f5-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="485f5-109">方法</span><span class="sxs-lookup"><span data-stu-id="485f5-109">Methods</span></span>  
  
|<span data-ttu-id="485f5-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="485f5-110">Method Name</span></span>|<span data-ttu-id="485f5-111">描述</span><span class="sxs-lookup"><span data-stu-id="485f5-111">Description</span></span>|<span data-ttu-id="485f5-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="485f5-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="485f5-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="485f5-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="485f5-114">全部</span><span class="sxs-lookup"><span data-stu-id="485f5-114">All</span></span>|<span data-ttu-id="485f5-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="485f5-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="485f5-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="485f5-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="485f5-117">任何</span><span class="sxs-lookup"><span data-stu-id="485f5-117">Any</span></span>|<span data-ttu-id="485f5-118">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="485f5-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="485f5-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="485f5-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="485f5-120">包含</span><span class="sxs-lookup"><span data-stu-id="485f5-120">Contains</span></span>|<span data-ttu-id="485f5-121">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="485f5-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="485f5-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="485f5-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="485f5-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="485f5-123">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="485f5-124">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="485f5-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="485f5-125">如何：在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="485f5-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
- [<span data-ttu-id="485f5-126">如何：查詢包含指定字組的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="485f5-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
