---
title: 數量詞作業 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635479"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="58ace-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="58ace-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="58ace-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="58ace-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="58ace-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="58ace-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="58ace-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="58ace-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="58ace-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="58ace-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="58ace-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="58ace-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58ace-109">方法</span><span class="sxs-lookup"><span data-stu-id="58ace-109">Methods</span></span>  
  
|<span data-ttu-id="58ace-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="58ace-110">Method Name</span></span>|<span data-ttu-id="58ace-111">描述</span><span class="sxs-lookup"><span data-stu-id="58ace-111">Description</span></span>|<span data-ttu-id="58ace-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="58ace-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="58ace-113">相關資訊</span><span class="sxs-lookup"><span data-stu-id="58ace-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="58ace-114">全部</span><span class="sxs-lookup"><span data-stu-id="58ace-114">All</span></span>|<span data-ttu-id="58ace-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="58ace-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="58ace-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="58ace-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="58ace-117">任意</span><span class="sxs-lookup"><span data-stu-id="58ace-117">Any</span></span>|<span data-ttu-id="58ace-118">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="58ace-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="58ace-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="58ace-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="58ace-120">包含</span><span class="sxs-lookup"><span data-stu-id="58ace-120">Contains</span></span>|<span data-ttu-id="58ace-121">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="58ace-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="58ace-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="58ace-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="58ace-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="58ace-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="58ace-124">全部</span><span class="sxs-lookup"><span data-stu-id="58ace-124">All</span></span>  
<span data-ttu-id="58ace-125">下面的示例使用`All`檢查所有字串的長度。</span><span class="sxs-lookup"><span data-stu-id="58ace-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="58ace-126">任意</span><span class="sxs-lookup"><span data-stu-id="58ace-126">Any</span></span>  
<span data-ttu-id="58ace-127">下面的示例使用`Any`檢查任何字串的開頭為"o"。</span><span class="sxs-lookup"><span data-stu-id="58ace-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="58ace-128">包含</span><span class="sxs-lookup"><span data-stu-id="58ace-128">Contains</span></span>  
<span data-ttu-id="58ace-129">下面的示例使用`Contains`檢查陣列具有特定元素。</span><span class="sxs-lookup"><span data-stu-id="58ace-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="58ace-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ace-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="58ace-131">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="58ace-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="58ace-132">在運行時動態指定謂詞篩選器</span><span class="sxs-lookup"><span data-stu-id="58ace-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="58ace-133">如何查詢包含指定單詞集 （LINQ） （C#） 的句子</span><span class="sxs-lookup"><span data-stu-id="58ace-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
