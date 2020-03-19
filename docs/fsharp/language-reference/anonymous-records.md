---
title: 匿名記錄
description: 瞭解如何使用構造和使用匿名記錄，匿名記錄是説明處理資料的語言功能。
ms.date: 06/12/2019
ms.openlocfilehash: ef3aa8fccdb6ff406542932816e4138040845a59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187486"
---
# <a name="anonymous-records"></a>匿名記錄

匿名記錄是命名值的簡單聚合，在使用前不需要聲明。 您可以將它們聲明為結構類型或參考型別。 預設情況下，它們是參考型別。

## <a name="syntax"></a>語法

以下示例演示了匿名記錄語法。 項分隔為`[item]`可選。

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>基本使用方式

匿名記錄最好視為 F# 記錄類型，不需要在具現化之前聲明。

例如，在這裡，如何與生成匿名記錄的函數進行交互：

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

下面的示例擴展了上一`printCircleStats`個示例，該函數將匿名記錄作為輸入：

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

使用`printCircleStats`與輸入類型沒有相同"形狀"的任何匿名記錄類型的調用將無法編譯：

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>結構匿名記錄

匿名記錄也可以定義為使用可選`struct`關鍵字進行結構。 以下示例通過生成和使用結構匿名記錄來增強前一個示例：

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

### <a name="structness-inference"></a>結構推理

結構匿名記錄還允許"結構推理"，其中不需要在呼叫網站指定`struct`關鍵字。 在此示例中，在調用`struct``printCircleStats`時刪除關鍵字：

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

反向模式 （指定`struct`輸入類型何時不是結構匿名記錄 ） 將無法編譯。

## <a name="embedding-anonymous-records-within-other-types"></a>將匿名記錄嵌入其他類型的

聲明案例為記錄[的受歧視工會](discriminated-unions.md)是很有用的。 但是，如果記錄中的資料與受區別的聯合類型相同，則必須將所有類型定義為互遞迴。 使用匿名記錄可避免此限制。 以下是模式與它匹配的示例類型和函數：

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

匿名記錄支援使用[複製和更新運算式構建](copy-and-update-record-expressions.md)。 例如，下面介紹如何構造複製現有資料的匿名記錄的新實例：

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

但是，與命名記錄不同，匿名記錄允許您使用複製和更新運算式構造完全不同的表單。 以下示例採用上一示例中的相同匿名記錄，並將其擴展到新的匿名記錄：

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

還可以從命名記錄實例構造匿名記錄：

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

您還可以將資料複製到引用和結構匿名記錄：

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

匿名記錄具有許多特徵，這些特徵對於完全理解如何使用這些特徵至關重要。

### <a name="anonymous-records-are-nominal"></a>匿名記錄是名義上的

匿名記錄是[名義類型](https://en.wikipedia.org/wiki/Nominal_type_system)。 它們最好視為不需要預先聲明的命名[記錄](records.md)類型（也是名義上的）。

請考慮以下包含兩個匿名記錄聲明的示例：

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

`x`和`y`值的類型不同，並且彼此不相容。 它們不相等，也不可比擬。 為了說明這一點，請考慮命名的記錄等效項：

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

與命名的記錄等效項相比，匿名記錄在類型等效性或比較方面沒有任何內在區別。

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>匿名記錄使用結構相等性和比較

與記錄類型一樣，匿名記錄在結構上是等同的，並且具有可比性。 僅當所有組成類型都支援相等性和比較性（如記錄類型）時，才如此。 為了支援相等或比較，兩個匿名記錄必須具有相同的"形狀"。

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>匿名記錄可序列化

您可以像使用命名記錄一樣序列化匿名記錄。 下面是一個使用[牛頓軟的示例。](https://www.nuget.org/packages/Newtonsoft.Json/)

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

匿名記錄可用於通過網路發送羽量級資料，而無需預先為序列化/反序列化類型定義域。

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>匿名記錄與 C# 匿名型別交互操作

可以使用需要使用[C# 匿名型別的](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).NET API。 使用匿名記錄進行交互操作的 C# 匿名型別微不足道。 下面的示例演示如何使用匿名記錄來調用需要匿名型別的[LINQ](../../csharp/programming-guide/concepts/linq/index.md)重載：

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

在 .NET 中使用許多其他 API 需要使用匿名型別傳遞。 匿名記錄是您處理這些記錄的工具。

## <a name="limitations"></a>限制

匿名記錄的使用有一些限制。 有些是其設計固有的，但另一些是可以改變的。

### <a name="limitations-with-pattern-matching"></a>模式匹配的限制

匿名記錄不支援模式匹配，與命名記錄不同。 有三個原因：

1. 模式必須考慮匿名記錄的每個欄位，這與命名的記錄類型不同。 這是因為匿名記錄不支援結構子類型 - 它們是標稱類型。
2. 由於 （1），無法在模式匹配運算式中具有其他模式，因為每個不同的模式都意味著不同的匿名記錄類型。
3. 由於 （3），任何匿名記錄模式將比使用"點"標記法更詳細。

有一個開放語言建議，[允許在有限的上下文中進行模式匹配](https://github.com/fsharp/fslang-suggestions/issues/713)。

### <a name="limitations-with-mutability"></a>具有可變性的限制

當前無法使用`mutable`資料定義匿名記錄。 有一個[開放語言建議](https://github.com/fsharp/fslang-suggestions/issues/732)，以允許可變數據。

### <a name="limitations-with-struct-anonymous-records"></a>結構匿名記錄的限制

無法將結構匿名記錄聲明為`IsByRefLike`或`IsReadOnly`。 對於`IsByRefLike`和`IsReadOnly`匿名記錄，有一個[開放語言建議](https://github.com/fsharp/fslang-suggestions/issues/712)。
