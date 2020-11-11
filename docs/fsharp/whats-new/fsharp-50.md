---
title: 'F # 5.0 中的新功能-F # 指南'
description: '深入瞭解 F # 5.0 中可用的新功能。'
ms.date: 11/06/2020
ms.openlocfilehash: 0c4c9f42c63a1dc8c90213c43edbadd4061c132d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445827"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="d0c5a-103">F # 5.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="d0c5a-103">What's new in F# 5.0</span></span>

<span data-ttu-id="d0c5a-104">F # 5.0 在 F # 語言和 F# 互動中新增了幾項改進。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="d0c5a-105">它是以 **.net 5** 發行。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-105">It is released with **.NET 5**.</span></span>

## <a name="get-started"></a><span data-ttu-id="d0c5a-106">開始使用</span><span class="sxs-lookup"><span data-stu-id="d0c5a-106">Get started</span></span>

<span data-ttu-id="d0c5a-107">F # 5.0 適用于所有 .NET Core 散發套件和 Visual Studio 工具。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-107">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="d0c5a-108">如需詳細資訊，請參閱 [F #](../get-started/index.md) 入門（英文）以深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-108">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="d0c5a-109">F # 腳本中的套件參考</span><span class="sxs-lookup"><span data-stu-id="d0c5a-109">Package references in F# scripts</span></span>

<span data-ttu-id="d0c5a-110">F # 5 以語法提供 F # 腳本中封裝參考的支援 `#r "nuget:..."` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-110">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="d0c5a-111">例如，請考慮下列套件參考：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-111">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

<span data-ttu-id="d0c5a-112">您也可以在套件名稱之後提供明確的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-112">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="d0c5a-113">封裝參考支援具有原生相依性的套件，例如 ML.NET。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-113">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="d0c5a-114">封裝參考也支援封裝參考相依的特殊需求的封裝 `.dll` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-114">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="d0c5a-115">例如， [FParsec](https://www.nuget.org/packages/FParsec/) 套件用來要求使用者在 `FParsecCS.dll` F# 互動中參考之前，先手動確定其相依的參考 `FParsec.dll` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-115">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="d0c5a-116">這已不再需要，您可以參考封裝，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-116">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

<span data-ttu-id="d0c5a-117">如需封裝參考的詳細資訊，請參閱 [F# 互動](../tutorials/fsharp-interactive/index.md) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-117">For more information on package references, see the [F# Interactive](../tutorials/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="d0c5a-118">字串插補</span><span class="sxs-lookup"><span data-stu-id="d0c5a-118">String interpolation</span></span>

<span data-ttu-id="d0c5a-119">F # 插入字串與 c # 或 JavaScript 插入字串相當類似，因為它們可讓您在字串常值中的「漏洞」內撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-119">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="d0c5a-120">以下是基本範例：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-120">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="d0c5a-121">不過，F # 插入字串也允許型別插補（就像函式一樣 `sprintf` ），以強制插入內容內的運算式符合特定的型別。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-121">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="d0c5a-122">它會使用相同的格式規範。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-122">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="d0c5a-123">在上述輸入的插補範例中， `%s` 需要插補是型別 `string` ，而 `%d` 需要插補是 `integer` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-123">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="d0c5a-124">此外，任何任意的 F # 運算式 (或運算式) 都可以放在插補內容的側邊。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-124">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="d0c5a-125">您甚至可以撰寫更複雜的運算式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-125">It is even possible to write a more complicated expression, like so:</span></span>

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

<span data-ttu-id="d0c5a-126">雖然我們不建議您這麼做，但我們不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-126">Although we don't recommend doing this too much in practice.</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="d0c5a-127">對 nameof 的支援</span><span class="sxs-lookup"><span data-stu-id="d0c5a-127">Support for nameof</span></span>

<span data-ttu-id="d0c5a-128">F # 5 支援 `nameof` 運算子，可解析其使用的符號，並在 F # 來源中產生其名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-128">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="d0c5a-129">這在各種情況下都很有用，例如記錄，並可保護您的記錄免于原始程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-129">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="d0c5a-130">最後一行將會擲回例外狀況，且會在錯誤訊息中顯示「月份」。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-130">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="d0c5a-131">您可以採用幾乎每個 F # 結構的名稱：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-131">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

<span data-ttu-id="d0c5a-132">有三個最後的新增專案是運算子運作方式的變更：加入 `nameof<'type-parameter>` 泛型型別參數的表單，以及在模式比對運算式中做為模式使用的功能 `nameof` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-132">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="d0c5a-133">採用運算子名稱可提供其來源字串。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-133">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="d0c5a-134">如果您需要編譯的表單，請使用運算子的編譯名稱：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-134">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="d0c5a-135">採用型別參數的名稱需要稍微不同的語法：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-135">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp

type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="d0c5a-136">這與 `typeof<'T>` 和 `typedefof<'T>` 運算子類似。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-136">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="d0c5a-137">F # 5 也加入了 `nameof` 可在運算式中使用的模式支援 `match` ：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-137">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

<span data-ttu-id="d0c5a-138">上述程式碼使用 ' nameof '，而不是比對運算式中的字串常值。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-138">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="d0c5a-139">開放式型別宣告</span><span class="sxs-lookup"><span data-stu-id="d0c5a-139">Open type declarations</span></span>

<span data-ttu-id="d0c5a-140">F # 5 也加入了對開放式型別宣告的支援。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-140">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="d0c5a-141">開啟的型別宣告就像在 c # 中開啟靜態類別一樣，除了有些不同的語法和一些稍微不同的行為，以配合 F # 語義。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-141">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="d0c5a-142">使用開放式型別宣告，您可以使用 `open` 任何類型來公開其內部的靜態內容。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-142">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="d0c5a-143">此外，您可以 `open` F # 定義的等位和記錄來公開其內容。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-143">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="d0c5a-144">例如，如果您的模組中有定義聯集，而且想要存取其案例，但不想要開啟整個模組，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-144">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

<span data-ttu-id="d0c5a-145">與 c # 不同的是，當您 `open type` 在兩種類型上公開具有相同名稱的成員時，最後一個型別中的成員會 `open` 遮蔽另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-145">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="d0c5a-146">這與已存在之遮蔽的 F # 語義一致。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-146">This is consistent with F# semantics around shadowing that exist already.</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="d0c5a-147">內建資料類型的一致切割行為</span><span class="sxs-lookup"><span data-stu-id="d0c5a-147">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="d0c5a-148">配量內建 `FSharp.Core` 資料類型的行為 (陣列、清單、字串、2d 陣列、3d 陣列、4d 陣列) 在 F # 5 之前用來不一致。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-148">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="d0c5a-149">某些邊緣案例行為擲回例外狀況，而有些則不會。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-149">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="d0c5a-150">在 F # 5 中，所有內建類型現在都會針對無法產生的配量傳回空白配量：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-150">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="d0c5a-151">固定-Fsharp.core 中3D 和4D 陣列的索引配量</span><span class="sxs-lookup"><span data-stu-id="d0c5a-151">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="d0c5a-152">F # 5.0 使用內建3D 和4D 陣列類型中具有固定索引的配量支援。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-152">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="d0c5a-153">為了說明這一點，請考慮下列3D 陣列：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-153">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="d0c5a-154">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="d0c5a-154">*z = 0*</span></span>
|<span data-ttu-id="d0c5a-155">x\y</span><span class="sxs-lookup"><span data-stu-id="d0c5a-155">x\y</span></span>|<span data-ttu-id="d0c5a-156">0</span><span class="sxs-lookup"><span data-stu-id="d0c5a-156">0</span></span>|<span data-ttu-id="d0c5a-157">1</span><span class="sxs-lookup"><span data-stu-id="d0c5a-157">1</span></span>|
|---|-|-|
|<span data-ttu-id="d0c5a-158">**0**</span><span class="sxs-lookup"><span data-stu-id="d0c5a-158">**0**</span></span>|<span data-ttu-id="d0c5a-159">0</span><span class="sxs-lookup"><span data-stu-id="d0c5a-159">0</span></span>|<span data-ttu-id="d0c5a-160">1</span><span class="sxs-lookup"><span data-stu-id="d0c5a-160">1</span></span>|
|<span data-ttu-id="d0c5a-161">**1**</span><span class="sxs-lookup"><span data-stu-id="d0c5a-161">**1**</span></span>|<span data-ttu-id="d0c5a-162">2</span><span class="sxs-lookup"><span data-stu-id="d0c5a-162">2</span></span>|<span data-ttu-id="d0c5a-163">3</span><span class="sxs-lookup"><span data-stu-id="d0c5a-163">3</span></span>|

<span data-ttu-id="d0c5a-164">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="d0c5a-164">*z = 1*</span></span>
|<span data-ttu-id="d0c5a-165">x\y</span><span class="sxs-lookup"><span data-stu-id="d0c5a-165">x\y</span></span>|<span data-ttu-id="d0c5a-166">0</span><span class="sxs-lookup"><span data-stu-id="d0c5a-166">0</span></span>|<span data-ttu-id="d0c5a-167">1</span><span class="sxs-lookup"><span data-stu-id="d0c5a-167">1</span></span>|
|---|-|-|
|<span data-ttu-id="d0c5a-168">**0**</span><span class="sxs-lookup"><span data-stu-id="d0c5a-168">**0**</span></span>|<span data-ttu-id="d0c5a-169">4</span><span class="sxs-lookup"><span data-stu-id="d0c5a-169">4</span></span>|<span data-ttu-id="d0c5a-170">5</span><span class="sxs-lookup"><span data-stu-id="d0c5a-170">5</span></span>|
|<span data-ttu-id="d0c5a-171">**1**</span><span class="sxs-lookup"><span data-stu-id="d0c5a-171">**1**</span></span>|<span data-ttu-id="d0c5a-172">6</span><span class="sxs-lookup"><span data-stu-id="d0c5a-172">6</span></span>|<span data-ttu-id="d0c5a-173">7</span><span class="sxs-lookup"><span data-stu-id="d0c5a-173">7</span></span>|

<span data-ttu-id="d0c5a-174">如果您想要從陣列解壓縮配量，該怎麼辦 `[| 4; 5 |]` ？</span><span class="sxs-lookup"><span data-stu-id="d0c5a-174">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="d0c5a-175">這現在很簡單！</span><span class="sxs-lookup"><span data-stu-id="d0c5a-175">This is now very simple!</span></span>

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

## <a name="applicative-computation-expressions"></a><span data-ttu-id="d0c5a-176">Applicative 計算運算式</span><span class="sxs-lookup"><span data-stu-id="d0c5a-176">Applicative Computation Expressions</span></span>

<span data-ttu-id="d0c5a-177">目前使用的[計算運算式 (CEs) ](../language-reference/computation-expressions.md)來建立「內容計算」的模型，或以更多功能的程式設計易記術語 monadic 計算。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-177">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming friendly terminology, monadic computations.</span></span>

<span data-ttu-id="d0c5a-178">F # 5 引進了 applicative CEs，可提供不同的計算模型。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-178">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="d0c5a-179">Applicative CEs 允許更有效率的計算，前提是每個計算都是獨立的，且其結果會在結尾累積。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-179">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="d0c5a-180">當計算彼此獨立時，也會完整可並行，讓 CE 作者可以撰寫更有效率的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-180">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="d0c5a-181">這項優點有一項限制，但不允許相依于先前計算值的計算。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-181">This benefit comes at a restriction, though: computations that depend on previously-computed values are not allowed.</span></span>

<span data-ttu-id="d0c5a-182">下列範例顯示類型的基本 applicative CE `Result` 。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-182">The follow example shows a basic applicative CE for the `Result` type.</span></span>

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="d0c5a-183">如果您是目前在其程式庫中公開 CEs 的程式庫作者，還有一些需要注意的其他考慮事項。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-183">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a><span data-ttu-id="d0c5a-184">可以在不同的泛型具現化 implemeneted 介面</span><span class="sxs-lookup"><span data-stu-id="d0c5a-184">Interfaces can be implemeneted at different generic instantiations</span></span>

<span data-ttu-id="d0c5a-185">您現在可以在不同的泛型具現化中執行相同的介面：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-185">You can now implement the same interface at different generic instantiations:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="default-interface-member-consumption"></a><span data-ttu-id="d0c5a-186">預設介面成員耗用量</span><span class="sxs-lookup"><span data-stu-id="d0c5a-186">Default interface member consumption</span></span>

<span data-ttu-id="d0c5a-187">F # 5 可讓您使用預設實作為 [介面](../../csharp/tutorials/default-interface-methods-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-187">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="d0c5a-188">請考慮以 c # 定義的介面，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-188">Consider an interface defined in C# like this:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="d0c5a-189">您可以使用 F # 來使用它來執行介面的任何標準方法：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-189">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

<span data-ttu-id="d0c5a-190">這可讓您安全地利用以新式 c # 撰寫的 c # 程式碼和 .NET 元件（當它們希望使用者能夠使用預設的實值）時。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-190">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="d0c5a-191">使用可為 null 的實數值型別簡化 interop</span><span class="sxs-lookup"><span data-stu-id="d0c5a-191">Simplified interop with nullable value types</span></span>

<span data-ttu-id="d0c5a-192">[可為 null 的 (值) 類型](https://docs.microsoft.com/dotnet/api/system.nullable-1) (稱為可為 null 的型別，在過去) 已經由 F # 所支援，但是與它們進行互動是因為您在 `Nullable` `Nullable<SomeType>` 每次想要傳遞值時都必須建立或包裝函式。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-192">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="d0c5a-193">現在， `Nullable<ThatValueType>` 如果目標型別相符，則編譯器會將實值型別隱含轉換成。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-193">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="d0c5a-194">現在可以執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-194">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

## <a name="preview-reverse-indexes"></a><span data-ttu-id="d0c5a-195">預覽：反向索引</span><span class="sxs-lookup"><span data-stu-id="d0c5a-195">Preview: reverse indexes</span></span>

<span data-ttu-id="d0c5a-196">F # 5 也引進了允許反向索引的預覽。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-196">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="d0c5a-197">語法是 `^idx`。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-197">The syntax is `^idx`.</span></span> <span data-ttu-id="d0c5a-198">以下是您可以如何從清單結尾的元素1值：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-198">Here’s how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="d0c5a-199">您也可以為自己的類型定義反向索引。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-199">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="d0c5a-200">若要這樣做，您必須執行下列方法：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-200">To do so, you’ll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="d0c5a-201">以下是此類型的範例 `Span<'T>` ：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-201">Here’s an example for the `Span<'T>` type:</span></span>

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="d0c5a-202">預覽：計算運算式中的自訂關鍵字多載</span><span class="sxs-lookup"><span data-stu-id="d0c5a-202">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="d0c5a-203">計算運算式是程式庫和架構作者的強大功能。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-203">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="d0c5a-204">它們可讓您定義知名的成員，並形成您正在使用之網域的 DSL，以大幅提升元件的表達。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-204">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="d0c5a-205">F # 5 新增了在計算運算式中多載自訂作業的預覽支援。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-205">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="d0c5a-206">它允許寫入和使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d0c5a-206">It allows the following code to be writen and consumed:</span></span>

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

<span data-ttu-id="d0c5a-207">在這項變更之前，您可以撰寫 `InputBuilder` 型別，但是您無法使用它在範例中使用的方式。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-207">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="d0c5a-208">因為可以使用多載、選擇性參數和現在的型別，所以一切都如同 `System.ParamArray` 預期般運作。</span><span class="sxs-lookup"><span data-stu-id="d0c5a-208">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>
