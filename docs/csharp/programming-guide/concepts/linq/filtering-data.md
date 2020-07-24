---
title: 篩選資料 (C#)
description: '篩選（也稱為選取）會根據條件來限制結果。 瞭解在 c # 中執行篩選的 LINQ 中的標準查詢運算子方法。'
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103922"
---
# <a name="filtering-data-c"></a><span data-ttu-id="0ad40-104">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="0ad40-104">Filtering Data (C#)</span></span>
<span data-ttu-id="0ad40-105">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="0ad40-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="0ad40-106">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="0ad40-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="0ad40-107">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="0ad40-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="0ad40-108">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="0ad40-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="0ad40-110">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="0ad40-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ad40-111">方法</span><span class="sxs-lookup"><span data-stu-id="0ad40-111">Methods</span></span>  
  
|<span data-ttu-id="0ad40-112">方法名稱</span><span class="sxs-lookup"><span data-stu-id="0ad40-112">Method Name</span></span>|<span data-ttu-id="0ad40-113">說明</span><span class="sxs-lookup"><span data-stu-id="0ad40-113">Description</span></span>|<span data-ttu-id="0ad40-114">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="0ad40-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="0ad40-115">相關資訊</span><span class="sxs-lookup"><span data-stu-id="0ad40-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0ad40-116">OfType</span><span class="sxs-lookup"><span data-stu-id="0ad40-116">OfType</span></span>|<span data-ttu-id="0ad40-117">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="0ad40-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="0ad40-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="0ad40-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0ad40-119">Where</span><span class="sxs-lookup"><span data-stu-id="0ad40-119">Where</span></span>|<span data-ttu-id="0ad40-120">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="0ad40-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="0ad40-121">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="0ad40-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="0ad40-122">下列範例使用 `where` 子句從陣列篩選出具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="0ad40-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ad40-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad40-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0ad40-124">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="0ad40-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0ad40-125">where 子句</span><span class="sxs-lookup"><span data-stu-id="0ad40-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="0ad40-126">在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="0ad40-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="0ad40-127">如何使用反映查詢元件的中繼資料（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="0ad40-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="0ad40-128">如何查詢具有指定屬性或名稱的檔案（c #）</span><span class="sxs-lookup"><span data-stu-id="0ad40-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="0ad40-129">如何依任何字或欄位排序或篩選文字資料（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="0ad40-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
