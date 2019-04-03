---
title: 資料分割的資料 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2da63a1f6b73c8592d6036a90fa374a0d4385f4c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839570"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="69aff-102">資料分割的資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69aff-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="69aff-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="69aff-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="69aff-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="69aff-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="69aff-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="69aff-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="69aff-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="69aff-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="69aff-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="69aff-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![顯示圖例，三個 LINQ 分割作業。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="69aff-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="69aff-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="69aff-110">運算子</span><span class="sxs-lookup"><span data-stu-id="69aff-110">Operators</span></span>  
  
|<span data-ttu-id="69aff-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="69aff-111">Operator Name</span></span>|<span data-ttu-id="69aff-112">描述</span><span class="sxs-lookup"><span data-stu-id="69aff-112">Description</span></span>|<span data-ttu-id="69aff-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="69aff-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="69aff-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="69aff-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="69aff-115">Skip</span><span class="sxs-lookup"><span data-stu-id="69aff-115">Skip</span></span>|<span data-ttu-id="69aff-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="69aff-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69aff-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="69aff-117">SkipWhile</span></span>|<span data-ttu-id="69aff-118">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="69aff-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69aff-119">Take</span><span class="sxs-lookup"><span data-stu-id="69aff-119">Take</span></span>|<span data-ttu-id="69aff-120">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="69aff-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69aff-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="69aff-121">TakeWhile</span></span>|<span data-ttu-id="69aff-122">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="69aff-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="69aff-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="69aff-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="69aff-124">Skip</span><span class="sxs-lookup"><span data-stu-id="69aff-124">Skip</span></span>  
 <span data-ttu-id="69aff-125">下列程式碼範例使用`Skip`略過的字串陣列中的前四個字串中，再傳回其餘的 Visual Basic 中的子句字串陣列中。</span><span class="sxs-lookup"><span data-stu-id="69aff-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="69aff-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="69aff-126">SkipWhile</span></span>  
 <span data-ttu-id="69aff-127">下列程式碼範例使用`Skip While`子句在 Visual Basic 中略過陣列中的字串，而該字串的第一個字母是"a"。</span><span class="sxs-lookup"><span data-stu-id="69aff-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="69aff-128">會傳回陣列中剩餘的字串。</span><span class="sxs-lookup"><span data-stu-id="69aff-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="69aff-129">Take</span><span class="sxs-lookup"><span data-stu-id="69aff-129">Take</span></span>  
 <span data-ttu-id="69aff-130">下列程式碼範例使用`Take`在返回前兩個字串的字串陣列中的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="69aff-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="69aff-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="69aff-131">TakeWhile</span></span>  
 <span data-ttu-id="69aff-132">下列程式碼範例使用`Take While`以陣列傳回字串，而字串的長度為五個或更少的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="69aff-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="69aff-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69aff-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="69aff-134">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69aff-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="69aff-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="69aff-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="69aff-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="69aff-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="69aff-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="69aff-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="69aff-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="69aff-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
