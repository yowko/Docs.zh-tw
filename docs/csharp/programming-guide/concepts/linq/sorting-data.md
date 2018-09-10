---
title: 排序資料 (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 6a7f687895385bfb77d2a1e3e785742a794bb1b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275167"
---
# <a name="sorting-data-c"></a><span data-ttu-id="d8942-102">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8942-102">Sorting Data (C#)</span></span>
<span data-ttu-id="d8942-103">排序作業會根據一個或多個屬性來排序序列的項目。</span><span class="sxs-lookup"><span data-stu-id="d8942-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="d8942-104">第一個排序準則會執行元素的主要排序；</span><span class="sxs-lookup"><span data-stu-id="d8942-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="d8942-105">您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。</span><span class="sxs-lookup"><span data-stu-id="d8942-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="d8942-106">下圖顯示對一系列字元執行字母順序排序作業的結果。</span><span class="sxs-lookup"><span data-stu-id="d8942-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="d8942-107">![LINQ 排序作業](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="d8942-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="d8942-108">下節列出可排序資料的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="d8942-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8942-109">方法</span><span class="sxs-lookup"><span data-stu-id="d8942-109">Methods</span></span>  
  
|<span data-ttu-id="d8942-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="d8942-110">Method Name</span></span>|<span data-ttu-id="d8942-111">描述</span><span class="sxs-lookup"><span data-stu-id="d8942-111">Description</span></span>|<span data-ttu-id="d8942-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="d8942-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="d8942-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="d8942-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d8942-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d8942-114">OrderBy</span></span>|<span data-ttu-id="d8942-115">依遞增順序排序值。</span><span class="sxs-lookup"><span data-stu-id="d8942-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d8942-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="d8942-116">OrderByDescending</span></span>|<span data-ttu-id="d8942-117">依遞減順序排序值。</span><span class="sxs-lookup"><span data-stu-id="d8942-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d8942-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="d8942-118">ThenBy</span></span>|<span data-ttu-id="d8942-119">依遞增順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d8942-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="d8942-120">ThenByDescending</span></span>|<span data-ttu-id="d8942-121">依遞減順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d8942-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="d8942-122">Reverse</span></span>|<span data-ttu-id="d8942-123">反轉集合中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="d8942-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="d8942-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="d8942-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d8942-125">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="d8942-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="d8942-126">主要排序範例</span><span class="sxs-lookup"><span data-stu-id="d8942-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="d8942-127">主要遞增排序</span><span class="sxs-lookup"><span data-stu-id="d8942-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="d8942-128">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，依字串長度以遞增順序來排序陣列中的字串。</span><span class="sxs-lookup"><span data-stu-id="d8942-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="d8942-129">主要遞減排序</span><span class="sxs-lookup"><span data-stu-id="d8942-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="d8942-130">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，依其第一個字母以遞減順序來排序字串。</span><span class="sxs-lookup"><span data-stu-id="d8942-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="d8942-131">次要排序範例</span><span class="sxs-lookup"><span data-stu-id="d8942-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="d8942-132">次要遞增排序</span><span class="sxs-lookup"><span data-stu-id="d8942-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="d8942-133">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，對陣列中的字串執行主要和次要排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="d8942-134">字串主要是依長度進行排序，其次依字串的第一個字母進行排序，而兩者都是遞增排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="d8942-135">次要遞減排序</span><span class="sxs-lookup"><span data-stu-id="d8942-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="d8942-136">下一個範例示範如何在 LINQ 查詢中使用 `orderby descending` 子句，執行依遞增順序的主要排序以及依遞減順序的次要排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="d8942-137">字串主要是依長度進行排序，其次依字串的第一個字母進行排序。</span><span class="sxs-lookup"><span data-stu-id="d8942-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8942-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8942-138">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="d8942-139">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8942-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="d8942-140">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="d8942-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)  
- [<span data-ttu-id="d8942-141">如何：排序 Join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="d8942-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
- [<span data-ttu-id="d8942-142">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8942-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
