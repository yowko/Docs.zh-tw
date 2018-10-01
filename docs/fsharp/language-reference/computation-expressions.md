---
title: 計算運算式 (F#)
description: '了解如何建立方便的語法，撰寫 F #，可以進行排序和合併使用控制流程建構和繫結中的計算。'
ms.date: 07/27/2018
ms.openlocfilehash: 148d1a661fb7630782c6dc48507a66e7bdc1d56b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459798"
---
# <a name="computation-expressions"></a>計算運算式

F # 中的計算運算式提供便利的語法來撰寫可以進行排序和合併使用控制流程建構和繫結的計算。 根據計算運算式的類型，它們可以視為 express monads、 monoids、 monad transformer 和 applicative 函式的方式。 不過，不同於其他語言 (例如*do 標記法*Haskell 中)，它們不會繫結至單一的抽象概念，並不依賴巨集或其他形式的 metaprogramming 完成方便且內容相關的語法。

## <a name="overview"></a>總覽

計算可以有許多形式。 計算的最常見形式是單一執行緒執行，也就是容易了解和修改。 不過，並非所有的形式是計算的單一執行緒執行一樣直接。 其中某些範例包括：

* 不具決定性的計算
* 非同步計算
* Effectful 計算
* 富有生產力的計算

更一般來說，有*即時線上*您必須執行的應用程式特定部分中的計算。 撰寫即時程式碼可能相當困難，因為很容易之外指定的內容，而不需要的抽象概念，讓您無法這樣的 「 洩漏 」 計算。 這些抽象概通常很難撰寫您自己，這就是為什麼 F # 提供一個通用的方法，可執行所謂**計算運算式**。

計算運算式提供統一的語法和抽象概念模型的即時線上計算的編碼方式。

每個計算運算式做為後盾*產生器*型別。 產生器型別會定義可供計算運算式的作業。 請參閱[建立新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中顯示如何建立自訂的計算運算式。

### <a name="syntax-overview"></a>語法概觀

所有的計算運算式具有下列格式：

```
builder-expr { cexper }
```

何處`builder-expr`是定義計算運算式產生器型別名稱和`cexper`是計算運算式的運算式主體。 比方說，`async`計算運算式程式碼可以看起來像這樣：

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

有可用的特殊的其他語法在計算運算式中，在上述範例所示。 下列運算式形式會使用計算運算式：

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

如果已定義在支援產生器類型，每個這些關鍵字，以及其他標準 F # 關鍵字所僅適用於計算運算式。 是唯一的例外`match!`，這是本身使用的語法捷徑`let!`後面模式比對的結果。

產生器型別是物件，定義方式結合，計算運算式的片段; 的特殊方法也就是它的方法來控制計算運算式的運作方式。 描述產生器類別的另一種方式是說，它可讓您自訂的許多 F # 建構，例如迴圈和繫結作業。

### `let!`

`let!`關鍵字的另一個計算運算式呼叫的結果繫結的名稱：

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

如果您繫結具有的計算運算式呼叫`let`，您不會計算運算式的結果。 相反地，您會有繫結的值*實現*呼叫該計算運算式。 使用`let!`繫結至結果。

`let!` 由定義`Bind(x, f)`產生器型別上的成員。

### `do!`

`do!`關鍵字是呼叫計算運算式，傳回`unit`-例如型別 (由`Zero`成員產生器):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

針對[非同步工作流程](asynchronous-workflows.md)，這個型別是`Async<unit>`。 如需其他計算運算式中，型別很可能是`CExpType<unit>`。

`do!` 由此`Bind(x, f)`成員產生器型別，其中`f`會產生`unit`。

### `yield`

`yield`關鍵字是從 計算運算式傳回值，以便它可以作為<xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

如同[產生 C# 關鍵字](../../csharp/language-reference/keywords/yield.md)，因為它會在逐一查看產生的計算運算式中的每個項目。

`yield` 由此`Yield(x)`成員產生器型別，其中`x`是要重新產生的項目。

### `yield!`

`yield!`關鍵字是簡維集合，從 計算運算式的值：

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

計算運算式評估時，由呼叫`yield!`將其項目產生後--逐一壓平合併結果。

`yield!` 由此`YieldFrom(x)`成員產生器型別，其中`x`是值的集合。

### `return`

`return`關鍵字包裝型別對應至 計算運算式中的值。 除了使用的計算運算式`yield`，它用來 「 完成 」 的計算運算式：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` 由此`Return(x)`成員產生器型別，其中`x`是要包裝的項目。

### `return!`

`return!`關鍵字發現計算運算式的值，並將結果包裝型別對應至 計算運算式中：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` 由此`ReturnFrom(x)`成員產生器型別，其中`x`是另一個計算運算式。

### `match!`

F # 從 4.5 開始，`match!`關鍵字可讓您將內嵌呼叫另一個計算運算式和模式比對其結果：

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

當呼叫的計算運算式`match!`，它將會了解像是呼叫的結果`let!`。 這通常用時呼叫的計算運算式結果的所在[選擇性](options.md)。

## <a name="built-in-computation-expressions"></a>內建的計算運算式

F # 核心程式庫會定義三個內建的計算運算式：[循序項運算式](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[查詢運算式](query-expressions.md)。

## <a name="creating-a-new-type-of-computation-expression"></a>建立新的計算運算式的類型

您可以建立產生器類別，並在類別上定義特定的特殊方法，以定義您自己的計算運算式的特性。 下表中所列，產生器類別可以選擇性地定義的方法。

下表描述可用於工作流程產生器類別的方法。

|**方法**|**典型的簽章**|**描述**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|針對呼叫`let!`和`do!`計算運算式中。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|包裝函式為計算運算式。|
|`Return`|`'T -> M<'T>`|針對呼叫`return`計算運算式中。|
|`ReturnFrom`|`M<'T> -> M<'T>`|針對呼叫`return!`計算運算式中。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|執行計算運算式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|呼叫在計算運算式中排序。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|針對呼叫`for...do`計算運算式中的運算式。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|針對呼叫`try...finally`計算運算式中的運算式。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|針對呼叫`try...with`計算運算式中的運算式。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|針對呼叫`use`計算運算式中的繫結。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|針對呼叫`while...do`計算運算式中的運算式。|
|`Yield`|`'T -> M<'T>`|針對呼叫`yield`計算運算式中的運算式。|
|`YieldFrom`|`M<'T> -> M<'T>`|針對呼叫`yield!`計算運算式中的運算式。|
|`Zero`|`unit -> M<'T>`|呼叫空`else`分支`if...then`計算運算式中的運算式。|

許多產生器類別中的方法使用，並傳回`M<'T>`建構，這通常是分開定義的類型特性的組合，計算種類，例如，`Async<'T>`非同步工作流程和`Seq<'T>`序列工作流程。 這些方法的簽章會啟用這些要結合並彼此巢狀，以便從一個建構傳回的工作流程物件可以傳遞至下一步。 剖析計算運算式時，編譯器會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一系列的巢狀函式呼叫。

巢狀的運算式是下列格式：

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上述程式碼來呼叫`Run`和`Delay`會省略所計算的運算式產生器類別中有未定義。 計算運算式，這裡表示為主體`{| cexpr |}`，轉譯成牽涉到的產生器類別方法的呼叫下表中所述的翻譯。 計算運算式`{| cexpr |}`會定義以遞迴方式，根據這些翻譯所在`expr`是 F # 運算式和`cexpr`是計算運算式。

|運算式|轉譯|
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
在上表中，`other-expr`告訴您，否則為未列在資料表的運算式。 產生器類別不必實作的所有方法，並支援所有在上表中列出的翻譯。 無法使用該類型的計算運算式中不會實作這些建構。 例如，如果您不想要支援`use`計算運算式中的關鍵字，您可以省略的定義`Use`產生器類別中。

下列程式碼範例會顯示封裝計算為一系列的步驟可評估一次的一個步驟的計算運算式。 差別等位型別， `OkOrException`，編碼錯誤狀態的運算式，評估為止。 此程式碼示範您可以使用您的計算運算式，例如產生器方法的一部分的未定案實作中的數種一般模式。

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

計算運算式具有基礎類型，則運算式會傳回。 計算的結果或可執行的延遲的計算，可能代表基礎類型，或者它可能提供逐一查看集合的某種類型的方法。 在上述範例中，基礎類型是**最終**。 序列運算式中，基礎類型是<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 查詢運算式的基礎類型是<xref:System.Linq.IQueryable?displayProperty=nameWithType>。 非同步工作流程的基礎類型是[ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。 `Async`物件代表要計算的結果執行的工作。 例如，您呼叫[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算並傳回結果。

## <a name="custom-operations"></a>自訂作業

您可以定義自訂的作業，在 計算運算式，並為計算運算式中運算子使用的自訂作業。 比方說，您可以在查詢運算式中包含的查詢運算子。 當您定義的自訂作業時，您必須定義在 Yield 和計算運算式中的方法。 若要定義自訂的作業，將它放在 計算運算式產生器類別，然後套用[ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)。 這個屬性會接受字串做為引數，也就是使用中的自訂作業的名稱。 此名稱來自進入範圍內的計算運算式的左大括號開頭。 因此，您不應該使用在這個區塊中有相同名稱的自訂作業的識別碼。 例如，避免識別項使用這類`all`或`last`查詢運算式中。

### <a name="extending-existing-builders-with-new-custom-operations"></a>擴充現有的產生器與新的自訂作業

如果您已經產生器類別，可以從擴充其自訂作業，此產生器的類別之外。 延伸模組必須在模組中宣告。 命名空間不能包含相同的檔案和相同的命名空間宣告群組定義類型的位置中的擴充成員除外。

下列範例示範的現有擴充`Microsoft.FSharp.Linq.QueryBuilder`類別。

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [非同步工作流程](asynchronous-workflows.md)
- [序列](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [查詢運算式](query-expressions.md)
