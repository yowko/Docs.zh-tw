---
title: 排序資料 (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346461"
---
# <a name="sorting-data-c"></a><span data-ttu-id="15ff5-102">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="15ff5-102">Sorting Data (C#)</span></span>
<span data-ttu-id="15ff5-103">排序作業會根據一個或多個屬性來排序序列的項目。</span><span class="sxs-lookup"><span data-stu-id="15ff5-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="15ff5-104">第一個排序準則會執行元素的主要排序；</span><span class="sxs-lookup"><span data-stu-id="15ff5-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="15ff5-105">您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。</span><span class="sxs-lookup"><span data-stu-id="15ff5-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="15ff5-106">下圖顯示對一系列字元執行字母順序排序作業的結果：</span><span class="sxs-lookup"><span data-stu-id="15ff5-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![顯示依字母順序排序作業的圖形。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="15ff5-108">下節列出可排序資料的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="15ff5-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15ff5-109">方法</span><span class="sxs-lookup"><span data-stu-id="15ff5-109">Methods</span></span>  
  
|<span data-ttu-id="15ff5-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="15ff5-110">Method Name</span></span>|<span data-ttu-id="15ff5-111">描述</span><span class="sxs-lookup"><span data-stu-id="15ff5-111">Description</span></span>|<span data-ttu-id="15ff5-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="15ff5-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="15ff5-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="15ff5-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="15ff5-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="15ff5-114">OrderBy</span></span>|<span data-ttu-id="15ff5-115">依遞增順序排序值。</span><span class="sxs-lookup"><span data-stu-id="15ff5-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15ff5-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="15ff5-116">OrderByDescending</span></span>|<span data-ttu-id="15ff5-117">依遞減順序排序值。</span><span class="sxs-lookup"><span data-stu-id="15ff5-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15ff5-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="15ff5-118">ThenBy</span></span>|<span data-ttu-id="15ff5-119">依遞增順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15ff5-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="15ff5-120">ThenByDescending</span></span>|<span data-ttu-id="15ff5-121">依遞減順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15ff5-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="15ff5-122">Reverse</span></span>|<span data-ttu-id="15ff5-123">反轉集合中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="15ff5-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="15ff5-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="15ff5-125">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="15ff5-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="15ff5-126">主要排序範例</span><span class="sxs-lookup"><span data-stu-id="15ff5-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="15ff5-127">主要遞增排序</span><span class="sxs-lookup"><span data-stu-id="15ff5-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="15ff5-128">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，依字串長度以遞增順序來排序陣列中的字串。</span><span class="sxs-lookup"><span data-stu-id="15ff5-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="15ff5-129">主要遞減排序</span><span class="sxs-lookup"><span data-stu-id="15ff5-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="15ff5-130">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，依其第一個字母以遞減順序來排序字串。</span><span class="sxs-lookup"><span data-stu-id="15ff5-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="15ff5-131">次要排序範例</span><span class="sxs-lookup"><span data-stu-id="15ff5-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="15ff5-132">次要遞增排序</span><span class="sxs-lookup"><span data-stu-id="15ff5-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="15ff5-133">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，對陣列中的字串執行主要和次要排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="15ff5-134">字串主要是依長度進行排序，其次依字串的第一個字母進行排序，而兩者都是遞增排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="15ff5-135">次要遞減排序</span><span class="sxs-lookup"><span data-stu-id="15ff5-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="15ff5-136">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，執行依遞增順序的主要排序以及依遞減順序的次要排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="15ff5-137">字串主要是依長度進行排序，其次依字串的第一個字母進行排序。</span><span class="sxs-lookup"><span data-stu-id="15ff5-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="15ff5-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="15ff5-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="15ff5-139">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="15ff5-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="15ff5-140">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="15ff5-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="15ff5-141">排序 Join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="15ff5-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="15ff5-142">如何依任何字或欄位排序或篩選文字資料（LINQ）（C#）</span><span class="sxs-lookup"><span data-stu-id="15ff5-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
