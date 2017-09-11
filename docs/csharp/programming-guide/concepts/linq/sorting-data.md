---
title: "排序資料 (C#)"
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
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff6ef81486074f2e738b62ce37e6cb58bff49bf8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="sorting-data-c"></a><span data-ttu-id="c3dbb-102">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="c3dbb-102">Sorting Data (C#)</span></span>
<span data-ttu-id="c3dbb-103">排序作業會根據一個或多個屬性來排序序列的項目。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="c3dbb-104">第一個排序準則會執行元素的主要排序；</span><span class="sxs-lookup"><span data-stu-id="c3dbb-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="c3dbb-105">您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="c3dbb-106">下圖顯示對一系列字元執行字母順序排序作業的結果。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="c3dbb-107">![LINQ 排序作業](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="c3dbb-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="c3dbb-108">下節列出可排序資料的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3dbb-109">方法</span><span class="sxs-lookup"><span data-stu-id="c3dbb-109">Methods</span></span>  
  
|<span data-ttu-id="c3dbb-110">方法名稱</span><span class="sxs-lookup"><span data-stu-id="c3dbb-110">Method Name</span></span>|<span data-ttu-id="c3dbb-111">描述</span><span class="sxs-lookup"><span data-stu-id="c3dbb-111">Description</span></span>|<span data-ttu-id="c3dbb-112">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="c3dbb-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="c3dbb-113">更多資訊</span><span class="sxs-lookup"><span data-stu-id="c3dbb-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c3dbb-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="c3dbb-114">OrderBy</span></span>|<span data-ttu-id="c3dbb-115">依遞增順序排序值。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName>|  
|<span data-ttu-id="c3dbb-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="c3dbb-116">OrderByDescending</span></span>|<span data-ttu-id="c3dbb-117">依遞減順序排序值。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName>|  
|<span data-ttu-id="c3dbb-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="c3dbb-118">ThenBy</span></span>|<span data-ttu-id="c3dbb-119">依遞增順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName>|  
|<span data-ttu-id="c3dbb-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="c3dbb-120">ThenByDescending</span></span>|<span data-ttu-id="c3dbb-121">依遞減順序執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName>|  
|<span data-ttu-id="c3dbb-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="c3dbb-122">Reverse</span></span>|<span data-ttu-id="c3dbb-123">反轉集合中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="c3dbb-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c3dbb-125">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="c3dbb-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="c3dbb-126">主要排序範例</span><span class="sxs-lookup"><span data-stu-id="c3dbb-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="c3dbb-127">主要遞增排序</span><span class="sxs-lookup"><span data-stu-id="c3dbb-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="c3dbb-128">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，依字串長度以遞增順序來排序陣列中的字串。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="c3dbb-129">主要遞減排序</span><span class="sxs-lookup"><span data-stu-id="c3dbb-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="c3dbb-130">下一個範例示範如何在 LINQ 查詢中使用 `orderby``descending` 子句，依其第一個字母以遞減順序來排序字串。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-130">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="c3dbb-131">次要排序範例</span><span class="sxs-lookup"><span data-stu-id="c3dbb-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="c3dbb-132">次要遞增排序</span><span class="sxs-lookup"><span data-stu-id="c3dbb-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="c3dbb-133">下列範例示範如何在 LINQ 查詢中使用 `orderby` 子句，對陣列中的字串執行主要和次要排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="c3dbb-134">字串主要是依長度進行排序，其次依字串的第一個字母進行排序，而兩者都是遞增排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="c3dbb-135">次要遞減排序</span><span class="sxs-lookup"><span data-stu-id="c3dbb-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="c3dbb-136">下一個範例示範如何在 LINQ 查詢中使用 `orderby``descending` 子句，執行依遞增順序的主要排序以及依遞減順序的次要排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-136">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="c3dbb-137">字串主要是依長度進行排序，其次依字串的第一個字母進行排序。</span><span class="sxs-lookup"><span data-stu-id="c3dbb-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3dbb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3dbb-138">See Also</span></span>  
 <span data-ttu-id="c3dbb-139"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="c3dbb-139"><xref:System.Linq></span></span>   
 <span data-ttu-id="c3dbb-140">[標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c3dbb-140">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="c3dbb-141">[orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c3dbb-141">[orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md) </span></span>  
 <span data-ttu-id="c3dbb-142">[如何：排序 Join 子句的結果](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c3dbb-142">[How to: Order the Results of a Join Clause](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span></span>  
 [<span data-ttu-id="c3dbb-143">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3dbb-143">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

