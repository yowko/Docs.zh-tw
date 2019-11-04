---
title: 篩選資料 (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: eb448c1c2ea6d9b3fcf0120043cafebc01cd3805
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418467"
---
# <a name="filtering-data-c"></a><span data-ttu-id="a729a-102">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="a729a-102">Filtering Data (C#)</span></span>
<span data-ttu-id="a729a-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="a729a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="a729a-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="a729a-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="a729a-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="a729a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="a729a-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="a729a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="a729a-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="a729a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a729a-109">方法</span><span class="sxs-lookup"><span data-stu-id="a729a-109">Methods</span></span>  
  
|<span data-ttu-id="a729a-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="a729a-110">Method Name</span></span>|<span data-ttu-id="a729a-111">描述</span><span class="sxs-lookup"><span data-stu-id="a729a-111">Description</span></span>|<span data-ttu-id="a729a-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="a729a-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="a729a-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="a729a-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a729a-114">OfType</span><span class="sxs-lookup"><span data-stu-id="a729a-114">OfType</span></span>|<span data-ttu-id="a729a-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="a729a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="a729a-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="a729a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a729a-117">位置</span><span class="sxs-lookup"><span data-stu-id="a729a-117">Where</span></span>|<span data-ttu-id="a729a-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="a729a-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="a729a-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="a729a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="a729a-120">下列範例使用 `where` 子句從陣列篩選出具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="a729a-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a729a-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a729a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a729a-122">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="a729a-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="a729a-123">where 子句</span><span class="sxs-lookup"><span data-stu-id="a729a-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="a729a-124">如何：在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="a729a-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="a729a-125">如何：使用反映查詢組件的中繼資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a729a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="a729a-126">如何：查詢具有指定之屬性或名稱的檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="a729a-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="a729a-127">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a729a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
