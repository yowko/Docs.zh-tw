---
title: 數量詞作業
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0c1c69cb36ac16126454dc0c24cd84fc85b0b218
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075300"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="93ef1-102">數量詞作業 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="93ef1-102">Quantifier Operations (Visual Basic)</span></span>

<span data-ttu-id="93ef1-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="93ef1-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="93ef1-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="93ef1-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="93ef1-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="93ef1-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="93ef1-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="93ef1-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="93ef1-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="93ef1-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93ef1-109">方法</span><span class="sxs-lookup"><span data-stu-id="93ef1-109">Methods</span></span>  
  
|<span data-ttu-id="93ef1-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="93ef1-110">Method Name</span></span>|<span data-ttu-id="93ef1-111">描述</span><span class="sxs-lookup"><span data-stu-id="93ef1-111">Description</span></span>|<span data-ttu-id="93ef1-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="93ef1-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="93ef1-113">相關資訊</span><span class="sxs-lookup"><span data-stu-id="93ef1-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="93ef1-114">全部</span><span class="sxs-lookup"><span data-stu-id="93ef1-114">All</span></span>|<span data-ttu-id="93ef1-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="93ef1-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="93ef1-116">任意</span><span class="sxs-lookup"><span data-stu-id="93ef1-116">Any</span></span>|<span data-ttu-id="93ef1-117">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="93ef1-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="93ef1-118">包含</span><span class="sxs-lookup"><span data-stu-id="93ef1-118">Contains</span></span>|<span data-ttu-id="93ef1-119">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="93ef1-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="93ef1-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="93ef1-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="93ef1-121">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="93ef1-121">Query Expression Syntax Examples</span></span>  

 <span data-ttu-id="93ef1-122">這些範例使用 `Aggregate` Visual Basic 中的子句作為 LINQ 查詢中篩選準則的一部分。</span><span class="sxs-lookup"><span data-stu-id="93ef1-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="93ef1-123">下列範例 `Aggregate` 會使用子句和 <xref:System.Linq.Enumerable.All%2A> 延伸方法，從集合中傳回其寵物全都早于指定年齡的人員。</span><span class="sxs-lookup"><span data-stu-id="93ef1-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="93ef1-124">下一個範例會使用 `Aggregate` 子句和 <xref:System.Linq.Enumerable.Any%2A> 延伸方法，從集合中傳回至少有一個寵物早于指定年齡的人。</span><span class="sxs-lookup"><span data-stu-id="93ef1-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="93ef1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93ef1-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="93ef1-126">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93ef1-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="93ef1-127">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="93ef1-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="93ef1-128">如何：查詢包含指定字組的句子 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93ef1-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
