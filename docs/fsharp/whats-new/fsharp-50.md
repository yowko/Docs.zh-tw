---
title: 'F # 5.0 中的新功能-F # 指南'
description: '深入瞭解 F # 5.0 中可用的新功能。'
ms.date: 11/06/2020
ms.openlocfilehash: 29b5b110379dec476d7c0aa51540984acb25f26e
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098693"
---
# <a name="whats-new-in-f-50"></a>F # 5.0 的新功能

F # 5.0 在 F # 語言和 F# 互動中新增了幾項改進。 它是以 **.net 5** 發行。

您可以從 [.net 下載頁面](https://dotnet.microsoft.com/download)下載最新的 .net SDK。

## <a name="get-started"></a>開始使用

F # 5.0 適用于所有 .NET Core 散發套件和 Visual Studio 工具。 如需詳細資訊，請參閱 [F #](../get-started/index.md) 入門（英文）以深入瞭解。

## <a name="package-references-in-f-scripts"></a>F # 腳本中的套件參考

F # 5 以語法提供 F # 腳本中封裝參考的支援 `#r "nuget:..."` 。 例如，請考慮下列套件參考：

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

您也可以在套件名稱之後提供明確的版本，如下所示：

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

封裝參考支援具有原生相依性的套件，例如 ML.NET。

封裝參考也支援封裝參考相依的特殊需求的封裝 `.dll` 。 例如， [FParsec](https://www.nuget.org/packages/FParsec/) 套件用來要求使用者在 `FParsecCS.dll` F# 互動中參考之前，先手動確定其相依的參考 `FParsec.dll` 。 這已不再需要，您可以參考封裝，如下所示：

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

這項功能會實行 [F # 工具 RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md)。 如需封裝參考的詳細資訊，請參閱 [F# 互動](../tutorials/fsharp-interactive/index.md) 教學課程。

## <a name="string-interpolation"></a>字串插補

F # 插入字串與 c # 或 JavaScript 插入字串相當類似，因為它們可讓您在字串常值中的「漏洞」內撰寫程式碼。 以下是基本範例：

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

不過，F # 插入字串也允許型別插補（就像函式一樣 `sprintf` ），以強制插入內容內的運算式符合特定的型別。 它會使用相同的格式規範。

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

在上述輸入的插補範例中， `%s` 需要插補是型別 `string` ，而 `%d` 需要插補是 `integer` 。

此外，任何任意的 F # 運算式 (或運算式) 都可以放在插補內容的側邊。 您甚至可以撰寫更複雜的運算式，如下所示：

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

雖然我們不建議您這麼做，但我們不建議這麼做。

這項功能會實行 [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md)。

## <a name="support-for-nameof"></a>對 nameof 的支援

F # 5 支援 `nameof` 運算子，可解析其使用的符號，並在 F # 來源中產生其名稱。 這在各種情況下都很有用，例如記錄，並可保護您的記錄免于原始程式碼中的變更。

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

最後一行將會擲回例外狀況，且會在錯誤訊息中顯示「月份」。

您可以採用幾乎每個 F # 結構的名稱：

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

有三個最後的新增專案是運算子運作方式的變更：加入 `nameof<'type-parameter>` 泛型型別參數的表單，以及在模式比對運算式中做為模式使用的功能 `nameof` 。

採用運算子名稱可提供其來源字串。 如果您需要編譯的表單，請使用運算子的編譯名稱：

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

採用型別參數的名稱需要稍微不同的語法：

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

這與 `typeof<'T>` 和 `typedefof<'T>` 運算子類似。

F # 5 也加入了 `nameof` 可在運算式中使用的模式支援 `match` ：

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

上述程式碼使用 ' nameof '，而不是比對運算式中的字串常值。

這項功能會實行 [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md)。

## <a name="open-type-declarations"></a>開放式型別宣告

F # 5 也加入了對開放式型別宣告的支援。 開啟的型別宣告就像在 c # 中開啟靜態類別一樣，除了有些不同的語法和一些稍微不同的行為，以配合 F # 語義。

使用開放式型別宣告，您可以使用 `open` 任何類型來公開其內部的靜態內容。 此外，您可以 `open` F # 定義的等位和記錄來公開其內容。 例如，如果您的模組中有定義聯集，而且想要存取其案例，但不想要開啟整個模組，這會很有用。

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

與 c # 不同的是，當您 `open type` 在兩種類型上公開具有相同名稱的成員時，最後一個型別中的成員會 `open` 遮蔽另一個名稱。 這與已存在之遮蔽的 F # 語義一致。

這項功能會實行 [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md)。

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>內建資料類型的一致切割行為

配量內建 `FSharp.Core` 資料類型的行為 (陣列、清單、字串、2d 陣列、3d 陣列、4d 陣列) 在 F # 5 之前用來不一致。 某些邊緣案例行為擲回例外狀況，而有些則不會。 在 F # 5 中，所有內建類型現在都會針對無法產生的配量傳回空白配量：

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

這項功能會實行 [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md)。

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>固定-Fsharp.core 中3D 和4D 陣列的索引配量

F # 5.0 使用內建3D 和4D 陣列類型中具有固定索引的配量支援。

為了說明這一點，請考慮下列3D 陣列：

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

如果您想要從陣列解壓縮配量，該怎麼辦 `[| 4; 5 |]` ？ 這現在很簡單！

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

這項功能會實行 [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md)。

## <a name="f-quotations-improvements"></a>F # 引號的增強功能

F # 程式 [代碼引號](../language-reference/code-quotations.md) 現在能夠保留類型條件約束資訊。 請考慮下列範例：

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

函數所產生的條件約束 `inline` 會保留在程式碼引號中。 `negate`現在可以評估函式的引號形式。

這項功能會實行 [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md)。

## <a name="applicative-computation-expressions"></a>Applicative 計算運算式

目前使用的[計算運算式 (CEs) ](../language-reference/computation-expressions.md)來建立「內容計算」的模型，或以更多功能的程式設計易懂術語 monadic 計算。

F # 5 引進了 applicative CEs，可提供不同的計算模型。 Applicative CEs 允許更有效率的計算，前提是每個計算都是獨立的，且其結果會在結尾累積。 當計算彼此獨立時，也會完整可並行，讓 CE 作者可以撰寫更有效率的程式庫。 這項優點有一項限制，但不允許相依于先前計算值的計算。

下列範例顯示類型的基本 applicative CE `Result` 。

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

如果您是目前在其程式庫中公開 CEs 的程式庫作者，還有一些需要注意的其他考慮事項。

這項功能會實行 [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md)。

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a>介面可以在不同的泛型具現化中執行

您現在可以在不同的泛型具現化中執行相同的介面：

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

這項功能會實行 [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md)。

## <a name="default-interface-member-consumption"></a>預設介面成員耗用量

F # 5 可讓您使用預設實作為 [介面](../../csharp/tutorials/default-interface-methods-versions.md)。

請考慮以 c # 定義的介面，如下所示：

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

您可以使用 F # 來使用它來執行介面的任何標準方法：

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

這可讓您安全地利用以新式 c # 撰寫的 c # 程式碼和 .NET 元件（當它們希望使用者能夠使用預設的實值）時。

這項功能會實行 [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md)。

## <a name="simplified-interop-with-nullable-value-types"></a>使用可為 null 的實數值型別簡化 interop

[可為 null 的 (值) 類型](https://docs.microsoft.com/dotnet/api/system.nullable-1) (稱為可為 null 的型別，在過去) 已經由 F # 所支援，但是與它們進行互動是因為您在 `Nullable` `Nullable<SomeType>` 每次想要傳遞值時都必須建立或包裝函式。 現在， `Nullable<ThatValueType>` 如果目標型別相符，則編譯器會將實值型別隱含轉換成。 現在可以執行下列程式碼：

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

這項功能會實行 [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md)。

## <a name="preview-reverse-indexes"></a>預覽：反向索引

F # 5 也引進了允許反向索引的預覽。 語法是 `^idx`。 以下是您可以如何從清單結尾的元素1值：

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

您也可以為自己的類型定義反向索引。 若要這樣做，您必須執行下列方法：

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

以下是此類型的範例 `Span<'T>` ：

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

這項功能會實行 [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md)。

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>預覽：計算運算式中的自訂關鍵字多載

計算運算式是程式庫和架構作者的強大功能。 它們可讓您定義知名的成員，並形成您正在使用之網域的 DSL，以大幅提升元件的表達。

F # 5 新增了在計算運算式中多載自訂作業的預覽支援。 它允許撰寫和使用下列程式碼：

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

在這項變更之前，您可以撰寫 `InputBuilder` 型別，但是您無法使用它在範例中使用的方式。 因為可以使用多載、選擇性參數和現在的型別，所以一切都如同 `System.ParamArray` 預期般運作。

這項功能會實行 [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md)。
