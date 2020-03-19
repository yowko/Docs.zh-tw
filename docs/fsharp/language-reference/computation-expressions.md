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
# <a name="computation-expressions"></a>計算運算式

F# 中的計算運算式為編寫可以使用控制流構造和綁定進行排序和組合的計算提供了方便的語法。 根據計算運算式的類型，它們可以被認為是一種表達單體、單體、莫納變壓器和施用器的方法。 但是，與其他語言（如 Haskell 中的*do-符號*）不同，它們不綁定到單個抽象，並且不依賴宏或其他形式的元程式設計來完成方便且上下文相關的語法。

## <a name="overview"></a>概觀

計算可以有多種形式。 最常見的計算形式是單線程執行，易於理解和修改。 但是，並非所有形式的計算都像單線程執行那樣簡單明瞭。 部分範例包括：

- 非確定性計算
- 非同步計算
- 有效的計算
- 生成計算

更一般情況下，必須在應用程式的某些部分執行*上下文相關的*計算。 編寫上下文敏感代碼可能具有挑戰性，因為很容易在給定上下文之外"洩漏"計算，而無需抽象來防止您這樣做。 這些抽象通常具有挑戰性，可以自己編寫，這就是為什麼 F# 具有一種通用的方式來執行此操作，稱為**計算運算式**。

計算運算式為編碼上下文敏感的計算提供了統一的語法和抽象模型。

每個計算運算式都由*產生器*類型支援。 產生器類型定義可用於計算運算式的操作。 請參閱[創建新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中演示如何創建自訂計算運算式。

### <a name="syntax-overview"></a>語法概觀

所有計算運算式都具有以下形式：

```fsharp
builder-expr { cexper }
```

其中`builder-expr`是定義計算運算式的產生器類型的名稱，是`cexper`計算運算式的運算式正文。 例如，`async`計算運算式代碼可以如下所示：

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

計算運算式中提供了一個特殊的附加語法，如上例所示。 計算運算式可以實現以下運算式形式：

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

這些關鍵字和其他標準 F# 關鍵字僅在支援產生器類型中定義時才在計算運算式中可用。 唯一的例外是`match!`，它本身就是使用後跟模式匹配結果的`let!`語法糖。

產生器類型是定義控制計算運算式片段組合方式的特殊方法的物件;也就是說，它的方法控制計算運算式的表現。 描述產生器類的另一種方法是說它使您能夠自訂許多 F# 構造（如迴圈和綁定）的操作。

### `let!`

關鍵字`let!`將調用到另一個計算運算式的結果綁定到名稱：

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

如果使用 將調用綁定到 計算運算式`let`，則不會獲取計算運算式的結果。 相反，您將綁定到該計算運算式的*未實現*調用的值。 用於`let!`綁定到結果。

`let!`由產生器類型上`Bind(x, f)`的成員定義。

### `do!`

關鍵字`do!`用於調用返回`unit`類似類型（由產生器上`Zero`的成員定義）的計算運算式：

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

對於[非同步工作流](asynchronous-workflows.md)，此類型為`Async<unit>`。 對於其他計算運算式，類型可能是`CExpType<unit>`。

`do!`由產生器類型上`Bind(x, f)`的成員定義，其中`f`生成 。 `unit`

### `yield`

關鍵字`yield`用於從計算運算式傳回值，以便它可以用作<xref:System.Collections.Generic.IEnumerable%601>：

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

在大多數情況下，調用方可以省略它。 省略的最常見方法是`yield`使用`->`運算子：

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

對於可能產生許多不同的值的更複雜的運算式，也許有條件地省略關鍵字可以執行以下操作：

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

與[C# 中的屈服關鍵字](../../csharp/language-reference/keywords/yield.md)一樣，計算運算式中的每個元素在反覆運算時都會返回。

`yield`由產生器類型上`Yield(x)`的成員定義，其中`x`要回產的專案。

### `yield!`

關鍵字`yield!`用於拼平計算運算式中的值集合：

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

計算時，調用`yield!`的計算運算式將使其項逐個返回，從而使結果平展。

`yield!`由產生器類型上`YieldFrom(x)`的成員定義，其中`x`是值的集合。

與`yield``yield!`必須顯式指定不同。 它的行為在計算運算式中不隱式。

### `return`

關鍵字`return`在與計算運算式對應的類型中換行值。 除了使用`yield`的計算運算式外，它還用於"完成"計算運算式：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`由產生器類型上`Return(x)`的成員定義，要包裝的項`x`所在的位置。

### `return!`

關鍵字`return!`實現計算運算式的值，並換行導致與計算運算式對應的類型：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`由產生器類型上`ReturnFrom(x)`的成員定義，其中`x`是另一個計算運算式。

### `match!`

關鍵字`match!`允許您在結果上內聯對另一個計算運算式和模式匹配的調用：

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

使用`match!`調用 計算運算式時，它將實現調用的結果，如`let!`。 這通常用於調用計算運算式時，其中結果為[可選](options.md)。

## <a name="built-in-computation-expressions"></a>內置計算運算式

F# 核心庫定義了三個內置計算運算式：[序列運算式](sequences.md)、[非同步工作流](asynchronous-workflows.md)和[查詢運算式](query-expressions.md)。

## <a name="creating-a-new-type-of-computation-expression"></a>創建新類型的計算運算式

您可以通過創建產生器類並在類上定義某些特殊方法來定義自己的計算運算式的特徵。 產生器類可以選擇定義下表中列出的方法。

下表描述了可在工作流產生器類中使用的方法。

|**方法**|**典型簽名**|**描述**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|調用`let!`和`do!`在計算運算式中。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|將計算運算式包裝為函數。|
|`Return`|`'T -> M<'T>`|在計算`return`運算式中調用。|
|`ReturnFrom`|`M<'T> -> M<'T>`|在計算`return!`運算式中調用。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|執行計算運算式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|調用計算運算式中的排序。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|在計算`for...do`運算式中調用運算式。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|在計算`try...finally`運算式中調用運算式。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|在計算`try...with`運算式中調用運算式。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|在計算`use`運算式中調用綁定。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|在計算`while...do`運算式中調用運算式。|
|`Yield`|`'T -> M<'T>`|在計算`yield`運算式中調用運算式。|
|`YieldFrom`|`M<'T> -> M<'T>`|在計算`yield!`運算式中調用運算式。|
|`Zero`|`unit -> M<'T>`|調用計算運算式`else`中的空`if...then`運算式分支。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|指示計算運算式作為引號傳遞給`Run`成員。 它將計算的所有實例轉換為引號。|

產生器類中的許多方法使用並返回`M<'T>`構造，該構造通常是單獨定義的類型，用於描述要組合的計算類型，例如，`Async<'T>`對於非同步工作流和`Seq<'T>`序列工作流。 這些方法的簽名使它們能夠相互組合和嵌套，以便從一個構造返回的工作流物件可以傳遞給下一個構造。 編譯器在解析計算運算式時，使用上表中的方法和計算運算式中的代碼將運算式轉換為一系列嵌套函式呼叫。

嵌套運算式的格式如下：

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上述代碼中，如果計算運算式`Run`產生器`Delay`類中未定義對 和 的調用，則省略它們。 計算運算式的正文（此處表示為`{| cexpr |}`）通過下表中描述的翻譯轉換為涉及產生器類方法的調用。 計算運算式`{| cexpr |}`根據這些翻譯以遞迴方式定義，其中`expr`是 F# 運算式，是`cexpr`計算運算式。

|運算是|翻譯|
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

在上表中，`other-expr`描述表中未以其他方式列出的運算式。 產生器類不需要實現所有方法並支援上表中列出的所有翻譯。 未實現的構造在該類型的計算運算式中不可用。 例如，如果不想在計算運算式中支援`use`關鍵字，則可以省略產生器類中的定義。 `Use`

下面的代碼示例顯示了一個計算運算式，該運算式將計算封裝為一系列步驟，可以一次計算一個步驟。 受歧視的聯合類型`OkOrException`， 編碼運算式的錯誤狀態，以計算到目前為止。 此代碼演示了可在計算運算式中使用的幾個典型模式，例如某些產生器方法的樣板實現。

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

計算運算式具有基礎類型，運算式返回該類型。 基礎類型可能表示可以執行的計算結果或延遲計算，或者它可能提供一種通過某些類型的集合反覆運算的方法。 在前面的示例中，基礎類型**為 最終**。 對於序列運算式，基礎類型為<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 對於查詢運算式，基礎類型為<xref:System.Linq.IQueryable?displayProperty=nameWithType>。 對於非同步工作流，基礎類型為[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。 物件`Async`表示要執行的工作來計算結果。 例如，調用[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)以執行計算並返回結果。

## <a name="custom-operations"></a>自訂作業

可以在計算運算式上定義自訂操作，並在計算運算式中使用自訂操作作為運算子。 例如，可以在查詢運算式中包括查詢運算子。 定義自訂操作時，必須在計算運算式中定義"產量"和"For"方法。 要定義自訂操作，請將其放在計算運算式的產生器類中，然後應用 。 [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19) 此屬性將字串作為參數，它是要在自訂操作中使用的名稱。 此名稱在計算運算式的開頭大括弧開始時進入作用域。 因此，不應使用此塊中與自訂操作同名的識別碼。 例如，避免使用識別碼（如`all`或`last`在查詢運算式中）。

### <a name="extending-existing-builders-with-new-custom-operations"></a>使用新的自訂操作擴展現有產生器

如果您已經具有產生器類，則可以在此產生器類之外擴展其自訂操作。 必須在模組中聲明擴展。 命名空間不能包含擴展成員，但在同一檔和定義該類型的同一命名空間聲明組中除外。

下面的示例顯示了現有`Microsoft.FSharp.Linq.QueryBuilder`類的擴展。

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [非同步工作流程](asynchronous-workflows.md)
- [序列](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [查詢運算式](query-expressions.md)
