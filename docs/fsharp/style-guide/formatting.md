---
title: 'F # 程式碼的 formattin 指導方針'
description: '了解 F # 程式碼格式化方針。'
ms.date: 05/14/2018
ms.openlocfilehash: e5c700ca9ae3968243f11c1237b9e4b26e580dcf
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="f-code-formatting-guidelines"></a>F # 程式碼格式化方針

這篇文章提供如何格式化您的程式碼，讓 F # 程式碼的指導方針：

* 通常以更易於閱讀檢視
* 會根據套用的 Visual Studio 中的工具和其他編輯器格式設定慣例
* 類似於線上的其他程式碼

這些方針根據[F # 格式設定慣例的完整指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)由[Anh 盜賊藩](https://github.com/dungpa)。

## <a name="general-rules-for-indentation"></a>縮排的一般規則

F # 預設會使用空白字元。 下列指導方針均提供指導方針來選擇龐大這也可能造成的一些挑戰。

### <a name="using-spaces"></a>使用空間

需要縮排時，您必須使用空間，而不是索引標籤。 需要至少一個空白字元。 您的組織可以建立以指定要用來縮排; 的空格數目編碼標準通常會發生縮排每個層級的縮排的兩個、 三或四個空格。

**我們建議您縮排每 4 個空格。**

話雖如此，縮排程式是主觀。 變化 [確定]，但是您應該遵循的第一個規則*縮排的一致性*。 選擇公認的縮排樣式，並在整個程式碼基底有系統地使用它。

## <a name="formatting-discriminated-union-declarations"></a>格式化差別等位宣告

縮排`|`由 4 個空格的類型定義中：

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

具現化差別等位分成多行，應該提供包含的資料包含縮排新的範圍：

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

右括號也可以是新的一行：

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>Tuple 的格式化

Tuple 的具現化應該是括號括住，而且內分隔逗號後面必須接著一個空格，例如： `(1, 2)`， `(x, y, z)`。

普遍接受的例外狀況是 tuple 的省略括號中的模式比對：

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>格式化的資料錄

簡短的記錄可以撰寫在一行中：

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

記錄的長度應該使用新行的標籤：

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

將左語彙基元放在同一行和新的一行的結尾語彙基元是也可以：

```fsharp
let rainbow = {
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
```

清單和陣列項目套用相同的規則。

## <a name="formatting-lists-and-arrays"></a>格式設定清單和陣列

寫入`x :: l`前後的空格與`::`運算子 (`::`是中置運算子，因此，以空格) 和`[1; 2; 3]`(`;`是分隔符號，因此後接空格)。

一律使用至少一個兩個不同的大括號類似運算子之間的空間。 例如，將保留之間的空格`[`和`{`。

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

清單和陣列分成多行，請依照下列類似的規則一樣記錄：

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a>如果格式運算式

縮排的條件取決於它們構成的運算式的大小。 如果`cond`，`e1`和`e2`很小，只要將它們寫入在一行上：

```fsharp
if cond then e1 else e2
```

如果`e1`和`cond`很小，但`e2`大：

```fsharp
if cond then e1
else
    e2
```

如果`e1`和`cond`大和`e2`小：

```fsharp
if cond then
    e1
else e2
```

如果所有運算式都是大型的：

```fsharp
if cond then
    e1
else
    e2
```

使用多個條件`elif`和`else`縮排在相同範圍`if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>模式比對的建構

使用`|`相符項目的每個子句不縮排。 如果運算式是短，您可以使用單行。

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"

// OK
match l with [] -> false | _ :: _ -> true
```

如果在模式比對箭號右邊的運算式太大，將它移至下列的行縮排一個步驟，從`match` / `|`。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

模式比對的匿名函式，來啟動`function`，應該通常不縮排太遠。 例如，縮排一個範圍，如下所示是可以：

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

模式比對所定義的函式中`let`或`let rec`之後開始進行縮排 4 個空格`let`，即使`function`關鍵字使用：

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

我們不建議對齊箭號。

## <a name="formatting-trywith-expressions"></a>格式化的 try / with 運算式

模式比對的例外狀況類型，應該在相同的層級縮排`with`。

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

如果您想要套用至新的一行函式的參數，則縮排一個領域。

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

匿名函式引數可以是下一行，或使用懸空`fun`引數的一行：

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a>格式化的中置運算子

以空格分開的運算子。 此規則的明顯例外狀況是`!`和`.`運算子。

中置運算式是在相同的資料行上的內容 [確定]:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>格式設定管線運算子

管線`|>`應該出現在正下方的運算式所操作的一行的開頭：

```fsharp
// OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat

// OK, but prefer previous
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

在本機的模組中的程式碼必須縮排相對於模組，但應該不會縮排在最上層的模組中的程式碼。 命名空間元素不具有縮排。

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

物件運算式和介面應該有相同的方式對齊`member`要縮排後 4 個空格。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>格式運算式中的空白字元

請避免多餘的空白字元，F # 運算式中。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

具名引數也不應該有周圍的空間`=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a>格式化空白行

* 個別最上層函式和類別定義具有兩個空白的行。
* 在類別內的方法定義會以單一的空白列分隔。
* 額外的空白的線條可能謹慎 （） 來分隔的相關函式群組。 一堆相關 one-liners （例如，一組虛擬實作） 之間，可能會省略空白的行。
* 用於空白的行在函數中，謹慎使用，表示邏輯區段。

## <a name="formatting-comments"></a>格式化的註解

通常，而不用多個雙斜線註解 ML 樣式區塊註解。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

內嵌註解應該將第一個字母變成大寫。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>命名規範

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>使用 camelCase 類別繫結、 運算式繫結和繫結模式值和函式

它通常會和接受的 F # 樣式 camelCase 用於所有名稱繫結，做為本機變數，或在模式比對和函式定義中。

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

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>CamelCase 用於內部及私人模組繫結值和函式

CamelCase 用於私用模組繫結值，如下所示：

* 臨機操作指令碼中的函式

* 構成模組或類型的內部實作的值

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="avoid-underscores-in-names"></a>避免在名稱中的底線

在過去，有些 F # 程式庫名稱中使用底線。 不過，這是不再被廣泛接受，這是因為它與.NET 的命名慣例發生衝突。 話雖如此，某些 F # 程式設計人員使用底線有很大，部分由於歷史原因，並容忍度及方面很重要。 不過，請注意樣式通常 disliked 其他人可以選擇要使用它。

有些例外狀況包含間的互通性與原生元件，其中底線很常見。

### <a name="use-standard-f-operators"></a>使用標準的 F # 運算子

下列運算子定義在 F # 標準程式庫，而且應該用於而不是定義對等項目。 因為它會使程式碼更容易讀取與慣用語，被建議使用這些運算子。 具有背景 OCaml 或其他功能的程式設計語言的開發人員可能會不同語言的習慣。 下列清單摘要說明建議的 F # 運算子。

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
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

F # 繼承這兩個的後置 ML 樣式命名泛型型別 (比方說， `int list`) 以及.NET 樣式的前置詞 (例如， `list<int>`)。 偏好的.NET 樣式，除了特定的四種類型：

1. F # 列出，請使用後置格式：`int list`而不是`list<int>`。
2. 使用 F # 選項，請使用 後置格式：`int option`而不是`option<int>`。
3. F # 陣列，使用的語法名稱`int[]`而`int array`或`array<int>`。
4. 參考儲存格，使用`int ref`而`ref<int>`或`Ref<int>`。

對於所有其他類型，使用的前置格式。