---
title: 資料分割 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e4e6d6db07a520b97911de5388b8e42b7e1acc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="0f5f1-102">資料分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5f1-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="0f5f1-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="0f5f1-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="0f5f1-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="0f5f1-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="0f5f1-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="0f5f1-108">![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="0f5f1-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="0f5f1-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="0f5f1-110">運算子</span><span class="sxs-lookup"><span data-stu-id="0f5f1-110">Operators</span></span>  
  
|<span data-ttu-id="0f5f1-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="0f5f1-111">Operator Name</span></span>|<span data-ttu-id="0f5f1-112">描述</span><span class="sxs-lookup"><span data-stu-id="0f5f1-112">Description</span></span>|<span data-ttu-id="0f5f1-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="0f5f1-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0f5f1-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="0f5f1-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="0f5f1-115">Skip</span><span class="sxs-lookup"><span data-stu-id="0f5f1-115">Skip</span></span>|<span data-ttu-id="0f5f1-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f5f1-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="0f5f1-117">SkipWhile</span></span>|<span data-ttu-id="0f5f1-118">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f5f1-119">Take</span><span class="sxs-lookup"><span data-stu-id="0f5f1-119">Take</span></span>|<span data-ttu-id="0f5f1-120">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f5f1-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="0f5f1-121">TakeWhile</span></span>|<span data-ttu-id="0f5f1-122">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0f5f1-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="0f5f1-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="0f5f1-124">Skip</span><span class="sxs-lookup"><span data-stu-id="0f5f1-124">Skip</span></span>  
 <span data-ttu-id="0f5f1-125">下列程式碼範例使用`Skip`子句來略過的字串陣列中的前四個字串，傳回剩餘之前的 Visual Basic 中字串陣列中。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="0f5f1-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="0f5f1-126">SkipWhile</span></span>  
 <span data-ttu-id="0f5f1-127">下列程式碼範例使用`Skip While`略過字串陣列中，字串的第一個字母時的 Visual Basic 中的子句"a"。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="0f5f1-128">會傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="0f5f1-129">Take</span><span class="sxs-lookup"><span data-stu-id="0f5f1-129">Take</span></span>  
 <span data-ttu-id="0f5f1-130">下列程式碼範例使用`Take`返回前兩個字串的字串陣列中的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="0f5f1-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="0f5f1-131">TakeWhile</span></span>  
 <span data-ttu-id="0f5f1-132">下列程式碼範例使用`Take While`來字串的長度超過五部時，傳回的字串陣列中的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="0f5f1-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0f5f1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f5f1-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="0f5f1-134">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5f1-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="0f5f1-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="0f5f1-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="0f5f1-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="0f5f1-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="0f5f1-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="0f5f1-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="0f5f1-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="0f5f1-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
