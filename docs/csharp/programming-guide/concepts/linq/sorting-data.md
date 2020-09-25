---
title: 排序資料 (C#)
description: '深入瞭解排序作業，以及在 c # 中以 LINQ 執行排序作業的標準查詢運算子方法。'
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 0665e5dec95fd2929d24d82568de66597df1c0bd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195502"
---
# <a name="sorting-data-c"></a><span data-ttu-id="811e5-103">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="811e5-103">Sorting Data (C#)</span></span>

<span data-ttu-id="811e5-104">排序作業會根據一個或多個屬性來排序序列的項目。</span><span class="sxs-lookup"><span data-stu-id="811e5-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="811e5-105">第一個排序準則會執行元素的主要排序；</span><span class="sxs-lookup"><span data-stu-id="811e5-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="811e5-106">您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。</span><span class="sxs-lookup"><span data-stu-id="811e5-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="811e5-107">下圖顯示對一系列字元執行字母順序排序作業的結果：</span><span class="sxs-lookup"><span data-stu-id="811e5-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![顯示依字母順序排序作業的圖形。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="811e5-109">下節列出可排序資料的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="811e5-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="811e5-110">方法</span><span class="sxs-lookup"><span data-stu-id="811e5-110">Methods</span></span>  
  
|<span data-ttu-id="811e5-111">方法名稱</span><span class="sxs-lookup"><span data-stu-id="811e5-111">Method Name</span></span>|<span data-ttu-id="811e5-112">描述</span><span class="sxs-lookup"><span data-stu-id="811e5-112">Description</span></span>|<span data-ttu-id="811e5-113">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="811e5-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="811e5-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="811e5-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="811e5-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="811e5-115">OrderBy</span></span>|<span data-ttu-id="811e5-116">依遞增順序排序值。</span><span class="sxs-lookup"><span data-stu-id="811e5-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="811e5-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="811e5-117">OrderByDescending</span></span>|<span data-ttu-id="811e5-118">依遞減順序排序值。</span><span class="sxs-lookup"><span data-stu-id="811e5-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="811e5-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="811e5-119">ThenBy</span></span>|<span data-ttu-id="811e5-120">依遞增順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="811e5-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="811e5-121">ThenByDescending</span></span>|<span data-ttu-id="811e5-122">依遞減順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="811e5-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="811e5-123">Reverse</span></span>|<span data-ttu-id="811e5-124">反轉集合中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="811e5-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="811e5-125">不適用。</span><span class="sxs-lookup"><span data-stu-id="811e5-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="811e5-126">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="811e5-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="811e5-127">主要排序範例</span><span class="sxs-lookup"><span data-stu-id="811e5-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="811e5-128">主要遞增排序</span><span class="sxs-lookup"><span data-stu-id="811e5-128">Primary Ascending Sort</span></span>  

 <span data-ttu-id="811e5-129">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，依字串長度以遞增順序來排序陣列中的字串。</span><span class="sxs-lookup"><span data-stu-id="811e5-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="811e5-130">主要遞減排序</span><span class="sxs-lookup"><span data-stu-id="811e5-130">Primary Descending Sort</span></span>  

 <span data-ttu-id="811e5-131">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，依其第一個字母以遞減順序來排序字串。</span><span class="sxs-lookup"><span data-stu-id="811e5-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="811e5-132">次要排序範例</span><span class="sxs-lookup"><span data-stu-id="811e5-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="811e5-133">次要遞增排序</span><span class="sxs-lookup"><span data-stu-id="811e5-133">Secondary Ascending Sort</span></span>  

 <span data-ttu-id="811e5-134">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，對陣列中的字串執行主要和次要排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="811e5-135">字串主要是依長度進行排序，其次依字串的第一個字母進行排序，而兩者都是遞增排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="811e5-136">次要遞減排序</span><span class="sxs-lookup"><span data-stu-id="811e5-136">Secondary Descending Sort</span></span>  

 <span data-ttu-id="811e5-137">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，執行依遞增順序的主要排序以及依遞減順序的次要排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="811e5-138">字串主要是依長度進行排序，其次依字串的第一個字母進行排序。</span><span class="sxs-lookup"><span data-stu-id="811e5-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="811e5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="811e5-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="811e5-140">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="811e5-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="811e5-141">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="811e5-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="811e5-142">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="811e5-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="811e5-143">如何依任何字或欄位排序或篩選文字資料 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="811e5-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
