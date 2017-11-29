---
title: "計算運算式 (F#)"
description: "了解如何建立方便的語法撰寫 F # 可以排序，合併使用控制流程建構和繫結中的計算。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: 15ba2e167efc1d295d81439dcf85bc7272e05265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="computation-expressions"></a><span data-ttu-id="879b0-104">計算運算式</span><span class="sxs-lookup"><span data-stu-id="879b0-104">Computation Expressions</span></span>

<span data-ttu-id="879b0-105">F # 中的計算運算式提供方便的語法撰寫，可以排序，並使用控制流程建構和繫結結合在一起的計算。</span><span class="sxs-lookup"><span data-stu-id="879b0-105">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="879b0-106">它們可以用來提供方便的語法*monad*，可用來管理資料、 控制和功能的程式中的副作用的功能性程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="879b0-106">They can be used to provide a convenient syntax for *monads*, a functional programming feature that can be used to manage data, control, and side effects in functional programs.</span></span>


## <a name="built-in-workflows"></a><span data-ttu-id="879b0-107">內建工作流程</span><span class="sxs-lookup"><span data-stu-id="879b0-107">Built-in Workflows</span></span>
<span data-ttu-id="879b0-108">循序項運算式是計算運算式的範例是非同步工作流程和查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-108">Sequence expressions are an example of a computation expression, as are asynchronous workflows and query expressions.</span></span> <span data-ttu-id="879b0-109">如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[查詢運算式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="879b0-109">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

<span data-ttu-id="879b0-110">某些功能通用於循序項運算式與非同步工作流程，並說明計算運算式的基本語法：</span><span class="sxs-lookup"><span data-stu-id="879b0-110">Certain features are common to both sequence expressions and asynchronous workflows and illustrate the basic syntax for a computation expression:</span></span>

```fsharp
builder-name { expression }
```

<span data-ttu-id="879b0-111">上述語法指定指定的運算式所指定類型的計算運算式*產生器名稱*。</span><span class="sxs-lookup"><span data-stu-id="879b0-111">The previous syntax specifies that the given expression is a computation expression of a type specified by *builder-name*.</span></span> <span data-ttu-id="879b0-112">計算運算式可以是內建的工作流程，例如`seq`或`async`，也可以是您定義的項目。</span><span class="sxs-lookup"><span data-stu-id="879b0-112">The computation expression can be a built-in workflow, such as `seq` or `async`, or it can be something you define.</span></span> <span data-ttu-id="879b0-113">*產生器名稱*稱為一種特殊類型的執行個體的識別碼*產生器類型*。</span><span class="sxs-lookup"><span data-stu-id="879b0-113">The *builder-name* is the identifier for an instance of a special type known as the *builder type*.</span></span> <span data-ttu-id="879b0-114">產生器類型是定義管理的片段計算運算式的組合時，也就是程式碼的方式，控制如何執行運算式的特殊方法的類別類型。</span><span class="sxs-lookup"><span data-stu-id="879b0-114">The builder type is a class type that defines special methods that govern the way the fragments of the computation expression are combined, that is, code that controls how the expression executes.</span></span> <span data-ttu-id="879b0-115">另一種方式來描述產生器類別是說，它可讓您自訂許多 F # 建構，例如迴圈和繫結作業。</span><span class="sxs-lookup"><span data-stu-id="879b0-115">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

<span data-ttu-id="879b0-116">在計算運算式中，兩種形式可供某些常見的語言建構。</span><span class="sxs-lookup"><span data-stu-id="879b0-116">In computation expressions, two forms are available for some common language constructs.</span></span> <span data-ttu-id="879b0-117">您可以使用叫用的 variant 建構 ！</span><span class="sxs-lookup"><span data-stu-id="879b0-117">You can invoke the variant constructs by using a !</span></span> <span data-ttu-id="879b0-118">（出問題） 後置詞特定關鍵字，例如`let!`， `do!`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="879b0-118">(bang) suffix on certain keywords, such as `let!`, `do!`, and so on.</span></span> <span data-ttu-id="879b0-119">這些特殊形式都會導致產生器類別來取代這些作業的一般內建行為中所定義的特定函式。</span><span class="sxs-lookup"><span data-stu-id="879b0-119">These special forms cause certain functions defined in the builder class to replace the ordinary built-in behavior of these operations.</span></span> <span data-ttu-id="879b0-120">這些形式類似`yield!`形式`yield`循序項運算式中使用的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="879b0-120">These forms resemble the `yield!` form of the `yield` keyword that is used in sequence expressions.</span></span> <span data-ttu-id="879b0-121">如需詳細資訊，請參閱[序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="879b0-121">For more information, see [Sequences](sequences.md).</span></span>


## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="879b0-122">建立新的計算運算式的類型</span><span class="sxs-lookup"><span data-stu-id="879b0-122">Creating a New Type of Computation Expression</span></span>
<span data-ttu-id="879b0-123">您可以建立產生器類別，以及在類別上定義某些特殊的方法，以定義您自己的計算運算式的特性。</span><span class="sxs-lookup"><span data-stu-id="879b0-123">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="879b0-124">下表所列，產生器類別可以選擇性地定義的方法。</span><span class="sxs-lookup"><span data-stu-id="879b0-124">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="879b0-125">下表描述可用於工作流程產生器類別的方法。</span><span class="sxs-lookup"><span data-stu-id="879b0-125">The following table describes methods that can be used in a workflow builder class.</span></span>


|<span data-ttu-id="879b0-126">**方法**</span><span class="sxs-lookup"><span data-stu-id="879b0-126">**Method**</span></span>|<span data-ttu-id="879b0-127">**典型的簽章**</span><span class="sxs-lookup"><span data-stu-id="879b0-127">**Typical signature(s)**</span></span>|<span data-ttu-id="879b0-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="879b0-128">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="879b0-129">針對呼叫`let!`和`do!`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="879b0-129">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="879b0-130">包裝函式將計算運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-130">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="879b0-131">針對呼叫`return`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="879b0-131">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="879b0-132">針對呼叫`return!`計算運算式中。</span><span class="sxs-lookup"><span data-stu-id="879b0-132">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="879b0-133">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="879b0-133">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="879b0-134">執行計算運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-134">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="879b0-135">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="879b0-135">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="879b0-136">用於計算運算式中的順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="879b0-136">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="879b0-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="879b0-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="879b0-138">針對呼叫`for...do`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-138">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="879b0-139">針對呼叫`try...finally`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-139">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="879b0-140">針對呼叫`try...with`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-140">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="879b0-141">針對呼叫`use`計算運算式中的繫結。</span><span class="sxs-lookup"><span data-stu-id="879b0-141">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="879b0-142">針對呼叫`while...do`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-142">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="879b0-143">針對呼叫`yield`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-143">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="879b0-144">針對呼叫`yield!`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-144">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="879b0-145">呼叫空白`else`分支`if...then`計算運算式中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-145">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
<span data-ttu-id="879b0-146">許多中產生器類別的方法使用，並傳回`M<'T>`建構，通常是分開定義的類型，表示特性的組合，計算種類，例如`Async<'T>`提供非同步工作流程和`Seq<'T>`序列工作流程。</span><span class="sxs-lookup"><span data-stu-id="879b0-146">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="879b0-147">這些方法的簽章會啟用它們要結合並使用彼此的巢狀以便從一個建構傳回的工作流程物件可以傳遞至下一步。</span><span class="sxs-lookup"><span data-stu-id="879b0-147">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="879b0-148">編譯器，當它會剖析為計算運算式，會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一系列的巢狀函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="879b0-148">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="879b0-149">巢狀的運算式是下列格式：</span><span class="sxs-lookup"><span data-stu-id="879b0-149">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="879b0-150">在上述程式碼呼叫`Run`和`Delay`如果他們未定義的計算運算式產生器類別中會省略。</span><span class="sxs-lookup"><span data-stu-id="879b0-150">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="879b0-151">計算運算式，這裡表示為主體`{| cexpr |}`，會轉譯成涉及產生器類別之方法的呼叫中依下表中描述的翻譯。</span><span class="sxs-lookup"><span data-stu-id="879b0-151">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="879b0-152">計算運算式`{| cexpr |}`會根據這些翻譯定義的遞迴其中`expr`是 F # 運算式和`cexpr`是計算運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-152">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="879b0-153">運算式</span><span class="sxs-lookup"><span data-stu-id="879b0-153">Expression</span></span>|<span data-ttu-id="879b0-154">轉譯</span><span class="sxs-lookup"><span data-stu-id="879b0-154">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}<code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}<code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="879b0-155">在上表中，`other-expr`描述否則未列在資料表中的運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-155">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="879b0-156">產生器類別不需要實作的所有方法和支援所有在上表中列出的翻譯。</span><span class="sxs-lookup"><span data-stu-id="879b0-156">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="879b0-157">無法使用該類型的計算運算式中不會實作這些建構。</span><span class="sxs-lookup"><span data-stu-id="879b0-157">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="879b0-158">例如，如果您不想要支援`use`計算運算式中的關鍵字，您可以省略的定義`Use`產生器類別中。</span><span class="sxs-lookup"><span data-stu-id="879b0-158">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="879b0-159">下列程式碼範例會顯示封裝計算為一系列的步驟可能會評估一次一個步驟的計算運算式。</span><span class="sxs-lookup"><span data-stu-id="879b0-159">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="879b0-160">A 差別等位型別， `OkOrException`，將運算式的錯誤狀態編碼成評估為止。</span><span class="sxs-lookup"><span data-stu-id="879b0-160">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="879b0-161">此程式碼示範數個典型的模式，您可以使用您的計算運算式，例如產生器方法的部分未定案實作中。</span><span class="sxs-lookup"><span data-stu-id="879b0-161">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="879b0-162">計算運算式具有基礎類型，則運算式會傳回。</span><span class="sxs-lookup"><span data-stu-id="879b0-162">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="879b0-163">代表運算的結果或可執行的延遲的計算基礎類型或它可能會提供方法來逐一查看集合的一些型別。</span><span class="sxs-lookup"><span data-stu-id="879b0-163">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="879b0-164">在上述範例中，為基礎型別**最終**。</span><span class="sxs-lookup"><span data-stu-id="879b0-164">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="879b0-165">基礎類型是循序項運算式，如<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="879b0-165">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="879b0-166">查詢運算式的基礎類型是<xref:System.Linq.IQueryable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="879b0-166">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="879b0-167">非同步工作流程的基礎類型是[ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。</span><span class="sxs-lookup"><span data-stu-id="879b0-167">For an asychronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="879b0-168">`Async`物件代表要執行，以計算結果的工作。</span><span class="sxs-lookup"><span data-stu-id="879b0-168">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="879b0-169">例如，您呼叫[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="879b0-169">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="879b0-170">自訂作業</span><span class="sxs-lookup"><span data-stu-id="879b0-170">Custom Operations</span></span>
<span data-ttu-id="879b0-171">您可以定義自訂計算運算式上的作業，並使用為計算運算式中運算子的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="879b0-171">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="879b0-172">例如，您可以在查詢運算式中包含查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="879b0-172">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="879b0-173">當您定義自訂的作業時，您必須定義結果和計算運算式中的方法。</span><span class="sxs-lookup"><span data-stu-id="879b0-173">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="879b0-174">若要定義自訂的作業，將其放在計算運算式產生器類別，然後套用[ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)。</span><span class="sxs-lookup"><span data-stu-id="879b0-174">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="879b0-175">這個屬性會接受字串做為引數是要用於自訂作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="879b0-175">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="879b0-176">此名稱來自於範圍的計算運算式的左大括號開頭。</span><span class="sxs-lookup"><span data-stu-id="879b0-176">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="879b0-177">因此，您不應該使用具有自訂作業相同的名稱，此區塊中的識別項。</span><span class="sxs-lookup"><span data-stu-id="879b0-177">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="879b0-178">例如，避免這類的識別項使用`all`或`last`查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="879b0-178">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

## <a name="see-also"></a><span data-ttu-id="879b0-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="879b0-179">See Also</span></span>
[<span data-ttu-id="879b0-180">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="879b0-180">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="879b0-181">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="879b0-181">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="879b0-182">序列</span><span class="sxs-lookup"><span data-stu-id="879b0-182">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="879b0-183">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="879b0-183">Query Expressions</span></span>](query-expressions.md)
