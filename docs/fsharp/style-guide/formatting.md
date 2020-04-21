---
title: F# 程式碼格式方針
description: 瞭解 F# 程式碼的格式設定指南。
ms.date: 11/04/2019
ms.openlocfilehash: b8be70dd29a04e71614308164e541b99a1724305
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739549"
---
# <a name="f-code-formatting-guidelines"></a>F# 程式碼格式方針

本文提供了如何設定代碼格式的指南,以便 F# 代碼具有:

* 更清晰
* 依視覺化工作室和其他編輯器中格式工具應用程式的約定
* 類似於其他線上碼

這些準則基於[由安-鄧潘](https://github.com/dungpa)[對 F# 格式約定的全面指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)。

## <a name="general-rules-for-indentation"></a>縮排的一般規則

默認情況下,F# 使用大量空白。 以下準則旨在就如何應對可能帶來的一些挑戰提供指導。

### <a name="using-spaces"></a>使用空白

當需要縮進時,必須使用空格,而不是選項卡。 至少需要一個空格。 您的組織可以創建編碼標準來指定用於縮進的空間數;在發生縮進的每個級別,2 個、3 個或 4 個縮進空間是典型的。

**我們建議每個縮進四個空格。**

這就是說,程式縮進是一個主觀問題。 變異是可以的,但您應該遵循的第一條規則是*縮進的一致性*。 選擇一種普遍接受的縮進樣式,並在代碼庫中系統地使用它。

## <a name="formatting-white-space"></a>設定空白格式

F# 對空白敏感。 儘管空白的大多數語義都由適當的縮進覆蓋,但還有其他一些需要考慮。

### <a name="formatting-operators-in-arithmetic-expressions"></a>算術表示式的運算子格式

始終在二進位算術表達式周圍使用空白:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

一元`-`運算子應始終立即跟隨他們否定的值:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

在`-`運算符之後添加空格字元可能會導致其他人混淆。

總之,始終:

* 環繞具有空白的二進位運算子
* 一個一元運算符後,永遠不會有尾隨空格

二進位算術運算符準則尤為重要。 如果無法包圍二進位`-`運算符,當與某些格式選項結合使用時,可能會導致將其解釋為一元`-`。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>以空白方繞自訂運算符定義

始終使用空白環繞運算符定義:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

對於任何以開頭`*`且具有多個字元的自定義運算符,都需要向定義開頭添加一個空格以避免編譯器歧義。 因此,我們建議您只需使用單個空格字元括括所有運算元的定義。

### <a name="surround-function-parameter-arrows-with-white-space"></a>帶空格的環繞函數參數箭頭

定義函數的簽名時,請使用`->`符號周圍的空白:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>帶空格的環繞函數參數

定義函數時,在每個參數周圍使用空白。

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>將參數放在長成員定義的新行上

如果您有很長的成員定義,則將參數放在新行上,並縮進它們一個作用域。

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

這也適用於建構函數:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>類型註解

#### <a name="right-pad-function-argument-type-annotations"></a>右墊函數參數類型註解

使用類型註釋定義參數時,在`:`符號之後使用空格:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>帶空格的環繞傳回類型註解

在允許結合函數或值型態註解(在函數的情況下傳回類型)中,`:`在符號之前和之後使用空格:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>設定空白列格式

* 使用兩條空白行分隔頂級函數和類定義。
* 類中的方法定義由單個空白行分隔。
* 額外的空白行可用於(謹慎)分隔相關函陣列。 在一堆相關的單行(例如,一組虛擬實現)之間可以省略空白行。
* 請謹慎在函數中使用空白行來指示邏輯部分。

## <a name="formatting-comments"></a>設定註解的格式

通常更喜歡多個雙斜杠註釋,而不是 ML 樣式塊註釋。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

內聯註釋應將第一個字母大寫。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>命名慣例

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>對類綁定、運算式綁定和模式綁定值和函數使用 camelCase

對於綁定為局部變數的所有名稱或在模式匹配和函數定義中,使用 camelCase 是常見且公認的 F# 樣式。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

類中的本地綁定函數還應使用 camelCase。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>將 CamelCase 用於模組的公共函數

當模組綁定函數是公共 API 的一部分時,它應使用 camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>將 camelCase 用於內部和私有模組綁定值和函數

對專用模組綁定值使用 camelCase,包括:

* 文稿中的暫存函數

* 組成模組或類型的內部實現的值

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>使用 camelCase 進行參數

所有參數都應根據 .NET 命名約定使用 camelCase。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>將帕斯卡套件用於模組

所有模組(頂級、內部、私有、嵌套)都應使用 PascalCase。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>將 PascalCase 用於類型聲明、成員和標籤

類、介面、結構、枚舉、委託、記錄和受歧視的聯合都應使用 PascalCase 命名。 記錄和受歧視結合的類型和標籤中的成員也應使用 PascalCase。

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>使用 PascalCase 進行 .NET 固有的建構

命名空間、異常、事件和專案/`.dll`名稱也應使用 PascalCase。 這不僅使來自其他 .NET 語言的消費者感覺更自然,而且與您可能遇到的 .NET 命名約定一致。

### <a name="avoid-underscores-in-names"></a>避免在名稱中下劃線

從歷史上看,某些 F# 庫在名稱中使用了下劃線。 但是,這不再被廣泛接受,部分原因是它與 .NET 命名約定衝突。 也就是說,一些 F# 程式師使用強調很大,部分原因是歷史原因,寬容和尊重很重要。 但是,請注意,對於是否使用該樣式,其他人通常不喜歡這種風格。

一個例外包括與本機組件進行互操作,其中下劃線很常見。

### <a name="use-standard-f-operators"></a>使用標準 F# 運算子

以下運算符在 F# 標準庫中定義,應使用而不是定義等效項。 建議使用這些運算符,因為它會使代碼更具可讀性和慣用性。 具有 OCaml 或其他函數程式設計語言背景的開發人員可能習慣於不同的習語。 下面的清單總結了推薦的 F# 運算符。

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>使用泛型的前置字語法`Foo<T>`( ) 優先於後`T Foo`綴語法 ( )

F# 既繼承命名泛型類型的後綴 ML 樣`int list`式(例如 ),也繼承前綴 .NET`list<int>`樣式(例如)。 首選 .NET 樣式,但五種特定類型除外:

1. 對於 F# 清單,請使用後修復`int list`窗型`list<int>`:而不是 。
2. 對 F# 選項,請使用後修復`int option`窗型`option<int>`:而不是 。
3. 對 F# 值選項,請使用後修復`int voption`窗型`voption<int>`:而不是 。
4. 對於 F# 陣列,請使用句`int[]`法`int array`名稱`array<int>`而不是或 。
5. 對參考儲存格,使用`int ref`而不是`ref<int>``Ref<int>`或 。

對於所有其他類型,請使用首碼窗體。

## <a name="formatting-tuples"></a>格式化中陣數

中繼實體資訊資訊設定為括弧,其中的分隔逗號應後跟單個空白,例如: `(1, 2)`。 `(x, y, z)`

在組合的圖案比對中省略括弧是通常接受的:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

如果元組是函數的返回值,則通常也接受省略括弧:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

總之,首選括弧組實例化,但當使用組合體進行模式匹配或返回值時,避免括弧被認為是好的。

## <a name="formatting-discriminated-union-declarations"></a>格式化受歧視的工會聲明

類型定義`|`中按四個空白縮排:

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

## <a name="formatting-discriminated-unions"></a>格式化受歧視的工會

跨多行拆分的實例化歧視聯合應為包含的數據提供具有縮進的新作用域:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

閉合括弧也可以位於新行上:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>格式化記錄聲明

按四`{`個空白在類型定義中縮進,並在同一行上啟動欄位清單:

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

如果要聲明介面實現或記錄上的成員,最好在新行上放置首開令牌,在新行上放置結束令牌:

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

## <a name="formatting-records"></a>設定記錄格式

短記錄可以寫在一行:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

較長的紀錄應使用新行用於標籤:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

將首開權杖放在新行上,內容在一個作用網域上選項卡,如果是:

* 在具有不同縮進作用網域的代碼中移動記錄
* 將它們放入函數中

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

相同的規則適用於清單和陣列元素。

## <a name="formatting-copy-and-update-record-expressions"></a>格式化複製及更新記錄表示式

複製和更新記錄表達式仍然是記錄,因此適用類似的準則。

短運算式可以適合在一行上:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

較長的運算式應使用新行:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

與記錄指南一樣,您可能希望為大括弧專用單獨的行,並將一個範圍縮進到右側。 在某些特殊情況下,例如使用可選的無括弧包裝值,您可能需要在一行上保留大括弧:

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

## <a name="formatting-lists-and-arrays"></a>設定清單與陣列格式

使用`x :: l``::`運算子周圍的空白寫入(`::`是一個內碼運算符,因此被空格包圍)。

在單行上聲明的清單和陣列應在開口括弧後和右括弧之前具有空格:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

始終在兩個不同的大括弧運算元之間至少使用一個空格。 例如,在和`[`之間留一個`{`空格。

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

同樣的準則也適用於元組的清單或陣列。

跨行拆分的清單和陣列遵循與紀錄類似的規則:

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

與記錄一樣,在自己的行上聲明首括弧和關閉括弧將使行動碼和管道進入功能變得更加容易。

以程式設計方式產生陣列和清單時,請`->`首`do ... yield`選 始終產生值時:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

在可能有條件地生成數據或可能需要`yield`計算連續運算式的情況下,需要指定較舊版本的 F# 語言。 預設的一般略`yield`這些 關鍵字,除非您必須使用較舊的 F# 語言版本進行編譯:

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

在某些情況下,`do...yield`可能有助於可讀性。 這些案件雖然是主觀的,但應當加以考慮。

## <a name="formatting-if-expressions"></a>格式化運算式

條件縮進取決於構成條件的表達式的大小。 如果`cond``e1``e2`和短,只需將它們寫在一行上:

```fsharp
if cond then e1 else e2
```

如果`cond``e1``e2`或較長,但不是多行:

```fsharp
if cond
then e1
else e2
```

如果任何表示式是多行的:

```fsharp
if cond then
    e1
else
    e2
```

具有`elif`與`else``if`的多個條件與

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>模式符合建構

`|`對匹配的每個子句使用,沒有縮進。 如果表達式較短,則可以考慮使用單行,如果每個子表達式也很簡單。

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

如果模式匹配箭頭右側的表達式太大,將其移動到下一行,從 縮進`match`/`|`一步。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

以 開`function`頭的匿名函數的模式匹配通常不應縮進太遠。 例如,按照如下方式縮進一個作用域可以:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

在`let`函數中定義`let rec`的 或應在 啟動後縮進四個`let`空白中的 模式`function`符合,即使使用關鍵字:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

我們不建議對齊箭頭。

## <a name="formatting-trywith-expressions"></a>設定設定/包含表示式的格式

異常類型的模式匹配應縮進與的級別`with`相同。

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

## <a name="formatting-function-parameter-application"></a>格式化功能參數應用程式

通常,大多數函數參數應用都在同一行上完成。

如果要將參數應用於新行上的函數,請按一個作用域縮進參數。

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

相同的準則適用於 lambda 運算式和函數參數。 如果 lambda 表示式的正文,正文可以有另一條線,由一個作用域縮進

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

但是,如果 lambda 表達式的正文是多行,請考慮將其分解為單獨的函數,而不是將多行構造作為單個參數應用於函數。

### <a name="formatting-infix-operators"></a>格式化固定運算子

按空格分隔運算符。 此規則的明顯例外是`!`和`.`運算符。

infix 表示式可以在同一列上提供陣容:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>格式化導管運算子

管道`|>`操作員應位於其操作的表達式下方。

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

本地模組中的代碼必須相對於模組縮進,但頂層模組中的代碼不應縮進。 命名空間元素不必縮進。

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

### <a name="formatting-object-expressions-and-interfaces"></a>設定物件運算式與介面的格式

對象運算式和介面應與在四個空格後縮`member`進 的方式對齊。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>設定式式空白格式

避免 F# 運算式中的無關空白。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

命名參數也不應圍繞`=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>設定屬性的格式

[屬性](../language-reference/attributes.md)放置在建構上方:

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

### <a name="formatting-attributes-on-parameters"></a>參數上的格式設定屬性

屬性也可以是參數上的放置。 在這種情況下,將放在與參數相同的行上,並在名稱之前:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>設定多個屬性的格式

當多個屬性應用於不是參數的建構時,應放置這些屬性,以便每行有一個屬性:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

應用於參數時,它們必須位於同一`;`行上,並由分隔符分隔。

## <a name="formatting-literals"></a>格式化文字

使用`Literal`屬性的[F# 文字](../language-reference/literals.md)應將屬性放在自己的行上,並使用 PascalCase 命名:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

避免將屬性放在與值相同的行上。
