---
title: 組建運算式樹狀架構
description: 了解建置運算式樹狀架構的技術。
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7e45f566f66c129111c65a1166a6c71ff518dfc7
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="building-expression-trees"></a><span data-ttu-id="0f995-104">組建運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="0f995-104">Building Expression Trees</span></span>

[<span data-ttu-id="0f995-105">上一篇 - 解譯運算式</span><span class="sxs-lookup"><span data-stu-id="0f995-105">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="0f995-106">目前為止看到的所有運算式樹狀架構都是由 C# 編譯器建立。</span><span class="sxs-lookup"><span data-stu-id="0f995-106">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="0f995-107">您唯一要做的是建立 Lambda 運算式，指派給類型為 `Expression<Func<T>>` 的變數或類似類型。</span><span class="sxs-lookup"><span data-stu-id="0f995-107">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="0f995-108">這不是建立運算式樹狀結構的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="0f995-108">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="0f995-109">在許多情況下，您會發現需要在執行階段的記憶體中建立一個運算式。</span><span class="sxs-lookup"><span data-stu-id="0f995-109">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="0f995-110">組建運算式樹狀架構很複雜，因為這些運算式樹狀架構是不可變的。</span><span class="sxs-lookup"><span data-stu-id="0f995-110">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="0f995-111">所謂不可變，表示樹狀結構必須從分葉向上組建到根。</span><span class="sxs-lookup"><span data-stu-id="0f995-111">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="0f995-112">您要用來組建運算式樹狀架構的 API 反映這項事實︰組建節點要使用的方法會採用其所有子系作為引數。</span><span class="sxs-lookup"><span data-stu-id="0f995-112">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="0f995-113">讓我們逐步解說幾個範例，向您示範技巧。</span><span class="sxs-lookup"><span data-stu-id="0f995-113">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="0f995-114">建立節點</span><span class="sxs-lookup"><span data-stu-id="0f995-114">Creating Nodes</span></span>

<span data-ttu-id="0f995-115">讓我們再次從相對簡單的開始。</span><span class="sxs-lookup"><span data-stu-id="0f995-115">Let's start relatively simply again.</span></span> <span data-ttu-id="0f995-116">在下列各節中，我們會使用前面用過的加法運算式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-116">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="0f995-117">若要建構該運算式樹狀架構，您必須建構分葉節點。</span><span class="sxs-lookup"><span data-stu-id="0f995-117">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="0f995-118">分葉節點為常數，因此您可以使用 `Expression.Constant` 方法建立節點︰</span><span class="sxs-lookup"><span data-stu-id="0f995-118">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="0f995-119">接下來，您要組建加法運算式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-119">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="0f995-120">建立加法運算式之後，您可以建立 Lambda 運算式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-120">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="0f995-121">這是非常簡單的 LambdaExpression，因為它不包含任何引數。</span><span class="sxs-lookup"><span data-stu-id="0f995-121">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="0f995-122">稍後在本節中，您會看到引數如何對應至參數，並組建更複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="0f995-122">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="0f995-123">針對和這個同樣簡單的運算式，您可以將所有呼叫結合成單一陳述式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-123">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="0f995-124">組建樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0f995-124">Building a Tree</span></span>

<span data-ttu-id="0f995-125">這就是在記憶體中組建運算式樹狀結構的基本概念。</span><span class="sxs-lookup"><span data-stu-id="0f995-125">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="0f995-126">更複雜的樹狀結構通常表示在樹狀目錄中有更多的節點類型和更多的節點。</span><span class="sxs-lookup"><span data-stu-id="0f995-126">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="0f995-127">讓我們再執行一個範例，並多顯示兩個當您建立運算式樹狀架構時，通常會組建的節點類型︰引數節點和方法呼叫節點。</span><span class="sxs-lookup"><span data-stu-id="0f995-127">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="0f995-128">我們要組建運算式樹狀架構來建立此運算式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-128">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="0f995-129">您要從建立 `x` 和 `y` 的參數運算式開始：</span><span class="sxs-lookup"><span data-stu-id="0f995-129">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="0f995-130">建立乘法和加法運算式要遵循您已見過的模式︰</span><span class="sxs-lookup"><span data-stu-id="0f995-130">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="0f995-131">接下來，您需要為 `Math.Sqrt` 呼叫建立方法呼叫運算式。</span><span class="sxs-lookup"><span data-stu-id="0f995-131">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="0f995-132">最後，將方法呼叫放入 Lambda 運算式中，確定定義 Lambda 運算式的引數︰</span><span class="sxs-lookup"><span data-stu-id="0f995-132">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="0f995-133">在這個更複雜的範例中，您會多看到幾個建立運算式樹狀架構經常需要的技巧。</span><span class="sxs-lookup"><span data-stu-id="0f995-133">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="0f995-134">首先，您需要先建立代表參數或區域變數的物件，再使用它們。</span><span class="sxs-lookup"><span data-stu-id="0f995-134">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="0f995-135">建立這些物件之後，就可以在您的運算式樹狀架構中隨時使用它們。</span><span class="sxs-lookup"><span data-stu-id="0f995-135">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="0f995-136">其次，您需要使用反映 API 的子集來建立 `MethodInfo` 物件，以便可以建立運算式樹狀架構來存取該方法。</span><span class="sxs-lookup"><span data-stu-id="0f995-136">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="0f995-137">您必須將自己限制在 .NET Core 平台上可用的反映 API 子集。</span><span class="sxs-lookup"><span data-stu-id="0f995-137">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="0f995-138">同樣地，這些技巧會延伸到其他的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="0f995-138">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="0f995-139">深度組建程式碼</span><span class="sxs-lookup"><span data-stu-id="0f995-139">Building Code In Depth</span></span>

<span data-ttu-id="0f995-140">您不會受限於使用這些 API 所可以組建的項目。</span><span class="sxs-lookup"><span data-stu-id="0f995-140">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="0f995-141">不過，想要組建的運算式樹狀架構越複雜，程式碼就越難管理及閱讀。</span><span class="sxs-lookup"><span data-stu-id="0f995-141">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="0f995-142">我們要組建相當於這個程式碼的運算式樹狀架構︰</span><span class="sxs-lookup"><span data-stu-id="0f995-142">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="0f995-143">請注意，上例中，我並未組建運算式樹狀架構，只有委派。</span><span class="sxs-lookup"><span data-stu-id="0f995-143">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="0f995-144">使用 `Expression` 類別就無法建立陳述式 Lambda。</span><span class="sxs-lookup"><span data-stu-id="0f995-144">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="0f995-145">以下是組建相同功能需要的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f995-145">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="0f995-146">它之所以複雜是因為沒有 API 可組建 `while` 迴圈，您需要改組建包含條件式測試的迴圈，以及脫離迴圈的標籤目標。</span><span class="sxs-lookup"><span data-stu-id="0f995-146">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="0f995-147">組建階乘函式運算式樹狀結構的程式碼相當長，也更複雜，滿是標籤和 break 陳述式及其他項目，是日常編碼工作想要避免的坑。</span><span class="sxs-lookup"><span data-stu-id="0f995-147">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="0f995-148">我在本節中也更新了訪客程式碼，可瀏覽此運算式樹狀結構中的每個節點，並寫出此範例所建立之節點的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0f995-148">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="0f995-149">您可以在 dotnet/docs GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/csharp/expression-trees)。</span><span class="sxs-lookup"><span data-stu-id="0f995-149">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="0f995-150">建置並執行範例來親自試驗。</span><span class="sxs-lookup"><span data-stu-id="0f995-150">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="0f995-151">如需下載指示，請參閱[範例和教學課程](../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="0f995-151">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="0f995-152">檢查 API</span><span class="sxs-lookup"><span data-stu-id="0f995-152">Examining the APIs</span></span>

<span data-ttu-id="0f995-153">運算式樹狀架構 API 是較難在 .NET Core 中巡覽的項目，但是沒關係。</span><span class="sxs-lookup"><span data-stu-id="0f995-153">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="0f995-154">其目的是相當複雜的任務︰撰寫會在執行階段產生程式碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f995-154">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="0f995-155">它們必須得複雜才能在支援 C# 語言提供的所有控制結構，以及在合理範圍內保持最小的 API 介面區之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="0f995-155">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="0f995-156">這項平衡表示許多控制結構不是由其 C# 建構所呈現，而是由代表基礎邏輯的建構所呈現，此基礎邏輯是編譯器從這些較高層級的建構所產生。</span><span class="sxs-lookup"><span data-stu-id="0f995-156">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="0f995-157">此外，在此階段中，還有不能直接使用內建 `Expression` 類別方法來組建的 C# 運算式。</span><span class="sxs-lookup"><span data-stu-id="0f995-157">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="0f995-158">這些通常是新增至 C# 5 和 C# 6 的最新運算子和運算式。</span><span class="sxs-lookup"><span data-stu-id="0f995-158">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="0f995-159">(例如，無法組建 `async` 運算式，也不能直接建立新的 `?.` 運算子。)</span><span class="sxs-lookup"><span data-stu-id="0f995-159">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="0f995-160">下一篇 - 轉譯運算式</span><span class="sxs-lookup"><span data-stu-id="0f995-160">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
