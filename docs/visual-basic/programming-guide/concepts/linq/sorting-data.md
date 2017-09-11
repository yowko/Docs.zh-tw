---
title: "排序資料 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
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
ms.openlocfilehash: 1870d401ffdeeb2452ace1b74a8fb70e19c9b9ed
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="8b8e0-102">排序資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b8e0-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="8b8e0-103">排序作業，排序順序，根據一個或多個屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="8b8e0-104">第一個排序準則會執行元素的主要排序；</span><span class="sxs-lookup"><span data-stu-id="8b8e0-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="8b8e0-105">您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="8b8e0-106">下圖顯示的字元序列的字母順序排序作業的結果。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="8b8e0-107">![LINQ 排序作業](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="8b8e0-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="8b8e0-108">排序資料的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b8e0-109">方法</span><span class="sxs-lookup"><span data-stu-id="8b8e0-109">Methods</span></span>  
  
|<span data-ttu-id="8b8e0-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="8b8e0-110">Method Name</span></span>|<span data-ttu-id="8b8e0-111">說明</span><span class="sxs-lookup"><span data-stu-id="8b8e0-111">Description</span></span>|<span data-ttu-id="8b8e0-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="8b8e0-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8b8e0-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="8b8e0-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="8b8e0-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="8b8e0-114">OrderBy</span></span>|<span data-ttu-id="8b8e0-115">值以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-115">Sorts values in ascending order.</span></span>|`Order By`|<span data-ttu-id="8b8e0-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8b8e0-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8b8e0-118">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="8b8e0-118">OrderByDescending</span></span>|<span data-ttu-id="8b8e0-119">值，以遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-119">Sorts values in descending order.</span></span>|`Order By … Descending`|<span data-ttu-id="8b8e0-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8b8e0-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8b8e0-122">ThenBy</span><span class="sxs-lookup"><span data-stu-id="8b8e0-122">ThenBy</span></span>|<span data-ttu-id="8b8e0-123">以遞增順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-123">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<span data-ttu-id="8b8e0-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8b8e0-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8b8e0-126">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="8b8e0-126">ThenByDescending</span></span>|<span data-ttu-id="8b8e0-127">以遞減的順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-127">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<span data-ttu-id="8b8e0-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8b8e0-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8b8e0-130">Reverse</span><span class="sxs-lookup"><span data-stu-id="8b8e0-130">Reverse</span></span>|<span data-ttu-id="8b8e0-131">反轉集合中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-131">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="8b8e0-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-132">Not applicable.</span></span>|<span data-ttu-id="8b8e0-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8b8e0-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8b8e0-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="8b8e0-135">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="8b8e0-135">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="8b8e0-136">主要排序範例</span><span class="sxs-lookup"><span data-stu-id="8b8e0-136">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="8b8e0-137">主要遞增排序</span><span class="sxs-lookup"><span data-stu-id="8b8e0-137">Primary Ascending Sort</span></span>  
 <span data-ttu-id="8b8e0-138">下列範例示範如何使用`Order By`子句，以將字串的長度，以遞增順序排序字串陣列中的 LINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-138">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="8b8e0-139">主要的遞減排序</span><span class="sxs-lookup"><span data-stu-id="8b8e0-139">Primary Descending Sort</span></span>  
 <span data-ttu-id="8b8e0-140">下一個範例示範如何使用`Order By Descending`LINQ 查詢，以其第一個字母，以遞減順序排序的字串中的子句。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-140">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="8b8e0-141">次要排序範例</span><span class="sxs-lookup"><span data-stu-id="8b8e0-141">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="8b8e0-142">次要遞增排序</span><span class="sxs-lookup"><span data-stu-id="8b8e0-142">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="8b8e0-143">下列範例示範如何使用`Order By`子句來執行主要和次要排序的字串陣列中的 LINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-143">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="8b8e0-144">字串的長度，然後再依遞增排序字串的第一個字母排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-144">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="8b8e0-145">次要遞減排序</span><span class="sxs-lookup"><span data-stu-id="8b8e0-145">Secondary Descending Sort</span></span>  
 <span data-ttu-id="8b8e0-146">下一個範例示範如何使用`Order By Descending`中 LINQ 查詢，以執行主要排序，以遞增順序，以及次要排序，以遞減順序子句。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-146">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="8b8e0-147">字串的長度，然後再依字串的第一個字母排序。</span><span class="sxs-lookup"><span data-stu-id="8b8e0-147">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b8e0-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b8e0-148">See Also</span></span>  
 <span data-ttu-id="8b8e0-149"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="8b8e0-149"><xref:System.Linq></span></span>   
<span data-ttu-id="8b8e0-150"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8b8e0-150"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="8b8e0-151"> [Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8b8e0-151"> [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="8b8e0-152"> [如何︰ 排序查詢結果](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="8b8e0-152"> [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="8b8e0-153"> [如何︰ 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="8b8e0-153"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
