---
title: "分割資料 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
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
ms.openlocfilehash: 9d0df2bc473f48fba4bbb094317166407f7c7ec2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="adcd1-102">資料分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adcd1-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="adcd1-103">LINQ 中的資料分割是指作業分成兩個區段，將輸入的序列，而不需要重新排列項目，並接著傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="adcd1-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="adcd1-104">下圖顯示三個不同資料分割的作業序列的字元的結果。</span><span class="sxs-lookup"><span data-stu-id="adcd1-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="adcd1-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="adcd1-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="adcd1-106">第二項作業會略過前三個項目，並傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="adcd1-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="adcd1-107">第三個作業會略過序列中的前兩個項目，並傳回接下來的三項目。</span><span class="sxs-lookup"><span data-stu-id="adcd1-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="adcd1-108">![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="adcd1-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="adcd1-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="adcd1-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="adcd1-110">運算子</span><span class="sxs-lookup"><span data-stu-id="adcd1-110">Operators</span></span>  
  
|<span data-ttu-id="adcd1-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="adcd1-111">Operator Name</span></span>|<span data-ttu-id="adcd1-112">描述</span><span class="sxs-lookup"><span data-stu-id="adcd1-112">Description</span></span>|<span data-ttu-id="adcd1-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="adcd1-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="adcd1-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="adcd1-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="adcd1-115">Skip</span><span class="sxs-lookup"><span data-stu-id="adcd1-115">Skip</span></span>|<span data-ttu-id="adcd1-116">略過項目直到序列中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="adcd1-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<span data-ttu-id="adcd1-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="adcd1-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="adcd1-119">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="adcd1-119">SkipWhile</span></span>|<span data-ttu-id="adcd1-120">根據述詞函式，直到項目不符合條件的項目會略過。</span><span class="sxs-lookup"><span data-stu-id="adcd1-120">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<span data-ttu-id="adcd1-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="adcd1-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="adcd1-123">Take</span><span class="sxs-lookup"><span data-stu-id="adcd1-123">Take</span></span>|<span data-ttu-id="adcd1-124">會採用最序列中的指定位置的項目。</span><span class="sxs-lookup"><span data-stu-id="adcd1-124">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<span data-ttu-id="adcd1-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="adcd1-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="adcd1-127">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="adcd1-127">TakeWhile</span></span>|<span data-ttu-id="adcd1-128">會根據述詞函式，直到項目不符合條件的項目。</span><span class="sxs-lookup"><span data-stu-id="adcd1-128">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<span data-ttu-id="adcd1-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="adcd1-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="adcd1-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="adcd1-131">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="adcd1-131">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="adcd1-132">Skip</span><span class="sxs-lookup"><span data-stu-id="adcd1-132">Skip</span></span>  
 <span data-ttu-id="adcd1-133">下列程式碼範例使用`Skip`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]略過的字串陣列中的前四個字串，再傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="adcd1-133">The following code example uses the `Skip` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 <span data-ttu-id="adcd1-134">[!code-vb[CsLINQPartitioning #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="adcd1-134">[!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span></span>  
  
### <a name="skipwhile"></a><span data-ttu-id="adcd1-135">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="adcd1-135">SkipWhile</span></span>  
 <span data-ttu-id="adcd1-136">下列程式碼範例使用`Skip While`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]略過時的第一個字母字串的陣列中的字串為"a"。</span><span class="sxs-lookup"><span data-stu-id="adcd1-136">The following code example uses the `Skip While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="adcd1-137">傳回陣列中的其餘字串。</span><span class="sxs-lookup"><span data-stu-id="adcd1-137">The remaining strings in the array are returned.</span></span>  
  
 <span data-ttu-id="adcd1-138">[!code-vb[CsLINQPartitioning #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="adcd1-138">[!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span></span>  
  
### <a name="take"></a><span data-ttu-id="adcd1-139">Take</span><span class="sxs-lookup"><span data-stu-id="adcd1-139">Take</span></span>  
 <span data-ttu-id="adcd1-140">下列程式碼範例使用`Take`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]傳回字串陣列中的前兩個字串。</span><span class="sxs-lookup"><span data-stu-id="adcd1-140">The following code example uses the `Take` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return the first two strings in an array of strings.</span></span>  
  
 <span data-ttu-id="adcd1-141">[!code-vb[CsLINQPartitioning #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="adcd1-141">[!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span></span>  
  
### <a name="takewhile"></a><span data-ttu-id="adcd1-142">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="adcd1-142">TakeWhile</span></span>  
 <span data-ttu-id="adcd1-143">下列程式碼範例使用`Take While`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]來傳回的字串陣列，而字串的長度為五個或更少。</span><span class="sxs-lookup"><span data-stu-id="adcd1-143">The following code example uses the `Take While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return strings from an array while the length of the string is five or less.</span></span>  
  
 <span data-ttu-id="adcd1-144">[!code-vb[CsLINQPartitioning #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="adcd1-144">[!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adcd1-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adcd1-145">See Also</span></span>  
 <span data-ttu-id="adcd1-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="adcd1-146"><xref:System.Linq></span></span>   
<span data-ttu-id="adcd1-147"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="adcd1-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="adcd1-148"> [Skip 子句](../../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="adcd1-148"> [Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="adcd1-149"> [Skip While 子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="adcd1-149"> [Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="adcd1-150"> [Take 子句](../../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="adcd1-150"> [Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="adcd1-151"> [Take While 子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span><span class="sxs-lookup"><span data-stu-id="adcd1-151"> [Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span></span>
