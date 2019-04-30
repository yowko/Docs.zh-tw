---
title: 篩選資料 (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826063"
---
# <a name="filtering-data-c"></a><span data-ttu-id="e7cc9-102">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-102">Filtering Data (C#)</span></span>
<span data-ttu-id="e7cc9-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="e7cc9-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="e7cc9-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="e7cc9-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="e7cc9-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="e7cc9-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7cc9-109">方法</span><span class="sxs-lookup"><span data-stu-id="e7cc9-109">Methods</span></span>  
  
|<span data-ttu-id="e7cc9-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="e7cc9-110">Method Name</span></span>|<span data-ttu-id="e7cc9-111">說明</span><span class="sxs-lookup"><span data-stu-id="e7cc9-111">Description</span></span>|<span data-ttu-id="e7cc9-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="e7cc9-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="e7cc9-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="e7cc9-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e7cc9-114">OfType</span><span class="sxs-lookup"><span data-stu-id="e7cc9-114">OfType</span></span>|<span data-ttu-id="e7cc9-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="e7cc9-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e7cc9-117">Where</span><span class="sxs-lookup"><span data-stu-id="e7cc9-117">Where</span></span>|<span data-ttu-id="e7cc9-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="e7cc9-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="e7cc9-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="e7cc9-120">下列範例使用 `where` 子句從陣列篩選出具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="e7cc9-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7cc9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7cc9-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e7cc9-122">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e7cc9-123">where 子句</span><span class="sxs-lookup"><span data-stu-id="e7cc9-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="e7cc9-124">如何：在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="e7cc9-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="e7cc9-125">如何：使用反映查詢組件的中繼資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="e7cc9-126">如何：查詢具有指定屬性或名稱的檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="e7cc9-127">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
