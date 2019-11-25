---
title: F# 程式碼格式方針
description: 瞭解格式化F#程式碼的指導方針。
ms.date: 11/04/2019
ms.openlocfilehash: 895c8211731b47bd4c59d762d5806cfc1bfe232d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089310"
---
# <a name="f-code-formatting-guidelines"></a>F# 程式碼格式方針

本文提供指導方針，說明如何格式化您的程式碼， F#讓您的程式碼：

* 一般視為更清晰
* 符合 Visual Studio 和其他編輯器中格式化工具所套用的慣例
* 類似于線上的其他程式碼

這些指導方針是[以F# ](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [Anh-ahn-dung Phan](https://github.com/dungpa)格式化慣例的完整指南為基礎。

## <a name="general-rules-for-indentation"></a>縮排的一般規則

F#預設會使用顯著的空白字元。 下列指導方針的目的是要提供如何操控這項挑戰的指引。

### <a name="using-spaces"></a>使用空格

需要縮排時，您必須使用空格，而不是定位字元。 至少需要一個空格。 您的組織可以建立編碼標準，以指定要用於縮排的空格數目;在縮排發生的每個層級，通常會有兩個、三個或四個空格的縮排。

**我們建議每個縮排有4個空格。**

話雖如此，程式的縮排就是一項主觀上的問題。 變化良好，但您應該遵循的第一個規則是*縮排的一致性*。 選擇一般接受的縮排樣式，並在整個程式碼基底中有系統地使用它。

## <a name="formatting-white-space"></a>格式化空白字元

F#是區分空白字元。 雖然來自空白字元的大部分語法都是由適當的縮排所涵蓋，但還有一些其他事項需要考慮。

### <a name="formatting-operators-in-arithmetic-expressions"></a>在算術運算式中格式化運算子

一律在二元算術運算式前後使用空白字元：

```fsharp
let subtractThenAdd x = x - 1 + 3
```

一元 `-` 運算子應一律具有立即否定的值，如下所示：

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

在 `-` 運算子之後加入空白字元，可能會對其他人造成混淆。

總而言之，一定要：

* 以空白字元括住二元運算子
* 一元運算子後面絕對不加尾端空白字元

二元算術運算子指導方針特別重要。 無法將二進位 `-` 運算子括住，並結合特定的格式化選項時，可能會導致將它解釋為一元 `-`。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>以空白字元括住自訂運算子定義

一律使用空白字元來括住運算子定義：

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

對於以 `*` 開頭且具有多個字元的自訂運算子，您需要在定義的開頭加上空白字元，以避免編譯器不明確。 因此，我們建議您只使用單一空白字元來括住所有運算子的定義。

### <a name="surround-function-parameter-arrows-with-white-space"></a>以空白字元括住函數參數箭號

定義函式的簽章時，請使用 `->` 符號前後的空白字元：

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>以空白字元括住函數引數

定義函式時，請在每個引數前後使用空白字元。

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a>針對非常長的成員定義，將參數放在新的一行上

如果您有很長的成員定義，請將參數放在新行上，並將其縮排到一個範圍內。

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

這也適用于函式：

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>類型注釋

#### <a name="right-pad-function-argument-type-annotations"></a>右面板函數引數類型注釋

定義具有類型注釋的引數時，請在 `:` 符號後面使用空白字元：

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>以空白字元括住傳回類型注釋

在 let 系結函式或實值型別注釋中（函數的大小寫），使用 `:` 符號前後的空白字元：

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>格式化空白行

* 以兩個空白行分隔最上層函式和類別定義。
* 類別內的方法定義會以一行分隔。
* 可能會使用額外的空白行（謹慎）來分隔相關函式的群組。 在一堆相關的囉（例如，一組虛擬的執行）之間，可能會省略空白行。
* 請謹慎使用函式中的空白行來表示邏輯區段。

## <a name="formatting-comments"></a>格式化批註

通常偏好透過 ML 樣式的區塊批註使用多個雙斜線批註。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

內嵌批註應為第一個字母大寫。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>命名規範

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>針對類別系結、運算式系結和模式系結值和函數使用 camelCase

對於系結為區域變數F#的所有名稱，或在模式比對和函式定義中使用 camelCase，這是常見且已接受的樣式。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

類別中的本機系結函數也應該使用 camelCase。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>針對模組系結的公用函式使用 camelCase

當模組系結函式是公用 API 的一部分時，它應該使用 camelCase：

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>將 camelCase 用於內部和私用模組系結的值和函數

將 camelCase 用於私用模組系結的值，包括下列各項：

* 腳本中的特定函式

* 組成模組或類型內部執行的值

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>針對參數使用 camelCase

所有參數都應該根據 .NET 命名慣例來使用 camelCase。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>使用模組的 PascalCase

所有模組（最上層、內部、私用、嵌套）都應該使用 PascalCase。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>針對類型宣告、成員和標籤使用 PascalCase

類別、介面、結構、列舉、委派、記錄和區分等位都應該使用 PascalCase 來命名。 記錄和區分等位的類型和標籤中的成員也應該使用 PascalCase。

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>將 PascalCase 用於 .NET 的內部結構

命名空間、例外狀況、事件和專案/`.dll` 名稱也應該使用 PascalCase。 這不僅讓其他 .NET 語言的耗用量更自然地取用者，也會與您可能會遇到的 .NET 命名慣例保持一致。

### <a name="avoid-underscores-in-names"></a>避免在名稱中有底線

在過去， F#某些程式庫在名稱中使用了底線。 不過，這已不再被廣泛接受，部分是因為它與 .NET 命名慣例衝突。 話雖如此， F#有些程式設計人員會大量使用底線，部分基於歷史原因，而容錯與尊重則很重要。 不過，請注意，樣式通常是由其他可選擇是否要使用它的人所不喜歡的。

部分例外狀況包括與原生元件互通，其中底線很常見。

### <a name="use-standard-f-operators"></a>使用標準F#運算子

下列運算子是在F#標準程式庫中定義，而且應該使用，而不是定義對等專案。 建議使用這些運算子，因為它可能會讓程式碼更容易閱讀和慣用。 具有 OCaml 或其他功能性程式設計語言背景的開發人員，可能會習慣不同的慣用語。 下列清單摘要說明建議F#的運算子。

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>在喜好設定中使用泛型（`Foo<T>`）前置詞語法（`T Foo`）

F#繼承命名泛型型別的後置 ML 樣式（例如，`int list`）以及前置詞 .NET 樣式（例如，`list<int>`）。 偏好使用 .NET 樣式，但五個特定類型除外：

1. 若F#為清單，請使用後置形式： `int list`，而不是 `list<int>`。
2. 針對F#選項，請使用後置形式： `int option`，而不是 `option<int>`。
3. 對於F#值選項，請使用後置形式： `int voption`，而不是 `voption<int>`。
4. 若F#為數組，請使用語法名稱 `int[]`，而不是 `int array` 或 `array<int>`。
5. 如需參考資料格，請使用 `int ref`，而不是 `ref<int>` 或 `Ref<int>`。

若為所有其他類型，請使用前置詞形式。

## <a name="formatting-tuples"></a>格式化元組

元組具現化應以括弧括住，而且內的分隔逗號後面應該接著一個空格，例如： `(1, 2)`、`(x, y, z)`。

在元組的模式比對中，通常會接受省略括弧：

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

如果元組是函式的傳回值，通常也會被接受省略括弧：

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

總而言之，偏好以括弧括住的元組具現化，但當使用元組進行模式比對或傳回值時，會將它視為可避免括弧的問題。

## <a name="formatting-discriminated-union-declarations"></a>格式化區分聯集宣告

將類型定義中的 `|` 縮排為4個空格：

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>格式化區分等位

分割成多行的具現化區分等位，應為包含的資料提供具有縮排的新範圍：

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

右括弧也可以在新行上：

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>格式化記錄宣告

將類型定義中的 `{` 縮排4個空格，並在同一行上啟動欄位清單：

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

如果您要在記錄上宣告介面執行或成員，最好將開頭標記放在新行上，並在新行上進行結束記號：

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>格式化記錄

短記錄可以用一行撰寫：

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

較長的記錄應該使用新的標籤行：

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

將開啟的 token 放在新行上，將內容索引標籤在一個範圍內，而在新行上的結束記號則比較適合下列情況：

* 以不同的縮排範圍在程式碼中移動記錄
* 將它們輸送至函式

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

List 和 array 元素也適用相同的規則。

## <a name="formatting-copy-and-update-record-expressions"></a>格式化複製和更新記錄運算式

複製和更新記錄運算式仍是一筆記錄，因此適用類似的指導方針。

簡短運算式可以放在一行中：

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

較長的運算式應該使用新的行：

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

如同記錄指導方針，您可能會想要為大括弧專用不同的行，並使用運算式將一個範圍向右縮排。 請注意，在某些特殊情況下，例如以不含括弧的選擇性包裝值，您可能需要在一行上保留一個大括弧：

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>格式化清單和陣列

撰寫 `::` 運算子前後有空格的 `x :: l` （`::` 是中置運算子，因此以空格括住）。

在單一行上宣告的清單和陣列，在左括弧後面和右括弧前面應該有一個空格：

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

在兩個不同的大括弧運算子之間一律使用至少一個空格。 例如，在 `[` 和 `{`之間保留一個空格。

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

相同的指導方針適用于元組的清單或陣列。

分割成多行的清單和陣列會遵循類似記錄的規則：

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

就像記錄一樣，在自己的行上宣告開頭和結尾括弧，會讓移動程式碼變得更容易。

以程式設計方式產生陣列和清單時，建議您在永遠產生值時，使用 `->` 而不是 `do ... yield`：

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

較舊版本的F#語言需要在可能有條件地產生資料的情況下指定 `yield`，或者可能會有連續的運算式進行評估。 除非您必須使用較舊F#的語言版本進行編譯，否則偏好省略這些 `yield` 關鍵字：

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

在某些情況下，`do...yield` 可能有助於閱讀。 不過，您應該將這些案例納入主觀。

## <a name="formatting-if-expressions"></a>設定運算式時的格式

條件的縮排取決於組成它們的運算式大小。 如果 `cond`、`e1` 和 `e2` 是簡短的，只要將它們寫在一行就行了：

```fsharp
if cond then e1 else e2
```

如果 `cond`，`e1` 或 `e2` 會較長，但不是多行：

```fsharp
if cond
then e1
else e2
```

如果有任何運算式是多行：

```fsharp
if cond then
    e1
else
    e2
```

具有 `elif` 和 `else` 的多個條件會在與 `if`相同的範圍內縮排：

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>模式比對結構

針對相符的每個子句使用 `|`，但不包含縮排。 如果運算式是 short，則如果每個子運算式也很簡單，您可以考慮使用單一行。

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

如果模式比對箭頭右邊的運算式太大，請將其移至下一行，從 `match`/`|`縮排一個步驟。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

匿名函式的模式比對（從 `function`開始）通常不應該縮排太遠。 例如，縮排一個範圍，如下所示：

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

`let` 或 `let rec` 所定義之函式中的模式比對應該在開始 `let`之後縮排4個空格，即使使用 `function` 關鍵字也一樣：

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

我們不建議對齊箭號。

## <a name="formatting-trywith-expressions"></a>格式化 try/with 運算式

例外狀況類型的模式比對應該在與 `with`相同的層級上縮排。

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>格式化函數參數應用程式

一般而言，大部分的函式參數應用程式都是在同一行上完成。

如果您想要將參數套用至新行上的函式，請依一個範圍來縮排它們。

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

相同的指導方針適用于 lambda 運算式做為函式引數。 如果 lambda 運算式的主體，主體可以有另一行，並以一個範圍縮排

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

不過，如果 lambda 運算式的主體超過一行，請考慮將它分解成不同的函式，而不是將多行結構套用為函式的單一引數。

### <a name="formatting-infix-operators"></a>格式化中綴運算子

以空格分隔運算子。 此規則的例外狀況是 `!` 和 `.` 運算子。

中綴運算式可以在相同的資料行上進行組合：

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>格式化管線運算子

管線 `|>` 運算子應該放在其操作所在的運算式之下。

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>格式化模組

本機模組中的程式碼必須相對於模組進行縮排，但最上層模組中的程式碼不應該縮排。 命名空間元素不必縮排。

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>格式化物件運算式和介面

物件運算式和介面的對齊方式應該與在4個空格之後縮排 `member`。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>格式化運算式中的空白字元

避免運算式中多餘的F#空白字元。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

具名引數也不應具有 `=`周圍的空間：

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>格式化屬性

[屬性](../language-reference/attributes.md)會放在結構的上方：

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>格式化參數上的屬性

屬性也可以放在參數上。 在此情況下，請將它放在與參數相同的行上，並在名稱之前：

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>格式化多個屬性

當多個屬性套用至不是參數的結構時，應該將它們放置在每一行有一個屬性：

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

套用至參數時，它們必須位於同一行，並以 `;` 分隔符號分隔。

## <a name="formatting-literals"></a>格式化常值

使用 `Literal` 屬性的常值應該將屬性放在它自己的行上，並使用 PascalCase 命名： [ F# ](../language-reference/literals.md)

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

避免將屬性放在與值相同的行上。
