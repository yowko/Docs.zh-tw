---
title: "數量詞作業 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="df041-102">數量詞作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df041-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="df041-103">數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="df041-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="df041-104">下圖說明兩個不同來源序列上的兩個不同數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="df041-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="df041-105">第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="df041-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="df041-106">第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="df041-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="df041-107">![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="df041-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="df041-108">下節列出執行數量詞作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="df041-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df041-109">方法</span><span class="sxs-lookup"><span data-stu-id="df041-109">Methods</span></span>  
  
|<span data-ttu-id="df041-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="df041-110">Method Name</span></span>|<span data-ttu-id="df041-111">說明</span><span class="sxs-lookup"><span data-stu-id="df041-111">Description</span></span>|<span data-ttu-id="df041-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="df041-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="df041-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="df041-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="df041-114">全部</span><span class="sxs-lookup"><span data-stu-id="df041-114">All</span></span>|<span data-ttu-id="df041-115">判斷序列中的所有項目是否都符合條件。</span><span class="sxs-lookup"><span data-stu-id="df041-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="df041-116">任何</span><span class="sxs-lookup"><span data-stu-id="df041-116">Any</span></span>|<span data-ttu-id="df041-117">判斷序列中的任何項目是否符合條件。</span><span class="sxs-lookup"><span data-stu-id="df041-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="df041-118">包含</span><span class="sxs-lookup"><span data-stu-id="df041-118">Contains</span></span>|<span data-ttu-id="df041-119">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="df041-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="df041-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="df041-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="df041-121">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="df041-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="df041-122">這些範例使用`Aggregate`子句在 Visual Basic 中的 LINQ 查詢的篩選條件的一部分。</span><span class="sxs-lookup"><span data-stu-id="df041-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="df041-123">下列範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.All%2A>擴充方法，從集合傳回其寵物是所有早於指定存在時間這些人。</span><span class="sxs-lookup"><span data-stu-id="df041-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="df041-124">下一個範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.Any%2A>擴充方法來傳回集合中至少有一個那些人 pet，小於指定存在時間。</span><span class="sxs-lookup"><span data-stu-id="df041-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="df041-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df041-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="df041-126">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df041-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="df041-127">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="df041-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="df041-128">如何： 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子</span><span class="sxs-lookup"><span data-stu-id="df041-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
