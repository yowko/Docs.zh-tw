---
title: F# 程式碼格式方針
description: '瞭解格式化 F # 程式碼的指導方針。'
ms.date: 11/04/2019
ms.openlocfilehash: fe8da6070e1c92bb5205e9cb408b8ac75372b061
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558305"
---
# <a name="f-code-formatting-guidelines"></a>F# 程式碼格式方針

本文提供如何格式化程式碼的指導方針，讓您的 F # 程式碼為：

* 更清晰
* 根據 Visual Studio 和其他編輯器中格式化工具所套用的慣例
* 類似于線上的其他程式碼

這些指導方針是根據[Anh->ahn-dung (英文 phan) ](https://github.com/dungpa)的[F # 格式慣例的完整指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)。

## <a name="general-rules-for-indentation"></a>縮排的一般規則

F # 預設會使用顯著的空白字元。 下列指導方針旨在提供有關如何操控這項可能強加的一些挑戰的指引。

### <a name="using-spaces"></a>使用空格

需要縮排時，您必須使用空格，而不是索引標籤。 至少需要一個空格。 您的組織可以建立編碼標準，以指定要用於縮排的空間數目;一般情況下，會在每個層級上有兩個、三個或四個空格的縮排。

**我們建議每個縮排有四個空格。**

也就是說，程式的縮排是一項主觀的考慮。 變化是正常的，但您應該遵循的第一個規則是 *縮排的一致性*。 選擇一般接受的縮排樣式，並在整個程式碼基底中有系統地使用。

## <a name="formatting-white-space"></a>將空白字元格式化

F # 是區分泛空白字元。 雖然泛空白字元的大部分語法都是由適當的縮排所涵蓋，但還有其他一些需要考慮的事項。

### <a name="formatting-operators-in-arithmetic-expressions"></a>算術運算式中的格式化運算子

一律在二元算術運算式周圍使用空白字元：

```fsharp
let subtractThenAdd x = x - 1 + 3
```

一元 `-` 運算子應該一律緊接在其所否定的值之後：

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

在操作員之後加入空白字元 `-` 可能會讓其他人混淆。

總而言之，一定要：

* 以空白字元括住二元運算子
* 一元運算子之後永遠沒有尾端空白字元

二元算術運算子的指導方針特別重要。 若無法圍住二元 `-` 運算子，與某些格式化選項結合時，可能會導致將它解釋為一元 `-` 。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>以空白字元括住自訂運算子定義

一律使用空白字元來圍繞運算子定義：

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

若為任何以和為開頭 `*` 且包含多個字元的自訂運算子，您需要在定義的開頭加上空白字元，以避免編譯器的混淆。 基於這個原因，我們建議您只使用單一空白字元來括住所有運算子的定義。

### <a name="surround-function-parameter-arrows-with-white-space"></a>以空白字元括住函式參數箭號

定義函式的簽章時，請使用空格括住 `->` 符號：

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>以空白字元括住函式引數

定義函式時，請在每個引數前後使用空白字元。

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a>將參數放置在新的一行上以進行長定義

如果您有非常長的函式定義，請將參數放在新行上，然後縮排它們，以符合後續參數的縮排層級。

```fsharp
module M =
    let LongFunctionWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        =
        // ... the body of the method follows
```

這也適用于使用元組的成員、函式和參數：

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method

type TC(aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

如果參數是 currified，或有明確的傳回型別批註，最好將 `=` 字元放在新行上：

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                            : AReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                =
        // ... the body of the method
```

這是避免太長的行 (的方法。如果傳回類型可能具有長名稱) ，而且在新增參數時有較少的行損毀。

### <a name="type-annotations"></a>類型注釋

#### <a name="right-pad-function-argument-type-annotations"></a>右邊的函式引數類型注釋

在定義具有類型注釋的引數時，請使用符號後面的空白字元 `:` ：

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>以空白字元括住傳回型別注釋

在 let 系結函式或實數值型別注釋中，如果函式) 的情況下 (傳回型別，請使用符號前後的空白字元 `:` ：

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

* 以兩個空白行分隔最上層函數和類別定義。
* 類別內的方法定義會以單一空白行分隔。
* 額外的空白行可 (謹慎地使用) 來分隔相關函式的群組。 您可以在一堆相關的囉 (之間省略空白行，例如，一組虛擬實) 。
* 請謹慎使用函式中的空白行，以表示邏輯區段。

## <a name="formatting-comments"></a>格式化批註

通常會優先使用多個雙斜線批註，而不是 ML 樣式的區塊批註。

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

這是常見且接受的 F # 樣式，可針對系結為區域變數或模式比對和函式定義中的所有名稱使用 camelCase。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

類別中的本機系結函式也應使用 camelCase。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>針對模組系結公用函式使用 camelCase

當模組系結函式是公用 API 的一部分時，它應該使用 camelCase：

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>針對內部和私用模組系結值和函式使用 camelCase

將 camelCase 用於私用模組系結的值，包括下列各項：

* 腳本中的特定函數

* 組成模組或型別內部執行的值

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>針對參數使用 camelCase

所有參數都應該根據 .NET 命名慣例使用 camelCase。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>針對模組使用 PascalCase

 (頂層、內部、私用、嵌套) 的所有模組都應該使用 PascalCase。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>針對類型宣告、成員和標籤使用 PascalCase

類別、介面、結構、列舉、委派、記錄和區分等位都應該以 PascalCase 命名。 記錄和差異聯集的類型與標籤內的成員也應使用 PascalCase。

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>針對 .NET 內建函式使用 PascalCase

命名空間、例外狀況、事件和專案/ `.dll` 名稱也應使用 PascalCase。 這不僅會讓取用者更自然地使用其他 .NET 語言，它也與您可能遇到的 .NET 命名慣例一致。

### <a name="avoid-underscores-in-names"></a>避免名稱中有底線

在過去，某些 F # 程式庫在名稱中使用底線。 不過，這不會再被廣泛接受，部分原因是它與 .NET 命名慣例相衝突。 話雖如此，某些 F # 程式設計人員會大量使用底線，部分基於歷史原因，而且容錯和尊重很重要。 不過，請注意，此樣式通常是由有關於是否使用它的其他人不喜歡。

其中一個例外狀況包含與原生元件的互通性，其中的底線是通用的。

### <a name="use-standard-f-operators"></a>使用標準 F # 運算子

下列運算子是在 F # 標準程式庫中定義，而且應該使用，而不是定義對等專案。 建議使用這些運算子，因為它通常會讓程式碼更容易閱讀及慣用。 背景 OCaml 或其他功能性程式設計語言的開發人員，可能習慣于不同的慣用語。 下列清單摘要說明建議的 F # 運算子。

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>使用泛型的前置詞語法 (`Foo<T>`) 喜好設定為後置語法 (`T Foo`) 

F # 會同時繼承命名泛型型別的後置 ML 樣式 (例如， `int list`) 和前置詞 .net 樣式 (例如 `list<int>`) 。 偏好使用 .NET 樣式，除了五個特定的類型：

1. 針對 F # 清單，請使用後置格式： `int list` 而不是 `list<int>` 。
2. 針對 F # 選項，請使用後置格式： `int option` 而不是 `option<int>` 。
3. 針對 F # 值選項，請使用後置格式： `int voption` 而不是 `voption<int>` 。
4. 針對 F # 陣列，請使用語法名稱， `int[]` 而不是 `int array` 或 `array<int>` 。
5. 針對參考資料格，請使用 `int ref` 而不是 `ref<int>` 或 `Ref<int>` 。

若為所有其他類型，請使用前置詞形式。

## <a name="formatting-tuples"></a>格式化元組

元組具現化應該是以括弧括住，而且其中的分隔逗點後面應該接著一個空格，例如： `(1, 2)` ， `(x, y, z)` 。

通常會接受在元組的模式比對中省略括弧：

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

如果元組是函式的傳回值，通常也會接受省略括弧：

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

總而言之，建議使用括弧化元組具現化，但使用元組進行模式比對或傳回值時，會將其視為可避免括弧。

## <a name="formatting-discriminated-union-declarations"></a>格式化區分聯集宣告

`|`在類型定義中縮排四個空格：

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

## <a name="formatting-discriminated-unions"></a>設定區分等位的格式

跨多行分割的具現化差異聯集，應該為包含的資料提供具有縮排的新範圍：

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

## <a name="formatting-record-declarations"></a>格式化記錄聲明

`{`在類型定義中縮排四個空格，並在同一行上啟動欄位清單：

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

如果您要在記錄上宣告介面或成員，最好將開頭標記放在新行上，然後將結束記號放在新行上：

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>格式化記錄

簡短記錄可以用一行撰寫：

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

較長的記錄應該使用新的標籤行：

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

如果您是下列情況，最好將開啟權杖放在新的一行上，將內容索引標籤為一個範圍，並將結束記號放在新行上：

* 在具有不同縮排範圍的程式碼中移動記錄
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

相同的規則適用于清單和陣列元素。

## <a name="formatting-copy-and-update-record-expressions"></a>格式化複製和更新記錄運算式

複製和更新記錄運算式仍是一筆記錄，因此適用類似的指導方針。

簡短運算式可以容納在同一行：

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

較長的運算式應該使用新的行：

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

如同記錄指引，您可能會想要為大括弧專用不同的行，並使用運算式將一個範圍向右縮排。 在某些特殊情況下（例如，使用不含括弧的選擇性包裝值），您可能需要將大括弧放在同一行：

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

`x :: l`以括弧括住的空格撰寫 `::` (`::` 是中置運算子，因此以空格) 括住。

在一行上宣告的清單和陣列，在左括弧之後和右括弧前面都必須有一個空格：

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

請一律在兩個不同的大括弧運算子之間使用至少一個空格。 例如，在和之間保留一個空格 `[` `{` 。

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

分割成多行的清單和陣列，會遵循與記錄相同的規則：

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

和記錄一樣，在自己的行上宣告左右括弧將會讓程式碼四處移動和輸送至函式。

以程式設計方式產生陣列和清單時，最好不要在 `->` `do ... yield` 永遠產生值時使用：

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

舊版的 F # 語言需要 `yield` 在可能有條件地產生資料的情況下指定，或可能有連續的運算式可供評估。 `yield`除非您必須使用較舊的 F # 語言版本進行編譯，否則偏好省略這些關鍵字：

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

在某些情況下， `do...yield` 可能有助於提高可讀性。 不過，您應該將這些情況納入主觀考慮。

## <a name="formatting-if-expressions"></a>格式化 if 運算式

條件的縮排取決於構成它們的運算式大小。 如果 `cond` `e1` 和 `e2` 很短，只要將它們寫在同一行：

```fsharp
if cond then e1 else e2
```

如果其中 `cond` 一個 `e1` 或 `e2` 更長，但不是多行：

```fsharp
if cond
then e1
else e2
```

如果任何運算式為多行：

```fsharp
if cond then
    e1
else
    e2
```

具有和的多個條件 `elif` `else` 會在與相同的範圍中縮排 `if` ：

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>模式比對結構

`|`針對相符的每個子句（沒有縮排）使用。 如果運算式很短，則如果每個子運算式也很簡單，您可以考慮使用一行。

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

如果模式比對箭號右邊的運算式太大，請將它移到下一行，從縮排一個步驟 `match` / `|` 。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

匿名函式的模式比對（從開始 `function` ）通常不會縮排太遠。 例如，如下所示將一個範圍縮排，如下所示：

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

在開頭的函式中的模式比 `let` `let rec` 對應該在開始之後縮排四個空格 `let` ，即使 `function` 使用關鍵字也是如此：

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

我們不建議對齊箭號。

## <a name="formatting-trywith-expressions"></a>格式化 try/with 運算式

例外狀況類型的模式比對應該在與相同的層級上縮排 `with` 。

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

## <a name="formatting-function-parameter-application"></a>格式化函式參數應用程式

一般而言，大部分的函式參數應用程式都是在同一行上完成。

如果您想要將參數套用至新行的函式，請依一個範圍將它們縮排。

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

Lambda 運算式的相同指導方針也適用于函式引數。 如果 lambda 運算式的主體，主體可以有另一行（以一個範圍縮排）

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

但是，如果 lambda 運算式的主體超過一行，請考慮將它分解成個別的函式，而不是將多行結構套用為函式的單一引數。

### <a name="formatting-infix-operators"></a>格式化中置運算子

以空格分隔運算子。 這項規則的明顯例外是 `!` 和 `.` 運算子。

中置運算式可在相同資料行上進行組合：

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>格式化管線運算子

管線 `|>` 運算子應該在其運作的運算式底下。

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

本機模組中的程式碼必須相對於模組進行縮排，但是最上層模組中的程式碼不應該縮排。 命名空間元素不需要縮排。

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>格式化物件運算式和介面

物件運算式和介面的對齊方式應該與在 `member` 四個空格之後縮排的方式相同。

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

避免 F # 運算式中有多餘的空白字元。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

具名引數也不應該有周圍的空格 `=` ：

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>格式化屬性

[屬性](../language-reference/attributes.md) 位於結構的上方：

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

屬性也可以放在參數上。 在此情況下，請將它放在與參數相同的行上，然後在名稱之前：

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>格式化多個屬性

當您將多個屬性套用至非參數的結構時，應該將它們放在每行一個屬性中：

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

套用至參數時，它們必須在同一行，並以 `;` 分隔符號分隔。

## <a name="formatting-literals"></a>格式化常值

使用屬性的[F # 常](../language-reference/literals.md)值 `Literal` 應該將屬性放在其本身的行，並使用 PascalCase 命名：

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

避免將屬性放在與值相同的行上。
