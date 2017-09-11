---
title: "基本 LINQ 查詢作業 (C#) | Microsoft Docs"
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
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48624d608c3eb8d1118a2492454595d46025cb3e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="df9eb-102">基本 LINQ 查詢作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="df9eb-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="df9eb-103">本主題簡介 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式以及在查詢中執行的一些一般類型的作業。</span><span class="sxs-lookup"><span data-stu-id="df9eb-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="df9eb-104">下列各主題提供更詳細的資訊：</span><span class="sxs-lookup"><span data-stu-id="df9eb-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="df9eb-105">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="df9eb-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="df9eb-106">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="df9eb-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="df9eb-107">逐步解說：在 C# 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="df9eb-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="df9eb-108">如果您已經熟悉 SQL 或 XQuery 這類查詢語言，則可以略過本主題的大部分內容。</span><span class="sxs-lookup"><span data-stu-id="df9eb-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="df9eb-109">閱讀下一節中的＜`from` 子句＞，以了解 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中的子句順序。</span><span class="sxs-lookup"><span data-stu-id="df9eb-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="df9eb-110">取得資料來源</span><span class="sxs-lookup"><span data-stu-id="df9eb-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="df9eb-111">在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，第一個步驟是指定資料來源。</span><span class="sxs-lookup"><span data-stu-id="df9eb-111">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="df9eb-112">在 C# 中，如同大多數程式設計語言一樣，必須先宣告變數，才能使用變數。</span><span class="sxs-lookup"><span data-stu-id="df9eb-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="df9eb-113">在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，依序會先出現 `from` 子句來引進資料來源 (`customers`) 和「範圍變數」**(`cust`)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-113">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 <span data-ttu-id="df9eb-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-115">範圍變數就像 `foreach` 迴圈中的反覆項目變數，差異在於查詢運算式中沒有實際反覆項目。</span><span class="sxs-lookup"><span data-stu-id="df9eb-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="df9eb-116">執行查詢時，範圍變數將會作為 `customers` 中每個後續項目的參考。</span><span class="sxs-lookup"><span data-stu-id="df9eb-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="df9eb-117">因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。</span><span class="sxs-lookup"><span data-stu-id="df9eb-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="df9eb-118">`let` 子句可以引進其他範圍變數。</span><span class="sxs-lookup"><span data-stu-id="df9eb-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="df9eb-119">如需詳細資訊，請參閱 [let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-119">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df9eb-120">針對 <xref:System.Collections.ArrayList> 這類非泛型資料來源，範圍變數的類型必須明確。</span><span class="sxs-lookup"><span data-stu-id="df9eb-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="df9eb-121">如需詳細資訊，請參閱[如何：使用 LINQ 查詢 ArrayList (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) 和 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-121">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="df9eb-122">篩選</span><span class="sxs-lookup"><span data-stu-id="df9eb-122">Filtering</span></span>  
 <span data-ttu-id="df9eb-123">最常見的查詢作業可能是以 Boolean 運算式的形式套用篩選條件。</span><span class="sxs-lookup"><span data-stu-id="df9eb-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="df9eb-124">篩選會導致查詢僅傳回運算式成立的項目。</span><span class="sxs-lookup"><span data-stu-id="df9eb-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="df9eb-125">結果是使用 `where` 子句所產生。</span><span class="sxs-lookup"><span data-stu-id="df9eb-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="df9eb-126">篩選實際上會指定要從來源序列中排除的項目。</span><span class="sxs-lookup"><span data-stu-id="df9eb-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="df9eb-127">在下列範例中，只會傳回地址在倫敦的 `customers`。</span><span class="sxs-lookup"><span data-stu-id="df9eb-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 <span data-ttu-id="df9eb-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-129">您可以使用熟悉的 C# 邏輯 `AND` 和 `OR` 運算式，在 `where` 子句中套用所需的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="df9eb-129">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="df9eb-130">例如，若只要傳回來自 "London" `AND` 名稱為 "Devon" 的客戶，請撰寫下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="df9eb-130">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 <span data-ttu-id="df9eb-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-132">若要傳回來自 London 或 Paris 的客戶，請撰寫下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="df9eb-132">To return customers from London or Paris, you would write the following code:</span></span>  
  
 <span data-ttu-id="df9eb-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-134">如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-134">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="df9eb-135">排序</span><span class="sxs-lookup"><span data-stu-id="df9eb-135">Ordering</span></span>  
 <span data-ttu-id="df9eb-136">通常很方便就可以排序所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="df9eb-136">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="df9eb-137">`orderby` 子句會根據所排序類型的預設比較子來排序所傳回序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="df9eb-137">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="df9eb-138">例如，可以擴充下列查詢，以根據 `Name` 屬性來排序結果。</span><span class="sxs-lookup"><span data-stu-id="df9eb-138">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="df9eb-139">因為 `Name` 是字串，所以預設比較子會執行從 A 到 Z 依字母順序排列的排序。</span><span class="sxs-lookup"><span data-stu-id="df9eb-139">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 <span data-ttu-id="df9eb-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-141">若要以相反順序排序結果 (從 Z 到 A)，請使用 `orderby…descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="df9eb-141">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="df9eb-142">如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-142">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="df9eb-143">群組</span><span class="sxs-lookup"><span data-stu-id="df9eb-143">Grouping</span></span>  
 <span data-ttu-id="df9eb-144">`group` 子句可讓您根據指定的索引鍵，將結果分組。</span><span class="sxs-lookup"><span data-stu-id="df9eb-144">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="df9eb-145">例如，您可以指定應該依 `City` 來群組結果；因此，來自 London 或 Paris 的所有客戶位於個別的群組中。</span><span class="sxs-lookup"><span data-stu-id="df9eb-145">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="df9eb-146">在此情況下，`cust.City` 是索引鍵。</span><span class="sxs-lookup"><span data-stu-id="df9eb-146">In this case, `cust.City` is the key.</span></span>  
  
 <span data-ttu-id="df9eb-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-148">使用 `group` 子句結束查詢時，結果的形式是一或多個清單。</span><span class="sxs-lookup"><span data-stu-id="df9eb-148">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="df9eb-149">清單中的每個項目都是一個物件，內含 `Key` 成員和群組在該索引鍵下的項目清單。</span><span class="sxs-lookup"><span data-stu-id="df9eb-149">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="df9eb-150">逐一查看產生一序列群組的查詢時，必須使用巢狀 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="df9eb-150">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="df9eb-151">外部迴圈會逐一查看每個群組，內部迴圈則會逐一查看每個群組的成員。</span><span class="sxs-lookup"><span data-stu-id="df9eb-151">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="df9eb-152">如果您必須參照群組作業的結果，則可以使用 `into` 關鍵字來建立可供進一步查詢的識別碼。</span><span class="sxs-lookup"><span data-stu-id="df9eb-152">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="df9eb-153">下列查詢只會傳回包含兩個以上客戶的群組︰</span><span class="sxs-lookup"><span data-stu-id="df9eb-153">The following query returns only those groups that contain more than two customers:</span></span>  
  
 <span data-ttu-id="df9eb-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-155">如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-155">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="df9eb-156">聯結</span><span class="sxs-lookup"><span data-stu-id="df9eb-156">Joining</span></span>  
 <span data-ttu-id="df9eb-157">聯結作業會建立資料來源中未明確模型化之序列間的關聯。</span><span class="sxs-lookup"><span data-stu-id="df9eb-157">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="df9eb-158">例如，您可以執行聯結來尋找位置相同的所有客戶和經銷商。</span><span class="sxs-lookup"><span data-stu-id="df9eb-158">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="df9eb-159">在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，`join` 子句一律會作用於物件集合，而不是直接作用於資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="df9eb-159">In [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 <span data-ttu-id="df9eb-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="df9eb-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span></span>  
  
 <span data-ttu-id="df9eb-161">在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，您不需要像在 SQL 中經常地使用 `join`，因為 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中的外部索引鍵在物件模型中會呈現為保存項目集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="df9eb-161">In [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="df9eb-162">例如，包含 `Order` 物件集合的 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="df9eb-162">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="df9eb-163">您可以使用點標記法來存取順序，而不是執行聯結：</span><span class="sxs-lookup"><span data-stu-id="df9eb-163">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="df9eb-164">如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-164">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="df9eb-165">選取 (投影)</span><span class="sxs-lookup"><span data-stu-id="df9eb-165">Selecting (Projections)</span></span>  
 <span data-ttu-id="df9eb-166">`select` 子句會產生查詢的結果，並指定每個所傳回項目的「圖形」或類型。</span><span class="sxs-lookup"><span data-stu-id="df9eb-166">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="df9eb-167">例如，您可以根據計算或新物件建立指定結果包含完整 `Customer` 物件、僅一個成員、成員子集，還是某個完全不同的結果類型。</span><span class="sxs-lookup"><span data-stu-id="df9eb-167">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="df9eb-168">`select` 子句不只產生一份來源項目時，作業稱為「投影」**。</span><span class="sxs-lookup"><span data-stu-id="df9eb-168">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="df9eb-169">使用投影來轉換資料是 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式的強大功能。</span><span class="sxs-lookup"><span data-stu-id="df9eb-169">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expressions.</span></span> <span data-ttu-id="df9eb-170">如需詳細資訊，請參閱[使用 LINQ 轉換資料 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) 和 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df9eb-170">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9eb-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df9eb-171">See Also</span></span>  
 <span data-ttu-id="df9eb-172">[開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="df9eb-172">[Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="df9eb-173"> [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="df9eb-173"> [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
<span data-ttu-id="df9eb-174"> [逐步解說：在 C# 中撰寫查詢](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="df9eb-174"> [Walkthrough: Writing Queries in C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
<span data-ttu-id="df9eb-175"> [查詢關鍵字 (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="df9eb-175"> [Query Keywords (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
<span data-ttu-id="df9eb-176"> [匿名類型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="df9eb-176"> [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span></span>
