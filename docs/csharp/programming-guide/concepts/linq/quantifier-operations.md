---
title: 數量詞作業 (C#)
description: 瞭解數量詞作業。 這些作業會傳回布林值，指出序列中的部分或所有元素是否符合條件。
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ffefe1715fd8a074692967e825e0f55673bb2b27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202535"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="afdf8-104">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="afdf8-104">Quantifier Operations (C#)</span></span>

<span data-ttu-id="afdf8-105">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="afdf8-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="afdf8-106">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="afdf8-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="afdf8-107">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="afdf8-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="afdf8-108">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="afdf8-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="afdf8-110">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="afdf8-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afdf8-111">方法</span><span class="sxs-lookup"><span data-stu-id="afdf8-111">Methods</span></span>  
  
|<span data-ttu-id="afdf8-112">方法名稱</span><span class="sxs-lookup"><span data-stu-id="afdf8-112">Method Name</span></span>|<span data-ttu-id="afdf8-113">描述</span><span class="sxs-lookup"><span data-stu-id="afdf8-113">Description</span></span>|<span data-ttu-id="afdf8-114">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="afdf8-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="afdf8-115">相關資訊</span><span class="sxs-lookup"><span data-stu-id="afdf8-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="afdf8-116">全部</span><span class="sxs-lookup"><span data-stu-id="afdf8-116">All</span></span>|<span data-ttu-id="afdf8-117">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="afdf8-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="afdf8-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="afdf8-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="afdf8-119">任意</span><span class="sxs-lookup"><span data-stu-id="afdf8-119">Any</span></span>|<span data-ttu-id="afdf8-120">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="afdf8-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="afdf8-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="afdf8-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="afdf8-122">包含</span><span class="sxs-lookup"><span data-stu-id="afdf8-122">Contains</span></span>|<span data-ttu-id="afdf8-123">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="afdf8-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="afdf8-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="afdf8-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="afdf8-125">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="afdf8-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="afdf8-126">全部</span><span class="sxs-lookup"><span data-stu-id="afdf8-126">All</span></span>  

<span data-ttu-id="afdf8-127">下列範例 `All` 會使用來檢查所有字串的長度是否為特定長度。</span><span class="sxs-lookup"><span data-stu-id="afdf8-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="afdf8-128">任意</span><span class="sxs-lookup"><span data-stu-id="afdf8-128">Any</span></span>  

<span data-ttu-id="afdf8-129">下列範例 `Any` 會使用來檢查任何字串是否以 ' o ' 開頭。</span><span class="sxs-lookup"><span data-stu-id="afdf8-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="afdf8-130">包含</span><span class="sxs-lookup"><span data-stu-id="afdf8-130">Contains</span></span>  

<span data-ttu-id="afdf8-131">下列範例 `Contains` 會使用來檢查陣列是否有特定的元素。</span><span class="sxs-lookup"><span data-stu-id="afdf8-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="afdf8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afdf8-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="afdf8-133">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="afdf8-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="afdf8-134">在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="afdf8-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="afdf8-135">如何查詢包含指定字組的句子 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="afdf8-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
