---
title: "數量詞作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4e0c982508640ef1ecb47d477d3e9330198474ca
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="12b68-102">數量詞作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12b68-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="12b68-103">數量詞作業傳回<xref:System.Boolean>值，指出部分或全部順序中的項目是否全都符合條件。</xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="12b68-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="12b68-104">下圖顯示兩個不同的來源序列的兩個不同的數量詞作業。</span><span class="sxs-lookup"><span data-stu-id="12b68-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="12b68-105">第一項作業會要求，是否一或多個項目是字元 'A'，且結果為`true`。</span><span class="sxs-lookup"><span data-stu-id="12b68-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="12b68-106">第二項作業會要求，是否所有的項目為字元 'A'，且結果為`true`。</span><span class="sxs-lookup"><span data-stu-id="12b68-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="12b68-107">![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="12b68-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="12b68-108">執行數量詞作業的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="12b68-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12b68-109">方法</span><span class="sxs-lookup"><span data-stu-id="12b68-109">Methods</span></span>  
  
|<span data-ttu-id="12b68-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="12b68-110">Method Name</span></span>|<span data-ttu-id="12b68-111">說明</span><span class="sxs-lookup"><span data-stu-id="12b68-111">Description</span></span>|<span data-ttu-id="12b68-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="12b68-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="12b68-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="12b68-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="12b68-114">全部</span><span class="sxs-lookup"><span data-stu-id="12b68-114">All</span></span>|<span data-ttu-id="12b68-115">判斷序列中的所有項目是否全都符合條件。</span><span class="sxs-lookup"><span data-stu-id="12b68-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<span data-ttu-id="12b68-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="12b68-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="12b68-118">任何</span><span class="sxs-lookup"><span data-stu-id="12b68-118">Any</span></span>|<span data-ttu-id="12b68-119">判斷序列中的任何項目是否全都符合條件。</span><span class="sxs-lookup"><span data-stu-id="12b68-119">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<span data-ttu-id="12b68-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="12b68-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="12b68-122">包含</span><span class="sxs-lookup"><span data-stu-id="12b68-122">Contains</span></span>|<span data-ttu-id="12b68-123">判斷序列是否包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="12b68-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="12b68-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="12b68-124">Not applicable.</span></span>|<span data-ttu-id="12b68-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="12b68-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b68-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="12b68-127">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="12b68-127">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="12b68-128">這些範例使用`Aggregate`子句在 Visual Basic 中的 LINQ 查詢的篩選條件的一部分。</span><span class="sxs-lookup"><span data-stu-id="12b68-128">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="12b68-129">下列範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.All%2A>擴充方法，從集合中傳回這些人的寵物是所有超過指定的年齡。</xref:System.Linq.Enumerable.All%2A></span><span class="sxs-lookup"><span data-stu-id="12b68-129">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 <span data-ttu-id="12b68-130">[!code-vb[CsLINQAnyAll #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="12b68-130">[!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="12b68-131">下一個範例使用`Aggregate`子句和<xref:System.Linq.Enumerable.Any%2A>擴充方法來傳回集合中至少有一個這些人拍拍，已超過指定的年齡。</xref:System.Linq.Enumerable.Any%2A></span><span class="sxs-lookup"><span data-stu-id="12b68-131">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 <span data-ttu-id="12b68-132">[!code-vb[CsLINQAnyAll #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="12b68-132">[!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b68-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12b68-133">See Also</span></span>  
 <span data-ttu-id="12b68-134"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="12b68-134"><xref:System.Linq></span></span>   
<span data-ttu-id="12b68-135"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="12b68-135"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="12b68-136"> [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="12b68-136"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="12b68-137"> [如何︰ 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span><span class="sxs-lookup"><span data-stu-id="12b68-137"> [How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span></span>
