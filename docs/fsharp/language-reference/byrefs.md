---
title: Byrefs
description: 深入瞭解中F#的 byref 和 byref 型別，其適用于低層級的程式設計。
ms.date: 11/04/2019
ms.openlocfilehash: 05a40059ad5b72829233b0c4135c76eb1cff4da5
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965811"
---
# <a name="byrefs"></a><span data-ttu-id="805e4-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="805e4-103">Byrefs</span></span>

<span data-ttu-id="805e4-104">F#有兩個主要的功能領域，可應付低層級程式設計的空間：</span><span class="sxs-lookup"><span data-stu-id="805e4-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="805e4-105">`byref`/`inref`/`outref` 類型，也就是 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="805e4-106">它們對使用方式有限制，因此您無法編譯在執行時間不正確程式。</span><span class="sxs-lookup"><span data-stu-id="805e4-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="805e4-107">`byref`類似的結構，這是具有類似的語義和 `byref<'T>`的編譯時間限制的[結構](structures.md)。</span><span class="sxs-lookup"><span data-stu-id="805e4-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="805e4-108">其中一個範例是 <xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="805e4-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="805e4-109">語法</span><span class="sxs-lookup"><span data-stu-id="805e4-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="805e4-110">Byref、inref 和 outref</span><span class="sxs-lookup"><span data-stu-id="805e4-110">Byref, inref, and outref</span></span>

<span data-ttu-id="805e4-111">有三種形式的 `byref`：</span><span class="sxs-lookup"><span data-stu-id="805e4-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="805e4-112">`inref<'T>`，這是用來讀取基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="805e4-113">`outref<'T>`，用於寫入基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="805e4-114">`byref<'T>`，這是用來讀取和寫入基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="805e4-115">`byref<'T>` 可以在預期 `inref<'T>` 的情況下傳遞。</span><span class="sxs-lookup"><span data-stu-id="805e4-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="805e4-116">同樣地，您可以在預期 `outref<'T>` 的位置傳遞 `byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="805e4-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="805e4-117">使用 byref</span><span class="sxs-lookup"><span data-stu-id="805e4-117">Using byrefs</span></span>

<span data-ttu-id="805e4-118">若要使用 `inref<'T>`，您需要取得具有 `&`的指標值：</span><span class="sxs-lookup"><span data-stu-id="805e4-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="805e4-119">若要使用 `outref<'T>` 或 `byref<'T>`來寫入指標，您也必須將此值設為您抓取 `mutable`的指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="805e4-120">如果您只是要撰寫指標，而不是讀取它，請考慮使用 `outref<'T>`，而不是 `byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="805e4-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="805e4-121">Inref 的語義</span><span class="sxs-lookup"><span data-stu-id="805e4-121">Inref semantics</span></span>

<span data-ttu-id="805e4-122">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="805e4-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="805e4-123">就語義而言，這表示下列各項：</span><span class="sxs-lookup"><span data-stu-id="805e4-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="805e4-124">`x` 指標的持有者可能只會使用它來讀取值。</span><span class="sxs-lookup"><span data-stu-id="805e4-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="805e4-125">取得至 `SomeStruct` 中的 `struct` 欄位的任何指標都會提供類型 `inref<_>`。</span><span class="sxs-lookup"><span data-stu-id="805e4-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="805e4-126">以下也是 true：</span><span class="sxs-lookup"><span data-stu-id="805e4-126">The following is also true:</span></span>

* <span data-ttu-id="805e4-127">不會隱含其他執行緒或別名不具有 `x`的寫入存取權。</span><span class="sxs-lookup"><span data-stu-id="805e4-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="805e4-128">這並不表示 `SomeStruct` 不會因為 `inref``x` 而變。</span><span class="sxs-lookup"><span data-stu-id="805e4-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="805e4-129">不過，如果F# **是不**變的實值型別，則會將 `this` 指標推斷為 `inref`。</span><span class="sxs-lookup"><span data-stu-id="805e4-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="805e4-130">所有這些規則都表示 `inref` 指標的持有者可能不會修改所指向之記憶體的立即內容。</span><span class="sxs-lookup"><span data-stu-id="805e4-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="805e4-131">Outref 的語義</span><span class="sxs-lookup"><span data-stu-id="805e4-131">Outref semantics</span></span>

<span data-ttu-id="805e4-132">`outref<'T>` 的目的是要指出指標應該只寫入至。</span><span class="sxs-lookup"><span data-stu-id="805e4-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="805e4-133">不預期地，`outref<'T>` 允許讀取基礎值，而不論其名稱。</span><span class="sxs-lookup"><span data-stu-id="805e4-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="805e4-134">這是為了相容性之故。</span><span class="sxs-lookup"><span data-stu-id="805e4-134">This is for compatibility purposes.</span></span> <span data-ttu-id="805e4-135">就語義而言，`outref<'T>` 與 `byref<'T>`不同。</span><span class="sxs-lookup"><span data-stu-id="805e4-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="805e4-136">與 C\# 的 Interop</span><span class="sxs-lookup"><span data-stu-id="805e4-136">Interop with C\#</span></span>

<span data-ttu-id="805e4-137">C#除了 `ref` 傳回以外，支援 `in ref` 和 `out ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="805e4-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="805e4-138">下表顯示如何F#解讀發出的C#內容：</span><span class="sxs-lookup"><span data-stu-id="805e4-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="805e4-139">C#建構</span><span class="sxs-lookup"><span data-stu-id="805e4-139">C# construct</span></span>|<span data-ttu-id="805e4-140">F#推測</span><span class="sxs-lookup"><span data-stu-id="805e4-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="805e4-141">`ref` 傳回值</span><span class="sxs-lookup"><span data-stu-id="805e4-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="805e4-142">`ref readonly` 傳回值</span><span class="sxs-lookup"><span data-stu-id="805e4-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="805e4-143">`in ref` 參數</span><span class="sxs-lookup"><span data-stu-id="805e4-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="805e4-144">`out ref` 參數</span><span class="sxs-lookup"><span data-stu-id="805e4-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="805e4-145">下表顯示發出的F#內容：</span><span class="sxs-lookup"><span data-stu-id="805e4-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="805e4-146">F#建構</span><span class="sxs-lookup"><span data-stu-id="805e4-146">F# construct</span></span>|<span data-ttu-id="805e4-147">發出的結構</span><span class="sxs-lookup"><span data-stu-id="805e4-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="805e4-148">`inref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="805e4-148">`inref<'T>` argument</span></span>|<span data-ttu-id="805e4-149">在引數上 `[In]` 屬性</span><span class="sxs-lookup"><span data-stu-id="805e4-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="805e4-150">`inref<'T>` 傳回</span><span class="sxs-lookup"><span data-stu-id="805e4-150">`inref<'T>` return</span></span>|<span data-ttu-id="805e4-151">值 `modreq` 屬性</span><span class="sxs-lookup"><span data-stu-id="805e4-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="805e4-152">抽象位置或執行中的 `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="805e4-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="805e4-153">`modreq` 引數或傳回</span><span class="sxs-lookup"><span data-stu-id="805e4-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="805e4-154">`outref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="805e4-154">`outref<'T>` argument</span></span>|<span data-ttu-id="805e4-155">在引數上 `[Out]` 屬性</span><span class="sxs-lookup"><span data-stu-id="805e4-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="805e4-156">型別推斷和多載規則</span><span class="sxs-lookup"><span data-stu-id="805e4-156">Type inference and overloading rules</span></span>

<span data-ttu-id="805e4-157">在下列情況下， F#編譯器會推斷 `inref<'T>` 型別：</span><span class="sxs-lookup"><span data-stu-id="805e4-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="805e4-158">具有 `IsReadOnly` 屬性的 .NET 參數或傳回型別。</span><span class="sxs-lookup"><span data-stu-id="805e4-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="805e4-159">結構型別上沒有可變欄位的 `this` 指標。</span><span class="sxs-lookup"><span data-stu-id="805e4-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="805e4-160">衍生自另一個 `inref<_>` 指標之記憶體位置的位址。</span><span class="sxs-lookup"><span data-stu-id="805e4-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="805e4-161">當取得 `inref` 的隱含位址時，會慣用具有類型 `SomeType` 引數的多載，而此多載具有類型 `inref<SomeType>`的引數。</span><span class="sxs-lookup"><span data-stu-id="805e4-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="805e4-162">例如：</span><span class="sxs-lookup"><span data-stu-id="805e4-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="805e4-163">在這兩種情況下，會解析採用 `System.DateTime` 的多載，而不是採用 `inref<System.DateTime>`的多載。</span><span class="sxs-lookup"><span data-stu-id="805e4-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="805e4-164">類似 Byref 的結構</span><span class="sxs-lookup"><span data-stu-id="805e4-164">Byref-like structs</span></span>

<span data-ttu-id="805e4-165">除了 `byref`/`inref`/`outref` 三個以外，您還可以定義自己的結構，以符合類似 `byref`的語義。</span><span class="sxs-lookup"><span data-stu-id="805e4-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="805e4-166">這會透過 <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> 屬性來完成：</span><span class="sxs-lookup"><span data-stu-id="805e4-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="805e4-167">`IsByRefLike` 不表示 `Struct`。</span><span class="sxs-lookup"><span data-stu-id="805e4-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="805e4-168">這兩者都必須存在於類型上。</span><span class="sxs-lookup"><span data-stu-id="805e4-168">Both must be present on the type.</span></span>

<span data-ttu-id="805e4-169">中F#的「`byref`贊」結構是堆疊系結的實值型別。</span><span class="sxs-lookup"><span data-stu-id="805e4-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="805e4-170">它永遠不會在受控堆積上配置。</span><span class="sxs-lookup"><span data-stu-id="805e4-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="805e4-171">`byref`類似的結構對高效能程式設計很有用，因為它會強制執行一組有關存留期和非捕捉的強式檢查。</span><span class="sxs-lookup"><span data-stu-id="805e4-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="805e4-172">規則包括：</span><span class="sxs-lookup"><span data-stu-id="805e4-172">The rules are:</span></span>

* <span data-ttu-id="805e4-173">它們可用來做為函式參數、方法參數、區域變數、方法傳回。</span><span class="sxs-lookup"><span data-stu-id="805e4-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="805e4-174">它們不能是類別或一般結構的靜態或實例成員。</span><span class="sxs-lookup"><span data-stu-id="805e4-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="805e4-175">它們無法由任何結束結構（`async` 方法或 lambda 運算式）來捕捉。</span><span class="sxs-lookup"><span data-stu-id="805e4-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="805e4-176">它們不能用來做為泛型參數。</span><span class="sxs-lookup"><span data-stu-id="805e4-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="805e4-177">這最後一點對F#管線型程式設計很重要，因為 `|>` 是參數化其輸入類型的泛型函式。</span><span class="sxs-lookup"><span data-stu-id="805e4-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="805e4-178">這項限制可能會在未來 `|>` 放寬，因為它是內嵌的，而且不會對其主體中的非內嵌泛型函式進行任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="805e4-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="805e4-179">雖然這些規則會嚴格限制使用方式，但它們會以安全的方式滿足高效能計算的承諾。</span><span class="sxs-lookup"><span data-stu-id="805e4-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="805e4-180">Byref 傳回</span><span class="sxs-lookup"><span data-stu-id="805e4-180">Byref returns</span></span>

<span data-ttu-id="805e4-181">可以產生和F#取用來自函數或成員的 Byref 回傳。</span><span class="sxs-lookup"><span data-stu-id="805e4-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="805e4-182">使用 `byref`傳回的方法時，會隱含地取值此值。</span><span class="sxs-lookup"><span data-stu-id="805e4-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="805e4-183">例如：</span><span class="sxs-lookup"><span data-stu-id="805e4-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="805e4-184">若要傳回值 byref，包含值的變數必須比目前的範圍長。</span><span class="sxs-lookup"><span data-stu-id="805e4-184">To return a value byref, the variable which contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="805e4-185">此外，若要傳回 byref，請使用 & 值（其中 value 是存留時間超過目前範圍的變數）。</span><span class="sxs-lookup"><span data-stu-id="805e4-185">Also, to return byref, use &value (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="805e4-186">若要避免隱含取值，例如透過多個連鎖呼叫傳遞參考，請使用 `&x` （其中 `x` 是值）。</span><span class="sxs-lookup"><span data-stu-id="805e4-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="805e4-187">您也可以直接指派給 return `byref`。</span><span class="sxs-lookup"><span data-stu-id="805e4-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="805e4-188">請考慮下列（高度命令式）程式：</span><span class="sxs-lookup"><span data-stu-id="805e4-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="805e4-189">此為輸出：</span><span class="sxs-lookup"><span data-stu-id="805e4-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="805e4-190">Byref 的範圍</span><span class="sxs-lookup"><span data-stu-id="805e4-190">Scoping for byrefs</span></span>

<span data-ttu-id="805e4-191">`let`系結的值不能有超過其定義範圍的參考。</span><span class="sxs-lookup"><span data-stu-id="805e4-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="805e4-192">例如，不允許下列情況：</span><span class="sxs-lookup"><span data-stu-id="805e4-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="805e4-193">這會根據您是否使用優化開啟或關閉來進行編譯，而無法取得不同的結果。</span><span class="sxs-lookup"><span data-stu-id="805e4-193">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
