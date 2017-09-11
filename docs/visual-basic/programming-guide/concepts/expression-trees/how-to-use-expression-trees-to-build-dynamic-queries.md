---
title: "如何︰ 使用運算式樹狀架構建置動態查詢 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="b5664-102">如何︰ 使用運算式樹狀架構建置動態查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5664-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="b5664-103">在 LINQ 中，運算式樹狀架構用來代表結構化的查詢該目標的資料來源實作<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="b5664-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="b5664-104">例如，LINQ 提供者會實作<xref:System.Linq.IQueryable%601>介面來查詢關聯式資料存放區。</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="b5664-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="b5664-105">Visual Basic 編譯器會編譯成建置運算式樹狀架構，在執行階段程式碼目標這類資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="b5664-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="b5664-106">查詢提供者可以周遊的運算式樹狀資料結構，並將它轉譯成適用於資料來源的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="b5664-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="b5664-107">運算式樹狀架構也用於 LINQ 中表示 lambda 運算式指派給變數的型別<xref:System.Linq.Expressions.Expression%601>。</xref:System.Linq.Expressions.Expression%601></span><span class="sxs-lookup"><span data-stu-id="b5664-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="b5664-108">本主題描述如何建立動態的 LINQ 查詢中使用運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="b5664-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="b5664-109">查詢的細節不知道在編譯時期，動態的查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="b5664-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="b5664-110">例如，應用程式可能會提供一個使用者介面，讓使用者指定一或多個述詞來篩選的資料。</span><span class="sxs-lookup"><span data-stu-id="b5664-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="b5664-111">若要使用 LINQ 查詢，這類應用程式必須使用運算式樹狀架構，在執行階段建立 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="b5664-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5664-112">範例</span><span class="sxs-lookup"><span data-stu-id="b5664-112">Example</span></span>  
 <span data-ttu-id="b5664-113">下列範例會示範如何使用運算式樹狀架構，來建構查詢`IQueryable`資料來源，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="b5664-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="b5664-114">代表下列查詢運算式樹狀架構建置程式碼︰</span><span class="sxs-lookup"><span data-stu-id="b5664-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="b5664-115">中的 factory 方法<xref:System.Linq.Expressions>命名空間用來建立運算式樹狀架構代表整體查詢所組成的運算式。</xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="b5664-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="b5664-116">代表標準查詢運算子方法呼叫運算式會參考<xref:System.Linq.Queryable>這些方法的實作。</xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="b5664-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="b5664-117">最後一個運算式樹狀結構傳遞給<xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>的提供者實作`IQueryable`來建立可執行的查詢類型的資料來源`IQueryable`。</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29></span><span class="sxs-lookup"><span data-stu-id="b5664-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="b5664-118">透過列舉查詢變數會取得結果。</span><span class="sxs-lookup"><span data-stu-id="b5664-118">The results are obtained by enumerating that query variable.</span></span>  
  
<span data-ttu-id="b5664-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b5664-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="b5664-120">此程式碼會使用固定的數目的運算式中述詞，可傳遞至`Queryable.Where`方法。</span><span class="sxs-lookup"><span data-stu-id="b5664-120">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="b5664-121">不過，您可以撰寫的應用程式，結合多個述詞運算式取決於使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="b5664-121">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="b5664-122">您也可以更改標準查詢運算子在查詢中，根據使用者輸入所呼叫。</span><span class="sxs-lookup"><span data-stu-id="b5664-122">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5664-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b5664-123">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b5664-124">建立新**主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="b5664-124">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="b5664-125">如果沒有參考，加入 system.core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="b5664-125">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="b5664-126">包括 System.Linq.Expressions 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b5664-126">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="b5664-127">複製程式碼範例中，並將它貼到`Main``Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="b5664-127">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5664-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5664-128">See Also</span></span>  
 <span data-ttu-id="b5664-129">[運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5664-129">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="b5664-130"> [如何︰ 執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="b5664-130"> [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span></span>
