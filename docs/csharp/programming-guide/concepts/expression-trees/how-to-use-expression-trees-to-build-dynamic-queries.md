---
title: "如何：使用運算式樹狀架構建立動態查詢 (C#) | Microsoft Docs"
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
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
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
ms.openlocfilehash: 76dc6ebe2cc2489d83a2693a3143d36d46c8ef82
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="c0824-102">如何：使用運算式樹狀架構建立動態查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="c0824-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="c0824-103">在 LINQ 中，您可以使用運算式樹狀架構，來代表以實作 <xref:System.Linq.IQueryable%601> 的資料來源為目標的結構化查詢。</span><span class="sxs-lookup"><span data-stu-id="c0824-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c0824-104">例如，LINQ 提供者會實作 <xref:System.Linq.IQueryable%601> 介面，來查詢關聯式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="c0824-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="c0824-105">C# 編譯器會將以這類資料來源為目標的查詢編譯為程式碼，以在執行階段建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c0824-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="c0824-106">查詢提供者可接著周遊運算式樹狀架構資料結構，並將它轉譯成適用於資料來源的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="c0824-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="c0824-107">您也可以在 LINQ 中使用運算式樹狀架構，來代表指派給 <xref:System.Linq.Expressions.Expression%601> 類型變數的 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c0824-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="c0824-108">本主題描述如何使用運算式樹狀架構建立動態 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="c0824-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="c0824-109">如果在編譯時不知道查詢的詳細資料，動態查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="c0824-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="c0824-110">例如，應用程式可能會提供一個使用者介面，讓終端使用者指定一或多個述詞來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="c0824-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="c0824-111">若要使用 LINQ 進行查詢，這類應用程式必須使用運算式樹狀架構在執行階段建立 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="c0824-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0824-112">範例</span><span class="sxs-lookup"><span data-stu-id="c0824-112">Example</span></span>  
 <span data-ttu-id="c0824-113">下列範例示範如何使用運算式樹狀架構，對 `IQueryable` 資料來源建構並接著執行查詢。</span><span class="sxs-lookup"><span data-stu-id="c0824-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="c0824-114">程式碼會建立運算式樹狀架構來代表下列查詢：</span><span class="sxs-lookup"><span data-stu-id="c0824-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <span data-ttu-id="c0824-115"><xref:System.Linq.Expressions> 命名空間中的 Factory 方法可用於建立運算式樹狀架構，來代表組成整體查詢的運算式。</span><span class="sxs-lookup"><span data-stu-id="c0824-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="c0824-116">代表標準查詢運算子方法呼叫的運算式會參考這些方法的 <xref:System.Linq.Queryable> 實作。</span><span class="sxs-lookup"><span data-stu-id="c0824-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="c0824-117">最後一個運算式樹狀架構會傳遞至 `IQueryable` 資料來源的 <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 實作，以建立 `IQueryable` 類型的可執行檔查詢。</span><span class="sxs-lookup"><span data-stu-id="c0824-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="c0824-118">藉由列舉查詢變數可取得結果。</span><span class="sxs-lookup"><span data-stu-id="c0824-118">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="c0824-119">此程式碼在傳遞至 `Queryable.Where` 方法的述詞中，使用固定數目的運算式。</span><span class="sxs-lookup"><span data-stu-id="c0824-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="c0824-120">不過，您可以撰寫一個應用程式，以根據使用者輸入合併可變數目的述詞運算式。</span><span class="sxs-lookup"><span data-stu-id="c0824-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="c0824-121">您也可以根據使用者輸入，更改查詢中所呼叫的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="c0824-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0824-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c0824-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c0824-123">建立新的**主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="c0824-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="c0824-124">如果 System.Core.dll 的參考原本未參考，請新增這項參考。</span><span class="sxs-lookup"><span data-stu-id="c0824-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="c0824-125">加入 System.Linq.Expressions 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c0824-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="c0824-126">將範例中的程式碼複製並貼到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="c0824-126">Copy the code from the example and paste it into the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0824-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0824-127">See Also</span></span>  
 <span data-ttu-id="c0824-128">[運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0824-128">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="c0824-129"> [如何：執行運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="c0824-129"> [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
<span data-ttu-id="c0824-130"> [如何：在執行階段動態指定述詞篩選](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="c0824-130"> [How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)</span></span>
