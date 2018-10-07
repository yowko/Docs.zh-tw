---
title: 計算運算式 (F#)
description: '了解如何建立方便的語法，撰寫 F #，可以進行排序和合併使用控制流程建構和繫結中的計算。'
ms.date: 07/27/2018
ms.openlocfilehash: 148d1a661fb7630782c6dc48507a66e7bdc1d56b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839865"
---
# <a name="computation-expressions"></a><span data-ttu-id="57d73-103">計算運算式</span><span class="sxs-lookup"><span data-stu-id="57d73-103">Computation Expressions</span></span>

<span data-ttu-id="57d73-104">F # 中的計算運算式提供便利的語法來撰寫可以進行排序和合併使用控制流程建構和繫結的計算。</span><span class="sxs-lookup"><span data-stu-id="57d73-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="57d73-105">根據計算運算式的類型，它們可以視為 express monads、 monoids、 monad transformer 和 applicative 函式的方式。</span><span class="sxs-lookup"><span data-stu-id="57d73-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="57d73-106">不過，不同於其他語言 (例如*do 標記法*Haskell 中)，它們不會繫結至單一的抽象概念，並不依賴巨集或其他形式的 metaprogramming 完成方便且內容相關的語法。</span><span class="sxs-lookup"><span data-stu-id="57d73-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="57d73-107">總覽</span><span class="sxs-lookup"><span data-stu-id="57d73-107">Overview</span></span>

<span data-ttu-id="57d73-108">計算可以有許多形式。</span><span class="sxs-lookup"><span data-stu-id="57d73-108">Computations can take many forms.</span></span> <span data-ttu-id="57d73-109">計算的最常見形式是單一執行緒執行，也就是容易了解和修改。</span><span class="sxs-lookup"><span data-stu-id="57d73-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="57d73-110">不過，並非所有的形式是計算的單一執行緒執行一樣直接。</span><span class="sxs-lookup"><span data-stu-id="57d73-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="57d73-111">其中某些範例包括：</span><span class="sxs-lookup"><span data-stu-id="57d73-111">Some examples include:</span></span>

* <span data-ttu-id="57d73-112">不具決定性的計算</span><span class="sxs-lookup"><span data-stu-id="57d73-112">Non-deterministic computations</span></span>
* <span data-ttu-id="57d73-113">非同步計算</span><span class="sxs-lookup"><span data-stu-id="57d73-113">Asynchronous computations</span></span>
* <span data-ttu-id="57d73-114">Effectful 計算</span><span class="sxs-lookup"><span data-stu-id="57d73-114">Effectful computations</span></span>
* <span data-ttu-id="57d73-115">富有生產力的計算</span><span class="sxs-lookup"><span data-stu-id="57d73-115">Generative computations</span></span>

<span data-ttu-id="57d73-116">更一般來說，有*即時線上*您必須執行的應用程式特定部分中的計算。</span><span class="sxs-lookup"><span data-stu-id="57d73-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="57d73-117">撰寫即時程式碼可能相當困難，因為很容易之外指定的內容，而不需要的抽象概念，讓您無法這樣的 「 洩漏 」 計算。</span><span class="sxs-lookup"><span data-stu-id="57d73-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="57d73-118">這些抽象概通常很難撰寫您自己，這就是為什麼 F # 提供一個通用的方法，可執行所謂**計算運算式**。</span><span class="sxs-lookup"><span data-stu-id="57d73-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="57d73-119">計算運算式提供統一的語法和抽象概念模型的即時線上計算的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="57d73-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="57d73-120">每個計算運算式做為後盾*產生器*型別。</span><span class="sxs-lookup"><span data-stu-id="57d73-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="57d73-121">產生器型別會定義可供計算運算式的作業。</span><span class="sxs-lookup"><span data-stu-id="57d73-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="57d73-122">請參閱[建立新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中顯示如何建立自訂的計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="57d73-123">語法概觀</span><span class="sxs-lookup"><span data-stu-id="57d73-123">Syntax overview</span></span>

<span data-ttu-id="57d73-124">所有的計算運算式具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="57d73-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="57d73-125">何處`builder-expr`是定義計算運算式產生器型別名稱和`cexper`是計算運算式的運算式主體。</span><span class="sxs-lookup"><span data-stu-id="57d73-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="57d73-126">比方說，`async`計算運算式程式碼可以看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="57d73-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="57d73-127">有可用的特殊的其他語法在計算運算式中，在上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="57d73-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="57d73-128">下列運算式形式會使用計算運算式：</span><span class="sxs-lookup"><span data-stu-id="57d73-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="57d73-129">如果已定義在支援產生器類型，每個這些關鍵字，以及其他標準 F # 關鍵字所僅適用於計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="57d73-130">是唯一的例外`match!`，這是本身使用的語法捷徑`let!`後面模式比對的結果。</span><span class="sxs-lookup"><span data-stu-id="57d73-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="57d73-131">產生器型別是物件，定義方式結合，計算運算式的片段; 的特殊方法也就是它的方法來控制計算運算式的運作方式。</span><span class="sxs-lookup"><span data-stu-id="57d73-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="57d73-132">描述產生器類別的另一種方式是說，它可讓您自訂的許多 F # 建構，例如迴圈和繫結作業。</span><span class="sxs-lookup"><span data-stu-id="57d73-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="57d73-133">`let!`關鍵字的另一個計算運算式呼叫的結果繫結的名稱：</span><span class="sxs-lookup"><span data-stu-id="57d73-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="57d73-134">如果您繫結具有的計算運算式呼叫`let`，您不會計算運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="57d73-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="57d73-135">相反地，您會有繫結的值*實現*呼叫該計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="57d73-136">使用`let!`繫結至結果。</span><span class="sxs-lookup"><span data-stu-id="57d73-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="57d73-137">`let!` 由定義`Bind(x, f)`產生器型別上的成員。</span><span class="sxs-lookup"><span data-stu-id="57d73-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="57d73-138">`do!`關鍵字是呼叫計算運算式，傳回`unit`-例如型別 (由`Zero`成員產生器):</span><span class="sxs-lookup"><span data-stu-id="57d73-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="57d73-139">針對[非同步工作流程](asynchronous-workflows.md)，這個型別是`Async<unit>`。</span><span class="sxs-lookup"><span data-stu-id="57d73-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="57d73-140">如需其他計算運算式中，型別很可能是`CExpType<unit>`。</span><span class="sxs-lookup"><span data-stu-id="57d73-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="57d73-141">`do!` 由此`Bind(x, f)`成員產生器型別，其中`f`會產生`unit`。</span><span class="sxs-lookup"><span data-stu-id="57d73-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="57d73-142">`yield`關鍵字是從 計算運算式傳回值，以便它可以作為<xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="57d73-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="57d73-143">如同[產生 C# 關鍵字](../../csharp/language-reference/keywords/yield.md)，因為它會在逐一查看產生的計算運算式中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="57d73-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="57d73-144">`yield` 由此`Yield(x)`成員產生器型別，其中`x`是要重新產生的項目。</span><span class="sxs-lookup"><span data-stu-id="57d73-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="57d73-145">`yield!`關鍵字是簡維集合，從 計算運算式的值：</span><span class="sxs-lookup"><span data-stu-id="57d73-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="57d73-146">計算運算式評估時，由呼叫`yield!`將其項目產生後--逐一壓平合併結果。</span><span class="sxs-lookup"><span data-stu-id="57d73-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="57d73-147">`yield!` 由此`YieldFrom(x)`成員產生器型別，其中`x`是值的集合。</span><span class="sxs-lookup"><span data-stu-id="57d73-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="57d73-148">`return`關鍵字包裝型別對應至 計算運算式中的值。</span><span class="sxs-lookup"><span data-stu-id="57d73-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="57d73-149">除了使用的計算運算式`yield`，它用來 「 完成 」 的計算運算式：</span><span class="sxs-lookup"><span data-stu-id="57d73-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="57d73-150">`return` 由此`Return(x)`成員產生器型別，其中`x`是要包裝的項目。</span><span class="sxs-lookup"><span data-stu-id="57d73-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="57d73-151">`return!`關鍵字發現計算運算式的值，並將結果包裝型別對應至 計算運算式中：</span><span class="sxs-lookup"><span data-stu-id="57d73-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="57d73-152">`return!` 由此`ReturnFrom(x)`成員產生器型別，其中`x`是另一個計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="57d73-153">F # 從 4.5 開始，`match!`關鍵字可讓您將內嵌呼叫另一個計算運算式和模式比對其結果：</span><span class="sxs-lookup"><span data-stu-id="57d73-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="57d73-154">當呼叫的計算運算式`match!`，它將會了解像是呼叫的結果`let!`。</span><span class="sxs-lookup"><span data-stu-id="57d73-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="57d73-155">這通常用時呼叫的計算運算式結果的所在[選擇性](options.md)。</span><span class="sxs-lookup"><span data-stu-id="57d73-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="57d73-156">內建的計算運算式</span><span class="sxs-lookup"><span data-stu-id="57d73-156">Built-in computation expressions</span></span>

<span data-ttu-id="57d73-157">F # 核心程式庫會定義三個內建的計算運算式：[循序項運算式](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[查詢運算式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="57d73-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="57d73-158">建立新的計算運算式的類型</span><span class="sxs-lookup"><span data-stu-id="57d73-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="57d73-159">您可以建立產生器類別，並在類別上定義特定的特殊方法，以定義您自己的計算運算式的特性。</span><span class="sxs-lookup"><span data-stu-id="57d73-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="57d73-160">下表中所列，產生器類別可以選擇性地定義的方法。</span><span class="sxs-lookup"><span data-stu-id="57d73-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="57d73-161">下表描述可用於工作流程產生器類別的方法。</span><span class="sxs-lookup"><span data-stu-id="57d73-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="57d73-162">**方法**</span><span class="sxs-lookup"><span data-stu-id="57d73-162">**Method**</span></span>|<span data-ttu-id="57d73-163">**典型的簽章**</span><span class="sxs-lookup"><span data-stu-id="57d73-163">**Typical signature(s)**</span></span>|<span data-ttu-id="57d73-164">**描述**</span><span class="sxs-lookup"><span data-stu-id="57d73-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="57d73-165">針對呼叫`let!`和`do!`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="57d73-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="57d73-166">包裝函式為計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="57d73-167">針對呼叫`return`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="57d73-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="57d73-168">針對呼叫`return!`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="57d73-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="57d73-169">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="57d73-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="57d73-170">執行計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="57d73-171">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="57d73-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="57d73-172">呼叫在計算運算式中排序。</span><span class="sxs-lookup"><span data-stu-id="57d73-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="57d73-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="57d73-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="57d73-174">針對呼叫`for...do`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="57d73-175">針對呼叫`try...finally`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="57d73-176">針對呼叫`try...with`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="57d73-177">針對呼叫`use`計算運算式中的繫結。</span><span class="sxs-lookup"><span data-stu-id="57d73-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="57d73-178">針對呼叫`while...do`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="57d73-179">針對呼叫`yield`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="57d73-180">針對呼叫`yield!`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="57d73-181">呼叫空`else`分支`if...then`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|

<span data-ttu-id="57d73-182">許多產生器類別中的方法使用，並傳回`M<'T>`建構，這通常是分開定義的類型特性的組合，計算種類，例如，`Async<'T>`非同步工作流程和`Seq<'T>`序列工作流程。</span><span class="sxs-lookup"><span data-stu-id="57d73-182">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="57d73-183">這些方法的簽章會啟用這些要結合並彼此巢狀，以便從一個建構傳回的工作流程物件可以傳遞至下一步。</span><span class="sxs-lookup"><span data-stu-id="57d73-183">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="57d73-184">剖析計算運算式時，編譯器會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一系列的巢狀函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="57d73-184">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="57d73-185">巢狀的運算式是下列格式：</span><span class="sxs-lookup"><span data-stu-id="57d73-185">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="57d73-186">在上述程式碼來呼叫`Run`和`Delay`會省略所計算的運算式產生器類別中有未定義。</span><span class="sxs-lookup"><span data-stu-id="57d73-186">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="57d73-187">計算運算式，這裡表示為主體`{| cexpr |}`，轉譯成牽涉到的產生器類別方法的呼叫下表中所述的翻譯。</span><span class="sxs-lookup"><span data-stu-id="57d73-187">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="57d73-188">計算運算式`{| cexpr |}`會定義以遞迴方式，根據這些翻譯所在`expr`是 F # 運算式和`cexpr`是計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-188">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="57d73-189">運算式</span><span class="sxs-lookup"><span data-stu-id="57d73-189">Expression</span></span>|<span data-ttu-id="57d73-190">轉譯</span><span class="sxs-lookup"><span data-stu-id="57d73-190">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="57d73-191">在上表中，`other-expr`告訴您，否則為未列在資料表的運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-191">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="57d73-192">產生器類別不必實作的所有方法，並支援所有在上表中列出的翻譯。</span><span class="sxs-lookup"><span data-stu-id="57d73-192">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="57d73-193">無法使用該類型的計算運算式中不會實作這些建構。</span><span class="sxs-lookup"><span data-stu-id="57d73-193">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="57d73-194">例如，如果您不想要支援`use`計算運算式中的關鍵字，您可以省略的定義`Use`產生器類別中。</span><span class="sxs-lookup"><span data-stu-id="57d73-194">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="57d73-195">下列程式碼範例會顯示封裝計算為一系列的步驟可評估一次的一個步驟的計算運算式。</span><span class="sxs-lookup"><span data-stu-id="57d73-195">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="57d73-196">差別等位型別， `OkOrException`，編碼錯誤狀態的運算式，評估為止。</span><span class="sxs-lookup"><span data-stu-id="57d73-196">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="57d73-197">此程式碼示範您可以使用您的計算運算式，例如產生器方法的一部分的未定案實作中的數種一般模式。</span><span class="sxs-lookup"><span data-stu-id="57d73-197">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="57d73-198">計算運算式具有基礎類型，則運算式會傳回。</span><span class="sxs-lookup"><span data-stu-id="57d73-198">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="57d73-199">計算的結果或可執行的延遲的計算，可能代表基礎類型，或者它可能提供逐一查看集合的某種類型的方法。</span><span class="sxs-lookup"><span data-stu-id="57d73-199">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="57d73-200">在上述範例中，基礎類型是**最終**。</span><span class="sxs-lookup"><span data-stu-id="57d73-200">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="57d73-201">序列運算式中，基礎類型是<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="57d73-201">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="57d73-202">查詢運算式的基礎類型是<xref:System.Linq.IQueryable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="57d73-202">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="57d73-203">非同步工作流程的基礎類型是[ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。</span><span class="sxs-lookup"><span data-stu-id="57d73-203">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="57d73-204">`Async`物件代表要計算的結果執行的工作。</span><span class="sxs-lookup"><span data-stu-id="57d73-204">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="57d73-205">例如，您呼叫[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="57d73-205">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="57d73-206">自訂作業</span><span class="sxs-lookup"><span data-stu-id="57d73-206">Custom Operations</span></span>

<span data-ttu-id="57d73-207">您可以定義自訂的作業，在 計算運算式，並為計算運算式中運算子使用的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="57d73-207">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="57d73-208">比方說，您可以在查詢運算式中包含的查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="57d73-208">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="57d73-209">當您定義的自訂作業時，您必須定義在 Yield 和計算運算式中的方法。</span><span class="sxs-lookup"><span data-stu-id="57d73-209">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="57d73-210">若要定義自訂的作業，將它放在 計算運算式產生器類別，然後套用[ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)。</span><span class="sxs-lookup"><span data-stu-id="57d73-210">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="57d73-211">這個屬性會接受字串做為引數，也就是使用中的自訂作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="57d73-211">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="57d73-212">此名稱來自進入範圍內的計算運算式的左大括號開頭。</span><span class="sxs-lookup"><span data-stu-id="57d73-212">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="57d73-213">因此，您不應該使用在這個區塊中有相同名稱的自訂作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57d73-213">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="57d73-214">例如，避免識別項使用這類`all`或`last`查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="57d73-214">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="57d73-215">擴充現有的產生器與新的自訂作業</span><span class="sxs-lookup"><span data-stu-id="57d73-215">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="57d73-216">如果您已經產生器類別，可以從擴充其自訂作業，此產生器的類別之外。</span><span class="sxs-lookup"><span data-stu-id="57d73-216">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="57d73-217">延伸模組必須在模組中宣告。</span><span class="sxs-lookup"><span data-stu-id="57d73-217">Extensions must be declared in modules.</span></span> <span data-ttu-id="57d73-218">命名空間不能包含相同的檔案和相同的命名空間宣告群組定義類型的位置中的擴充成員除外。</span><span class="sxs-lookup"><span data-stu-id="57d73-218">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="57d73-219">下列範例示範的現有擴充`Microsoft.FSharp.Linq.QueryBuilder`類別。</span><span class="sxs-lookup"><span data-stu-id="57d73-219">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="57d73-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57d73-220">See also</span></span>

- [<span data-ttu-id="57d73-221">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="57d73-221">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="57d73-222">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="57d73-222">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="57d73-223">序列</span><span class="sxs-lookup"><span data-stu-id="57d73-223">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="57d73-224">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="57d73-224">Query Expressions</span></span>](query-expressions.md)
