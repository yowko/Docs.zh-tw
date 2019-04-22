---
title: HOW TO：使用運算式樹狀架構建置動態查詢 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827675"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="ca0f3-102">HOW TO：使用運算式樹狀架構建置動態查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca0f3-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="ca0f3-103">在 LINQ 中，您可以使用運算式樹狀架構，來代表以實作 <xref:System.Linq.IQueryable%601> 的資料來源為目標的結構化查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="ca0f3-104">例如，LINQ 提供者會實作 <xref:System.Linq.IQueryable%601> 介面，來查詢關聯式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="ca0f3-105">Visual Basic 編譯器會編譯成運算式樹狀架構在執行階段會建置的程式碼目標這類資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="ca0f3-106">查詢提供者可接著周遊運算式樹狀架構資料結構，並將它轉譯成適用於資料來源的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="ca0f3-107">您也可以在 LINQ 中使用運算式樹狀架構，來代表指派給 <xref:System.Linq.Expressions.Expression%601> 類型變數的 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="ca0f3-108">本主題描述如何使用運算式樹狀架構建立動態 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="ca0f3-109">如果在編譯時不知道查詢的詳細資料，動態查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="ca0f3-110">例如，應用程式可能會提供一個使用者介面，讓終端使用者指定一或多個述詞來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="ca0f3-111">若要使用 LINQ 進行查詢，這類應用程式必須使用運算式樹狀架構在執行階段建立 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca0f3-112">範例</span><span class="sxs-lookup"><span data-stu-id="ca0f3-112">Example</span></span>  
 <span data-ttu-id="ca0f3-113">下列範例示範如何使用運算式樹狀架構，對 `IQueryable` 資料來源建構並接著執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="ca0f3-114">程式碼會建立運算式樹狀架構來代表下列查詢：</span><span class="sxs-lookup"><span data-stu-id="ca0f3-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="ca0f3-115"><xref:System.Linq.Expressions> 命名空間中的 Factory 方法可用於建立運算式樹狀架構，來代表組成整體查詢的運算式。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="ca0f3-116">代表標準查詢運算子方法呼叫的運算式會參考這些方法的 <xref:System.Linq.Queryable> 實作。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="ca0f3-117">最後一個運算式樹狀結構會傳遞至 `IQueryable` 資料來源之提供者的 <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 實作，以建立類型為 `IQueryable` 的可執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="ca0f3-118">藉由列舉查詢變數可取得結果。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-118">The results are obtained by enumerating that query variable.</span></span>  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 <span data-ttu-id="ca0f3-119">此程式碼在傳遞至 `Queryable.Where` 方法的述詞中，使用固定數目的運算式。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="ca0f3-120">不過，您可以撰寫一個應用程式，以根據使用者輸入合併可變數目的述詞運算式。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="ca0f3-121">您也可以根據使用者輸入，更改查詢中所呼叫的標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca0f3-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ca0f3-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ca0f3-123">建立新的**主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="ca0f3-124">如果 System.Core.dll 的參考原本未參考，請新增這項參考。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="ca0f3-125">加入 System.Linq.Expressions 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="ca0f3-126">複製程式碼範例中，並將它貼至`Main``Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="ca0f3-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0f3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca0f3-127">See also</span></span>

- [<span data-ttu-id="ca0f3-128">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca0f3-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="ca0f3-129">如何：執行運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca0f3-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
