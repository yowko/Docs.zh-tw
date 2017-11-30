---
title: "篩選資料 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31e3a4729a98e1f4b588cd415a15fff270587234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="73a45-102">篩選資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a45-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="73a45-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="73a45-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="73a45-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="73a45-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="73a45-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="73a45-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="73a45-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="73a45-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="73a45-107">![LINQ 篩選作業](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="73a45-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="73a45-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="73a45-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73a45-109">方法</span><span class="sxs-lookup"><span data-stu-id="73a45-109">Methods</span></span>  
  
|<span data-ttu-id="73a45-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="73a45-110">Method Name</span></span>|<span data-ttu-id="73a45-111">說明</span><span class="sxs-lookup"><span data-stu-id="73a45-111">Description</span></span>|<span data-ttu-id="73a45-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="73a45-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="73a45-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="73a45-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="73a45-114">OfType</span><span class="sxs-lookup"><span data-stu-id="73a45-114">OfType</span></span>|<span data-ttu-id="73a45-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="73a45-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="73a45-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="73a45-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="73a45-117">位置</span><span class="sxs-lookup"><span data-stu-id="73a45-117">Where</span></span>|<span data-ttu-id="73a45-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="73a45-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="73a45-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="73a45-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="73a45-120">下列範例會使用`Where`從陣列中篩選這些有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="73a45-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73a45-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73a45-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="73a45-122">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a45-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="73a45-123">Where 子句</span><span class="sxs-lookup"><span data-stu-id="73a45-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="73a45-124">如何：篩選查詢結果</span><span class="sxs-lookup"><span data-stu-id="73a45-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="73a45-125">如何： 查詢組件的中繼資料，使用反映 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a45-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="73a45-126">如何： 查詢的檔案與指定的屬性或名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a45-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="73a45-127">如何： 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73a45-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
