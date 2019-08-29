---
title: 計算運算式
description: 瞭解如何在中F#建立可使用控制流程結構和系結進行排序和合併的方便撰寫運算語法。
ms.date: 03/15/2019
ms.openlocfilehash: bca328a09ff61fb76d30960221ee3350fcc25fc1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106575"
---
# <a name="computation-expressions"></a>計算運算式

中F#的計算運算式提供便利的語法, 可讓您撰寫使用控制流程結構和系結進行排序和結合的計算。 視計算運算式的種類而定, 您可以將其視為表示 monad、monoids、monad 轉換器和 applicative 函子的方式。 不過, 不同于其他語言 (例如 Haskell 中的*標記法*), 它們不會系結至單一抽象概念, 而且不依賴宏或其他形式的元處理來完成方便且內容相關的語法。

## <a name="overview"></a>總覽

計算可能會採用許多形式。 最常見的計算形式是單一執行緒執行, 這很容易瞭解和修改。 不過, 並非所有形式的計算都是單一執行緒執行的簡單方式。 其中某些範例包括：

- 不具決定性的計算
- 非同步計算
- Effectful 計算
- 有生產力計算

一般來說, 您必須在應用程式的某些部分中執行*內容相關*的計算。 撰寫與內容相關的程式碼可能很有挑戰性, 因為在沒有抽象概念的情況下, 您可以輕鬆地在指定的內容外部「流失」計算, 以避免發生這種情況。 這些抽象概念通常是很難撰寫的, 這也是F#為什麼有一般化的方法, 稱為**計算運算式**。

計算運算式提供統一的語法和抽象概念, 以編碼內容相關的計算。

每個計算運算式都是由產生器型別支援。 產生器型別會定義可用於計算運算式的作業。 請參閱[建立新類型的計算運算式](computation-expressions.md#creating-a-new-type-of-computation-expression), 其中會顯示如何建立自訂計算運算式。

### <a name="syntax-overview"></a>語法總覽

所有計算運算式的形式如下:

```
builder-expr { cexper }
```

其中`builder-expr` , 是定義計算運算式的產生器型別名稱, 而`cexper`是計算運算式的運算式主體。 例如, `async`計算運算式程式碼看起來會像這樣:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

計算運算式中有特殊的額外語法可用, 如先前範例所示。 下列運算式形式可以搭配計算運算式使用:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

這些關鍵字和其他標準F#關鍵字僅適用于計算運算式 (如果已在支援產生器型別中定義)。 唯一的例外是`match!`, 這本身就是語法, 可供`let!`使用, 後面接著結果的模式比對。

產生器型別是一個物件, 它會定義特殊方法來管理計算運算式片段的結合方式;也就是說, 它的方法會控制計算運算式的行為。 描述 builder 類別的另一種方式, 就是讓您自訂許多F#結構的作業, 例如迴圈和系結。

### `let!`

`let!`關鍵字會將另一個計算運算式的呼叫結果系結至名稱:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

如果您使用`let`來系結計算運算式的呼叫, 則不會取得計算運算式的結果。 相反地, 您會將無法使用的呼叫值系結至該計算運算式。 使用`let!`系結至結果。

`let!`由產生器型`Bind(x, f)`別上的成員定義。

### `do!`

關鍵字是用來呼叫會傳回類似類型的計算`unit`運算式 (由產生器上的`Zero`成員定義): `do!`

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

針對[非同步工作流程](asynchronous-workflows.md), 此類型為`Async<unit>`。 對於其他計算運算式, 類型可能`CExpType<unit>`是。

`do!`是由產生器`Bind(x, f)`型別上的成員所定義`f` , 其中`unit`會產生。

### `yield`

關鍵字是用來從計算運算式傳回值, 讓它可以當做來使用<xref:System.Collections.Generic.IEnumerable%601>: `yield`

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

如同[ C#中的 yield 關鍵字](../../csharp/language-reference/keywords/yield.md), 計算運算式中的每個專案都會在反覆運算時傳回。

`yield`是由`Yield(x)`產生器型別上的成員所定義`x` , 其中是要傳回的專案。

### `yield!`

`yield!`關鍵字是用來從計算運算式簡維值的集合:

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

評估時, 所呼叫`yield!`的計算運算式會將其專案逐一傳回, 並將結果簡維。

`yield!`是由產生器`YieldFrom(x)`型別上的成員所定義`x` , 其中是值的集合。

### `return`

`return`關鍵字會包裝對應于計算運算式之類型中的值。 除了使用`yield`的計算運算式之外, 它還可用來「完成」計算運算式:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`是由`Return(x)`產生器型別上的成員所定義`x` , 其中是要包裝的專案。

### `return!`

`return!`關鍵字會發現計算運算式的值, 並將結果包裝為對應于計算運算式的類型:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`是由產生器`ReturnFrom(x)`型別上的成員所定義`x` , 其中是另一個計算運算式。

### `match!`

從F# 4.5 開始, `match!`關鍵字可讓您內嵌對另一個計算運算式的呼叫, 並對其結果進行模式比對:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

使用`match!`呼叫計算運算式時, 它會實現呼叫的結果, 例如`let!`。 這通常是在呼叫計算運算式 (其中的結果為[選擇性](options.md)) 時使用。

## <a name="built-in-computation-expressions"></a>內建計算運算式

F#核心程式庫會定義三個內建計算運算式:[順序運算式](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[查詢運算式](query-expressions.md)。

## <a name="creating-a-new-type-of-computation-expression"></a>建立新類型的計算運算式

您可以藉由建立產生器類別並在類別上定義某些特殊方法, 來定義自己的計算運算式的特性。 Builder 類別可以選擇性地定義下表所列的方法。

下表描述可在工作流程產生器類別中使用的方法。

|**方法**|**一般簽章**|**描述**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|在計算`let!`運算式`do!`中針對和呼叫。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|將計算運算式包裝為函數。|
|`Return`|`'T -> M<'T>`|在計算`return`運算式中針對進行呼叫。|
|`ReturnFrom`|`M<'T> -> M<'T>`|在計算`return!`運算式中針對進行呼叫。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|執行計算運算式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|呼叫以在計算運算式中進行排序。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|針對計算`for...do`運算式中的運算式呼叫。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|針對計算`try...finally`運算式中的運算式呼叫。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|針對計算`try...with`運算式中的運算式呼叫。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|在計算`use`運算式中呼叫以進行系結。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|針對計算`while...do`運算式中的運算式呼叫。|
|`Yield`|`'T -> M<'T>`|針對計算`yield`運算式中的運算式呼叫。|
|`YieldFrom`|`M<'T> -> M<'T>`|針對計算`yield!`運算式中的運算式呼叫。|
|`Zero`|`unit -> M<'T>`|在計算運算式`else`中針對`if...then`運算式的空分支呼叫。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|指出計算運算式會以引號的形式傳遞`Run`給成員。 它會將計算的所有實例轉譯為引號。|

產生器類別中的許多方法都會使用並`M<'T>`傳回結構, 這通常是個別定義的型別, 以表示要合併的運算種類, 例如, `Async<'T>`針對非同步工作流程和`Seq<'T>`適用于序列工作流程。 這些方法的簽章可讓它們彼此結合並加以合併, 讓從一個結構傳回的工作流程物件可以傳遞至下一個。 編譯器在剖析計算運算式時, 會使用上表中的方法和計算運算式中的程式碼, 將運算式轉換成一系列的嵌套函式呼叫。

此嵌套運算式的格式如下:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上述程式碼中, 如果不`Run`是`Delay`在計算運算式產生器類別中定義, 則會省略和的呼叫。 計算運算式的主體 (此處所表示`{| cexpr |}`的) 會轉譯為包含 builder 類別之方法的呼叫, 其方式如下表中所述。 計算運算式`{| cexpr |}`會根據這些翻譯以遞迴方式定義, `expr`其中是F#運算式, `cexpr`而是計算運算式。

|運算式|轉譯|
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

在上表中, `other-expr`描述資料表中未列出的運算式。 產生器類別不需要執行所有方法, 並且支援上表中所列的所有翻譯。 該類型的計算運算式無法使用未實作為的結構。 例如, 如果您不想要在計算運算式中`use`支援關鍵字, 可以`Use`在您的 builder 類別中省略的定義。

下列程式碼範例顯示的計算運算式會將計算封裝成一系列步驟, 一次可以評估一個步驟。 區分聯集類型`OkOrException`, 會編碼到目前為止所評估之運算式的錯誤狀態。 這段程式碼會示範幾個您可以在計算運算式中使用的一般模式, 例如一些產生器方法的樣板化。

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

計算運算式具有基礎類型, 此運算式會傳回。 基礎類型可能代表可執行檔計算結果或延遲計算, 或可提供方法來逐一查看某種類型的集合。 在上述範例中, 基礎類型**最後**是。 若為序列運算式, 基礎類型為<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若為查詢運算式, 基礎類型為<xref:System.Linq.IQueryable?displayProperty=nameWithType>。 針對非同步工作流程, 基礎類型為[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。 `Async`物件代表要執行以計算結果的工作。 例如, 您呼叫[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行計算, 並傳回結果。

## <a name="custom-operations"></a>自訂作業

您可以在計算運算式上定義自訂運算, 並使用自訂作業作為計算運算式中的運算子。 例如, 您可以在查詢運算式中包含查詢運算子。 當您定義自訂作業時, 您必須在計算運算式中定義 Yield 和 For 方法。 若要定義自訂作業, 請將它放在計算運算式的產生器類別中, 然後[`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)套用。 這個屬性會採用字串做為引數, 這是要在自訂作業中使用的名稱。 在計算運算式的左大括弧開頭, 此名稱會進入範圍內。 因此, 您不應該使用與此區塊中的自訂作業同名的識別碼。 例如, 請避免在查詢運算式中使用識別碼`all` , `last`例如或。

### <a name="extending-existing-builders-with-new-custom-operations"></a>以新的自訂作業擴充現有的產生器

如果您已經有 builder 類別, 則可以從這個產生器類別的外部延伸其自訂作業。 擴充功能必須在模組中宣告。 命名空間不能包含延伸成員, 除非在相同檔案和定義類型的相同命名空間宣告群組中。

下列範例會顯示現有`Microsoft.FSharp.Linq.QueryBuilder`類別的延伸。

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
