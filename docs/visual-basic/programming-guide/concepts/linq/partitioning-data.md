---
title: 分割資料
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 34749f9d7b137bade66b6103650871246c3cc532
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406842"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="cd9a2-102">分割資料（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cd9a2-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="cd9a2-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="cd9a2-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="cd9a2-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="cd9a2-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="cd9a2-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![顯示三個 LINQ 分割作業的圖例。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="cd9a2-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="cd9a2-110">運算子</span><span class="sxs-lookup"><span data-stu-id="cd9a2-110">Operators</span></span>  
  
|<span data-ttu-id="cd9a2-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="cd9a2-111">Operator Name</span></span>|<span data-ttu-id="cd9a2-112">Description</span><span class="sxs-lookup"><span data-stu-id="cd9a2-112">Description</span></span>|<span data-ttu-id="cd9a2-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="cd9a2-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="cd9a2-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="cd9a2-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="cd9a2-115">跳過</span><span class="sxs-lookup"><span data-stu-id="cd9a2-115">Skip</span></span>|<span data-ttu-id="cd9a2-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd9a2-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="cd9a2-117">SkipWhile</span></span>|<span data-ttu-id="cd9a2-118">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd9a2-119">Take</span><span class="sxs-lookup"><span data-stu-id="cd9a2-119">Take</span></span>|<span data-ttu-id="cd9a2-120">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd9a2-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="cd9a2-121">TakeWhile</span></span>|<span data-ttu-id="cd9a2-122">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="cd9a2-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="cd9a2-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="cd9a2-124">跳過</span><span class="sxs-lookup"><span data-stu-id="cd9a2-124">Skip</span></span>  
 <span data-ttu-id="cd9a2-125">下列程式碼範例會 `Skip` 在 Visual Basic 中使用子句，以略過字串陣列中的前四個字串，然後才傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="cd9a2-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="cd9a2-126">SkipWhile</span></span>  
 <span data-ttu-id="cd9a2-127">下列程式碼範例會使用 `Skip While` Visual Basic 中的子句，略過陣列中的字串，而字串的第一個字母是 "a"。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="cd9a2-128">系統會傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="cd9a2-129">Take</span><span class="sxs-lookup"><span data-stu-id="cd9a2-129">Take</span></span>  
 <span data-ttu-id="cd9a2-130">下列程式碼範例會 `Take` 在 Visual Basic 中使用子句，以傳回字串陣列中的前兩個字串。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="cd9a2-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="cd9a2-131">TakeWhile</span></span>  
 <span data-ttu-id="cd9a2-132">下列程式碼範例會使用 `Take While` Visual Basic 中的子句，從陣列傳回字串，而字串長度為五個或更少。</span><span class="sxs-lookup"><span data-stu-id="cd9a2-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="cd9a2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd9a2-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="cd9a2-134">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd9a2-134">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="cd9a2-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="cd9a2-135">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="cd9a2-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="cd9a2-136">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="cd9a2-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="cd9a2-137">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="cd9a2-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="cd9a2-138">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)
