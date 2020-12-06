---
title: 計算運算式
description: '瞭解如何建立方便的語法，以 F # 撰寫可使用控制流程結構和系結來排序和結合的計算。'
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: a0a71533ea1bc87b75f028ad0d416326f627672a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739297"
---
# <a name="computation-expressions"></a>計算運算式

F # 中的計算運算式提供一個方便的語法，可用來撰寫可使用控制流程結構和系結來排序和結合的計算。 視計算運算式的種類而定，您可以將它們視為表示 monads、monoids、monad 轉換器和 applicative 函子的方式。 不過，不同于其他語言 (例如 Haskell) 中 *的標記法* ，它們並不會系結至單一抽象概念，也不會依賴宏或其他形式的元程式來完成方便且上下文相關的語法。

## <a name="overview"></a>概觀

計算可以採用許多形式。 最常見的計算形式是單一執行緒執行，這很容易理解和修改。 不過，並非所有形式的計算都像單一執行緒執行一樣簡單。 部分範例包括：

- 不具決定性的計算
- 非同步計算
- Effectful 計算
- 有生產力計算

一般來說，您必須在應用程式的某些部分中執行 *內容相關* 的計算。 撰寫內容相關的程式碼可能是一項挑戰，因為在沒有抽象的情況下，可以輕易地在指定的內容之外「流失」計算，以防止您這樣做。 這些抽象概念通常很難自行撰寫，這也是為什麼 F # 有一般化的方法，稱為 **計算運算式**。

計算運算式提供統一的語法和抽象模型，用於編碼內容相關計算。

每個計算運算式 *都是由產生器型別* 所支援。 產生器類型會定義可供計算運算式使用的作業。 請參閱 [建立新的計算運算式類型](computation-expressions.md#creating-a-new-type-of-computation-expression)，其會顯示如何建立自訂計算運算式。

### <a name="syntax-overview"></a>語法概觀

所有計算運算式的格式如下：

```fsharp
builder-expr { cexper }
```

其中 `builder-expr` 是定義計算運算式之產生器類型的名稱，而 `cexper` 則是計算運算式的運算式主體。 例如， `async` 計算運算式程式碼看起來會像這樣：

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

在計算運算式中有特殊的額外語法可用，如先前的範例所示。 下列運算式形式可以搭配計算運算式使用：

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

這些關鍵字和其他標準 F # 關鍵字只有在支援產生器型別中已定義時，才可在計算運算式中使用。 唯一的例外是 `match!` ，它本身就是可供使用的語法， `let!` 後面接著結果的模式比對。

產生器型別是一個物件，它會定義特殊方法來管理計算運算式片段的組合方式;也就是說，其方法會控制計算運算式的行為。 另一種描述 builder 類別的方式，就是假設它可讓您自訂許多 F # 結構的作業，例如迴圈和系結。

### `let!`

關鍵字會將呼叫的結果系結至 `let!` 另一個計算運算式的名稱：

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

如果您使用來系結計算運算式的呼叫 `let` ，將不會取得計算運算式的結果。 相反地，您會將未產生的呼叫值系結 *至該計算* 運算式。 使用系結 `let!` 至結果。

`let!` 由產生器 `Bind(x, f)` 類型上的成員定義。

### `do!`

`do!`關鍵字是用來呼叫計算運算式，該運算式會傳回類似型別的 `unit` (由產生器 `Zero`) 的成員定義：

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

針對 [非同步工作流程](asynchronous-workflows.md)，此類型為 `Async<unit>` 。 針對其他計算運算式，類型可能是 `CExpType<unit>` 。

`do!` 是由產生者 `Bind(x, f)` 類型上的成員所定義 `f` `unit` 。

### `yield`

`yield`關鍵字是用來從計算運算式傳回值，讓它可以作為 <xref:System.Collections.Generic.IEnumerable%601> ：

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

在大部分的情況下，呼叫端可以省略它。 最常見的省略方法 `yield` 是使用 `->` 運算子：

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

針對可能會產生許多不同值的更複雜運算式，而且可能有條件地省略關鍵字可以執行下列作業：

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

如同 [c # 中的 yield 關鍵字](../../csharp/language-reference/keywords/yield.md)，計算運算式中的每個專案都會在反覆運算時產生回來。

`yield` 由 `Yield(x)` 產生器型別的成員定義，其中 `x` 是要傳回的專案。

### `yield!`

`yield!`關鍵字是用來壓平合併計算運算式中的值集合：

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

printfn $"{squaresAndCubes}"  // Prints - 1; 4; 9; 1; 8; 27
```

進行評估時，所呼叫的計算運算式 `yield!` 會將其專案逐一產生，並將結果壓平合併。

`yield!` 由產生器 `YieldFrom(x)` 型別上的成員定義，其中 `x` 是值的集合。

不同于 `yield` ， `yield!` 必須明確指定。 其行為在計算運算式中不是隱含的。

### `return`

`return`關鍵字會在對應至計算運算式的型別中包裝一個值。 除了使用的計算運算式之外 `yield` ，它也用來「完成」計算運算式：

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` 是由產生器 `Return(x)` 型別上的成員所定義，其中 `x` 是要換行的專案。

### `return!`

`return!`關鍵字會知道計算運算式的值，並將結果包裝為對應于計算運算式的型別：

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` 由產生器 `ReturnFrom(x)` 型別上的成員定義，其中 `x` 是另一個計算運算式。

### `match!`

`match!`關鍵字可讓您內嵌對另一個計算運算式的呼叫，以及其結果的模式比對：

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

使用呼叫計算運算式時 `match!` ，它會瞭解呼叫的結果（例如） `let!` 。 這通常用於呼叫計算運算式，其中的結果是 [選擇性](options.md)的。

## <a name="built-in-computation-expressions"></a>內建計算運算式

F # 核心程式庫會定義三個內建的計算運算式： [順序運算式](sequences.md)、 [非同步工作流程](asynchronous-workflows.md)和 [查詢運算式](query-expressions.md)。

## <a name="creating-a-new-type-of-computation-expression"></a>建立新的計算運算式類型

您可以藉由建立產生器類別，並在類別上定義某些特殊方法，來定義您自己的計算運算式的特性。 Builder 類別可以選擇性地定義下表所列的方法。

下表說明可在工作流程產生器類別中使用的方法。

|**方法**|**一般簽章 (s)**|**描述**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|`let!` `do!` 在計算運算式中呼叫和。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|將計算運算式包裝為函數。|
|`Return`|`'T -> M<'T>`|`return`在計算運算式中呼叫。|
|`ReturnFrom`|`M<'T> -> M<'T>`|`return!`在計算運算式中呼叫。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|執行計算運算式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|在計算運算式中呼叫以進行排序。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|針對 `for...do` 計算運算式中的運算式呼叫。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|針對 `try...finally` 計算運算式中的運算式呼叫。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|針對 `try...with` 計算運算式中的運算式呼叫。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|在計算運算式中呼叫以進行系結 `use` 。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|針對 `while...do` 計算運算式中的運算式呼叫。|
|`Yield`|`'T -> M<'T>`|針對 `yield` 計算運算式中的運算式呼叫。|
|`YieldFrom`|`M<'T> -> M<'T>`|針對 `yield!` 計算運算式中的運算式呼叫。|
|`Zero`|`unit -> M<'T>`|`else` `if...then` 在計算運算式中針對運算式的空分支呼叫。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|指出計算運算式以 `Run` 引號形式傳遞至成員。 它會將計算的所有實例轉譯成引號。|

產生器類別中的許多方法都會使用並傳回 `M<'T>` 結構，而這通常是個別定義型別，可區分要合併的計算類型，例如， `Async<'T>` 針對非同步工作流程和 `Seq<'T>` 序列工作流程。 這些方法的簽章可讓它們彼此合併和互相合併，以便將從一個結構傳回的工作流程物件傳遞給下一個結構。 編譯器在剖析計算運算式時，會使用上表中的方法和計算運算式中的程式碼，將運算式轉換成一連串的嵌套函式呼叫。

嵌套運算式的格式如下：

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上述程式碼中， `Run` `Delay` 如果未在計算運算式產生器類別中定義，則會省略和的呼叫。 計算運算式的主體（在此表示為 `{| cexpr |}` ）會轉譯成包含產生器類別之方法的呼叫，並遵循下表所述的翻譯。 計算運算式 `{| cexpr |}` 會根據這些轉譯以遞迴方式定義，其中 `expr` 是 F # 運算式且 `cexpr` 為計算運算式。

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

在上表中， `other-expr` 描述資料表中未列出的運算式。 產生器類別不需要執行所有方法，並支援上表所列的所有翻譯。 在該類型的計算運算式中，未執行的這些結構無法使用。 例如，如果您不想要 `use` 在計算運算式中支援關鍵字，可以省略 `Use` builder 類別中的定義。

下列程式碼範例會示範將計算封裝成一系列步驟的計算運算式，這些步驟可以一次一個步驟來評估。 差異聯集型別，會將 `OkOrException` 目前所評估的運算式的錯誤狀態編碼。 這段程式碼示範一些您可以在計算運算式中使用的一般模式，例如一些產生器方法的未定案實作為。

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
        printfn $" x = %d{x}"
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

計算運算式具有運算式傳回的基礎類型。 基礎類型可能代表可執行檔計算結果或延遲計算，或可能提供逐一查看某些類型集合的方法。 在上述範例中， **最後** 是基礎類型。 若為序列運算式，基礎類型為 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 。 若為查詢運算式，基礎類型為 <xref:System.Linq.IQueryable?displayProperty=nameWithType> 。 如果是非同步工作流程，基礎類型為 [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) 。 `Async`物件代表要執行以計算結果的工作。 例如，您可以呼叫 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) 來執行計算，並傳回結果。

## <a name="custom-operations"></a>自訂作業

您可以在計算運算式上定義自訂作業，並使用自訂作業做為運算運算式中的運算子。 例如，您可以在查詢運算式中包含查詢運算子。 當您定義自訂作業時，您必須在計算運算式中定義 Yield 和方法。 若要定義自訂作業，請將它放在計算運算式的 builder 類別中，然後套用 [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) 。 這個屬性會採用字串做為引數，這是要在自訂作業中使用的名稱。 這個名稱會在計算運算式的左大括弧開頭的範圍內。 因此，您不應該使用與此區塊中的自訂作業同名的識別碼。 例如，請避免在 `all` 查詢運算式中使用識別碼，例如或 `last` 。

### <a name="extending-existing-builders-with-new-custom-operations"></a>以新的自訂作業擴充現有的產生器

如果您已經有 builder 類別，則可以從這個產生器類別外部延伸其自訂作業。 擴充功能必須在模組中宣告。 命名空間不能包含延伸成員，除了在相同檔案和定義類型的相同命名空間宣告群組中。

下列範例顯示現有類別的擴充 `FSharp.Linq.QueryBuilder` 。

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [非同步工作流程](asynchronous-workflows.md)
- [序列](sequences.md)
- [查詢運算式](query-expressions.md)
