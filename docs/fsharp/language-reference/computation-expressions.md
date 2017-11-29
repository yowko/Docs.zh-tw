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
# <a name="computation-expressions"></a>計算運算式

F # 中的計算運算式提供方便的語法撰寫，可以排序，並使用控制流程建構和繫結結合在一起的計算。 它們可以用來提供方便的語法*monad*，可用來管理資料、 控制和功能的程式中的副作用的功能性程式設計功能。


## <a name="built-in-workflows"></a>內建工作流程
循序項運算式是計算運算式的範例是非同步工作流程和查詢運算式。 如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[查詢運算式](query-expressions.md)。

某些功能通用於循序項運算式與非同步工作流程，並說明計算運算式的基本語法：

```fsharp
builder-name { expression }
```

上述語法指定指定的運算式所指定類型的計算運算式*產生器名稱*。 計算運算式可以是內建的工作流程，例如`seq`或`async`，也可以是您定義的項目。 *產生器名稱*稱為一種特殊類型的執行個體的識別碼*產生器類型*。 產生器類型是定義管理的片段計算運算式的組合時，也就是程式碼的方式，控制如何執行運算式的特殊方法的類別類型。 另一種方式來描述產生器類別是說，它可讓您自訂許多 F # 建構，例如迴圈和繫結作業。

在計算運算式中，兩種形式可供某些常見的語言建構。 您可以使用叫用的 variant 建構 ！ （出問題） 後置詞特定關鍵字，例如`let!`， `do!`，依此類推。 這些特殊形式都會導致產生器類別來取代這些作業的一般內建行為中所定義的特定函式。 這些形式類似`yield!`形式`yield`循序項運算式中使用的關鍵字。 如需詳細資訊，請參閱[序列](sequences.md)。


## <a name="creating-a-new-type-of-computation-expression"></a>建立新的計算運算式的類型
您可以建立產生器類別，以及在類別上定義某些特殊的方法，以定義您自己的計算運算式的特性。 下表所列，產生器類別可以選擇性地定義的方法。

下表描述可用於工作流程產生器類別的方法。


|**方法**|**典型的簽章**|**說明**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|針對呼叫`let!`和`do!`計算運算式中。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|包裝函式將計算運算式。|
|`Return`|`'T -> M<'T>`|針對呼叫`return`計算運算式中。|
|`ReturnFrom`|`M<'T> -> M<'T>`|針對呼叫`return!`計算運算式中。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|執行計算運算式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|用於計算運算式中的順序呼叫。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|針對呼叫`for...do`計算運算式中的運算式。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|針對呼叫`try...finally`計算運算式中的運算式。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|針對呼叫`try...with`計算運算式中的運算式。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|針對呼叫`use`計算運算式中的繫結。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|針對呼叫`while...do`計算運算式中的運算式。|
|`Yield`|`'T -> M<'T>`|針對呼叫`yield`計算運算式中的運算式。|
|`YieldFrom`|`M<'T> -> M<'T>`|針對呼叫`yield!`計算運算式中的運算式。|
|`Zero`|`unit -> M<'T>`|呼叫空白`else`分支`if...then`計算運算式中的運算式。|
許多中產生器類別的方法使用，並傳回`M<'T>`建構，通常是分開定義的類型，表示特性的組合，計算種類，例如`Async<'T>`提供非同步工作流程和`Seq<'T>`序列工作流程。 這些方法的簽章會啟用它們要結合並使用彼此的巢狀以便從一個建構傳回的工作流程物件可以傳遞至下一步。 編譯器，當它會剖析為計算運算式，會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一系列的巢狀函式呼叫。

巢狀的運算式是下列格式：

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上述程式碼呼叫`Run`和`Delay`如果他們未定義的計算運算式產生器類別中會省略。 計算運算式，這裡表示為主體`{| cexpr |}`，會轉譯成涉及產生器類別之方法的呼叫中依下表中描述的翻譯。 計算運算式`{| cexpr |}`會根據這些翻譯定義的遞迴其中`expr`是 F # 運算式和`cexpr`是計算運算式。



|運算式|轉譯|
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
在上表中，`other-expr`描述否則未列在資料表中的運算式。 產生器類別不需要實作的所有方法和支援所有在上表中列出的翻譯。 無法使用該類型的計算運算式中不會實作這些建構。 例如，如果您不想要支援`use`計算運算式中的關鍵字，您可以省略的定義`Use`產生器類別中。

下列程式碼範例會顯示封裝計算為一系列的步驟可能會評估一次一個步驟的計算運算式。 A 差別等位型別， `OkOrException`，將運算式的錯誤狀態編碼成評估為止。 此程式碼示範數個典型的模式，您可以使用您的計算運算式，例如產生器方法的部分未定案實作中。

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

計算運算式具有基礎類型，則運算式會傳回。 代表運算的結果或可執行的延遲的計算基礎類型或它可能會提供方法來逐一查看集合的一些型別。 在上述範例中，為基礎型別**最終**。 基礎類型是循序項運算式，如<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 查詢運算式的基礎類型是<xref:System.Linq.IQueryable?displayProperty=nameWithType>。 非同步工作流程的基礎類型是[ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。 `Async`物件代表要執行，以計算結果的工作。 例如，您呼叫[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算並傳回結果。

## <a name="custom-operations"></a>自訂作業
您可以定義自訂計算運算式上的作業，並使用為計算運算式中運算子的自訂作業。 例如，您可以在查詢運算式中包含查詢運算子。 當您定義自訂的作業時，您必須定義結果和計算運算式中的方法。 若要定義自訂的作業，將其放在計算運算式產生器類別，然後套用[ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)。 這個屬性會接受字串做為引數是要用於自訂作業的名稱。 此名稱來自於範圍的計算運算式的左大括號開頭。 因此，您不應該使用具有自訂作業相同的名稱，此區塊中的識別項。 例如，避免這類的識別項使用`all`或`last`查詢運算式中。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[非同步工作流程](asynchronous-workflows.md)

[序列](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[查詢運算式](query-expressions.md)
