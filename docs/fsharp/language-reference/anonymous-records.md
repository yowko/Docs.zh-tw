---
title: 匿名記錄
description: 瞭解如何使用構造和使用匿名記錄,匿名記錄是幫助處理數據的語言功能。
ms.date: 06/12/2019
ms.openlocfilehash: 121f0f638dff2ae529b2488d8e3b1ad9c064cf90
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738506"
---
# <a name="anonymous-records"></a><span data-ttu-id="0a026-103">匿名記錄</span><span class="sxs-lookup"><span data-stu-id="0a026-103">Anonymous Records</span></span>

<span data-ttu-id="0a026-104">匿名記錄是命名值的簡單聚合,在使用前不需要聲明。</span><span class="sxs-lookup"><span data-stu-id="0a026-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="0a026-105">您可以將它們聲明為結構類型或引用類型。</span><span class="sxs-lookup"><span data-stu-id="0a026-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="0a026-106">預設情況下,它們是引用類型。</span><span class="sxs-lookup"><span data-stu-id="0a026-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a026-107">語法</span><span class="sxs-lookup"><span data-stu-id="0a026-107">Syntax</span></span>

<span data-ttu-id="0a026-108">以下示例演示了匿名記錄語法。</span><span class="sxs-lookup"><span data-stu-id="0a026-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="0a026-109">項分隔為`[item]`可選。</span><span class="sxs-lookup"><span data-stu-id="0a026-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="0a026-110">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="0a026-110">Basic usage</span></span>

<span data-ttu-id="0a026-111">匿名記錄最好視為 F# 記錄類型,不需要在實例化之前聲明。</span><span class="sxs-lookup"><span data-stu-id="0a026-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="0a026-112">例如,在這裡,如何與生成匿名記錄的函數進行交互:</span><span class="sxs-lookup"><span data-stu-id="0a026-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="0a026-113">下面的範例擴展了上一`printCircleStats`個範例,該函數將匿名記錄作為輸入:</span><span class="sxs-lookup"><span data-stu-id="0a026-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="0a026-114">使用`printCircleStats`與輸入類型沒有相同「形狀」的任何匿名記錄類型的呼叫將無法編譯:</span><span class="sxs-lookup"><span data-stu-id="0a026-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="0a026-115">結構匿名記錄</span><span class="sxs-lookup"><span data-stu-id="0a026-115">Struct anonymous records</span></span>

<span data-ttu-id="0a026-116">匿名記錄也可以定義為使用可選`struct`關鍵字進行結構。</span><span class="sxs-lookup"><span data-stu-id="0a026-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="0a026-117">以下範例透過產生和使用結構匿名記錄來增強前一個範例:</span><span class="sxs-lookup"><span data-stu-id="0a026-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="0a026-118">結構推理</span><span class="sxs-lookup"><span data-stu-id="0a026-118">Structness inference</span></span>

<span data-ttu-id="0a026-119">結構匿名記錄還允許「結構推理」,其中不需要在呼叫網站指定`struct`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0a026-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="0a026-120">這個範例中, 在呼`struct``printCircleStats`叫 時移除關鍵字:</span><span class="sxs-lookup"><span data-stu-id="0a026-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="0a026-121">反向模式 (`struct`指定輸入類型何時不是結構匿名記錄 ) 將無法編譯。</span><span class="sxs-lookup"><span data-stu-id="0a026-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="0a026-122">將匿名紀錄嵌入其他類型的</span><span class="sxs-lookup"><span data-stu-id="0a026-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="0a026-123">聲明案例為記錄[的受歧視工會](discriminated-unions.md)是很有用的。</span><span class="sxs-lookup"><span data-stu-id="0a026-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="0a026-124">但是,如果記錄中的數據與受區別的聯合類型相同,則必須將所有類型定義為互遞歸。</span><span class="sxs-lookup"><span data-stu-id="0a026-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="0a026-125">使用匿名記錄可避免此限制。</span><span class="sxs-lookup"><span data-stu-id="0a026-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="0a026-126">以下是模式與它符合的範例類型和函數:</span><span class="sxs-lookup"><span data-stu-id="0a026-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="0a026-127">複製並更新式</span><span class="sxs-lookup"><span data-stu-id="0a026-127">Copy and update expressions</span></span>

<span data-ttu-id="0a026-128">匿名紀錄支援使用[複製與更新表示式建譯](copy-and-update-record-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="0a026-129">例如,下面介紹如何建構複製現有數據的匿名記錄的新實例:</span><span class="sxs-lookup"><span data-stu-id="0a026-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="0a026-130">但是,與命名記錄不同,匿名記錄允許您使用複製和更新表達式構造完全不同的窗體。</span><span class="sxs-lookup"><span data-stu-id="0a026-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="0a026-131">以下範例採用上一示例中的相同匿名記錄,並將其擴展到新的匿名記錄:</span><span class="sxs-lookup"><span data-stu-id="0a026-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="0a026-132">還可以從命名記錄實例建構匿名記錄:</span><span class="sxs-lookup"><span data-stu-id="0a026-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="0a026-133">您還可以將資料複製到參考和結構匿名記錄:</span><span class="sxs-lookup"><span data-stu-id="0a026-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="0a026-134">匿名記錄的屬性</span><span class="sxs-lookup"><span data-stu-id="0a026-134">Properties of anonymous records</span></span>

<span data-ttu-id="0a026-135">匿名記錄具有許多特徵,這些特徵對於完全理解如何使用這些特徵至關重要。</span><span class="sxs-lookup"><span data-stu-id="0a026-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="0a026-136">匿名紀錄是名義上的</span><span class="sxs-lookup"><span data-stu-id="0a026-136">Anonymous records are nominal</span></span>

<span data-ttu-id="0a026-137">匿名紀錄是[一個名義類型](https://en.wikipedia.org/wiki/Nominal_type_system)。</span><span class="sxs-lookup"><span data-stu-id="0a026-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="0a026-138">它們最好視為不需要預先聲明的命名[記錄](records.md)類型(也是名義上的)。</span><span class="sxs-lookup"><span data-stu-id="0a026-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="0a026-139">請考慮以下包含兩個匿名記錄聲明的範例:</span><span class="sxs-lookup"><span data-stu-id="0a026-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="0a026-140">`x`和`y`值的類型不同,並且彼此不相容。</span><span class="sxs-lookup"><span data-stu-id="0a026-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="0a026-141">它們不相等,也不可比擬。</span><span class="sxs-lookup"><span data-stu-id="0a026-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="0a026-142">為了說明這一點,請考慮命名的記錄等效項:</span><span class="sxs-lookup"><span data-stu-id="0a026-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="0a026-143">與命名的記錄等效項相比,匿名記錄在類型等效性或比較方面沒有任何內在區別。</span><span class="sxs-lookup"><span data-stu-id="0a026-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="0a026-144">匿名紀錄使用結構相等性和比較</span><span class="sxs-lookup"><span data-stu-id="0a026-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="0a026-145">與記錄類型一樣,匿名記錄在結構上是等同的,並且具有可比性。</span><span class="sxs-lookup"><span data-stu-id="0a026-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="0a026-146">僅當所有組成類型都支援相等性和比較性(如記錄類型)時,才如此。</span><span class="sxs-lookup"><span data-stu-id="0a026-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="0a026-147">為了支援相等或比較,兩個匿名記錄必須具有相同的"形狀"。</span><span class="sxs-lookup"><span data-stu-id="0a026-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="0a026-148">匿名記錄可序列化</span><span class="sxs-lookup"><span data-stu-id="0a026-148">Anonymous records are serializable</span></span>

<span data-ttu-id="0a026-149">您可以像使用命名記錄一樣序列化匿名記錄。</span><span class="sxs-lookup"><span data-stu-id="0a026-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="0a026-150">下面是一個使用[牛頓軟的範例。](https://www.nuget.org/packages/Newtonsoft.Json/)</span><span class="sxs-lookup"><span data-stu-id="0a026-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="0a026-151">匿名記錄可用於通過網路發送輕量級數據,而無需預先為序列化/反序列化類型定義域。</span><span class="sxs-lookup"><span data-stu-id="0a026-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="0a026-152">匿名記錄與 C# 匿名類型互通</span><span class="sxs-lookup"><span data-stu-id="0a026-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="0a026-153">可以使用需要使用[C# 匿名類型的](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).NET API。</span><span class="sxs-lookup"><span data-stu-id="0a026-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="0a026-154">使用匿名記錄進行互操作的 C# 匿名類型微不足道。</span><span class="sxs-lookup"><span data-stu-id="0a026-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="0a026-155">下面的範例展示如何使用匿名記錄來呼叫需要匿名類型的[LINQ](../../csharp/programming-guide/concepts/linq/index.md)重載:</span><span class="sxs-lookup"><span data-stu-id="0a026-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="0a026-156">在 .NET 中使用許多其他 API 需要使用匿名類型傳遞。</span><span class="sxs-lookup"><span data-stu-id="0a026-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="0a026-157">匿名記錄是您處理這些記錄的工具。</span><span class="sxs-lookup"><span data-stu-id="0a026-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="0a026-158">限制</span><span class="sxs-lookup"><span data-stu-id="0a026-158">Limitations</span></span>

<span data-ttu-id="0a026-159">匿名記錄的使用有一些限制。</span><span class="sxs-lookup"><span data-stu-id="0a026-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="0a026-160">有些是其設計固有的,但另一些是可以改變的。</span><span class="sxs-lookup"><span data-stu-id="0a026-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="0a026-161">模式符合的限制</span><span class="sxs-lookup"><span data-stu-id="0a026-161">Limitations with pattern matching</span></span>

<span data-ttu-id="0a026-162">匿名記錄不支援模式匹配,與命名記錄不同。</span><span class="sxs-lookup"><span data-stu-id="0a026-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="0a026-163">有三個原因:</span><span class="sxs-lookup"><span data-stu-id="0a026-163">There are three reasons:</span></span>

1. <span data-ttu-id="0a026-164">模式必須考慮匿名記錄的每個欄位,這與命名的記錄類型不同。</span><span class="sxs-lookup"><span data-stu-id="0a026-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="0a026-165">這是因為匿名記錄不支援結構子類型 - 它們是標稱類型。</span><span class="sxs-lookup"><span data-stu-id="0a026-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="0a026-166">由於 (1),無法在模式匹配表達式中具有其他模式,因為每個不同的模式都意味著不同的匿名記錄類型。</span><span class="sxs-lookup"><span data-stu-id="0a026-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="0a026-167">由於 (3),任何匿名記錄模式將比使用"點"表示法更詳細。</span><span class="sxs-lookup"><span data-stu-id="0a026-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="0a026-168">有開放語言建議,[允許在有限的上下文中進行模式符合](https://github.com/fsharp/fslang-suggestions/issues/713)。</span><span class="sxs-lookup"><span data-stu-id="0a026-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="0a026-169">具有可變性的限制</span><span class="sxs-lookup"><span data-stu-id="0a026-169">Limitations with mutability</span></span>

<span data-ttu-id="0a026-170">當前無法使用`mutable`數據定義匿名記錄。</span><span class="sxs-lookup"><span data-stu-id="0a026-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="0a026-171">有一個[開放語言建議](https://github.com/fsharp/fslang-suggestions/issues/732),以允許可變數據。</span><span class="sxs-lookup"><span data-stu-id="0a026-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="0a026-172">結構匿名記錄的限制</span><span class="sxs-lookup"><span data-stu-id="0a026-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="0a026-173">無法將結構匿名紀錄聲明為`IsByRefLike``IsReadOnly`或 。</span><span class="sxs-lookup"><span data-stu-id="0a026-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="0a026-174">對`IsByRefLike`對`IsReadOnly`匿名紀錄,有一個[開放語言建議](https://github.com/fsharp/fslang-suggestions/issues/712)。</span><span class="sxs-lookup"><span data-stu-id="0a026-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
