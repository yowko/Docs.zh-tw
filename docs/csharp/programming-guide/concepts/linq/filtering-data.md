---
title: 篩選資料 (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346997"
---
# <a name="filtering-data-c"></a><span data-ttu-id="cf3c4-102">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf3c4-102">Filtering Data (C#)</span></span>
<span data-ttu-id="cf3c4-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="cf3c4-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="cf3c4-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="cf3c4-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="cf3c4-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="cf3c4-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf3c4-109">方法</span><span class="sxs-lookup"><span data-stu-id="cf3c4-109">Methods</span></span>  
  
|<span data-ttu-id="cf3c4-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="cf3c4-110">Method Name</span></span>|<span data-ttu-id="cf3c4-111">描述</span><span class="sxs-lookup"><span data-stu-id="cf3c4-111">Description</span></span>|<span data-ttu-id="cf3c4-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="cf3c4-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="cf3c4-113">相關資訊</span><span class="sxs-lookup"><span data-stu-id="cf3c4-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="cf3c4-114">OfType</span><span class="sxs-lookup"><span data-stu-id="cf3c4-114">OfType</span></span>|<span data-ttu-id="cf3c4-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="cf3c4-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf3c4-117">Where</span><span class="sxs-lookup"><span data-stu-id="cf3c4-117">Where</span></span>|<span data-ttu-id="cf3c4-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="cf3c4-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="cf3c4-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="cf3c4-120">下列範例使用 `where` 子句從陣列篩選出具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="cf3c4-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf3c4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf3c4-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="cf3c4-122">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf3c4-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cf3c4-123">其中條款</span><span class="sxs-lookup"><span data-stu-id="cf3c4-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="cf3c4-124">在運行時動態指定謂詞篩選器</span><span class="sxs-lookup"><span data-stu-id="cf3c4-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="cf3c4-125">如何使用反射 （LINQ） （C#） 查詢程式集的中繼資料</span><span class="sxs-lookup"><span data-stu-id="cf3c4-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="cf3c4-126">如何查詢具有指定屬性或名稱 （C#） 的檔</span><span class="sxs-lookup"><span data-stu-id="cf3c4-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="cf3c4-127">如何按任何單詞或欄位 （LINQ） （C#） 對文本資料進行排序或篩選</span><span class="sxs-lookup"><span data-stu-id="cf3c4-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
