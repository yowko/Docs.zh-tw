---
title: Language-Integrated Query (LINQ) (C#)
ms.custom: 
ms.date: 02/02/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0a721bba36eb1ed4ae94b99e25a1dcce33faef6e
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="language-integrated-query-linq"></a><span data-ttu-id="858a1-102">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="858a1-102">Language Integrated Query (LINQ)</span></span>

<span data-ttu-id="858a1-103">Language Integrated Query (LINQ) 是一組以直接將查詢功能整合至 C# 語言為基礎之技術的名稱。</span><span class="sxs-lookup"><span data-stu-id="858a1-103">Language-Integrated Query (LINQ) is the name for a set of technologies based on the integration of query capabilities directly into the C# language.</span></span> <span data-ttu-id="858a1-104">傳統上，針對資料的查詢是以簡單字串表示，而不會在編譯期間進行型別檢查，或提供 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="858a1-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="858a1-105">此外，您必須針對每個資料來源型別 (例如 SQL 資料庫、XML 文件、各種 Web 服務等等) 學習不同的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="858a1-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="858a1-106">透過 LINQ，查詢會是第一級語言建構，和類別、方法及事件相同。</span><span class="sxs-lookup"><span data-stu-id="858a1-106">With LINQ, a query is a first-class language construct, just like classes, methods, events.</span></span>

<span data-ttu-id="858a1-107">對於撰寫查詢的開發人員來說，LINQ 最明顯的「語言整合」部分就是查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="858a1-107">For a developer who writes queries, the most visible "language-integrated" part of LINQ is the query expression.</span></span> <span data-ttu-id="858a1-108">查詢運算式是以宣告式「查詢語法」撰寫。</span><span class="sxs-lookup"><span data-stu-id="858a1-108">Query expressions are written in a declarative *query syntax*.</span></span> <span data-ttu-id="858a1-109">透過使用查詢語法，您就可以利用最少的程式碼，針對資料來源執行篩選、排序及分組作業。</span><span class="sxs-lookup"><span data-stu-id="858a1-109">By using query syntax, you can perform filtering, ordering, and grouping operations on data sources with a minimum of code.</span></span> <span data-ttu-id="858a1-110">您可以使用相同的基本查詢運算式模式，來查詢並轉換 SQL 資料庫、ADO .NET 資料集、XML 文件及資料流，以及 .NET 集合中的資料。</span><span class="sxs-lookup"><span data-stu-id="858a1-110">You use the same basic query expression patterns to query and transform data in SQL databases, ADO .NET Datasets, XML documents and streams, and .NET collections.</span></span>

<span data-ttu-id="858a1-111">下列範例示範完整的查詢作業。</span><span class="sxs-lookup"><span data-stu-id="858a1-111">The following example shows the complete query operation.</span></span> <span data-ttu-id="858a1-112">完整的作業包括建立資料來源、定義查詢運算式，並在 `foreach` 陳述式中執行查詢。</span><span class="sxs-lookup"><span data-stu-id="858a1-112">The complete operation includes creating a data source, defining the query expression, and executing the query in a `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a><span data-ttu-id="858a1-113">查詢運算式概觀</span><span class="sxs-lookup"><span data-stu-id="858a1-113">Query expression overview</span></span>

-   <span data-ttu-id="858a1-114">查詢運算式可以用來查詢並轉換來自任何已啟用 LINQ 之資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="858a1-114">Query expressions can be used to query and to transform data from any LINQ-enabled data source.</span></span> <span data-ttu-id="858a1-115">例如，單一查詢可以從 SQL 資料庫擷取資料，並產生 XML 資料流做為輸出。</span><span class="sxs-lookup"><span data-stu-id="858a1-115">For example, a single query can retrieve data from a SQL database, and produce an XML stream as output.</span></span>  
  
-   <span data-ttu-id="858a1-116">查詢運算式很容易學習，因為其中使用許多熟悉的 C# 語言建構。</span><span class="sxs-lookup"><span data-stu-id="858a1-116">Query expressions are easy to master because they use many familiar C# language constructs.</span></span>  
  
-   <span data-ttu-id="858a1-117">查詢運算式中的變數皆為強型別，不過您在很多情況下並不需要明確提供型別，因為編譯器能夠自行推斷它。</span><span class="sxs-lookup"><span data-stu-id="858a1-117">The variables in a query expression are all strongly typed, although in many cases you do not have to provide the type explicitly because the compiler can infer it.</span></span> <span data-ttu-id="858a1-118">如需詳細資訊，請參閱 [LINQ 查詢作業中的型別關聯性](type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-118">For more information, see [Type relationships in LINQ query operations](type-relationships-in-linq-query-operations.md).</span></span>  
  
-   <span data-ttu-id="858a1-119">在您針對查詢變數進行逐一查看之前 (例如，在 `foreach` 陳述式中)，查詢將不會執行。</span><span class="sxs-lookup"><span data-stu-id="858a1-119">A query is not executed until you iterate over the query variable, for example, in a `foreach` statement.</span></span> <span data-ttu-id="858a1-120">如需詳細資訊，請參閱 [LINQ 查詢簡介](introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-120">For more information, see [Introduction to LINQ queries](introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="858a1-121">在編譯期間，查詢運算式會根據 C# 規格中提出的規則，轉換成「標準查詢運算子」方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="858a1-121">At compile time, query expressions are converted to Standard Query Operator method calls according to the rules set forth in the C# specification.</span></span> <span data-ttu-id="858a1-122">所有可使用查詢語法表示的查詢，也都可以利用方法語法來表示。</span><span class="sxs-lookup"><span data-stu-id="858a1-122">Any query that can be expressed by using query syntax can also be expressed by using method syntax.</span></span> <span data-ttu-id="858a1-123">不過，在大多數情況下，查詢語法較容易閱讀且更簡潔。</span><span class="sxs-lookup"><span data-stu-id="858a1-123">However, in most cases query syntax is more readable and concise.</span></span> <span data-ttu-id="858a1-124">如需詳細資訊，請參閱 [C# 語言規格](../../../language-reference/language-specification/index.md)和[標準查詢運算子概觀](standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-124">For more information, see [C# language specification](../../../language-reference/language-specification/index.md) and [Standard query operators overview](standard-query-operators-overview.md).</span></span>  
  
-   <span data-ttu-id="858a1-125">做為撰寫 LINQ 查詢的規則，我們建議您優先使用查詢語法，且只有在必要時才使用方法語法。</span><span class="sxs-lookup"><span data-stu-id="858a1-125">As a rule when you write LINQ queries, we recommend that you use query syntax whenever possible and method syntax whenever necessary.</span></span> <span data-ttu-id="858a1-126">這兩個形式之間並沒有語意或效能上的差異。</span><span class="sxs-lookup"><span data-stu-id="858a1-126">There is no semantic or performance difference between the two different forms.</span></span> <span data-ttu-id="858a1-127">相較於以方法語法撰寫的對等運算式，查詢運算式通常更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="858a1-127">Query expressions are often more readable than equivalent expressions written in method syntax.</span></span>  
  
-   <span data-ttu-id="858a1-128">某些查詢作業 (例如 <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.Max%2A>) 沒有同等的查詢運算式子句，因此必須以方法呼叫來表示。</span><span class="sxs-lookup"><span data-stu-id="858a1-128">Some query operations, such as <xref:System.Linq.Enumerable.Count%2A> or <xref:System.Linq.Enumerable.Max%2A>, have no equivalent query expression clause and must therefore be expressed as a method call.</span></span> <span data-ttu-id="858a1-129">方法語法能以數種方式來與查詢語法結合。</span><span class="sxs-lookup"><span data-stu-id="858a1-129">Method syntax can be combined with query syntax in various ways.</span></span> <span data-ttu-id="858a1-130">如需詳細資訊，請參閱 [LINQ 中的查詢語法和方法語法](query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-130">For more information, see [Query syntax and method syntax in LINQ](query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
-   <span data-ttu-id="858a1-131">根據查詢所套用的型別，可將查詢運算式編譯為運算式樹狀結構或委派。</span><span class="sxs-lookup"><span data-stu-id="858a1-131">Query expressions can be compiled to expression trees or to delegates, depending on the type that the query is applied to.</span></span> <span data-ttu-id="858a1-132"><xref:System.Collections.Generic.IEnumerable%601> 查詢會編譯成委派。</span><span class="sxs-lookup"><span data-stu-id="858a1-132"><xref:System.Collections.Generic.IEnumerable%601> queries are compiled to delegates.</span></span> <span data-ttu-id="858a1-133"><xref:System.Linq.IQueryable> 和 <xref:System.Linq.IQueryable%601> 查詢會編譯成運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="858a1-133"><xref:System.Linq.IQueryable> and <xref:System.Linq.IQueryable%601> queries are compiled to expression trees.</span></span> <span data-ttu-id="858a1-134">如需詳細資訊，請參閱[運算式樹狀結構](../../../expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-134">For more information, see [Expression trees](../../../expression-trees.md).</span></span>  

## <a name="next-steps"></a><span data-ttu-id="858a1-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="858a1-135">Next steps</span></span>

<span data-ttu-id="858a1-136">若要深入了解 LINQ 的詳細資料，請先參閱[查詢運算式基本概念](../../../linq/query-expression-basics.md)以熟悉基本概念，然後閱讀您感興趣的 LINQ 技術文件：</span><span class="sxs-lookup"><span data-stu-id="858a1-136">To learn more details about LINQ, start by becoming familiar with some basic concepts in [Query expression basics](../../../linq/query-expression-basics.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>   
-   <span data-ttu-id="858a1-137">XML 文件：[LINQ to XML](linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="858a1-137">XML documents: [LINQ to XML](linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="858a1-138">ADO.NET Entity Framework：[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)</span><span class="sxs-lookup"><span data-stu-id="858a1-138">ADO.NET Entity Framework: [LINQ to entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)</span></span>  
  
-   <span data-ttu-id="858a1-139">.NET 集合、檔案、字串等等：[LINQ to Objects](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="858a1-139">.NET collections, files, strings and so on: [LINQ to objects](linq-to-objects.md)</span></span>

<span data-ttu-id="858a1-140">若要深入了解 LINQ 的一般資訊，請參閱 [C# 中的 LINQ](../../../linq/linq-in-csharp.md)。</span><span class="sxs-lookup"><span data-stu-id="858a1-140">To gain a deeper understanding of LINQ in general, see [LINQ in C#](../../../linq/linq-in-csharp.md).</span></span>

<span data-ttu-id="858a1-141">若要開始使用 C# 中的 LINQ，請參閱[使用 LINQ](../../../tutorials/working-with-linq.md) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="858a1-141">To start working with LINQ in C#, see the tutorial [Working with LINQ](../../../tutorials/working-with-linq.md).</span></span>



