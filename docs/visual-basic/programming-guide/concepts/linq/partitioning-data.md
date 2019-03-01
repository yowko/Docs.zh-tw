---
title: 資料分割的資料 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 06db2ac3e556e647fed576a7fa0c89b881b748c9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202141"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="ecf0d-102">資料分割的資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecf0d-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="ecf0d-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="ecf0d-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="ecf0d-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="ecf0d-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="ecf0d-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="ecf0d-108">![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="ecf0d-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="ecf0d-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="ecf0d-110">運算子</span><span class="sxs-lookup"><span data-stu-id="ecf0d-110">Operators</span></span>  
  
|<span data-ttu-id="ecf0d-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="ecf0d-111">Operator Name</span></span>|<span data-ttu-id="ecf0d-112">描述</span><span class="sxs-lookup"><span data-stu-id="ecf0d-112">Description</span></span>|<span data-ttu-id="ecf0d-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="ecf0d-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ecf0d-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="ecf0d-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ecf0d-115">Skip</span><span class="sxs-lookup"><span data-stu-id="ecf0d-115">Skip</span></span>|<span data-ttu-id="ecf0d-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ecf0d-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="ecf0d-117">SkipWhile</span></span>|<span data-ttu-id="ecf0d-118">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ecf0d-119">Take</span><span class="sxs-lookup"><span data-stu-id="ecf0d-119">Take</span></span>|<span data-ttu-id="ecf0d-120">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ecf0d-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="ecf0d-121">TakeWhile</span></span>|<span data-ttu-id="ecf0d-122">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ecf0d-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="ecf0d-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="ecf0d-124">Skip</span><span class="sxs-lookup"><span data-stu-id="ecf0d-124">Skip</span></span>  
 <span data-ttu-id="ecf0d-125">下列程式碼範例使用`Skip`略過的字串陣列中的前四個字串中，再傳回其餘的 Visual Basic 中的子句字串陣列中。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="ecf0d-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="ecf0d-126">SkipWhile</span></span>  
 <span data-ttu-id="ecf0d-127">下列程式碼範例使用`Skip While`子句在 Visual Basic 中略過陣列中的字串，而該字串的第一個字母是"a"。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="ecf0d-128">會傳回陣列中剩餘的字串。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="ecf0d-129">Take</span><span class="sxs-lookup"><span data-stu-id="ecf0d-129">Take</span></span>  
 <span data-ttu-id="ecf0d-130">下列程式碼範例使用`Take`在返回前兩個字串的字串陣列中的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="ecf0d-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="ecf0d-131">TakeWhile</span></span>  
 <span data-ttu-id="ecf0d-132">下列程式碼範例使用`Take While`以陣列傳回字串，而字串的長度為五個或更少的 Visual Basic 中的子句。</span><span class="sxs-lookup"><span data-stu-id="ecf0d-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ecf0d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf0d-133">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="ecf0d-134">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecf0d-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ecf0d-135">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="ecf0d-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="ecf0d-136">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="ecf0d-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="ecf0d-137">Take 子句</span><span class="sxs-lookup"><span data-stu-id="ecf0d-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="ecf0d-138">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="ecf0d-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
