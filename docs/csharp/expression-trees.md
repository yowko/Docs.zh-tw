---
title: Expression Trees
description: 了解 .NET Core 中的運算式樹狀架構，以及如何使用它們來表示您可以檢查、修改和執行的程式碼結構。
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees"></a><span data-ttu-id="7cef8-103">Expression Trees</span><span class="sxs-lookup"><span data-stu-id="7cef8-103">Expression Trees</span></span>

<span data-ttu-id="7cef8-104">如果您使用過 LINQ，您會有豐富的程式庫使用經驗，其中 `Func` 類型是 API 集合的一部分</span><span class="sxs-lookup"><span data-stu-id="7cef8-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="7cef8-105">(如果您不熟悉 LINQ，則可能需要閱讀 [LINQ 教學課程](linq/index.md)及有關 [Lambda 運算式](lambda-expressions.md)的教學課程，再開始進行本主題)。「運算式樹狀架構」提供與函式引數更豐富的互動。</span><span class="sxs-lookup"><span data-stu-id="7cef8-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="7cef8-106">當您建立 LINQ 查詢時，通常會使用 Lambda 運算式來撰寫函式引數。</span><span class="sxs-lookup"><span data-stu-id="7cef8-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="7cef8-107">在一般 LINQ 查詢中，這些函式引數會轉換成編譯器所建立的委派。</span><span class="sxs-lookup"><span data-stu-id="7cef8-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="7cef8-108">當您想要有更豐富的互動時，您必須使用「運算式樹狀架構」。</span><span class="sxs-lookup"><span data-stu-id="7cef8-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="7cef8-109">運算式樹狀架構會以您可以查看、修改或執行的結構來表示程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cef8-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="7cef8-110">這些工具可讓您在執行階段操作程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cef8-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="7cef8-111">您可以撰寫程式碼來查看執行中的演算法，或插入新功能。</span><span class="sxs-lookup"><span data-stu-id="7cef8-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="7cef8-112">在更進階的案例中，您可以修改執行中的演算法，甚至將 C# 運算式轉譯為其他格式，以便在其他環境中執行。</span><span class="sxs-lookup"><span data-stu-id="7cef8-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="7cef8-113">您可能已撰寫使用運算式樹狀架構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cef8-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="7cef8-114">Entity Framework 的 LINQ API 接受運算式樹狀架構作為 LINQ 查詢運算式模式的引數。</span><span class="sxs-lookup"><span data-stu-id="7cef8-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="7cef8-115">這可讓 [Entity Framework](http://docs.efproject.net/en/latest/) 將以 C# 撰寫的查詢，轉譯為在資料庫引擎中執行的 SQL。</span><span class="sxs-lookup"><span data-stu-id="7cef8-115">That enables [Entity Framework](http://docs.efproject.net/en/latest/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="7cef8-116">另一個範例是 [Moq](https://github.com/Moq/moq)，這是 .NET 的熱門模擬架構。</span><span class="sxs-lookup"><span data-stu-id="7cef8-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="7cef8-117">本教學課程的其餘章節會探索運算式樹狀架構為何、查看支援運算式樹狀架構的架構類別，並示範如何使用運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="7cef8-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="7cef8-118">您將了解如何讀取運算式樹狀架構、如何建立運算式樹狀架構、如何建立修改後的運算式樹狀架構，以及如何執行由運算式樹狀架構表示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cef8-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="7cef8-119">閱讀完後，您將能夠使用這些結構來建立豐富彈性的演算法。</span><span class="sxs-lookup"><span data-stu-id="7cef8-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="7cef8-120">說明運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="7cef8-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="7cef8-121">了解「運算式樹狀架構」背後的結構和概念。</span><span class="sxs-lookup"><span data-stu-id="7cef8-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="7cef8-122">支援運算式樹狀架構的架構類型</span><span class="sxs-lookup"><span data-stu-id="7cef8-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="7cef8-123">了解定義及操作運算式樹狀架構的結構和類別。</span><span class="sxs-lookup"><span data-stu-id="7cef8-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="7cef8-124">執行運算式</span><span class="sxs-lookup"><span data-stu-id="7cef8-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="7cef8-125">了解如何將以 Lambda 運算式表示的運算式樹狀架構轉換成委派，再執行所產生的委派。</span><span class="sxs-lookup"><span data-stu-id="7cef8-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="7cef8-126">解譯運算式</span><span class="sxs-lookup"><span data-stu-id="7cef8-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="7cef8-127">了解如何周遊及查看「運算式樹狀架構」，以了解運算式樹狀架構所表示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cef8-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="7cef8-128">建置運算式</span><span class="sxs-lookup"><span data-stu-id="7cef8-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="7cef8-129">了解如何建構運算式樹狀架構的節點，並建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="7cef8-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="7cef8-130">轉譯運算式</span><span class="sxs-lookup"><span data-stu-id="7cef8-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="7cef8-131">了解如何建立修改後的運算式樹狀架構複本，或將運算式樹狀架構轉譯為其他格式。</span><span class="sxs-lookup"><span data-stu-id="7cef8-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="7cef8-132">總結</span><span class="sxs-lookup"><span data-stu-id="7cef8-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="7cef8-133">檢閱運算式樹狀架構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7cef8-133">Review the information on expression trees.</span></span>
    
