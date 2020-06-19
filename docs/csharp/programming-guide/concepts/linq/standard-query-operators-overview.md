---
title: 標準查詢運算子概觀 (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 095a0b7a7a8265f235d28a4634ea82cdcd7a60c0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990005"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="27c64-102">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="27c64-103">「標準查詢運算子」\*\* 是形成 LINQ 模式的方法。</span><span class="sxs-lookup"><span data-stu-id="27c64-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="27c64-104">這些方法大多會在序列上運作，而序列是指其類型會實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或 <xref:System.Linq.IQueryable%601> 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="27c64-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="27c64-105">標準查詢運算子所提供的查詢功能包括篩選、投影、彙總、排序等等。</span><span class="sxs-lookup"><span data-stu-id="27c64-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="27c64-106">有兩組 LINQ 標準查詢運算子：一個是在類型的物件上運作，另一個則是在 <xref:System.Collections.Generic.IEnumerable%601> 類型的物件上運作 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="27c64-106">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="27c64-107">構成每個集合的方法分別是 <xref:System.Linq.Enumerable> 和 <xref:System.Linq.Queryable> 類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="27c64-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="27c64-108">它們定義為其所運作的類型的「擴充方法」\*\*。</span><span class="sxs-lookup"><span data-stu-id="27c64-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="27c64-109">您可以使用靜態方法語法或實例方法語法來呼叫擴充方法。</span><span class="sxs-lookup"><span data-stu-id="27c64-109">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="27c64-110">此外，數個標準查詢運算子方法也會根據 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 之類型以外的類型運作。</span><span class="sxs-lookup"><span data-stu-id="27c64-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="27c64-111"><xref:System.Linq.Enumerable> 類型定義同時在 <xref:System.Collections.IEnumerable> 類型的物件上運作的兩個這類方法。</span><span class="sxs-lookup"><span data-stu-id="27c64-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="27c64-112"><xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 和 <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> 這些方法可讓您查詢 LINQ 模式中的非參數化或非泛型集合。</span><span class="sxs-lookup"><span data-stu-id="27c64-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="27c64-113">他們會藉由建立物件的強型別集合來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="27c64-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="27c64-114"><xref:System.Linq.Queryable> 類別定義在 <xref:System.Linq.Queryable> 類型的物件上運作的兩個類似方法 <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> 和 <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>。</span><span class="sxs-lookup"><span data-stu-id="27c64-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="27c64-115">根據傳回單一值還是一系列的值，標準查詢運算子的執行時機會不同。</span><span class="sxs-lookup"><span data-stu-id="27c64-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="27c64-116">這些傳回單一值的方法 (例如，<xref:System.Linq.Enumerable.Average%2A> 和 <xref:System.Linq.Enumerable.Sum%2A>) 就會立即執行。</span><span class="sxs-lookup"><span data-stu-id="27c64-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="27c64-117">傳回序列的方法會延後執行查詢，並傳回可列舉的物件。</span><span class="sxs-lookup"><span data-stu-id="27c64-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="27c64-118">對於在記憶體內部集合上運作的方法（也就是擴充的方法）， <xref:System.Collections.Generic.IEnumerable%601> 傳回的可列舉物件會捕捉傳遞至方法的引數。</span><span class="sxs-lookup"><span data-stu-id="27c64-118">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="27c64-119">列舉該物件時，會採用查詢運算子的邏輯，並傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="27c64-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="27c64-120">相反地，擴充的方法 <xref:System.Linq.IQueryable%601> 不會執行任何查詢行為。</span><span class="sxs-lookup"><span data-stu-id="27c64-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="27c64-121">它們會建立代表要執行之查詢的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="27c64-121">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="27c64-122">查詢處理是由來源 <xref:System.Linq.IQueryable%601> 物件所處理。</span><span class="sxs-lookup"><span data-stu-id="27c64-122">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="27c64-123">在一個查詢中，可以將查詢方法呼叫鏈結在一起，這樣會讓查詢變得更為複雜。</span><span class="sxs-lookup"><span data-stu-id="27c64-123">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="27c64-124">下列程式碼範例示範如何使用標準查詢運算子來取得序列的資訊。</span><span class="sxs-lookup"><span data-stu-id="27c64-124">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="27c64-125">查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="27c64-125">Query Expression Syntax</span></span>  
 <span data-ttu-id="27c64-126">某些更常用的標準查詢運算子具有專用 C# 和 Visual Basic 語言關鍵字語法，可將它們呼叫為「查詢運算式」\*\* \*\* 的一部分。</span><span class="sxs-lookup"><span data-stu-id="27c64-126">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="27c64-127">如需具有專用關鍵字和其對應語法之標準查詢運算子的詳細資訊，請參閱[標準查詢運算子的查詢運算式語法 (C#)](./query-expression-syntax-for-standard-query-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="27c64-127">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="27c64-128">擴充標準查詢運算子</span><span class="sxs-lookup"><span data-stu-id="27c64-128">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="27c64-129">您可以建立適用於目標定義域或技術的定義域特定方法，來擴增一組標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="27c64-129">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="27c64-130">您也可以將標準查詢運算子取代為提供額外服務的專屬實作，例如遠端評估、查詢轉譯和最佳化。</span><span class="sxs-lookup"><span data-stu-id="27c64-130">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="27c64-131">如需範例，請參閱 <xref:System.Linq.Enumerable.AsEnumerable%2A>。</span><span class="sxs-lookup"><span data-stu-id="27c64-131">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27c64-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="27c64-132">Related Sections</span></span>  
 <span data-ttu-id="27c64-133">下列連結會帶您前往可根據功能提供各種標準查詢運算子之其他相關資訊的文章。</span><span class="sxs-lookup"><span data-stu-id="27c64-133">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="27c64-134">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-134">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="27c64-135">設定作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-135">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="27c64-136">篩選資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-136">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="27c64-137">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-137">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="27c64-138">投射作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-138">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="27c64-139">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-139">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="27c64-140">聯結作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-140">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="27c64-141">分組資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-141">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="27c64-142">產生作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-142">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="27c64-143">相等比較作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-143">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="27c64-144">項目作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-144">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="27c64-145">轉換資料類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-145">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="27c64-146">串連作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-146">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="27c64-147">彙總作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-147">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="27c64-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c64-148">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="27c64-149">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-149">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="27c64-150">標準查詢運算子的查詢運算式語法 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-150">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="27c64-151">依據執行方式將標準查詢運算子分類 (C#)</span><span class="sxs-lookup"><span data-stu-id="27c64-151">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="27c64-152">擴充方法</span><span class="sxs-lookup"><span data-stu-id="27c64-152">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
