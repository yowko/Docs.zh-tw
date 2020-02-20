---
title: 匿名記錄
description: 瞭解如何使用「結構和使用匿名記錄」，這是一種可協助運算元據的語言功能。
ms.date: 06/12/2019
ms.openlocfilehash: 061fd3279c84b9a3161c687d9392947ee7ce9c83
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453022"
---
# <a name="anonymous-records"></a>匿名記錄

匿名記錄是不需要在使用前宣告之命名值的簡單匯總。 您可以將它們宣告為結構或參考型別。 它們預設是參考型別。

## <a name="syntax"></a>語法

下列範例示範匿名記錄語法。 以 `[item]` 分隔的專案是選擇性的。

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>基本使用方式

匿名記錄最好視為不需要在F#具現化之前宣告的記錄類型。

例如，在這裡您可以如何與產生匿名記錄的函式互動：

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

下列範例會使用接受匿名記錄做為輸入的 `printCircleStats` 函式，在前一個程式中展開：

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

使用任何匿名記錄類型呼叫 `printCircleStats`，而不具有與輸入類型相同的「圖形」，將無法編譯：

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>結構匿名記錄

匿名記錄也可以定義為具有選擇性 `struct` 關鍵字的結構。 下列範例會藉由產生和取用結構匿名記錄來增強前一個：

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

結構匿名記錄也允許「structness 推斷」，您不需要在呼叫位置指定 `struct` 關鍵字。 在此範例中，您會在呼叫 `printCircleStats`時省略 `struct` 關鍵字：

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

反向模式-指定當輸入類型不是結構匿名記錄時 `struct`，將無法編譯。

## <a name="embedding-anonymous-records-within-other-types"></a>在其他類型中內嵌匿名記錄

宣告其案例為記錄的[區分](discriminated-unions.md)等位是很有用的。 但是，如果記錄中的資料與「區分聯集」屬於相同類型，您就必須將所有類型定義為「相互遞迴」。 使用匿名記錄可避免這種限制。 以下是模式比對的範例型別和函式：

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
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

匿名記錄支援具有[複製和更新運算式](copy-and-update-record-expressions.md)的結構。 例如，以下說明如何建立可複製現有資料的匿名記錄新實例：

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

不過，與命名記錄不同的是，匿名記錄可讓您使用複製和更新運算式來建立完全不同的表單。 下列範例會採用先前範例中的相同匿名記錄，並將它展開為新的匿名記錄：

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

您也可以從命名的記錄實例中，建立匿名記錄：

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

匿名記錄具有許多特性，完全瞭解其使用方式是不可或缺的。

### <a name="anonymous-records-are-nominal"></a>匿名記錄為名義

匿名記錄是[名義類型](https://en.wikipedia.org/wiki/Nominal_type_system)。 它們最好視為不需要前期宣告的命名[記錄](records.md)類型（也就是名義）。

請考慮下列包含兩個匿名記錄宣告的範例：

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x` 和 `y` 值的類型不同，而且彼此不相容。 它們不會 equatable，而且也無法比較。 為了說明這一點，請考慮名為的記錄對等用法：

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

與匿名記錄相比，與對應的類型相等或比較時，與其命名的記錄對等專案之間，沒有任何本質上的差異。

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>匿名記錄使用結構相等和比較

就像記錄類型，匿名記錄在結構上是 equatable 且可比較的。 只有當所有組成型別都支援相等和比較（例如記錄類型）時，才會出現這種情況。 若要支援相等或比較，兩個匿名記錄必須具有相同的「圖形」。

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>匿名記錄可序列化

您可以序列化匿名記錄，就像您可以使用命名的記錄一樣。 以下是使用[Newtonsoft](https://www.nuget.org/packages/Newtonsoft.Json/)的範例：

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip') 

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

匿名記錄適用于透過網路傳送輕量資料，而不需要事先定義序列化/還原序列化類型的網域。

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>匿名記錄與C#匿名型別相交互操作

您可以使用需要使用[ C#匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)的 .net API。 C#匿名型別是使用匿名記錄來與相交互操作的簡單類型。 下列範例顯示如何使用匿名記錄來呼叫需要匿名型別的[LINQ](../../csharp/programming-guide/concepts/linq/index.md)多載：

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

在 .NET 中，有許多其他應用程式開發介面需要使用傳入匿名型別。 匿名記錄是您用來處理它們的工具。

## <a name="limitations"></a>限制

匿名記錄的使用方式有一些限制。 有些是其設計的固有部分，但其他則適合變更。

### <a name="limitations-with-pattern-matching"></a>模式比對的限制

匿名記錄不支援模式比對，不同于命名的記錄。 有三個原因：

1. 模式必須考慮匿名記錄的每個欄位，而不像命名的記錄類型。 這是因為匿名記錄不支援結構化 subtyping –它們是名義類型。
2. 由於（1），模式比對運算式中沒有其他模式的功能，因為每個不同的模式都代表不同的匿名記錄類型。
3. 由於（3），任何匿名記錄模式會比使用「點」標記法更為詳細。

有一個開放語言建議，可[在有限的內容中允許模式](https://github.com/fsharp/fslang-suggestions/issues/713)比對。

### <a name="limitations-with-mutability"></a>可變動性的限制

目前無法定義具有 `mutable` 資料的匿名記錄。 有開放的[語言建議](https://github.com/fsharp/fslang-suggestions/issues/732)可允許變動的資料。

### <a name="limitations-with-struct-anonymous-records"></a>結構匿名記錄的限制

不可能將結構匿名記錄宣告為 `IsByRefLike` 或 `IsReadOnly`。 `IsByRefLike` 和 `IsReadOnly` 匿名記錄都有[開放的語言建議](https://github.com/fsharp/fslang-suggestions/issues/712)。
