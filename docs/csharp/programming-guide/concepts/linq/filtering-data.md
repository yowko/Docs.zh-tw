---
title: "篩選資料 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: defa6716f677c44da5dd27cb64b3b1d140a65272
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="filtering-data-c"></a><span data-ttu-id="cb823-102">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="cb823-102">Filtering Data (C#)</span></span>
<span data-ttu-id="cb823-103">篩選指的是將結果集限制為只包含符合指定條件之元素的作業，</span><span class="sxs-lookup"><span data-stu-id="cb823-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="cb823-104">也稱為選取。</span><span class="sxs-lookup"><span data-stu-id="cb823-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="cb823-105">下圖顯示字元序列的篩選結果。</span><span class="sxs-lookup"><span data-stu-id="cb823-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="cb823-106">篩選作業的述詞指定字元必須為 'A'。</span><span class="sxs-lookup"><span data-stu-id="cb823-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="cb823-107">![LINQ 篩選作業](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="cb823-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="cb823-108">執行選取的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="cb823-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb823-109">方法</span><span class="sxs-lookup"><span data-stu-id="cb823-109">Methods</span></span>  
  
|<span data-ttu-id="cb823-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="cb823-110">Method Name</span></span>|<span data-ttu-id="cb823-111">描述</span><span class="sxs-lookup"><span data-stu-id="cb823-111">Description</span></span>|<span data-ttu-id="cb823-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="cb823-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="cb823-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="cb823-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="cb823-114">OfType</span><span class="sxs-lookup"><span data-stu-id="cb823-114">OfType</span></span>|<span data-ttu-id="cb823-115">根據可轉換為所指定類型的能力來選取值。</span><span class="sxs-lookup"><span data-stu-id="cb823-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="cb823-116">不適用。</span><span class="sxs-lookup"><span data-stu-id="cb823-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|<span data-ttu-id="cb823-117">位置</span><span class="sxs-lookup"><span data-stu-id="cb823-117">Where</span></span>|<span data-ttu-id="cb823-118">根據述詞函式來選取值。</span><span class="sxs-lookup"><span data-stu-id="cb823-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="cb823-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="cb823-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="cb823-120">下列範例使用 `where` 子句從陣列篩選出具有特定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="cb823-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb823-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb823-121">See Also</span></span>  
 <span data-ttu-id="cb823-122"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="cb823-122"><xref:System.Linq></span></span>   
 <span data-ttu-id="cb823-123">[標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="cb823-123">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="cb823-124">[where 子句](../../../../csharp/language-reference/keywords/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cb823-124">[where clause](../../../../csharp/language-reference/keywords/where-clause.md) </span></span>  
 <span data-ttu-id="cb823-125">[如何：在執行階段動態指定述詞篩選](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="cb823-125">[How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
 <span data-ttu-id="cb823-126">[如何：使用反映查詢組件的中繼資料 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="cb823-126">[How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
 <span data-ttu-id="cb823-127">[如何：查詢具有指定之屬性或名稱的檔案 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="cb823-127">[How to: Query for Files with a Specified Attribute or Name (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
 [<span data-ttu-id="cb823-128">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cb823-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

