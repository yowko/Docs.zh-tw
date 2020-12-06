---
title: 匿名記錄
description: 瞭解如何使用結構和匿名記錄，這是可協助運算元據的語言功能。
ms.date: 06/12/2019
ms.openlocfilehash: 13950048f02ab74362f8174725f5f8615d9d7654
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739811"
---
# <a name="anonymous-records"></a>匿名記錄

匿名記錄是命名值的簡單匯總，不需要在使用之前宣告。 您可以將它們宣告為結構或參考型別。 它們預設是參考型別。

## <a name="syntax"></a>語法

下列範例示範匿名記錄語法。 分隔為 `[item]` 的專案是選擇性的。

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>基本使用方式

匿名記錄最好被視為不需要在具現化之前宣告的 F # 記錄類型。

例如，在這裡，您可以如何與產生匿名記錄的函式互動：

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

下列範例 `printCircleStats` 會使用接受匿名記錄做為輸入的函式來展開上一個範例：

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

`printCircleStats`使用任何匿名記錄類型呼叫，而該類型與輸入類型沒有相同的「圖形」，將無法編譯：

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>結構匿名記錄

您也可以使用選擇性關鍵字將匿名記錄定義為結構 `struct` 。 下列範例會藉由產生和取用結構匿名記錄來擴大前一個範例：

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Structness 推斷

結構匿名記錄也允許「structness 推斷」，您不需要在呼叫位置指定 `struct` 關鍵字。 在此範例中，您會在 `struct` 呼叫時省略關鍵字 `printCircleStats` ：

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

反向模式-指定 `struct` 輸入類型不是結構匿名記錄時，將無法編譯。

## <a name="embedding-anonymous-records-within-other-types"></a>在其他類型中內嵌匿名記錄

宣告案例為記錄的 [區分](discriminated-unions.md) 等位是很有用的。 但是，如果記錄中的資料與不同聯集的類型相同，您就必須將所有類型定義為相互遞迴。 使用匿名記錄可避免這種限制。 以下是模式比對的範例型別和函數：

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named record for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>複製和更新運算式

匿名記錄支援具有 [複製和更新運算式](copy-and-update-record-expressions.md)的結構。 例如，以下是您可以如何建立匿名記錄的新實例，以複製現有的資料：

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

不過，不同于命名記錄，匿名記錄可讓您使用複製和更新運算式來建立完全不同的表單。 下列範例會使用先前範例中的相同匿名記錄，並將它擴充至新的匿名記錄：

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

您也可以從命名記錄的實例中，建立匿名記錄：

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

您也可以將資料複製到參考和結構匿名記錄：

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>匿名記錄的屬性

匿名記錄有許多特性，對於完全瞭解其使用方式而言是不可或缺的。

### <a name="anonymous-records-are-nominal"></a>匿名記錄為名義

匿名記錄是 [名義類型](https://en.wikipedia.org/wiki/Nominal_type_system)。 最好將它們視為命名 [記錄](records.md) 類型 (這也是不需要前置宣告的名義) 。

請考慮下列兩個匿名記錄宣告的範例：

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x`和 `y` 值有不同的類型，且彼此不相容。 它們不會 equatable，而且也不能比較。 為了說明這一點，請考慮對等的命名記錄：

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

與類型相等或比較有關的匿名記錄與其命名記錄相等時，並沒有任何固有的差異。

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>匿名記錄會使用結構相等和比較

就像記錄類型一樣，匿名記錄是結構 equatable 且可比較的。 只有在所有組成類型都支援相等和比較（例如記錄類型）的情況下，才會出現此情況。 若要支援相等或比較，兩個匿名記錄必須具有相同的「圖形」。

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>匿名記錄可序列化

您可以將匿名記錄序列化，就像您可以使用命名記錄一樣。 以下是使用 [Newtonsoft.Js的](https://www.nuget.org/packages/Newtonsoft.Json/)範例：

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn $"Name: {phillip.name} Age: %d{phillip.age}"
```

匿名記錄適用于透過網路傳送輕量資料，而不需要事先為您的序列化/還原序列化類型定義網域。

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>匿名記錄與 c # 匿名型別交互操作

您可以使用需要使用 [c # 匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)的 .net API。 C # 匿名型別很容易使用匿名記錄來與相交互操作。 下列範例示範如何使用匿名記錄來呼叫需要匿名型別的 [LINQ](../../csharp/programming-guide/concepts/linq/index.md) 多載：

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn $"{ng.Name} has first letter {ng.FirstLetter}"
```

在整個 .NET 中，有許多其他的 Api 都需要使用匿名型別來傳遞。 匿名記錄是您使用它們的工具。

## <a name="limitations"></a>限制

匿名記錄對於其使用方式有一些限制。 有些是其設計固有的，但有些則適合變更。

### <a name="limitations-with-pattern-matching"></a>模式比對的限制

匿名記錄不支援模式比對，不同于命名記錄。 有三個原因：

1. 模式必須考慮匿名記錄的每個欄位，與命名的記錄類型不同。 這是因為匿名記錄不支援結構化 subtyping –它們是名義類型。
2. 由於 (1) ，因此無法在模式比對運算式中使用其他模式，因為每個不同的模式會代表不同的匿名記錄類型。
3. 由於 (3) ，任何匿名記錄模式都比使用 "dot" 標記法更詳細。

有開放語言的建議，可 [讓您在有限的內容中進行模式](https://github.com/fsharp/fslang-suggestions/issues/713)比對。

### <a name="limitations-with-mutability"></a>可變動性的限制

目前無法以資料定義匿名記錄 `mutable` 。 有開放的 [語言建議](https://github.com/fsharp/fslang-suggestions/issues/732) 可允許可變數據。

### <a name="limitations-with-struct-anonymous-records"></a>結構匿名記錄的限制

您無法將結構匿名記錄宣告為 `IsByRefLike` 或 `IsReadOnly` 。 和匿名記錄有 [開放的語言建議](https://github.com/fsharp/fslang-suggestions/issues/712) `IsByRefLike` `IsReadOnly` 。
