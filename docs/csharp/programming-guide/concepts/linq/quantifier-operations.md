---
title: 數量詞作業 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635479"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="7f9fb-102">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f9fb-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="7f9fb-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="7f9fb-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="7f9fb-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="7f9fb-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="7f9fb-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f9fb-109">方法</span><span class="sxs-lookup"><span data-stu-id="7f9fb-109">Methods</span></span>  
  
|<span data-ttu-id="7f9fb-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="7f9fb-110">Method Name</span></span>|<span data-ttu-id="7f9fb-111">描述</span><span class="sxs-lookup"><span data-stu-id="7f9fb-111">Description</span></span>|<span data-ttu-id="7f9fb-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="7f9fb-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="7f9fb-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="7f9fb-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7f9fb-114">全部</span><span class="sxs-lookup"><span data-stu-id="7f9fb-114">All</span></span>|<span data-ttu-id="7f9fb-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7f9fb-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f9fb-117">任何</span><span class="sxs-lookup"><span data-stu-id="7f9fb-117">Any</span></span>|<span data-ttu-id="7f9fb-118">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7f9fb-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f9fb-120">Contains</span><span class="sxs-lookup"><span data-stu-id="7f9fb-120">Contains</span></span>|<span data-ttu-id="7f9fb-121">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="7f9fb-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="7f9fb-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="7f9fb-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="7f9fb-124">全部</span><span class="sxs-lookup"><span data-stu-id="7f9fb-124">All</span></span>  
<span data-ttu-id="7f9fb-125">下列範例會使用 `All` 來檢查所有字串是否為特定長度。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="7f9fb-126">任何</span><span class="sxs-lookup"><span data-stu-id="7f9fb-126">Any</span></span>  
<span data-ttu-id="7f9fb-127">下列範例會使用 `Any` 來檢查任何字串都是以 ' o ' 開頭。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="7f9fb-128">Contains</span><span class="sxs-lookup"><span data-stu-id="7f9fb-128">Contains</span></span>  
<span data-ttu-id="7f9fb-129">下列範例會使用 `Contains` 來檢查陣列是否有特定的元素。</span><span class="sxs-lookup"><span data-stu-id="7f9fb-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9fb-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9fb-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7f9fb-131">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f9fb-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7f9fb-132">在執行階段動態指定述詞篩選條件</span><span class="sxs-lookup"><span data-stu-id="7f9fb-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="7f9fb-133">如何查詢包含指定字組的句子（LINQ）（C#）</span><span class="sxs-lookup"><span data-stu-id="7f9fb-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
