---
title: 匿名的記錄
description: 了解如何使用建構，並使用匿名的記錄，可協助進行資料操作語言功能。
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041802"
---
# <a name="anonymous-records"></a><span data-ttu-id="d64ca-103">匿名的記錄</span><span class="sxs-lookup"><span data-stu-id="d64ca-103">Anonymous Records</span></span>

<span data-ttu-id="d64ca-104">匿名的記錄是不需要使用前宣告的具名值的簡單彙總。</span><span class="sxs-lookup"><span data-stu-id="d64ca-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="d64ca-105">您可以將它們宣告為結構或參考類型上。</span><span class="sxs-lookup"><span data-stu-id="d64ca-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="d64ca-106">它們是預設的參考型別。</span><span class="sxs-lookup"><span data-stu-id="d64ca-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="d64ca-107">語法</span><span class="sxs-lookup"><span data-stu-id="d64ca-107">Syntax</span></span>

<span data-ttu-id="d64ca-108">下列範例示範匿名記錄語法。</span><span class="sxs-lookup"><span data-stu-id="d64ca-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="d64ca-109">項目分隔為`[item]`是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d64ca-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="d64ca-110">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="d64ca-110">Basic usage</span></span>

<span data-ttu-id="d64ca-111">匿名記錄最適合想像成F#記錄不必具現化之前宣告的類型。</span><span class="sxs-lookup"><span data-stu-id="d64ca-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="d64ca-112">例如，這裡您可以使用函式互動的方式，會產生匿名的記錄：</span><span class="sxs-lookup"><span data-stu-id="d64ca-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="d64ca-113">下列範例會在與前一個`printCircleStats`採用匿名的記錄，做為輸入的函式：</span><span class="sxs-lookup"><span data-stu-id="d64ca-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="d64ca-114">呼叫`printCircleStats`與任何匿名的記錄型別沒有相同的 「 圖形 」，因為在輸入型別將無法編譯：</span><span class="sxs-lookup"><span data-stu-id="d64ca-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="d64ca-115">匿名結構的記錄</span><span class="sxs-lookup"><span data-stu-id="d64ca-115">Struct anonymous records</span></span>

<span data-ttu-id="d64ca-116">匿名記錄也可以定義與選擇性結構`struct`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d64ca-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="d64ca-117">下列範例會擴大上一個產生和取用結構匿名的記錄：</span><span class="sxs-lookup"><span data-stu-id="d64ca-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="d64ca-118">Structness 推斷</span><span class="sxs-lookup"><span data-stu-id="d64ca-118">Structness inference</span></span>

<span data-ttu-id="d64ca-119">結構匿名記錄也可讓 「 structness 推斷 」，您不需要指定`struct`呼叫位置的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d64ca-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="d64ca-120">在此範例中，您 elide`struct`關鍵字時呼叫`printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="d64ca-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="d64ca-121">反向模式-指定`struct`時輸入的類型不是結構匿名的記錄集，將無法編譯。</span><span class="sxs-lookup"><span data-stu-id="d64ca-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="d64ca-122">內嵌在其他類型的匿名資料錄</span><span class="sxs-lookup"><span data-stu-id="d64ca-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="d64ca-123">它適合用來宣告[差別聯集](discriminated-unions.md)大小寫不會有記錄。</span><span class="sxs-lookup"><span data-stu-id="d64ca-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="d64ca-124">但是，如果相同的已區分的聯集類型的記錄中的資料，您必須定義所有型別為相互遞迴。</span><span class="sxs-lookup"><span data-stu-id="d64ca-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="d64ca-125">使用匿名的記錄，可避免這項限制。</span><span class="sxs-lookup"><span data-stu-id="d64ca-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="d64ca-126">以下是範例類型和函式該模式會透過它比對：</span><span class="sxs-lookup"><span data-stu-id="d64ca-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="d64ca-127">複製並更新運算式</span><span class="sxs-lookup"><span data-stu-id="d64ca-127">Copy and update expressions</span></span>

<span data-ttu-id="d64ca-128">匿名記錄支援建構函式與[複製並更新運算式](copy-and-update-record-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d64ca-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="d64ca-129">例如，以下是如何建構複製現有的匿名資料錄的新執行個體資料：</span><span class="sxs-lookup"><span data-stu-id="d64ca-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="d64ca-130">不過，與不同的具名記錄，是匿名的記錄可讓您建構完全不同的形式複製與並更新運算式。</span><span class="sxs-lookup"><span data-stu-id="d64ca-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="d64ca-131">下列範例會採用前一個範例相同的匿名記錄，並將它擴充到新的匿名記錄：</span><span class="sxs-lookup"><span data-stu-id="d64ca-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="d64ca-132">此外，也可以建構匿名的記錄，從執行個體的具名記錄：</span><span class="sxs-lookup"><span data-stu-id="d64ca-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="d64ca-133">您也可以在參考和結構的匿名記錄來回複製資料：</span><span class="sxs-lookup"><span data-stu-id="d64ca-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="d64ca-134">匿名記錄的屬性</span><span class="sxs-lookup"><span data-stu-id="d64ca-134">Properties of anonymous records</span></span>

<span data-ttu-id="d64ca-135">匿名記錄都有許多是必要項目完全了解如何使用的特性。</span><span class="sxs-lookup"><span data-stu-id="d64ca-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="d64ca-136">匿名記錄是名義上</span><span class="sxs-lookup"><span data-stu-id="d64ca-136">Anonymous records are nominal</span></span>

<span data-ttu-id="d64ca-137">匿名記錄[名義型別](https://en.wikipedia.org/wiki/Nominal_type_system)。</span><span class="sxs-lookup"><span data-stu-id="d64ca-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="d64ca-138">它們是最佳的想法，因為名為[記錄](records.md)類型 （也就是也名義） 不需要預付的宣告。</span><span class="sxs-lookup"><span data-stu-id="d64ca-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="d64ca-139">請考慮下列範例使用兩個匿名記錄宣告：</span><span class="sxs-lookup"><span data-stu-id="d64ca-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="d64ca-140">`x`和`y`值具有不同的類型，並與彼此不相容。</span><span class="sxs-lookup"><span data-stu-id="d64ca-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="d64ca-141">它們不是可比較相等，故無法比較。</span><span class="sxs-lookup"><span data-stu-id="d64ca-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="d64ca-142">為了說明這點，認為是具名的記錄相等的：</span><span class="sxs-lookup"><span data-stu-id="d64ca-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="d64ca-143">沒有任何關於匿名記錄有關類型的對應項或比較時，相較於其具名的記錄對等項目本質上不同。</span><span class="sxs-lookup"><span data-stu-id="d64ca-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="d64ca-144">匿名的記錄，請使用結構化相等和比較</span><span class="sxs-lookup"><span data-stu-id="d64ca-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="d64ca-145">記錄類型，例如匿名的記錄是結構上相等和比較。</span><span class="sxs-lookup"><span data-stu-id="d64ca-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="d64ca-146">這只是如果所有構成類型都支援相等和比較，例如具有 record 類型則為 true。</span><span class="sxs-lookup"><span data-stu-id="d64ca-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="d64ca-147">若要支援等號比較時，兩個匿名的記錄必須相同的 「 圖形 」。</span><span class="sxs-lookup"><span data-stu-id="d64ca-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="d64ca-148">匿名記錄都是可序列化</span><span class="sxs-lookup"><span data-stu-id="d64ca-148">Anonymous records are serializable</span></span>

<span data-ttu-id="d64ca-149">正如同您可以使用具名的記錄，您可以將序列化匿名的記錄。</span><span class="sxs-lookup"><span data-stu-id="d64ca-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="d64ca-150">以下是範例使用[Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="d64ca-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="d64ca-151">匿名記錄可用於透過網路而不需要定義您序列化/還原序列化的型別最前面位置的網域傳送輕量的資料。</span><span class="sxs-lookup"><span data-stu-id="d64ca-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="d64ca-152">匿名的記錄與交互操作C#匿名型別</span><span class="sxs-lookup"><span data-stu-id="d64ca-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="d64ca-153">您可使用.NET API，需要使用[C#匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d64ca-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="d64ca-154">C#匿名型別是 trivial 使用匿名的記錄與交互操作。</span><span class="sxs-lookup"><span data-stu-id="d64ca-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="d64ca-155">下列範例示範如何使用匿名的記錄來呼叫[LINQ](../../csharp/programming-guide/concepts/linq/index.md)需要匿名型別多載：</span><span class="sxs-lookup"><span data-stu-id="d64ca-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="d64ca-156">有許多用於整個.NET 需要傳遞匿名類型中使用之其他 Api。</span><span class="sxs-lookup"><span data-stu-id="d64ca-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="d64ca-157">匿名的記錄會加以使用的工具。</span><span class="sxs-lookup"><span data-stu-id="d64ca-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="d64ca-158">限制</span><span class="sxs-lookup"><span data-stu-id="d64ca-158">Limitations</span></span>

<span data-ttu-id="d64ca-159">匿名記錄其使用方式中有一些限制。</span><span class="sxs-lookup"><span data-stu-id="d64ca-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="d64ca-160">有些是將它們的設計原本就，但有些則是適合變更。</span><span class="sxs-lookup"><span data-stu-id="d64ca-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="d64ca-161">模式比對的限制</span><span class="sxs-lookup"><span data-stu-id="d64ca-161">Limitations with pattern matching</span></span>

<span data-ttu-id="d64ca-162">匿名記錄並不支援模式比對，不同於已命名的記錄。</span><span class="sxs-lookup"><span data-stu-id="d64ca-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="d64ca-163">有三個原因：</span><span class="sxs-lookup"><span data-stu-id="d64ca-163">There are three reasons:</span></span>

1. <span data-ttu-id="d64ca-164">模式必須以帳戶為匿名的記錄，不同於已命名的記錄類型的每個欄位。</span><span class="sxs-lookup"><span data-stu-id="d64ca-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="d64ca-165">這是因為匿名的記錄不支援結構化的子型別，它們名義型別。</span><span class="sxs-lookup"><span data-stu-id="d64ca-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="d64ca-166">(1)，因為沒有任何能夠在模式比對運算式中，有其他模式因為每個不同的模式會代表不同匿名的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="d64ca-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="d64ca-167">(3)，因為任何匿名的記錄模式會比使用 「 點 」 標記法的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d64ca-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="d64ca-168">沒有開啟的語言建議[允許在模式比對限制內容](https://github.com/fsharp/fslang-suggestions/issues/713)。</span><span class="sxs-lookup"><span data-stu-id="d64ca-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="d64ca-169">可變動性的限制</span><span class="sxs-lookup"><span data-stu-id="d64ca-169">Limitations with mutability</span></span>

<span data-ttu-id="d64ca-170">不是目前可以定義具有匿名記錄`mutable`資料。</span><span class="sxs-lookup"><span data-stu-id="d64ca-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="d64ca-171">沒有[開啟語言建議](https://github.com/fsharp/fslang-suggestions/issues/732)允許可變動的資料。</span><span class="sxs-lookup"><span data-stu-id="d64ca-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="d64ca-172">具有匿名結構的記錄限制</span><span class="sxs-lookup"><span data-stu-id="d64ca-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="d64ca-173">不可以宣告結構匿名的記錄，當做`IsByRefLike`或`IsReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="d64ca-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="d64ca-174">沒有[開啟語言建議](https://github.com/fsharp/fslang-suggestions/issues/712)若要針對`IsByRefLike`和`IsReadOnly`匿名的記錄。</span><span class="sxs-lookup"><span data-stu-id="d64ca-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
