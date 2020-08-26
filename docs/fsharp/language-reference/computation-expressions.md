---
title: 計算運算式
description: '瞭解如何建立方便的語法，以 F # 撰寫可使用控制流程結構和系結來排序和結合的計算。'
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: 1649d8c57ea9e025d40ef6d39d92b96795964150
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812155"
---
# <a name="computation-expressions"></a><span data-ttu-id="f82cf-103">計算運算式</span><span class="sxs-lookup"><span data-stu-id="f82cf-103">Computation Expressions</span></span>

<span data-ttu-id="f82cf-104">F # 中的計算運算式提供一個方便的語法，可用來撰寫可使用控制流程結構和系結來排序和結合的計算。</span><span class="sxs-lookup"><span data-stu-id="f82cf-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="f82cf-105">視計算運算式的種類而定，您可以將它們視為表示 monads、monoids、monad 轉換器和 applicative 函子的方式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="f82cf-106">不過，不同于其他語言 (例如 Haskell) 中 *的標記法* ，它們並不會系結至單一抽象概念，也不會依賴宏或其他形式的元程式來完成方便且上下文相關的語法。</span><span class="sxs-lookup"><span data-stu-id="f82cf-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="f82cf-107">概觀</span><span class="sxs-lookup"><span data-stu-id="f82cf-107">Overview</span></span>

<span data-ttu-id="f82cf-108">計算可以採用許多形式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-108">Computations can take many forms.</span></span> <span data-ttu-id="f82cf-109">最常見的計算形式是單一執行緒執行，這很容易理解和修改。</span><span class="sxs-lookup"><span data-stu-id="f82cf-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="f82cf-110">不過，並非所有形式的計算都像單一執行緒執行一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="f82cf-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="f82cf-111">部分範例包括：</span><span class="sxs-lookup"><span data-stu-id="f82cf-111">Some examples include:</span></span>

- <span data-ttu-id="f82cf-112">不具決定性的計算</span><span class="sxs-lookup"><span data-stu-id="f82cf-112">Non-deterministic computations</span></span>
- <span data-ttu-id="f82cf-113">非同步計算</span><span class="sxs-lookup"><span data-stu-id="f82cf-113">Asynchronous computations</span></span>
- <span data-ttu-id="f82cf-114">Effectful 計算</span><span class="sxs-lookup"><span data-stu-id="f82cf-114">Effectful computations</span></span>
- <span data-ttu-id="f82cf-115">有生產力計算</span><span class="sxs-lookup"><span data-stu-id="f82cf-115">Generative computations</span></span>

<span data-ttu-id="f82cf-116">一般來說，您必須在應用程式的某些部分中執行 *內容相關* 的計算。</span><span class="sxs-lookup"><span data-stu-id="f82cf-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="f82cf-117">撰寫內容相關的程式碼可能是一項挑戰，因為在沒有抽象的情況下，可以輕易地在指定的內容之外「流失」計算，以防止您這樣做。</span><span class="sxs-lookup"><span data-stu-id="f82cf-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="f82cf-118">這些抽象概念通常很難自行撰寫，這也是為什麼 F # 有一般化的方法，稱為 **計算運算式**。</span><span class="sxs-lookup"><span data-stu-id="f82cf-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="f82cf-119">計算運算式提供統一的語法和抽象模型，用於編碼內容相關計算。</span><span class="sxs-lookup"><span data-stu-id="f82cf-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="f82cf-120">每個計算運算式 *都是由產生器型別* 所支援。</span><span class="sxs-lookup"><span data-stu-id="f82cf-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="f82cf-121">產生器類型會定義可供計算運算式使用的作業。</span><span class="sxs-lookup"><span data-stu-id="f82cf-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="f82cf-122">請參閱 [建立新的計算運算式類型](computation-expressions.md#creating-a-new-type-of-computation-expression)，其會顯示如何建立自訂計算運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="f82cf-123">語法概觀</span><span class="sxs-lookup"><span data-stu-id="f82cf-123">Syntax overview</span></span>

<span data-ttu-id="f82cf-124">所有計算運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="f82cf-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="f82cf-125">其中 `builder-expr` 是定義計算運算式之產生器類型的名稱，而 `cexper` 則是計算運算式的運算式主體。</span><span class="sxs-lookup"><span data-stu-id="f82cf-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="f82cf-126">例如， `async` 計算運算式程式碼看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="f82cf-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="f82cf-127">在計算運算式中有特殊的額外語法可用，如先前的範例所示。</span><span class="sxs-lookup"><span data-stu-id="f82cf-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="f82cf-128">下列運算式形式可以搭配計算運算式使用：</span><span class="sxs-lookup"><span data-stu-id="f82cf-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="f82cf-129">這些關鍵字和其他標準 F # 關鍵字只有在支援產生器型別中已定義時，才可在計算運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="f82cf-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="f82cf-130">唯一的例外是 `match!` ，它本身就是可供使用的語法， `let!` 後面接著結果的模式比對。</span><span class="sxs-lookup"><span data-stu-id="f82cf-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="f82cf-131">產生器型別是一個物件，它會定義特殊方法來管理計算運算式片段的組合方式;也就是說，其方法會控制計算運算式的行為。</span><span class="sxs-lookup"><span data-stu-id="f82cf-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="f82cf-132">另一種描述 builder 類別的方式，就是假設它可讓您自訂許多 F # 結構的作業，例如迴圈和系結。</span><span class="sxs-lookup"><span data-stu-id="f82cf-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="f82cf-133">關鍵字會將呼叫的結果系結至 `let!` 另一個計算運算式的名稱：</span><span class="sxs-lookup"><span data-stu-id="f82cf-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="f82cf-134">如果您使用來系結計算運算式的呼叫 `let` ，將不會取得計算運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="f82cf-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="f82cf-135">相反地，您會將未產生的呼叫值系結 *至該計算* 運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="f82cf-136">使用系結 `let!` 至結果。</span><span class="sxs-lookup"><span data-stu-id="f82cf-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="f82cf-137">`let!` 由產生器 `Bind(x, f)` 類型上的成員定義。</span><span class="sxs-lookup"><span data-stu-id="f82cf-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="f82cf-138">`do!`關鍵字是用來呼叫計算運算式，該運算式會傳回類似型別的 `unit` (由產生器 `Zero`) 的成員定義：</span><span class="sxs-lookup"><span data-stu-id="f82cf-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="f82cf-139">針對 [非同步工作流程](asynchronous-workflows.md)，此類型為 `Async<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="f82cf-140">針對其他計算運算式，類型可能是 `CExpType<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="f82cf-141">`do!` 是由產生者 `Bind(x, f)` 類型上的成員所定義 `f` `unit` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="f82cf-142">`yield`關鍵字是用來從計算運算式傳回值，讓它可以作為 <xref:System.Collections.Generic.IEnumerable%601> ：</span><span class="sxs-lookup"><span data-stu-id="f82cf-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="f82cf-143">在大部分的情況下，呼叫端可以省略它。</span><span class="sxs-lookup"><span data-stu-id="f82cf-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="f82cf-144">最常見的省略方法 `yield` 是使用 `->` 運算子：</span><span class="sxs-lookup"><span data-stu-id="f82cf-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="f82cf-145">針對可能會產生許多不同值的更複雜運算式，而且可能有條件地省略關鍵字可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f82cf-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

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

<span data-ttu-id="f82cf-146">如同 [c # 中的 yield 關鍵字](../../csharp/language-reference/keywords/yield.md)，計算運算式中的每個專案都會在反覆運算時產生回來。</span><span class="sxs-lookup"><span data-stu-id="f82cf-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="f82cf-147">`yield` 由 `Yield(x)` 產生器型別的成員定義，其中 `x` 是要傳回的專案。</span><span class="sxs-lookup"><span data-stu-id="f82cf-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="f82cf-148">`yield!`關鍵字是用來壓平合併計算運算式中的值集合：</span><span class="sxs-lookup"><span data-stu-id="f82cf-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="f82cf-149">進行評估時，所呼叫的計算運算式 `yield!` 會將其專案逐一產生，並將結果壓平合併。</span><span class="sxs-lookup"><span data-stu-id="f82cf-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="f82cf-150">`yield!` 由產生器 `YieldFrom(x)` 型別上的成員定義，其中 `x` 是值的集合。</span><span class="sxs-lookup"><span data-stu-id="f82cf-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="f82cf-151">不同于 `yield` ， `yield!` 必須明確指定。</span><span class="sxs-lookup"><span data-stu-id="f82cf-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="f82cf-152">其行為在計算運算式中不是隱含的。</span><span class="sxs-lookup"><span data-stu-id="f82cf-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="f82cf-153">`return`關鍵字會在對應至計算運算式的型別中包裝一個值。</span><span class="sxs-lookup"><span data-stu-id="f82cf-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="f82cf-154">除了使用的計算運算式之外 `yield` ，它也用來「完成」計算運算式：</span><span class="sxs-lookup"><span data-stu-id="f82cf-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="f82cf-155">`return` 是由產生器 `Return(x)` 型別上的成員所定義，其中 `x` 是要換行的專案。</span><span class="sxs-lookup"><span data-stu-id="f82cf-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="f82cf-156">`return!`關鍵字會知道計算運算式的值，並將結果包裝為對應于計算運算式的型別：</span><span class="sxs-lookup"><span data-stu-id="f82cf-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="f82cf-157">`return!` 由產生器 `ReturnFrom(x)` 型別上的成員定義，其中 `x` 是另一個計算運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="f82cf-158">`match!`關鍵字可讓您內嵌對另一個計算運算式的呼叫，以及其結果的模式比對：</span><span class="sxs-lookup"><span data-stu-id="f82cf-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="f82cf-159">使用呼叫計算運算式時 `match!` ，它會瞭解呼叫的結果（例如） `let!` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="f82cf-160">這通常用於呼叫計算運算式，其中的結果是 [選擇性](options.md)的。</span><span class="sxs-lookup"><span data-stu-id="f82cf-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="f82cf-161">內建計算運算式</span><span class="sxs-lookup"><span data-stu-id="f82cf-161">Built-in computation expressions</span></span>

<span data-ttu-id="f82cf-162">F # 核心程式庫會定義三個內建的計算運算式： [順序運算式](sequences.md)、 [非同步工作流程](asynchronous-workflows.md)和 [查詢運算式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f82cf-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="f82cf-163">建立新的計算運算式類型</span><span class="sxs-lookup"><span data-stu-id="f82cf-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="f82cf-164">您可以藉由建立產生器類別，並在類別上定義某些特殊方法，來定義您自己的計算運算式的特性。</span><span class="sxs-lookup"><span data-stu-id="f82cf-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="f82cf-165">Builder 類別可以選擇性地定義下表所列的方法。</span><span class="sxs-lookup"><span data-stu-id="f82cf-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="f82cf-166">下表說明可在工作流程產生器類別中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="f82cf-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="f82cf-167">**方法**</span><span class="sxs-lookup"><span data-stu-id="f82cf-167">**Method**</span></span>|<span data-ttu-id="f82cf-168">\*\*一般簽章 (s) \*\*</span><span class="sxs-lookup"><span data-stu-id="f82cf-168">**Typical signature(s)**</span></span>|<span data-ttu-id="f82cf-169">**說明**</span><span class="sxs-lookup"><span data-stu-id="f82cf-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="f82cf-170">`let!` `do!` 在計算運算式中呼叫和。</span><span class="sxs-lookup"><span data-stu-id="f82cf-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="f82cf-171">將計算運算式包裝為函數。</span><span class="sxs-lookup"><span data-stu-id="f82cf-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="f82cf-172">`return`在計算運算式中呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="f82cf-173">`return!`在計算運算式中呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="f82cf-174">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="f82cf-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="f82cf-175">執行計算運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="f82cf-176">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="f82cf-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="f82cf-177">在計算運算式中呼叫以進行排序。</span><span class="sxs-lookup"><span data-stu-id="f82cf-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="f82cf-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="f82cf-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="f82cf-179">針對 `for...do` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="f82cf-180">針對 `try...finally` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="f82cf-181">針對 `try...with` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="f82cf-182">在計算運算式中呼叫以進行系結 `use` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="f82cf-183">針對 `while...do` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="f82cf-184">針對 `yield` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="f82cf-185">針對 `yield!` 計算運算式中的運算式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="f82cf-186">`else` `if...then` 在計算運算式中針對運算式的空分支呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="f82cf-187">指出計算運算式以 `Run` 引號形式傳遞至成員。</span><span class="sxs-lookup"><span data-stu-id="f82cf-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="f82cf-188">它會將計算的所有實例轉譯成引號。</span><span class="sxs-lookup"><span data-stu-id="f82cf-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="f82cf-189">產生器類別中的許多方法都會使用並傳回 `M<'T>` 結構，而這通常是個別定義型別，可區分要合併的計算類型，例如， `Async<'T>` 針對非同步工作流程和 `Seq<'T>` 序列工作流程。</span><span class="sxs-lookup"><span data-stu-id="f82cf-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="f82cf-190">這些方法的簽章可讓它們彼此合併和互相合併，以便將從一個結構傳回的工作流程物件傳遞給下一個結構。</span><span class="sxs-lookup"><span data-stu-id="f82cf-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="f82cf-191">編譯器在剖析計算運算式時，會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一連串的嵌套函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="f82cf-192">嵌套運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="f82cf-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="f82cf-193">在上述程式碼中， `Run` `Delay` 如果未在計算運算式產生器類別中定義，則會省略和的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f82cf-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="f82cf-194">計算運算式的主體（在此表示為 `{| cexpr |}` ）會轉譯成包含產生器類別之方法的呼叫，並遵循下表所述的翻譯。</span><span class="sxs-lookup"><span data-stu-id="f82cf-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="f82cf-195">計算運算式 `{| cexpr |}` 會根據這些轉譯以遞迴方式定義，其中 `expr` 是 F # 運算式且 `cexpr` 為計算運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="f82cf-196">運算是</span><span class="sxs-lookup"><span data-stu-id="f82cf-196">Expression</span></span>|<span data-ttu-id="f82cf-197">翻譯</span><span class="sxs-lookup"><span data-stu-id="f82cf-197">Translation</span></span>|
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

<span data-ttu-id="f82cf-198">在上表中， `other-expr` 描述資料表中未列出的運算式。</span><span class="sxs-lookup"><span data-stu-id="f82cf-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="f82cf-199">產生器類別不需要執行所有方法，並支援上表所列的所有翻譯。</span><span class="sxs-lookup"><span data-stu-id="f82cf-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="f82cf-200">在該類型的計算運算式中，未執行的這些結構無法使用。</span><span class="sxs-lookup"><span data-stu-id="f82cf-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="f82cf-201">例如，如果您不想要 `use` 在計算運算式中支援關鍵字，可以省略 `Use` builder 類別中的定義。</span><span class="sxs-lookup"><span data-stu-id="f82cf-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="f82cf-202">下列程式碼範例會示範將計算封裝成一系列步驟的計算運算式，這些步驟可以一次一個步驟來評估。</span><span class="sxs-lookup"><span data-stu-id="f82cf-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="f82cf-203">差異聯集型別，會將 `OkOrException` 目前所評估的運算式的錯誤狀態編碼。</span><span class="sxs-lookup"><span data-stu-id="f82cf-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="f82cf-204">這段程式碼示範一些您可以在計算運算式中使用的一般模式，例如一些產生器方法的未定案實作為。</span><span class="sxs-lookup"><span data-stu-id="f82cf-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="f82cf-205">計算運算式具有運算式傳回的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="f82cf-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="f82cf-206">基礎類型可能代表可執行檔計算結果或延遲計算，或可能提供逐一查看某些類型集合的方法。</span><span class="sxs-lookup"><span data-stu-id="f82cf-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="f82cf-207">在上述範例中， **最後**是基礎類型。</span><span class="sxs-lookup"><span data-stu-id="f82cf-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="f82cf-208">若為序列運算式，基礎類型為 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f82cf-209">若為查詢運算式，基礎類型為 <xref:System.Linq.IQueryable?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f82cf-210">如果是非同步工作流程，基礎類型為 [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-210">For an asynchronous workflow, the underlying type is [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html).</span></span> <span data-ttu-id="f82cf-211">`Async`物件代表要執行以計算結果的工作。</span><span class="sxs-lookup"><span data-stu-id="f82cf-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="f82cf-212">例如，您可以呼叫 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) 來執行計算，並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="f82cf-212">For example, you call [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="f82cf-213">自訂作業</span><span class="sxs-lookup"><span data-stu-id="f82cf-213">Custom Operations</span></span>

<span data-ttu-id="f82cf-214">您可以在計算運算式上定義自訂作業，並使用自訂作業做為運算運算式中的運算子。</span><span class="sxs-lookup"><span data-stu-id="f82cf-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="f82cf-215">例如，您可以在查詢運算式中包含查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="f82cf-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="f82cf-216">當您定義自訂作業時，您必須在計算運算式中定義 Yield 和方法。</span><span class="sxs-lookup"><span data-stu-id="f82cf-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="f82cf-217">若要定義自訂作業，請將它放在計算運算式的 builder 類別中，然後套用 [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html).</span></span> <span data-ttu-id="f82cf-218">這個屬性會採用字串做為引數，這是要在自訂作業中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="f82cf-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="f82cf-219">這個名稱會在計算運算式的左大括弧開頭的範圍內。</span><span class="sxs-lookup"><span data-stu-id="f82cf-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="f82cf-220">因此，您不應該使用與此區塊中的自訂作業同名的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f82cf-220">Therefore, you shouldn't use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="f82cf-221">例如，請避免在 `all` 查詢運算式中使用識別碼，例如或 `last` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="f82cf-222">以新的自訂作業擴充現有的產生器</span><span class="sxs-lookup"><span data-stu-id="f82cf-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="f82cf-223">如果您已經有 builder 類別，則可以從這個產生器類別外部延伸其自訂作業。</span><span class="sxs-lookup"><span data-stu-id="f82cf-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="f82cf-224">擴充功能必須在模組中宣告。</span><span class="sxs-lookup"><span data-stu-id="f82cf-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="f82cf-225">命名空間不能包含延伸成員，除了在相同檔案和定義類型的相同命名空間宣告群組中。</span><span class="sxs-lookup"><span data-stu-id="f82cf-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="f82cf-226">下列範例顯示現有類別的擴充 `FSharp.Linq.QueryBuilder` 。</span><span class="sxs-lookup"><span data-stu-id="f82cf-226">The following example shows the extension of the existing `FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="f82cf-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f82cf-227">See also</span></span>

- [<span data-ttu-id="f82cf-228">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="f82cf-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f82cf-229">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="f82cf-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="f82cf-230">序列</span><span class="sxs-lookup"><span data-stu-id="f82cf-230">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="f82cf-231">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="f82cf-231">Query Expressions</span></span>](query-expressions.md)
