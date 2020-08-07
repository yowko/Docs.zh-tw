---
title: 純文字格式
description: '瞭解如何在 F # 應用程式和腳本中使用 printf 和其他純文字格式。'
ms.date: 07/22/2020
ms.openlocfilehash: 6b14633e074961757d0f0cd258d1b1667f5fd8ee
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854915"
---
# <a name="plain-text-formatting"></a>純文字格式

F # 使用 `printf` 、 `printfn` 、和相關函式，支援純文字的類型檢查格式 `sprintf` 。
例如

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

提供輸出

```fsharp
Hello world, 2 + 2 is 4
```

F # 也允許將結構化值格式化為純文字。
例如，請考慮下列範例，其會將輸出格式化為類似矩陣的元組顯示。

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

當您 `%A` 在格式化字串中使用格式時，會啟用結構化純文字格式 `printf` 。
它也會在 F # interactive 中格式化值的輸出時啟用，其中輸出會包含額外的資訊，而且還可自訂。
純文字格式也可透過任何對 `x.ToString()` F # union 和記錄值的呼叫來觀察，包括在偵錯工具、記錄和其他工具中隱含發生的。

## <a name="checking-of-printf-format-strings"></a>檢查 `printf` 格式字串

如果 `printf` 使用格式函數搭配的引數與格式字串中的 printf 格式規範不相符，就會回報編譯時期錯誤。  例如

```fsharp
sprintf "Hello %s" (2+2)
```

提供輸出

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

技術上而言，當使用 `printf` 和其他相關函式時，F # 編譯器中的特殊規則會檢查當做格式字串傳遞的字串常值，確保後續套用的引數是正確的類型，以符合所使用的格式規範。

## <a name="format-specifiers-for-printf"></a>的格式規範`printf`

格式規格 `printf` 是具有 `%` 標記的字串，表示格式。 格式預留位置是由類型的解讀方式所組成 `%[flags][width][.precision][type]` ，如下所示：

| 格式規範   | 輸入 (s)         | 備註                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | bool      | 格式化為 `true` 或`false`                |
| `%s`               | 字串    | 格式化為其非的非格式內容         |
| `%c`               | char      | 格式化為字元常值  |
| `%d`, `%i`         | 基本整數類型 | 格式化為十進位整數，如果基本整數類型已簽署，則為帶正負號 |
| `%u`               | 基本整數類型 | 格式化為不帶正負號的十進位整數   |
| `%x`, `%X`         | 基本整數類型 | 已格式化為不帶正負號的十六進位數位 (-f 或-F 分別用於十六進位數位)   |
|  `%o`              | 基本整數類型 | 格式化為不帶正負號的八進位數位 |
| `%e`, `%E`         | 基本浮點類型 | 格式化為具有格式的帶正負號值 `[-]d.dddde[sign]ddd` ，其中 d 是單一十進位數，dddd 是一或多個十進位數，ddd 只是三個小數位數，而 sign 是 `+` 或`-` |
| `%f`               | 基本浮點類型 | 格式化為具有格式的帶正負號值 `[-]dddd.dddd` ，其中 `dddd` 是一或多個十進位數。 小數點前面的位數取決於數字的大小，小數點後面的位數則取決於要求的精確度。 |
| `%g`, `%G` | 基本浮點類型 |  使用當做以或格式列印的帶正負號值進行格式化，以較 `%f` `%e` 精簡的指定值和有效位數為准。 |
| `%M` | `System.Decimal`值  |    使用的 `"G"` 格式標準格式化`System.Decimal.ToString(format)` |
| `%O` | 任何值  |   藉由將物件裝箱並呼叫其方法來進行格式化 `System.Object.ToString()` |
| `%A` | 任何值  |   使用預設版面配置設定，以[結構化純文字格式](plaintext-formatting.md)格式化 |
| `%a` | 任何值  |   需要兩個引數：格式函數接受內容參數和值，以及要列印的特定值 |
| `%t` | 任何值  |   需要一個引數：格式化函數接受內容參數，以輸出或傳回適當的文字 |

基本整數類型 `byte` (`System.Byte`) 、 `sbyte` (`System.SByte`) 、 `int16` (`System.Int16`) 、 `uint16` (`System.UInt16`) 、 `int32` (`System.Int32`) 、 `uint32` (`System.UInt32`) 、 `int64` (`System.Int64`) 、 `uint64` (`System.UInt64`) 、 `nativeint` (`System.IntPtr`) 和 () `unativeint` `System.UIntPtr` 。
基本浮點類型 `float` (`System.Double`) 和 `float32` (`System.Single`) 。

選擇性寬度是一個整數，表示結果的最小寬度。 例如， `%6d` 會列印一個整數，並在前面加上空格，以填滿至少六個字元。 如果 width 為 `*` ，則會採用額外的整數引數來指定對應的寬度。

有效的旗標如下：

| 旗標   | 效果        | 備註                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | 新增零（而不是空格）來組成所需的寬度 |    |
| `-` |  靠左對齊指定寬度內的結果 |   |
| `+`  | `+`如果數位是正數 (以符合否定的正負號，請新增一個字元 `-`)  |   |
| 空白字元 | 如果數位是正數 (以符合否定的 '-' 正負號，請新增額外的空間)  |

Printf `#` 旗標無效，如果使用，將會回報編譯時期錯誤。

值是使用不因文化特性而異的格式。 文化特性設定與格式無關， `printf` 不同之處在于它們會影響 `%O` 和格式化的結果 `%A` 。 如需詳細資訊，請參閱[結構化純文字格式](plaintext-formatting.md)。

## <a name="a-formatting"></a>`%A`樣式

`%A`格式規範是用來以人類看得懂的方式來格式化值，也適用于報告診斷資訊。

### <a name="primitive-values"></a>基本值

使用規範來格式化純文字時 `%A` ，F # 數值會使用其後綴和不因文化特性而異。 使用浮點精確度的10個位置來格式化浮點值。 例如

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

塊

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

使用規範時 `%A` ，字串會使用引號來格式化。 不會新增轉義碼，而是會列印原始字元。 例如

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

塊

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a>.NET 值

使用規範來格式化純文字時 `%A` ，非 F # .net 物件是使用 `x.ToString()` 和所指定的 .net 預設設定來格式化 `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` 。  例如

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

塊

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a>結構化值

使用規範來格式化純文字時 `%A` ，區塊縮排會用於 F # 清單和元組。 如先前範例所示。
陣列的結構也會使用，包括多維度陣列。  一維陣列會以語法顯示 `[| ... |]` 。 例如

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

塊

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

預設列印寬度為80。  您可以使用格式規範中的列印寬度來自訂此寬度。 例如

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

塊

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

將列印寬度指定為0會導致不使用列印寬度。 除了輸出中的內嵌字串包含分行符號以外，會產生一行文字。  例如：

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

塊

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

深度限制4用於順序 (`IEnumerable`) 值，這會顯示為 `seq { ...}` 。 [深度限制] 100 用於清單和陣列值。
例如

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

塊

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

區塊縮排也會用於公用記錄和聯集值的結構。 例如

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

塊

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

如果 `%+A` 使用了，則也會使用反映來顯示記錄和等位的私用結構。 例如：

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

塊

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a>大型、迴圈或深層的嵌套值

大型結構化的值會格式化為最大整體物件節點計數10000。
深層的嵌套值會格式化為深度100。  在這兩種情況下 `...` ，都是用來省略部分輸出。  例如

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

會產生具有部分省略的大型輸出：

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

迴圈會在物件圖形中偵測到，並在偵測 `...` 到迴圈的位置使用。 例如：

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

塊

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a>Lazy、null 和 function 值

當尚未評估值時，延遲值會列印成 `Value is not created` 或對等的文字。

Null 值會列印成， `null` 除非將值的靜態類型判斷為 `null` 允許標記法的聯集類型。

F # 函式值會列印為其內部產生的關閉名稱，例如 `<fun:it@43-7>` 。

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a>使用自訂純文字格式`StructuredFormatDisplay`

使用規範時 `%A` ， `StructuredFormatDisplay` 會遵守類型宣告上的屬性是否存在。  這可用來指定用來顯示值的代理文字和屬性。 例如：

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

塊

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a>藉由覆寫自訂純文字格式`ToString`

的預設執行 `ToString` 在 F # 程式設計中是可觀察的。 通常，預設結果不適合在程式設計人員面向的資訊顯示或使用者輸出中使用，因此，通常會覆寫預設的執行。  

根據預設，F # 記錄和聯集類型會以使用的執行來覆寫的執行 `ToString` `sprintf "%+A"` 。  例如

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

塊

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

針對類別類型，不會提供的預設實作為， `ToString` 而且會使用 .net 預設值，這會報告類型的名稱。 例如

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

塊

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

新增的覆寫 `ToString` 可以提供更好的格式。

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

塊

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a>F # 互動式結構化列印

F # Interactive (`dotnet fsi`) 會使用延伸版本的結構化純文字格式來報告值，並允許其他自訂能力。 如需詳細資訊，請參閱[F # Interactive](fsharp-interactive-options.md)。

## <a name="customize-debug-displays"></a>自訂 debug 顯示

適用于 .NET 的偵錯工具會使用和之類的屬性 `DebuggerDisplay` `DebuggerTypeProxy` ，而且這些屬性會影響偵錯工具檢查視窗中物件的結構化顯示。
F # 編譯器會針對區分聯集和記錄類型自動產生這些屬性，但不會針對類別、介面或結構類型來產生。

F # 純文字格式會忽略這些屬性，但在進行 F # 型別的調試時，執行這些方法以改善顯示會很有用。

## <a name="see-also"></a>另請參閱

- [字串](strings.md)
- [記錄](records.md)
- [差別聯集](discriminated-unions.md)
- [F# 互動](fsharp-interactive-options.md)
