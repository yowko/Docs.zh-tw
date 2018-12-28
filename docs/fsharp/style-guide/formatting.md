---
title: F#程式碼格式化方針
description: 了解格式的指導方針F#程式碼。
ms.date: 11/26/2018
ms.openlocfilehash: e8e0af2ebffd0e2f3720896bf710961afa11e7bd
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396821"
---
# <a name="f-code-formatting-guidelines"></a>F#程式碼格式化方針

這篇文章提供如何格式化您的程式碼的指導方針，讓您F#的程式碼：

* 通常視為更易於閱讀
* 會根據套用在 Visual Studio 中的工具和其他的編輯器格式設定慣例
* 類似於線上的其他程式碼

這些指導方針根據[的完整指南F#格式設定慣例](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)所[Anh phan （英文)](https://github.com/dungpa)。

## <a name="general-rules-for-indentation"></a>縮排的一般規則

F#預設會使用顯著泛空白字元。 下列指導方針的用意在於提供指引來選擇要掌握這造成一些挑戰。

### <a name="using-spaces"></a>使用空間

需要縮排時，您必須使用空格，而不是索引標籤。 需要至少一個空白字元。 您的組織可以建立以指定要用來縮排; 的空格數目的程式碼撰寫標準通常會發生縮排每個層級的縮排的兩個、 三個或四個空格。

**我們建議每個縮排的 4 個空格。**

話雖如此，程式的縮排是主觀的問題而已。 變化都沒問題，但您應該遵循的第一個規則*縮排的一致性*。 選擇通常可接受的縮排樣式，並在整個程式碼基底有系統地使用它。

## <a name="formatting-white-space"></a>格式化的泛空白字元

F#是機密的泛空白字元。 雖然大部分的語意，空白字元係由其適當縮排，有一些其他考量事項。

### <a name="formatting-operators-in-arithmetic-expressions"></a>設定格式化的算術運算式中的運算子

一律使用二進位算術運算式周圍的空白字元：

```fsharp
let subtractThenAdd x = x - 1 + 3
```

一元`-`運算子應一律具有的值，它們會否定緊接：

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

新增之後的空格字元`-`運算子可能會導致其他人的混淆。

總而言之，務必一律：

* 範圍陳述式以空白字元的二元運算子
* 永遠不會將尾端空白之後的一元運算子

二進位的算術運算子的指導方針是特別重要。 失敗來括住二進位`-`運算子，以特定格式設定的選項組合時可能會導致解譯為一元`-`。

### <a name="surround-a-custom-operator-definition-with-white-space"></a>括住空白字元的自訂運算子定義

一律使用泛空白字元來括住運算子定義：

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

開始任何自訂運算子`*`，您必須定義，以避免編譯器模稜兩可的開頭加入泛空白字元。 因為這個緣故，建議您只需括住的所有運算子以單一空格字元定義。

### <a name="surround-function-parameter-arrows-with-white-space"></a>括住函式參數的箭號以空白字元

在定義的函式簽章時，使用周圍的空白`->`符號：

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a>格式化的空白行

* 另一個最上層函式和類別定義兩個空白的行。
* 在類別內的方法定義是以單一的空白行分隔。
* 額外的空白的行可能會用來分隔組相關的函式的 （謹慎使用）。 一大堆相關單行 （比方說，一組虛擬實作） 之間，可能會省略空白的行。
* 使用空白列在函式，盡量節制，來指出邏輯區段。

## <a name="formatting-comments"></a>格式化註解

通常不用 ML 樣式區塊註解的多個雙斜線註解。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

第一個字母時，應大寫內嵌註解。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>命名規範

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>使用 camelCase 類別繫結、 繫結運算式和模式繫結的值和函式

它很常見而且可接受F#使用 camelCase 的所有名稱繫結為本機變數，或在模式比對，而函式定義的樣式。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

本機繫結類別中的函式也應該使用 camelCase。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>針對模組繫結的公用函式使用 camelCase

當模組繫結函式是公用 API 的一部分時，它應該使用 camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>使用 camelCase 的內部與私用模組繫結值和函式

使用 camelCase 的私用模組繫結值，包括下列：

* 在指令碼中的特定函式

* 組成模組或類型的內部實作的值

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>針對參數使用 camelCase

所有參數都應該都使用 camelCase 根據.NET 命名慣例。

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>使用 PascalCase 的模組

（最上層、 內部、 私用、 巢狀） 的所有模組都應該都使用 PascalCase。

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>使用 PascalCase 的型別宣告、 成員和標籤

類別、 介面、 結構、 列舉、 委派、 記錄和差別聯的集全部命名為使用 PascalCase。 型別和用於記錄和差別聯的集的標籤內的成員也應該使用 PascalCase。

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>適用於.NET 內建函式建構的使用 PascalCase

命名空間、 例外狀況、 事件和專案 /`.dll`名稱也應該使用 PascalCase。 不只這樣清楚感受更自然的取用者從其他.NET 語言使用，也是配合您可能會遇到的.NET 命名慣例。

### <a name="avoid-underscores-in-names"></a>避免在名稱中的底線

在過去，某些F#程式庫名稱中使用底線。 不過，這是不會再被廣泛接受，這是因為它與.NET 命名慣例衝突。 話雖如此，一些F#程式設計人員使用底線大量、 部分基於歷史原因，並容錯] 和 [方面很重要。 不過，請注意樣式通常會不喜歡的人可以選擇要使用它。

某些例外狀況包含間的互通性與原生元件，其中底線很常見。

### <a name="use-standard-f-operators"></a>使用標準F#運算子

在定義了下列運算子F#標準程式庫，應使用而不是定義對等項目。 因為它會使程式碼，更容易理解且慣用語，建議使用這些運算子。 具有背景的 OCaml 或其他功能的程式設計語言的開發人員可能習慣將不同的習慣用語。 下列清單摘要說明建議F#運算子。

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>使用泛型的前置詞的語法 (`Foo<T>`) 而非後置語法 (`T Foo`)

F#繼承這兩個後置 ML 的樣式命名泛型型別 (例如`int list`) 以及.NET 樣式的前置詞 (例如`list<int>`)。 偏好的.NET 樣式，除了特定的四種類型：

1. 針對F#清單中，使用後置格式：`int list`而非`list<int>`。
2. 針對F#選項，請使用後置格式：`int option`而非`option<int>`。
3. 針對F#陣列，請使用語法的名稱`int[]`而非`int array`或是`array<int>`。
4. 參考儲存格，使用`int ref`而非`ref<int>`或`Ref<int>`。

對於所有其他類型，使用前置詞的表單。

## <a name="formatting-tuples"></a>格式化的 tuple

Tuple 的具現化應該是括號括住，而且中分隔的逗號後面必須接著一個空格，例如： `(1, 2)`， `(x, y, z)`。

通常可接受省略括號中的 tuple 模式比對：

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a>設定格式化的差別等位宣告

縮排`|`由 4 個空格的型別定義中：

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

## <a name="formatting-discriminated-unions"></a>格式化差別聯集

具現化差別聯集分割成多行，應該會產生包含的資料附縮排新的範圍：

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

右括號也可以在新的一行：

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>格式設定記錄的宣告

縮排`{`在類型定義由 4 空間，開始在同一行上的 [欄位] 清單：

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

在新行和結尾語彙基元，在新行上的放置的左語彙基元是下班時間，如果您在記錄上宣告的介面實作或成員：

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
        SomeField : int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>格式化的記錄

可以在同一行撰寫簡短的記錄：

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

較長的記錄應該使用新行標籤：

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

放置開頭索引標籤式的語彙基元的新行上，內容一段範圍內，，並在新的一行的結尾語彙基元是下班時間，如果您是：

* 在不同的縮排的領域的程式碼中四處移動記錄
* 將它們傳送到函式

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
        SomeField : int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

相同的規則適用於清單和陣列的項目。

## <a name="formatting-lists-and-arrays"></a>格式化的清單和陣列

撰寫`x :: l`與前後的空格`::`運算子 (`::`是中置運算子，因此括住空格)。

清單和陣列宣告在單行上應該有空格之後的左括弧和右括弧之前：

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

一律使用兩個不同的大括號類似運算子之間的至少一個空白字元。 例如，將保留之間保留一個空格`[`和`{`。

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

相同的指導方針適用於清單或陣列的 tuple。

清單和陣列分成多行，請遵循類似的規則記錄也一樣：

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

如同記錄，在各自的行上宣告的開頭和結尾括號會簡化移動程式碼的位置和管線執行函式。

## <a name="formatting-if-expressions"></a>如果格式運算式

縮排的條件取決於它們構成的運算式的大小。 如果`cond`，`e1`和`e2`簡短，只要將它們寫入在同一行：

```fsharp
if cond then e1 else e2
```

如果有任一`cond`，`e1`或`e2`更久，但不多行：

```fsharp
if cond
then e1
else e2
```

如果任何運算式是多行：

```fsharp
if cond then
    e1
else
    e2
```

使用多個條件`elif`並`else`縮排在相同範圍`if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>模式比對建構

使用`|`不縮排每個子句的相符項目。 如果運算式很短，您可以考慮使用單一行，如果每一個子運算式也很簡單。

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

如果在模式比對的箭號右側的運算式太大，將它移至下列這一行，縮排的一個步驟，從`match` / `|`。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

模式比對的匿名函式，來啟動`function`，應該通常不縮排牽扯太廣。 例如，縮排一個範圍，如下所示沒關係：

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

模式比對中所定義的函式`let`或是`let rec`之後開始進行縮排的 4 個空格`let`，即使`function`關鍵字可用於：

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

我們不建議對齊箭號。

## <a name="formatting-trywith-expressions"></a>格式化的 try / with 運算式

模式比對的例外狀況類型應位於相同層級會縮排`with`。

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

## <a name="formatting-function-parameter-application"></a>格式函式參數的應用程式

一般而言，大部分函式參數的應用程式是在同一行。

如果您想要套用至新的一行中的函式的參數，則由一個範圍縮排。

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

函式引數的 lambda 運算式套用相同的指導方針。 如果 lambda 運算式主體的主體可以有另一條，縮排一個範圍

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

不過，如果多行 lambda 運算式的主體，請考慮一下重構到個別函式而非已做為單一引數套用至函式的多行建構。

### <a name="formatting-infix-operators"></a>格式化 中置運算子

以空格分開的運算子。 明顯的例外狀況，此規則會`!`和`.`運算子。

中置運算式會為同一個資料行的組合中的 [確定]:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>格式設定管線運算子

管線`|>`運算子都應下它們對的運算式。

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

### <a name="formatting-modules"></a>格式化的模組

在本機的模組中的程式碼必須相對於模組，縮排，但應該不會縮排在最上層模組中的程式碼。 縮排沒有命名空間項目。

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

### <a name="formatting-object-expressions-and-interfaces"></a>格式化的物件運算式和介面

物件運算式和介面應該使用相同的方式對齊`member`正在後 4 個空格縮排。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>設定格式化的運算式中的泛空白字元

避免多餘的泛空白字元，在F#運算式。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

具名引數也不應該周圍的空間`=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>格式化屬性

[屬性](../language-reference/attributes.md)位於上述建構：

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

### <a name="formatting-attributes-on-parameters"></a>參數的格式化屬性

屬性也可以在參數上的位置。 在此情況下，將再置於相同的行做為參數，並在名稱前面：

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>格式化多個屬性

當多個屬性會套用至不是參數的建構時，它們應該放使得每行一個屬性：

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

套用至參數時，則它們必須在同一行中，以分隔`;`分隔符號。

## <a name="formatting-literals"></a>格式化常值

[F#常值](../language-reference/literals.md)使用`Literal`應該將屬性放在它自己的行並使用 camelCase 的命名屬性：

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

避免將屬性放在同一行的值。
