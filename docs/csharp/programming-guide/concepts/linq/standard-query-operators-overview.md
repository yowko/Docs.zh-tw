---
title: "標準查詢運算子概觀 (C#) | Microsoft Docs"
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
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 785b10fec450c7f8b42c28d81df2a2e4f9dd031b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="e7326-102">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="e7326-103">「標準查詢運算子」**是形成 LINQ 模式的方法。</span><span class="sxs-lookup"><span data-stu-id="e7326-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="e7326-104">這些方法大多會在序列上運作，而序列是指其類型會實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或 <xref:System.Linq.IQueryable%601> 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="e7326-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="e7326-105">標準查詢運算子所提供的查詢功能包括篩選、投影、彙總、排序等等。</span><span class="sxs-lookup"><span data-stu-id="e7326-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="e7326-106">有兩組 LINQ 標準查詢運算子，一個運作於類型 <xref:System.Collections.Generic.IEnumerable%601> 的物件，另一個則運作於類型 <xref:System.Linq.IQueryable%601> 的物件。</span><span class="sxs-lookup"><span data-stu-id="e7326-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e7326-107">構成每組的方法分別是 <xref:System.Linq.Enumerable> 和 <xref:System.Linq.Queryable> 類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="e7326-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="e7326-108">它們定義為其所運作的類型的「擴充方法」**。</span><span class="sxs-lookup"><span data-stu-id="e7326-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="e7326-109">這表示可以使用靜態方法語法或執行個體方法語法來呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="e7326-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="e7326-110">此外，數個標準查詢運算子方法運作於根據 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 的類型以外的類型。</span><span class="sxs-lookup"><span data-stu-id="e7326-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="e7326-111"><xref:System.Linq.Enumerable> 類型定義兩個這類方法，可同時運作於 <xref:System.Collections.IEnumerable> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="e7326-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="e7326-112">這些 <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 和 <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> 方法可讓您在 LINQ 模式查詢非參數化或非泛型集合。</span><span class="sxs-lookup"><span data-stu-id="e7326-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="e7326-113">建立物件的強類型集合即可進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="e7326-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="e7326-114"><xref:System.Linq.Queryable> 類別定義兩個類似的方法 (<xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> 和 <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>)，以運作於 <xref:System.Linq.Queryable> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="e7326-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="e7326-115">根據傳回單一值還是一系列的值，標準查詢運算子的執行時機會不同。</span><span class="sxs-lookup"><span data-stu-id="e7326-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="e7326-116">會立即執行傳回單一值的方法 (例如，<xref:System.Linq.Enumerable.Average%2A> 和 <xref:System.Linq.Enumerable.Sum%2A>)。</span><span class="sxs-lookup"><span data-stu-id="e7326-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="e7326-117">傳回序列的方法會延後執行查詢，並傳回可列舉的物件。</span><span class="sxs-lookup"><span data-stu-id="e7326-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="e7326-118">如果是運作於記憶體內部集合的方法，即擴充 <xref:System.Collections.Generic.IEnumerable%601> 的方法，則傳回的可列舉物件會擷取已傳遞給方法的引數。</span><span class="sxs-lookup"><span data-stu-id="e7326-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="e7326-119">列舉該物件時，會採用查詢運算子的邏輯，並傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="e7326-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="e7326-120">相反地，擴充 <xref:System.Linq.IQueryable%601> 的方法不會實作任何查詢行為，但會建置代表要執行查詢的運算式樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e7326-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="e7326-121">來源 <xref:System.Linq.IQueryable%601> 物件會處理查詢處理。</span><span class="sxs-lookup"><span data-stu-id="e7326-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="e7326-122">在一個查詢中，可以將查詢方法呼叫鏈結在一起，這樣會讓查詢變得更為複雜。</span><span class="sxs-lookup"><span data-stu-id="e7326-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="e7326-123">下列程式碼範例示範如何使用標準查詢運算子來取得序列的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7326-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="e7326-124">查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="e7326-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="e7326-125">某些更常用的標準查詢運算子具有專用 C# 和 Visual Basic 語言關鍵字語法，可將它們呼叫為「查詢運算式」****的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7326-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="e7326-126">如需具有專用關鍵字和其對應語法之標準查詢運算子的詳細資訊，請參閱[標準查詢運算子的查詢運算式語法 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="e7326-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="e7326-127">擴充標準查詢運算子</span><span class="sxs-lookup"><span data-stu-id="e7326-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="e7326-128">您可以建立適用於目標定義域或技術的定義域特定方法，來擴增一組標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="e7326-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="e7326-129">您也可以將標準查詢運算子取代為提供額外服務的專屬實作，例如遠端評估、查詢轉譯和最佳化。</span><span class="sxs-lookup"><span data-stu-id="e7326-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="e7326-130">請參閱 <xref:System.Linq.Enumerable.AsEnumerable%2A> 中的範例。</span><span class="sxs-lookup"><span data-stu-id="e7326-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7326-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="e7326-131">Related Sections</span></span>  
 <span data-ttu-id="e7326-132">下列連結會將您帶到根據功能而提供各種標準查詢運算子的其他資訊的主題。</span><span class="sxs-lookup"><span data-stu-id="e7326-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="e7326-133">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="e7326-134">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="e7326-135">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="e7326-136">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="e7326-137">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="e7326-138">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="e7326-139">聯結作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="e7326-140">分組資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="e7326-141">產生作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="e7326-142">相等比較作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="e7326-143">項目作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="e7326-144">轉換資料類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="e7326-145">串連作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="e7326-146">彙總作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e7326-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7326-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7326-147">See Also</span></span>  
 <span data-ttu-id="e7326-148"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="e7326-148"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="e7326-149"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="e7326-149"><xref:System.Linq.Queryable></span></span>   
<span data-ttu-id="e7326-150"> [LINQ 查詢簡介 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) </span><span class="sxs-lookup"><span data-stu-id="e7326-150"> [Introduction to LINQ Queries (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) </span></span>  
<span data-ttu-id="e7326-151"> [標準查詢運算子的查詢運算式語法 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e7326-151"> [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span></span>  
<span data-ttu-id="e7326-152"> [依據執行方式將標準查詢運算子分類 (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span><span class="sxs-lookup"><span data-stu-id="e7326-152"> [Classification of Standard Query Operators by Manner of Execution (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span></span>  
<span data-ttu-id="e7326-153"> [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="e7326-153"> [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)</span></span>
