---
title: 計算運算式
description: 瞭解如何在中F#建立可使用控制流程結構和系結進行排序和合併的方便撰寫運算語法。
ms.date: 03/15/2019
ms.openlocfilehash: 9222be5a585914761d3001d6649b196030eec05e
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083048"
---
# <a name="computation-expressions"></a><span data-ttu-id="83066-103">計算運算式</span><span class="sxs-lookup"><span data-stu-id="83066-103">Computation Expressions</span></span>

<span data-ttu-id="83066-104">中F#的計算運算式提供便利的語法，可讓您撰寫使用控制流程結構和系結進行排序和結合的計算。</span><span class="sxs-lookup"><span data-stu-id="83066-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="83066-105">視計算運算式的種類而定，您可以將其視為表示 monad、monoids、monad 轉換器和 applicative 函子的方式。</span><span class="sxs-lookup"><span data-stu-id="83066-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="83066-106">不過，不同于其他語言（例如 Haskell 中的*標記法*），它們不會系結至單一抽象概念，而且不依賴宏或其他形式的元處理來完成方便且內容相關的語法。</span><span class="sxs-lookup"><span data-stu-id="83066-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="83066-107">總覽</span><span class="sxs-lookup"><span data-stu-id="83066-107">Overview</span></span>

<span data-ttu-id="83066-108">計算可能會採用許多形式。</span><span class="sxs-lookup"><span data-stu-id="83066-108">Computations can take many forms.</span></span> <span data-ttu-id="83066-109">最常見的計算形式是單一執行緒執行，這很容易瞭解和修改。</span><span class="sxs-lookup"><span data-stu-id="83066-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="83066-110">不過，並非所有形式的計算都是單一執行緒執行的簡單方式。</span><span class="sxs-lookup"><span data-stu-id="83066-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="83066-111">其中某些範例包括：</span><span class="sxs-lookup"><span data-stu-id="83066-111">Some examples include:</span></span>

- <span data-ttu-id="83066-112">不具決定性的計算</span><span class="sxs-lookup"><span data-stu-id="83066-112">Non-deterministic computations</span></span>
- <span data-ttu-id="83066-113">非同步計算</span><span class="sxs-lookup"><span data-stu-id="83066-113">Asynchronous computations</span></span>
- <span data-ttu-id="83066-114">Effectful 計算</span><span class="sxs-lookup"><span data-stu-id="83066-114">Effectful computations</span></span>
- <span data-ttu-id="83066-115">有生產力計算</span><span class="sxs-lookup"><span data-stu-id="83066-115">Generative computations</span></span>

<span data-ttu-id="83066-116">一般來說，您必須在應用程式的某些部分中執行*內容相關*的計算。</span><span class="sxs-lookup"><span data-stu-id="83066-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="83066-117">撰寫與內容相關的程式碼可能很有挑戰性，因為在沒有抽象概念的情況下，您可以輕鬆地在指定的內容外部「流失」計算，以避免發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="83066-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="83066-118">這些抽象概念通常是很難撰寫的，這也是F#為什麼有一般化的方法，稱為**計算運算式**。</span><span class="sxs-lookup"><span data-stu-id="83066-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="83066-119">計算運算式提供統一的語法和抽象概念，以編碼內容相關的計算。</span><span class="sxs-lookup"><span data-stu-id="83066-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="83066-120">每個計算運算式*都是由產生器型別*支援。</span><span class="sxs-lookup"><span data-stu-id="83066-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="83066-121">產生器型別會定義可用於計算運算式的作業。</span><span class="sxs-lookup"><span data-stu-id="83066-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="83066-122">請參閱[建立新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中會顯示如何建立自訂計算運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="83066-123">語法總覽</span><span class="sxs-lookup"><span data-stu-id="83066-123">Syntax overview</span></span>

<span data-ttu-id="83066-124">所有計算運算式的形式如下：</span><span class="sxs-lookup"><span data-stu-id="83066-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="83066-125">其中`builder-expr` ，是定義計算運算式的產生器型別名稱，而`cexper`是計算運算式的運算式主體。</span><span class="sxs-lookup"><span data-stu-id="83066-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="83066-126">例如， `async`計算運算式程式碼看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="83066-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="83066-127">計算運算式中有特殊的額外語法可用，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="83066-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="83066-128">下列運算式形式可以搭配計算運算式使用：</span><span class="sxs-lookup"><span data-stu-id="83066-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="83066-129">這些關鍵字和其他標準F#關鍵字僅適用于計算運算式（如果已在支援產生器型別中定義）。</span><span class="sxs-lookup"><span data-stu-id="83066-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="83066-130">唯一的例外是`match!`，這本身就是語法，可供`let!`使用，後面接著結果的模式比對。</span><span class="sxs-lookup"><span data-stu-id="83066-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="83066-131">產生器型別是一個物件，它會定義特殊方法來管理計算運算式片段的結合方式;也就是說，它的方法會控制計算運算式的行為。</span><span class="sxs-lookup"><span data-stu-id="83066-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="83066-132">描述 builder 類別的另一種方式，就是讓您自訂許多F#結構的作業，例如迴圈和系結。</span><span class="sxs-lookup"><span data-stu-id="83066-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="83066-133">`let!`關鍵字會將另一個計算運算式的呼叫結果系結至名稱：</span><span class="sxs-lookup"><span data-stu-id="83066-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="83066-134">如果您使用`let`來系結計算運算式的呼叫，則不會取得計算運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="83066-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="83066-135">相反地，您會將無法使用的呼叫值系結*至該計算*運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="83066-136">使用`let!`系結至結果。</span><span class="sxs-lookup"><span data-stu-id="83066-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="83066-137">`let!`由產生器型`Bind(x, f)`別上的成員定義。</span><span class="sxs-lookup"><span data-stu-id="83066-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="83066-138">關鍵字是用來呼叫會傳回類似類型的計算`unit`運算式（由產生器上的`Zero`成員定義）： `do!`</span><span class="sxs-lookup"><span data-stu-id="83066-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="83066-139">針對[非同步工作流程](asynchronous-workflows.md)，此類型為`Async<unit>`。</span><span class="sxs-lookup"><span data-stu-id="83066-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="83066-140">對於其他計算運算式，類型可能`CExpType<unit>`是。</span><span class="sxs-lookup"><span data-stu-id="83066-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="83066-141">`do!`是由產生器`Bind(x, f)`型別上的成員所定義`f` ，其中`unit`會產生。</span><span class="sxs-lookup"><span data-stu-id="83066-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="83066-142">關鍵字是用來從計算運算式傳回值，讓它可以當做來使用<xref:System.Collections.Generic.IEnumerable%601>： `yield`</span><span class="sxs-lookup"><span data-stu-id="83066-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="83066-143">如同[ C#中的 yield 關鍵字](../../csharp/language-reference/keywords/yield.md)，計算運算式中的每個專案都會在反覆運算時傳回。</span><span class="sxs-lookup"><span data-stu-id="83066-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="83066-144">`yield`是由`Yield(x)`產生器型別上的成員所定義`x` ，其中是要傳回的專案。</span><span class="sxs-lookup"><span data-stu-id="83066-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="83066-145">`yield!`關鍵字是用來從計算運算式簡維值的集合：</span><span class="sxs-lookup"><span data-stu-id="83066-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="83066-146">評估時，所呼叫`yield!`的計算運算式會將其專案逐一傳回，並將結果簡維。</span><span class="sxs-lookup"><span data-stu-id="83066-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="83066-147">`yield!`是由產生器`YieldFrom(x)`型別上的成員所定義`x` ，其中是值的集合。</span><span class="sxs-lookup"><span data-stu-id="83066-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="83066-148">`return`關鍵字會包裝對應于計算運算式之類型中的值。</span><span class="sxs-lookup"><span data-stu-id="83066-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="83066-149">除了使用`yield`的計算運算式之外，它還可用來「完成」計算運算式：</span><span class="sxs-lookup"><span data-stu-id="83066-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="83066-150">`return`是由`Return(x)`產生器型別上的成員所定義`x` ，其中是要包裝的專案。</span><span class="sxs-lookup"><span data-stu-id="83066-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="83066-151">`return!`關鍵字會發現計算運算式的值，並將結果包裝為對應于計算運算式的類型：</span><span class="sxs-lookup"><span data-stu-id="83066-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="83066-152">`return!`是由產生器`ReturnFrom(x)`型別上的成員所定義`x` ，其中是另一個計算運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="83066-153">從F# 4.5 開始， `match!`關鍵字可讓您內嵌對另一個計算運算式的呼叫，並對其結果進行模式比對：</span><span class="sxs-lookup"><span data-stu-id="83066-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="83066-154">使用`match!`呼叫計算運算式時，它會實現呼叫的結果，例如`let!`。</span><span class="sxs-lookup"><span data-stu-id="83066-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="83066-155">這通常是在呼叫計算運算式（其中的結果為[選擇性](options.md)）時使用。</span><span class="sxs-lookup"><span data-stu-id="83066-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="83066-156">內建計算運算式</span><span class="sxs-lookup"><span data-stu-id="83066-156">Built-in computation expressions</span></span>

<span data-ttu-id="83066-157">F#核心程式庫會定義三個內建計算運算式：[順序運算式](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[查詢運算式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="83066-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="83066-158">建立新類型的計算運算式</span><span class="sxs-lookup"><span data-stu-id="83066-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="83066-159">您可以藉由建立產生器類別並在類別上定義某些特殊方法，來定義自己的計算運算式的特性。</span><span class="sxs-lookup"><span data-stu-id="83066-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="83066-160">Builder 類別可以選擇性地定義下表所列的方法。</span><span class="sxs-lookup"><span data-stu-id="83066-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="83066-161">下表描述可在工作流程產生器類別中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="83066-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="83066-162">**方法**</span><span class="sxs-lookup"><span data-stu-id="83066-162">**Method**</span></span>|<span data-ttu-id="83066-163">**一般簽章**</span><span class="sxs-lookup"><span data-stu-id="83066-163">**Typical signature(s)**</span></span>|<span data-ttu-id="83066-164">**描述**</span><span class="sxs-lookup"><span data-stu-id="83066-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="83066-165">在計算`let!`運算式`do!`中針對和呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="83066-166">將計算運算式包裝為函數。</span><span class="sxs-lookup"><span data-stu-id="83066-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="83066-167">在計算`return`運算式中針對進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="83066-168">在計算`return!`運算式中針對進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="83066-169">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="83066-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="83066-170">執行計算運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="83066-171">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="83066-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="83066-172">呼叫以在計算運算式中進行排序。</span><span class="sxs-lookup"><span data-stu-id="83066-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="83066-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="83066-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="83066-174">針對計算`for...do`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="83066-175">針對計算`try...finally`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="83066-176">針對計算`try...with`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="83066-177">在計算`use`運算式中呼叫以進行系結。</span><span class="sxs-lookup"><span data-stu-id="83066-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="83066-178">針對計算`while...do`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="83066-179">針對計算`yield`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="83066-180">針對計算`yield!`運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="83066-181">在計算運算式`else`中針對`if...then`運算式的空分支呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="83066-182">指出計算運算式會以引號的形式傳遞`Run`給成員。</span><span class="sxs-lookup"><span data-stu-id="83066-182">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="83066-183">它會將計算的所有實例轉譯為引號。</span><span class="sxs-lookup"><span data-stu-id="83066-183">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="83066-184">產生器類別中的許多方法都會使用並`M<'T>`傳回結構，這通常是個別定義的型別，以表示要合併的運算種類，例如， `Async<'T>`針對非同步工作流程和`Seq<'T>`適用于序列工作流程。</span><span class="sxs-lookup"><span data-stu-id="83066-184">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="83066-185">這些方法的簽章可讓它們彼此結合並加以合併，讓從一個結構傳回的工作流程物件可以傳遞至下一個。</span><span class="sxs-lookup"><span data-stu-id="83066-185">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="83066-186">編譯器在剖析計算運算式時，會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一系列的嵌套函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-186">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="83066-187">此嵌套運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="83066-187">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="83066-188">在上述程式碼中，如果不`Run`是`Delay`在計算運算式產生器類別中定義，則會省略和的呼叫。</span><span class="sxs-lookup"><span data-stu-id="83066-188">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="83066-189">計算運算式的主體（此處所表示`{| cexpr |}`的）會轉譯為包含 builder 類別之方法的呼叫，其方式如下表中所述。</span><span class="sxs-lookup"><span data-stu-id="83066-189">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="83066-190">計算運算式`{| cexpr |}`會根據這些翻譯以遞迴方式定義， `expr`其中是F#運算式， `cexpr`而是計算運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-190">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="83066-191">運算式</span><span class="sxs-lookup"><span data-stu-id="83066-191">Expression</span></span>|<span data-ttu-id="83066-192">轉譯</span><span class="sxs-lookup"><span data-stu-id="83066-192">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="83066-193">在上表中， `other-expr`描述資料表中未列出的運算式。</span><span class="sxs-lookup"><span data-stu-id="83066-193">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="83066-194">產生器類別不需要執行所有方法，並且支援上表中所列的所有翻譯。</span><span class="sxs-lookup"><span data-stu-id="83066-194">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="83066-195">該類型的計算運算式無法使用未實作為的結構。</span><span class="sxs-lookup"><span data-stu-id="83066-195">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="83066-196">例如，如果您不想要在計算運算式中`use`支援關鍵字，可以`Use`在您的 builder 類別中省略的定義。</span><span class="sxs-lookup"><span data-stu-id="83066-196">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="83066-197">下列程式碼範例顯示的計算運算式會將計算封裝成一系列步驟，一次可以評估一個步驟。</span><span class="sxs-lookup"><span data-stu-id="83066-197">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="83066-198">區分聯集類型`OkOrException`，會編碼到目前為止所評估之運算式的錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="83066-198">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="83066-199">這段程式碼會示範幾個您可以在計算運算式中使用的一般模式，例如一些產生器方法的樣板化。</span><span class="sxs-lookup"><span data-stu-id="83066-199">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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
        | Done value -> func value
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
// returns "Done 7"
comp |> step |> step |> step |> step 
```

<span data-ttu-id="83066-200">計算運算式具有基礎類型，此運算式會傳回。</span><span class="sxs-lookup"><span data-stu-id="83066-200">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="83066-201">基礎類型可能代表可執行檔計算結果或延遲計算，或可提供方法來逐一查看某種類型的集合。</span><span class="sxs-lookup"><span data-stu-id="83066-201">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="83066-202">在上述範例中，基礎類型**最後**是。</span><span class="sxs-lookup"><span data-stu-id="83066-202">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="83066-203">若為序列運算式，基礎類型為<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="83066-203">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83066-204">若為查詢運算式，基礎類型為<xref:System.Linq.IQueryable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="83066-204">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83066-205">針對非同步工作流程，基礎類型為[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。</span><span class="sxs-lookup"><span data-stu-id="83066-205">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="83066-206">`Async`物件代表要執行以計算結果的工作。</span><span class="sxs-lookup"><span data-stu-id="83066-206">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="83066-207">例如，您呼叫[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算，並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="83066-207">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="83066-208">自訂作業</span><span class="sxs-lookup"><span data-stu-id="83066-208">Custom Operations</span></span>

<span data-ttu-id="83066-209">您可以在計算運算式上定義自訂運算，並使用自訂作業作為計算運算式中的運算子。</span><span class="sxs-lookup"><span data-stu-id="83066-209">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="83066-210">例如，您可以在查詢運算式中包含查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="83066-210">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="83066-211">當您定義自訂作業時，您必須在計算運算式中定義 Yield 和 For 方法。</span><span class="sxs-lookup"><span data-stu-id="83066-211">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="83066-212">若要定義自訂作業，請將它放在計算運算式的產生器類別中，然後[`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)套用。</span><span class="sxs-lookup"><span data-stu-id="83066-212">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="83066-213">這個屬性會採用字串做為引數，這是要在自訂作業中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="83066-213">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="83066-214">在計算運算式的左大括弧開頭，此名稱會進入範圍內。</span><span class="sxs-lookup"><span data-stu-id="83066-214">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="83066-215">因此，您不應該使用與此區塊中的自訂作業同名的識別碼。</span><span class="sxs-lookup"><span data-stu-id="83066-215">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="83066-216">例如，請避免在查詢運算式中使用識別碼`all` ， `last`例如或。</span><span class="sxs-lookup"><span data-stu-id="83066-216">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="83066-217">以新的自訂作業擴充現有的產生器</span><span class="sxs-lookup"><span data-stu-id="83066-217">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="83066-218">如果您已經有 builder 類別，則可以從這個產生器類別的外部延伸其自訂作業。</span><span class="sxs-lookup"><span data-stu-id="83066-218">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="83066-219">擴充功能必須在模組中宣告。</span><span class="sxs-lookup"><span data-stu-id="83066-219">Extensions must be declared in modules.</span></span> <span data-ttu-id="83066-220">命名空間不能包含延伸成員，除非在相同檔案和定義類型的相同命名空間宣告群組中。</span><span class="sxs-lookup"><span data-stu-id="83066-220">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="83066-221">下列範例會顯示現有`Microsoft.FSharp.Linq.QueryBuilder`類別的延伸。</span><span class="sxs-lookup"><span data-stu-id="83066-221">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="83066-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83066-222">See also</span></span>

- [<span data-ttu-id="83066-223">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="83066-223">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="83066-224">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="83066-224">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="83066-225">序列</span><span class="sxs-lookup"><span data-stu-id="83066-225">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="83066-226">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="83066-226">Query Expressions</span></span>](query-expressions.md)
