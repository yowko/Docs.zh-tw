---
title: "篩選資料 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fa2d3b6c5b81f137ab3a81f9b18707bb2da91f6e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="0cd17-102">篩選資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cd17-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="0cd17-103">篩選作業的結果集限制為包含符合指定的條件之那些項目的參考。</span><span class="sxs-lookup"><span data-stu-id="0cd17-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="0cd17-104">它也就是選取項目。</span><span class="sxs-lookup"><span data-stu-id="0cd17-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="0cd17-105">下圖顯示的字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="0cd17-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="0cd17-106">篩選作業的述詞指定的字元必須是 'A'。</span><span class="sxs-lookup"><span data-stu-id="0cd17-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="0cd17-107">![LINQ 篩選作業](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="0cd17-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="0cd17-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="0cd17-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cd17-109">方法</span><span class="sxs-lookup"><span data-stu-id="0cd17-109">Methods</span></span>  
  
|<span data-ttu-id="0cd17-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="0cd17-110">Method Name</span></span>|<span data-ttu-id="0cd17-111">說明</span><span class="sxs-lookup"><span data-stu-id="0cd17-111">Description</span></span>|<span data-ttu-id="0cd17-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="0cd17-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0cd17-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="0cd17-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="0cd17-114">OfType</span><span class="sxs-lookup"><span data-stu-id="0cd17-114">OfType</span></span>|<span data-ttu-id="0cd17-115">選取值，視其可以轉換為指定型別而定。</span><span class="sxs-lookup"><span data-stu-id="0cd17-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="0cd17-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="0cd17-116">Not applicable.</span></span>|<span data-ttu-id="0cd17-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0cd17-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="0cd17-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0cd17-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="0cd17-119">位置</span><span class="sxs-lookup"><span data-stu-id="0cd17-119">Where</span></span>|<span data-ttu-id="0cd17-120">選取述詞函式為基礎的值。</span><span class="sxs-lookup"><span data-stu-id="0cd17-120">Selects values that are based on a predicate function.</span></span>|`Where`|<span data-ttu-id="0cd17-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0cd17-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="0cd17-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0cd17-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="0cd17-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="0cd17-123">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="0cd17-124">下列範例會使用`Where`來篩選陣列中具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="0cd17-124">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cd17-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd17-125">See Also</span></span>  
 <span data-ttu-id="0cd17-126"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="0cd17-126"><xref:System.Linq></span></span>   
<span data-ttu-id="0cd17-127"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0cd17-127"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="0cd17-128"> [其中子句](../../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0cd17-128"> [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="0cd17-129"> [如何︰ 篩選查詢結果](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0cd17-129"> [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="0cd17-130"> [如何︰ 查詢組件的中繼資料，使用反映 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0cd17-130"> [How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
<span data-ttu-id="0cd17-131"> [如何︰ 查詢具有指定之的屬性或名稱 (Visual Basic) 的檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="0cd17-131"> [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
<span data-ttu-id="0cd17-132"> [如何︰ 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="0cd17-132"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
