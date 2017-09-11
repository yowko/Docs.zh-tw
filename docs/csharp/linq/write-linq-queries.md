---
title: "在 C 中撰寫 LINQ 查詢#"
description: "如何撰寫查詢。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a2306d3456fd641a56a78e4b62629adfd9c5ce38
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---

# <a name="write-linq-queries-in-c"></a><span data-ttu-id="9169f-104">在 C 中撰寫 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="9169f-104">Write LINQ queries in C</span></span>#

<span data-ttu-id="9169f-105">本主題示範您可以在 C# 中撰寫 LINQ 查詢的三種方式︰</span><span class="sxs-lookup"><span data-stu-id="9169f-105">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="9169f-106">使用查詢語法。</span><span class="sxs-lookup"><span data-stu-id="9169f-106">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="9169f-107">使用方法語法。</span><span class="sxs-lookup"><span data-stu-id="9169f-107">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="9169f-108">合併使用查詢語法與方法語法。</span><span class="sxs-lookup"><span data-stu-id="9169f-108">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="9169f-109">下列範例會使用先前列出的每種方法，來示範一些簡單 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="9169f-109">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="9169f-110">一般而言，規則會在可能時使用 (1)，並在需要時使用 (2) 和 (3)。</span><span class="sxs-lookup"><span data-stu-id="9169f-110">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9169f-111">這些查詢是在簡單記憶體內部集合上運作，但，基本語法與用於 LINQ to Entities 和 LINQ to XML 的語法完全相同。</span><span class="sxs-lookup"><span data-stu-id="9169f-111">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9169f-112">範例</span><span class="sxs-lookup"><span data-stu-id="9169f-112">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="9169f-113">查詢語法</span><span class="sxs-lookup"><span data-stu-id="9169f-113">Query syntax</span></span>  
 <span data-ttu-id="9169f-114">撰寫大部分查詢的建議方式是使用「查詢語法」**來建立「查詢運算式」**。</span><span class="sxs-lookup"><span data-stu-id="9169f-114">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="9169f-115">下列範例示範三個查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="9169f-115">The following example shows three query expressions.</span></span> <span data-ttu-id="9169f-116">第一個查詢運算式示範如何使用 `where` 子句套用條件來篩選或限制結果。</span><span class="sxs-lookup"><span data-stu-id="9169f-116">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="9169f-117">它會傳回值大於 7 或小於 3 的來源序列中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="9169f-117">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="9169f-118">第二個運算式示範如何排序傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="9169f-118">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="9169f-119">第三個運算式示範如何根據索引鍵來分組結果。</span><span class="sxs-lookup"><span data-stu-id="9169f-119">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="9169f-120">此查詢會根據單字的第一個字母來傳回兩個群組。</span><span class="sxs-lookup"><span data-stu-id="9169f-120">This query returns two groups based on the first letter of the word.</span></span>  
  
 <span data-ttu-id="9169f-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9169f-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span></span>  
  
 <span data-ttu-id="9169f-122">請注意，查詢的類型是 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="9169f-122">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="9169f-123">使用 `var` 可以撰寫所有這些查詢，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="9169f-123">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="9169f-124">在每個上述範例中，除非您逐一查看 `foreach` 陳述式或其他陳述式中的查詢變數，否則不會實際執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9169f-124">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="9169f-125">如需詳細資訊，請參閱 [LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9169f-125">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9169f-126">範例</span><span class="sxs-lookup"><span data-stu-id="9169f-126">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="9169f-127">方法語法</span><span class="sxs-lookup"><span data-stu-id="9169f-127">Method syntax</span></span>  
 <span data-ttu-id="9169f-128">某些查詢作業必須以方法呼叫形式表示。</span><span class="sxs-lookup"><span data-stu-id="9169f-128">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="9169f-129">最常見的這類方法就是傳回單一數值的方法，例如 <xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Average%2A> 等等。</span><span class="sxs-lookup"><span data-stu-id="9169f-129">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="9169f-130">一律必須在任何查詢中最後才呼叫這些方法，因為它們只代表單一值，並不能作為其他查詢作業的來源。</span><span class="sxs-lookup"><span data-stu-id="9169f-130">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="9169f-131">下列範例示範查詢運算式中的方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="9169f-131">The following example shows a method call in a query expression:</span></span>  
  
 <span data-ttu-id="9169f-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9169f-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9169f-133">範例</span><span class="sxs-lookup"><span data-stu-id="9169f-133">Example</span></span>  
 <span data-ttu-id="9169f-134">如果方法具有 Action 或 Func 參數，則這些項目是以 [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) 運算式形式提供，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="9169f-134">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 <span data-ttu-id="9169f-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9169f-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span></span>  
  
 <span data-ttu-id="9169f-136">在先前的查詢中，只會立即執行查詢 #4。</span><span class="sxs-lookup"><span data-stu-id="9169f-136">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="9169f-137">這是因為它會傳回單一值，而不是泛型 <xref:System.Collections.Generic.IEnumerable%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="9169f-137">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="9169f-138">方法本身必須使用 `foreach`，才能計算其值。</span><span class="sxs-lookup"><span data-stu-id="9169f-138">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="9169f-139">搭配使用隱含類型與 [var](../language-reference/keywords/var.md)，可以撰寫每個先前的查詢，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="9169f-139">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 <span data-ttu-id="9169f-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9169f-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9169f-141">範例</span><span class="sxs-lookup"><span data-stu-id="9169f-141">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="9169f-142">混合查詢和方法語法</span><span class="sxs-lookup"><span data-stu-id="9169f-142">Mixed query and method syntax</span></span>  
 <span data-ttu-id="9169f-143">這個範例示範如何在查詢子句結果上使用方法語法。</span><span class="sxs-lookup"><span data-stu-id="9169f-143">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="9169f-144">只需要用括號括住查詢運算式，然後套用點運算子並呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="9169f-144">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="9169f-145">在下列範例中，查詢 #7 會傳回其值介於 3 與 7 之間的數字計數。</span><span class="sxs-lookup"><span data-stu-id="9169f-145">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="9169f-146">不過，一般而言，最好使用第二個變數來儲存方法呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="9169f-146">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="9169f-147">如此一來，查詢就比較不容易與查詢結果混淆。</span><span class="sxs-lookup"><span data-stu-id="9169f-147">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 <span data-ttu-id="9169f-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="9169f-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span></span>  
  
 <span data-ttu-id="9169f-149">因為查詢 #7 會傳回單一值，而不是集合，所以會立即執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9169f-149">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="9169f-150">搭配使用隱含類型與 `var`，可以撰寫前一個查詢，如下列所示︰</span><span class="sxs-lookup"><span data-stu-id="9169f-150">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="9169f-151">它可以撰寫於方法語法中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9169f-151">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="9169f-152">它可以使用明確類型進行撰寫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9169f-152">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="9169f-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9169f-153">See Also</span></span>  
  <span data-ttu-id="9169f-154">[逐步解說：在 C# 中撰寫查詢](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="9169f-154">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
<span data-ttu-id="9169f-155"> [LINQ 查詢運算式](index.md) </span><span class="sxs-lookup"><span data-stu-id="9169f-155"> [LINQ Query Expressions](index.md) </span></span>  
<span data-ttu-id="9169f-156"> [where 子句](../language-reference/keywords/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="9169f-156"> [where clause](../language-reference/keywords/where-clause.md)</span></span>
