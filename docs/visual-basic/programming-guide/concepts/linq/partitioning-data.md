---
title: 分割資料
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353145"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="9cb5c-102">分割資料（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9cb5c-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="9cb5c-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="9cb5c-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="9cb5c-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="9cb5c-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="9cb5c-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![顯示三個 LINQ 分割作業的圖例。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="9cb5c-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="9cb5c-110">運算子</span><span class="sxs-lookup"><span data-stu-id="9cb5c-110">Operators</span></span>  
  
|<span data-ttu-id="9cb5c-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="9cb5c-111">Operator Name</span></span>|<span data-ttu-id="9cb5c-112">描述</span><span class="sxs-lookup"><span data-stu-id="9cb5c-112">Description</span></span>|<span data-ttu-id="9cb5c-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="9cb5c-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9cb5c-114">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9cb5c-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9cb5c-115">Skip</span><span class="sxs-lookup"><span data-stu-id="9cb5c-115">Skip</span></span>|<span data-ttu-id="9cb5c-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9cb5c-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="9cb5c-117">SkipWhile</span></span>|<span data-ttu-id="9cb5c-118">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9cb5c-119">Take</span><span class="sxs-lookup"><span data-stu-id="9cb5c-119">Take</span></span>|<span data-ttu-id="9cb5c-120">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9cb5c-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="9cb5c-121">TakeWhile</span></span>|<span data-ttu-id="9cb5c-122">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9cb5c-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="9cb5c-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="9cb5c-124">Skip</span><span class="sxs-lookup"><span data-stu-id="9cb5c-124">Skip</span></span>  
 <span data-ttu-id="9cb5c-125">下列程式碼範例會使用 Visual Basic 中的 `Skip` 子句，先跳過字串陣列中的前四個字串，再傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="9cb5c-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="9cb5c-126">SkipWhile</span></span>  
 <span data-ttu-id="9cb5c-127">下列程式碼範例會使用 Visual Basic 中的 `Skip While` 子句，略過陣列中的字串，而字串的第一個字母是 "a"。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="9cb5c-128">系統會傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="9cb5c-129">Take</span><span class="sxs-lookup"><span data-stu-id="9cb5c-129">Take</span></span>  
 <span data-ttu-id="9cb5c-130">下列程式碼範例會在 Visual Basic 中使用 `Take` 子句，以傳回字串陣列中的前兩個字串。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="9cb5c-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="9cb5c-131">TakeWhile</span></span>  
 <span data-ttu-id="9cb5c-132">下列程式碼範例會使用 Visual Basic 中的 `Take While` 子句來傳回陣列中的字串，而字串長度則為五個或更少。</span><span class="sxs-lookup"><span data-stu-id="9cb5c-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9cb5c-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb5c-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9cb5c-134">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5c-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9cb5c-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="9cb5c-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="9cb5c-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="9cb5c-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="9cb5c-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="9cb5c-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="9cb5c-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="9cb5c-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
