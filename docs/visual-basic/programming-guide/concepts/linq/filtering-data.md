---
title: 篩選資料 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: a673126d928a97bf522783e73fc254debe2a9de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051451"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="3a9f3-102">篩選資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9f3-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="3a9f3-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="3a9f3-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="3a9f3-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="3a9f3-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="3a9f3-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="3a9f3-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a9f3-109">方法</span><span class="sxs-lookup"><span data-stu-id="3a9f3-109">Methods</span></span>  
  
|<span data-ttu-id="3a9f3-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="3a9f3-110">Method Name</span></span>|<span data-ttu-id="3a9f3-111">描述</span><span class="sxs-lookup"><span data-stu-id="3a9f3-111">Description</span></span>|<span data-ttu-id="3a9f3-112">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="3a9f3-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3a9f3-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="3a9f3-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3a9f3-114">OfType</span><span class="sxs-lookup"><span data-stu-id="3a9f3-114">OfType</span></span>|<span data-ttu-id="3a9f3-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="3a9f3-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a9f3-117">Where</span><span class="sxs-lookup"><span data-stu-id="3a9f3-117">Where</span></span>|<span data-ttu-id="3a9f3-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="3a9f3-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="3a9f3-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="3a9f3-120">下列範例會使用`Where`若要從陣列篩選具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="3a9f3-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a9f3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a9f3-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3a9f3-122">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9f3-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3a9f3-123">Where 子句</span><span class="sxs-lookup"><span data-stu-id="3a9f3-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="3a9f3-124">如何：篩選查詢結果</span><span class="sxs-lookup"><span data-stu-id="3a9f3-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="3a9f3-125">如何：查詢組件的中繼資料，使用反映 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9f3-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="3a9f3-126">如何：查詢具有指定之屬性或名稱 (Visual Basic) 的檔案</span><span class="sxs-lookup"><span data-stu-id="3a9f3-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="3a9f3-127">如何：排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9f3-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
