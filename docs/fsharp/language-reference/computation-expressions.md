---
title: 計算運算式
description: 瞭解如何創建用於在 F# 中編寫可使用控制流構造和綁定進行排序和組合的計算的便捷語法。
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400229"
---
# <a name="computation-expressions"></a><span data-ttu-id="1f398-103">計算運算式</span><span class="sxs-lookup"><span data-stu-id="1f398-103">Computation Expressions</span></span>

<span data-ttu-id="1f398-104">F# 中的計算運算式為編寫可以使用控制流構造和綁定進行排序和組合的計算提供了方便的語法。</span><span class="sxs-lookup"><span data-stu-id="1f398-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="1f398-105">根據計算運算式的類型，它們可以被認為是一種表達單體、單體、莫納變壓器和施用器的方法。</span><span class="sxs-lookup"><span data-stu-id="1f398-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="1f398-106">但是，與其他語言（如 Haskell 中的*do-符號*）不同，它們不綁定到單個抽象，並且不依賴宏或其他形式的元程式設計來完成方便且上下文相關的語法。</span><span class="sxs-lookup"><span data-stu-id="1f398-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="1f398-107">概觀</span><span class="sxs-lookup"><span data-stu-id="1f398-107">Overview</span></span>

<span data-ttu-id="1f398-108">計算可以有多種形式。</span><span class="sxs-lookup"><span data-stu-id="1f398-108">Computations can take many forms.</span></span> <span data-ttu-id="1f398-109">最常見的計算形式是單線程執行，易於理解和修改。</span><span class="sxs-lookup"><span data-stu-id="1f398-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="1f398-110">但是，並非所有形式的計算都像單線程執行那樣簡單明瞭。</span><span class="sxs-lookup"><span data-stu-id="1f398-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="1f398-111">部分範例包括：</span><span class="sxs-lookup"><span data-stu-id="1f398-111">Some examples include:</span></span>

- <span data-ttu-id="1f398-112">非確定性計算</span><span class="sxs-lookup"><span data-stu-id="1f398-112">Non-deterministic computations</span></span>
- <span data-ttu-id="1f398-113">非同步計算</span><span class="sxs-lookup"><span data-stu-id="1f398-113">Asynchronous computations</span></span>
- <span data-ttu-id="1f398-114">有效的計算</span><span class="sxs-lookup"><span data-stu-id="1f398-114">Effectful computations</span></span>
- <span data-ttu-id="1f398-115">生成計算</span><span class="sxs-lookup"><span data-stu-id="1f398-115">Generative computations</span></span>

<span data-ttu-id="1f398-116">更一般情況下，必須在應用程式的某些部分執行*上下文相關的*計算。</span><span class="sxs-lookup"><span data-stu-id="1f398-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="1f398-117">編寫上下文敏感代碼可能具有挑戰性，因為很容易在給定上下文之外"洩漏"計算，而無需抽象來防止您這樣做。</span><span class="sxs-lookup"><span data-stu-id="1f398-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="1f398-118">這些抽象通常具有挑戰性，可以自己編寫，這就是為什麼 F# 具有一種通用的方式來執行此操作，稱為**計算運算式**。</span><span class="sxs-lookup"><span data-stu-id="1f398-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="1f398-119">計算運算式為編碼上下文敏感的計算提供了統一的語法和抽象模型。</span><span class="sxs-lookup"><span data-stu-id="1f398-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="1f398-120">每個計算運算式都由*產生器*類型支援。</span><span class="sxs-lookup"><span data-stu-id="1f398-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="1f398-121">產生器類型定義可用於計算運算式的操作。</span><span class="sxs-lookup"><span data-stu-id="1f398-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="1f398-122">請參閱[創建新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中演示如何創建自訂計算運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="1f398-123">語法概觀</span><span class="sxs-lookup"><span data-stu-id="1f398-123">Syntax overview</span></span>

<span data-ttu-id="1f398-124">所有計算運算式都具有以下形式：</span><span class="sxs-lookup"><span data-stu-id="1f398-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="1f398-125">其中`builder-expr`是定義計算運算式的產生器類型的名稱，是`cexper`計算運算式的運算式正文。</span><span class="sxs-lookup"><span data-stu-id="1f398-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="1f398-126">例如，`async`計算運算式代碼可以如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f398-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="1f398-127">計算運算式中提供了一個特殊的附加語法，如上例所示。</span><span class="sxs-lookup"><span data-stu-id="1f398-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="1f398-128">計算運算式可以實現以下運算式形式：</span><span class="sxs-lookup"><span data-stu-id="1f398-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="1f398-129">這些關鍵字和其他標準 F# 關鍵字僅在支援產生器類型中定義時才在計算運算式中可用。</span><span class="sxs-lookup"><span data-stu-id="1f398-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="1f398-130">唯一的例外是`match!`，它本身就是使用後跟模式匹配結果的`let!`語法糖。</span><span class="sxs-lookup"><span data-stu-id="1f398-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="1f398-131">產生器類型是定義控制計算運算式片段組合方式的特殊方法的物件;也就是說，它的方法控制計算運算式的表現。</span><span class="sxs-lookup"><span data-stu-id="1f398-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="1f398-132">描述產生器類的另一種方法是說它使您能夠自訂許多 F# 構造（如迴圈和綁定）的操作。</span><span class="sxs-lookup"><span data-stu-id="1f398-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="1f398-133">關鍵字`let!`將調用到另一個計算運算式的結果綁定到名稱：</span><span class="sxs-lookup"><span data-stu-id="1f398-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="1f398-134">如果使用 將調用綁定到 計算運算式`let`，則不會獲取計算運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="1f398-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="1f398-135">相反，您將綁定到該計算運算式的*未實現*調用的值。</span><span class="sxs-lookup"><span data-stu-id="1f398-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="1f398-136">用於`let!`綁定到結果。</span><span class="sxs-lookup"><span data-stu-id="1f398-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="1f398-137">`let!`由產生器類型上`Bind(x, f)`的成員定義。</span><span class="sxs-lookup"><span data-stu-id="1f398-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="1f398-138">關鍵字`do!`用於調用返回`unit`類似類型（由產生器上`Zero`的成員定義）的計算運算式：</span><span class="sxs-lookup"><span data-stu-id="1f398-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="1f398-139">對於[非同步工作流](asynchronous-workflows.md)，此類型為`Async<unit>`。</span><span class="sxs-lookup"><span data-stu-id="1f398-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="1f398-140">對於其他計算運算式，類型可能是`CExpType<unit>`。</span><span class="sxs-lookup"><span data-stu-id="1f398-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="1f398-141">`do!`由產生器類型上`Bind(x, f)`的成員定義，其中`f`生成 。 `unit`</span><span class="sxs-lookup"><span data-stu-id="1f398-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="1f398-142">關鍵字`yield`用於從計算運算式傳回值，以便它可以用作<xref:System.Collections.Generic.IEnumerable%601>：</span><span class="sxs-lookup"><span data-stu-id="1f398-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="1f398-143">在大多數情況下，調用方可以省略它。</span><span class="sxs-lookup"><span data-stu-id="1f398-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="1f398-144">省略的最常見方法是`yield`使用`->`運算子：</span><span class="sxs-lookup"><span data-stu-id="1f398-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="1f398-145">對於可能產生許多不同的值的更複雜的運算式，也許有條件地省略關鍵字可以執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1f398-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="1f398-146">與[C# 中的屈服關鍵字](../../csharp/language-reference/keywords/yield.md)一樣，計算運算式中的每個元素在反覆運算時都會返回。</span><span class="sxs-lookup"><span data-stu-id="1f398-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="1f398-147">`yield`由產生器類型上`Yield(x)`的成員定義，其中`x`要回產的專案。</span><span class="sxs-lookup"><span data-stu-id="1f398-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="1f398-148">關鍵字`yield!`用於拼平計算運算式中的值集合：</span><span class="sxs-lookup"><span data-stu-id="1f398-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="1f398-149">計算時，調用`yield!`的計算運算式將使其項逐個返回，從而使結果平展。</span><span class="sxs-lookup"><span data-stu-id="1f398-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="1f398-150">`yield!`由產生器類型上`YieldFrom(x)`的成員定義，其中`x`是值的集合。</span><span class="sxs-lookup"><span data-stu-id="1f398-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="1f398-151">與`yield``yield!`必須顯式指定不同。</span><span class="sxs-lookup"><span data-stu-id="1f398-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="1f398-152">它的行為在計算運算式中不隱式。</span><span class="sxs-lookup"><span data-stu-id="1f398-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="1f398-153">關鍵字`return`在與計算運算式對應的類型中換行值。</span><span class="sxs-lookup"><span data-stu-id="1f398-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="1f398-154">除了使用`yield`的計算運算式外，它還用於"完成"計算運算式：</span><span class="sxs-lookup"><span data-stu-id="1f398-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="1f398-155">`return`由產生器類型上`Return(x)`的成員定義，要包裝的項`x`所在的位置。</span><span class="sxs-lookup"><span data-stu-id="1f398-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="1f398-156">關鍵字`return!`實現計算運算式的值，並換行導致與計算運算式對應的類型：</span><span class="sxs-lookup"><span data-stu-id="1f398-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="1f398-157">`return!`由產生器類型上`ReturnFrom(x)`的成員定義，其中`x`是另一個計算運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="1f398-158">關鍵字`match!`允許您在結果上內聯對另一個計算運算式和模式匹配的調用：</span><span class="sxs-lookup"><span data-stu-id="1f398-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="1f398-159">使用`match!`調用 計算運算式時，它將實現調用的結果，如`let!`。</span><span class="sxs-lookup"><span data-stu-id="1f398-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="1f398-160">這通常用於調用計算運算式時，其中結果為[可選](options.md)。</span><span class="sxs-lookup"><span data-stu-id="1f398-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="1f398-161">內置計算運算式</span><span class="sxs-lookup"><span data-stu-id="1f398-161">Built-in computation expressions</span></span>

<span data-ttu-id="1f398-162">F# 核心庫定義了三個內置計算運算式：[序列運算式](sequences.md)、[非同步工作流](asynchronous-workflows.md)和[查詢運算式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1f398-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="1f398-163">創建新類型的計算運算式</span><span class="sxs-lookup"><span data-stu-id="1f398-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="1f398-164">您可以通過創建產生器類並在類上定義某些特殊方法來定義自己的計算運算式的特徵。</span><span class="sxs-lookup"><span data-stu-id="1f398-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="1f398-165">產生器類可以選擇定義下表中列出的方法。</span><span class="sxs-lookup"><span data-stu-id="1f398-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="1f398-166">下表描述了可在工作流產生器類中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="1f398-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="1f398-167">**方法**</span><span class="sxs-lookup"><span data-stu-id="1f398-167">**Method**</span></span>|<span data-ttu-id="1f398-168">**典型簽名**</span><span class="sxs-lookup"><span data-stu-id="1f398-168">**Typical signature(s)**</span></span>|<span data-ttu-id="1f398-169">**描述**</span><span class="sxs-lookup"><span data-stu-id="1f398-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="1f398-170">調用`let!`和`do!`在計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="1f398-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="1f398-171">將計算運算式包裝為函數。</span><span class="sxs-lookup"><span data-stu-id="1f398-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="1f398-172">在計算`return`運算式中調用。</span><span class="sxs-lookup"><span data-stu-id="1f398-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1f398-173">在計算`return!`運算式中調用。</span><span class="sxs-lookup"><span data-stu-id="1f398-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="1f398-174">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="1f398-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="1f398-175">執行計算運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="1f398-176">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="1f398-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="1f398-177">調用計算運算式中的排序。</span><span class="sxs-lookup"><span data-stu-id="1f398-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="1f398-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="1f398-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="1f398-179">在計算`for...do`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="1f398-180">在計算`try...finally`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="1f398-181">在計算`try...with`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="1f398-182">在計算`use`運算式中調用綁定。</span><span class="sxs-lookup"><span data-stu-id="1f398-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="1f398-183">在計算`while...do`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="1f398-184">在計算`yield`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1f398-185">在計算`yield!`運算式中調用運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="1f398-186">調用計算運算式`else`中的空`if...then`運算式分支。</span><span class="sxs-lookup"><span data-stu-id="1f398-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="1f398-187">指示計算運算式作為引號傳遞給`Run`成員。</span><span class="sxs-lookup"><span data-stu-id="1f398-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="1f398-188">它將計算的所有實例轉換為引號。</span><span class="sxs-lookup"><span data-stu-id="1f398-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="1f398-189">產生器類中的許多方法使用並返回`M<'T>`構造，該構造通常是單獨定義的類型，用於描述要組合的計算類型，例如，`Async<'T>`對於非同步工作流和`Seq<'T>`序列工作流。</span><span class="sxs-lookup"><span data-stu-id="1f398-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="1f398-190">這些方法的簽名使它們能夠相互組合和嵌套，以便從一個構造返回的工作流物件可以傳遞給下一個構造。</span><span class="sxs-lookup"><span data-stu-id="1f398-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="1f398-191">編譯器在解析計算運算式時，使用上表中的方法和計算運算式中的代碼將運算式轉換為一系列嵌套函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="1f398-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="1f398-192">嵌套運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="1f398-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="1f398-193">在上述代碼中，如果計算運算式`Run`產生器`Delay`類中未定義對 和 的調用，則省略它們。</span><span class="sxs-lookup"><span data-stu-id="1f398-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="1f398-194">計算運算式的正文（此處表示為`{| cexpr |}`）通過下表中描述的翻譯轉換為涉及產生器類方法的調用。</span><span class="sxs-lookup"><span data-stu-id="1f398-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="1f398-195">計算運算式`{| cexpr |}`根據這些翻譯以遞迴方式定義，其中`expr`是 F# 運算式，是`cexpr`計算運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="1f398-196">運算是</span><span class="sxs-lookup"><span data-stu-id="1f398-196">Expression</span></span>|<span data-ttu-id="1f398-197">翻譯</span><span class="sxs-lookup"><span data-stu-id="1f398-197">Translation</span></span>|
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
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
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

<span data-ttu-id="1f398-198">在上表中，`other-expr`描述表中未以其他方式列出的運算式。</span><span class="sxs-lookup"><span data-stu-id="1f398-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="1f398-199">產生器類不需要實現所有方法並支援上表中列出的所有翻譯。</span><span class="sxs-lookup"><span data-stu-id="1f398-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="1f398-200">未實現的構造在該類型的計算運算式中不可用。</span><span class="sxs-lookup"><span data-stu-id="1f398-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="1f398-201">例如，如果不想在計算運算式中支援`use`關鍵字，則可以省略產生器類中的定義。 `Use`</span><span class="sxs-lookup"><span data-stu-id="1f398-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="1f398-202">下面的代碼示例顯示了一個計算運算式，該運算式將計算封裝為一系列步驟，可以一次計算一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1f398-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="1f398-203">受歧視的聯合類型`OkOrException`， 編碼運算式的錯誤狀態，以計算到目前為止。</span><span class="sxs-lookup"><span data-stu-id="1f398-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="1f398-204">此代碼演示了可在計算運算式中使用的幾個典型模式，例如某些產生器方法的樣板實現。</span><span class="sxs-lookup"><span data-stu-id="1f398-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="1f398-205">計算運算式具有基礎類型，運算式返回該類型。</span><span class="sxs-lookup"><span data-stu-id="1f398-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="1f398-206">基礎類型可能表示可以執行的計算結果或延遲計算，或者它可能提供一種通過某些類型的集合反覆運算的方法。</span><span class="sxs-lookup"><span data-stu-id="1f398-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="1f398-207">在前面的示例中，基礎類型**為 最終**。</span><span class="sxs-lookup"><span data-stu-id="1f398-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="1f398-208">對於序列運算式，基礎類型為<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1f398-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f398-209">對於查詢運算式，基礎類型為<xref:System.Linq.IQueryable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1f398-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f398-210">對於非同步工作流，基礎類型為[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。</span><span class="sxs-lookup"><span data-stu-id="1f398-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="1f398-211">物件`Async`表示要執行的工作來計算結果。</span><span class="sxs-lookup"><span data-stu-id="1f398-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="1f398-212">例如，調用[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)以執行計算並返回結果。</span><span class="sxs-lookup"><span data-stu-id="1f398-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="1f398-213">自訂作業</span><span class="sxs-lookup"><span data-stu-id="1f398-213">Custom Operations</span></span>

<span data-ttu-id="1f398-214">可以在計算運算式上定義自訂操作，並在計算運算式中使用自訂操作作為運算子。</span><span class="sxs-lookup"><span data-stu-id="1f398-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="1f398-215">例如，可以在查詢運算式中包括查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="1f398-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="1f398-216">定義自訂操作時，必須在計算運算式中定義"產量"和"For"方法。</span><span class="sxs-lookup"><span data-stu-id="1f398-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="1f398-217">要定義自訂操作，請將其放在計算運算式的產生器類中，然後應用 。 [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)</span><span class="sxs-lookup"><span data-stu-id="1f398-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="1f398-218">此屬性將字串作為參數，它是要在自訂操作中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f398-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="1f398-219">此名稱在計算運算式的開頭大括弧開始時進入作用域。</span><span class="sxs-lookup"><span data-stu-id="1f398-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="1f398-220">因此，不應使用此塊中與自訂操作同名的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f398-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="1f398-221">例如，避免使用識別碼（如`all`或`last`在查詢運算式中）。</span><span class="sxs-lookup"><span data-stu-id="1f398-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="1f398-222">使用新的自訂操作擴展現有產生器</span><span class="sxs-lookup"><span data-stu-id="1f398-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="1f398-223">如果您已經具有產生器類，則可以在此產生器類之外擴展其自訂操作。</span><span class="sxs-lookup"><span data-stu-id="1f398-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="1f398-224">必須在模組中聲明擴展。</span><span class="sxs-lookup"><span data-stu-id="1f398-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="1f398-225">命名空間不能包含擴展成員，但在同一檔和定義該類型的同一命名空間聲明組中除外。</span><span class="sxs-lookup"><span data-stu-id="1f398-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="1f398-226">下面的示例顯示了現有`Microsoft.FSharp.Linq.QueryBuilder`類的擴展。</span><span class="sxs-lookup"><span data-stu-id="1f398-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="1f398-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f398-227">See also</span></span>

- [<span data-ttu-id="1f398-228">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="1f398-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1f398-229">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="1f398-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="1f398-230">序列</span><span class="sxs-lookup"><span data-stu-id="1f398-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="1f398-231">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="1f398-231">Query Expressions</span></span>](query-expressions.md)
