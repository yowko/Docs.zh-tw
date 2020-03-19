---
title: Byrefs
description: 瞭解 F# 中的 byref 和類似 byref 的類型，這些類型用於低級程式設計。
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187044"
---
# <a name="byrefs"></a><span data-ttu-id="96dc9-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="96dc9-103">Byrefs</span></span>

<span data-ttu-id="96dc9-104">F# 具有在低級程式設計領域處理的兩個主要功能領域：</span><span class="sxs-lookup"><span data-stu-id="96dc9-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="96dc9-105">`byref` /類型`inref`，/託管`outref`指標。</span><span class="sxs-lookup"><span data-stu-id="96dc9-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="96dc9-106">它們對使用有限制，因此您不能編譯在運行時不正確程式。</span><span class="sxs-lookup"><span data-stu-id="96dc9-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="96dc9-107">類似`byref`結構的結構，它是具有與 相似的語義和相同的編譯時間限制[的結構](structures.md)`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="96dc9-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="96dc9-108">一個例子是<xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="96dc9-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="96dc9-109">語法</span><span class="sxs-lookup"><span data-stu-id="96dc9-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="96dc9-110">Byref、inref 和 outref</span><span class="sxs-lookup"><span data-stu-id="96dc9-110">Byref, inref, and outref</span></span>

<span data-ttu-id="96dc9-111">有三種形式： `byref`</span><span class="sxs-lookup"><span data-stu-id="96dc9-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="96dc9-112">`inref<'T>`，用於讀取基礎值的託管指標。</span><span class="sxs-lookup"><span data-stu-id="96dc9-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="96dc9-113">`outref<'T>`，用於寫入基礎值的託管指標。</span><span class="sxs-lookup"><span data-stu-id="96dc9-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="96dc9-114">`byref<'T>`，用於讀取和寫入基礎值的託管指標。</span><span class="sxs-lookup"><span data-stu-id="96dc9-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="96dc9-115">`byref<'T>`可以傳遞預期 為`inref<'T>`的 。</span><span class="sxs-lookup"><span data-stu-id="96dc9-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="96dc9-116">同樣，`byref<'T>`可以傳遞預期 為`outref<'T>`的 。</span><span class="sxs-lookup"><span data-stu-id="96dc9-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="96dc9-117">使用參考</span><span class="sxs-lookup"><span data-stu-id="96dc9-117">Using byrefs</span></span>

<span data-ttu-id="96dc9-118">要使用`inref<'T>`， 需要獲取具有 的`&`指標值：</span><span class="sxs-lookup"><span data-stu-id="96dc9-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="96dc9-119">要使用`outref<'T>`或`byref<'T>`寫入指標，還必須使獲取指向`mutable`的指標的值。</span><span class="sxs-lookup"><span data-stu-id="96dc9-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="96dc9-120">如果只編寫指標而不是讀取指標，請考慮使用`outref<'T>`而不是`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="96dc9-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="96dc9-121">Inref 語義</span><span class="sxs-lookup"><span data-stu-id="96dc9-121">Inref semantics</span></span>

<span data-ttu-id="96dc9-122">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="96dc9-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="96dc9-123">從語義上講，這意味著以下內容：</span><span class="sxs-lookup"><span data-stu-id="96dc9-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="96dc9-124">指標的`x`持有者只能使用它讀取該值。</span><span class="sxs-lookup"><span data-stu-id="96dc9-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="96dc9-125">任何獲取到`struct`嵌套在其中`SomeStruct`的欄位的指標都是`inref<_>`給定的類型。</span><span class="sxs-lookup"><span data-stu-id="96dc9-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="96dc9-126">以下內容也是如此：</span><span class="sxs-lookup"><span data-stu-id="96dc9-126">The following is also true:</span></span>

* <span data-ttu-id="96dc9-127">其他執行緒或別名對 沒有寫入存取權限，這沒有任何含義`x`。</span><span class="sxs-lookup"><span data-stu-id="96dc9-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="96dc9-128">沒有任何暗示是`SomeStruct`不變的`x`，因為是一個。 `inref`</span><span class="sxs-lookup"><span data-stu-id="96dc9-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="96dc9-129">但是，**對於不可變**的 F# 數值型別，`this`將指標推斷為`inref`。</span><span class="sxs-lookup"><span data-stu-id="96dc9-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="96dc9-130">所有這些規則加在一`inref`起意味著指標的持有者不能修改指向的記憶體的即時內容。</span><span class="sxs-lookup"><span data-stu-id="96dc9-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="96dc9-131">外部參照語義</span><span class="sxs-lookup"><span data-stu-id="96dc9-131">Outref semantics</span></span>

<span data-ttu-id="96dc9-132">的目的是`outref<'T>`指示指標應只寫入。</span><span class="sxs-lookup"><span data-stu-id="96dc9-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="96dc9-133">出乎意料的是`outref<'T>`，允許讀取基礎值，儘管它的名稱。</span><span class="sxs-lookup"><span data-stu-id="96dc9-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="96dc9-134">這是出於相容性目的。</span><span class="sxs-lookup"><span data-stu-id="96dc9-134">This is for compatibility purposes.</span></span> <span data-ttu-id="96dc9-135">從語義上講`outref<'T>`，與 沒有什麼`byref<'T>`不同。</span><span class="sxs-lookup"><span data-stu-id="96dc9-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="96dc9-136">與 C 的互通\#</span><span class="sxs-lookup"><span data-stu-id="96dc9-136">Interop with C\#</span></span>

<span data-ttu-id="96dc9-137">除了`in ref``ref`返回之外，C# 還支援 和`out ref`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="96dc9-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="96dc9-138">下表顯示了 F# 如何解釋 C# 發出的內容：</span><span class="sxs-lookup"><span data-stu-id="96dc9-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="96dc9-139">C# 構造</span><span class="sxs-lookup"><span data-stu-id="96dc9-139">C# construct</span></span>|<span data-ttu-id="96dc9-140">F# 推斷</span><span class="sxs-lookup"><span data-stu-id="96dc9-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="96dc9-141">`ref`傳回值</span><span class="sxs-lookup"><span data-stu-id="96dc9-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="96dc9-142">`ref readonly`傳回值</span><span class="sxs-lookup"><span data-stu-id="96dc9-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="96dc9-143">`in ref` 參數</span><span class="sxs-lookup"><span data-stu-id="96dc9-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="96dc9-144">`out ref` 參數</span><span class="sxs-lookup"><span data-stu-id="96dc9-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="96dc9-145">下表顯示了 F# 發出的內容：</span><span class="sxs-lookup"><span data-stu-id="96dc9-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="96dc9-146">F# 構造</span><span class="sxs-lookup"><span data-stu-id="96dc9-146">F# construct</span></span>|<span data-ttu-id="96dc9-147">已發出構造</span><span class="sxs-lookup"><span data-stu-id="96dc9-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="96dc9-148">`inref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="96dc9-148">`inref<'T>` argument</span></span>|<span data-ttu-id="96dc9-149">`[In]`參數上的屬性</span><span class="sxs-lookup"><span data-stu-id="96dc9-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="96dc9-150">`inref<'T>`返回</span><span class="sxs-lookup"><span data-stu-id="96dc9-150">`inref<'T>` return</span></span>|<span data-ttu-id="96dc9-151">`modreq`值的屬性</span><span class="sxs-lookup"><span data-stu-id="96dc9-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="96dc9-152">`inref<'T>`抽象插槽或實現</span><span class="sxs-lookup"><span data-stu-id="96dc9-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="96dc9-153">`modreq`在參數或返回</span><span class="sxs-lookup"><span data-stu-id="96dc9-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="96dc9-154">`outref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="96dc9-154">`outref<'T>` argument</span></span>|<span data-ttu-id="96dc9-155">`[Out]`參數上的屬性</span><span class="sxs-lookup"><span data-stu-id="96dc9-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="96dc9-156">型別推斷和重載規則</span><span class="sxs-lookup"><span data-stu-id="96dc9-156">Type inference and overloading rules</span></span>

<span data-ttu-id="96dc9-157">在`inref<'T>`以下情況下，F# 編譯器會推斷類型：</span><span class="sxs-lookup"><span data-stu-id="96dc9-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="96dc9-158">具有`IsReadOnly`屬性的 .NET 參數或返回類型。</span><span class="sxs-lookup"><span data-stu-id="96dc9-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="96dc9-159">沒有`this`可變欄位的結構類型的指標。</span><span class="sxs-lookup"><span data-stu-id="96dc9-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="96dc9-160">從其他`inref<_>`指標派生的記憶體位置的位址。</span><span class="sxs-lookup"><span data-stu-id="96dc9-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="96dc9-161">當採用 隱式位址`inref`時，具有類型`SomeType`參數的重載優先于具有類型`inref<SomeType>`類型的重載。</span><span class="sxs-lookup"><span data-stu-id="96dc9-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="96dc9-162">例如：</span><span class="sxs-lookup"><span data-stu-id="96dc9-162">For example:</span></span>

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

<span data-ttu-id="96dc9-163">在這兩種情況下，重`System.DateTime`載將得到解決，而不是重載。 `inref<System.DateTime>`</span><span class="sxs-lookup"><span data-stu-id="96dc9-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="96dc9-164">類似 Byref 的結構</span><span class="sxs-lookup"><span data-stu-id="96dc9-164">Byref-like structs</span></span>

<span data-ttu-id="96dc9-165">`byref` /除了`outref``byref`三者組之外，您還可以定義自己的結構，這些結構可以遵循類似語義。 `inref` /</span><span class="sxs-lookup"><span data-stu-id="96dc9-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="96dc9-166">這與屬性一<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>起完成：</span><span class="sxs-lookup"><span data-stu-id="96dc9-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="96dc9-167">`IsByRefLike`並不意味著`Struct`.</span><span class="sxs-lookup"><span data-stu-id="96dc9-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="96dc9-168">兩者都必須存在於類型上。</span><span class="sxs-lookup"><span data-stu-id="96dc9-168">Both must be present on the type.</span></span>

<span data-ttu-id="96dc9-169">F#`byref`中的"類似"結構是一種堆疊綁定數值型別。</span><span class="sxs-lookup"><span data-stu-id="96dc9-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="96dc9-170">它永遠不會在託管堆上分配。</span><span class="sxs-lookup"><span data-stu-id="96dc9-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="96dc9-171">`byref`類似結構對於高性能程式設計非常有用，因為它通過一組有關存留期和非捕獲的強檢查強制執行。</span><span class="sxs-lookup"><span data-stu-id="96dc9-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="96dc9-172">規則包括：</span><span class="sxs-lookup"><span data-stu-id="96dc9-172">The rules are:</span></span>

* <span data-ttu-id="96dc9-173">它們可用作函數參數、方法參數、區域變數、方法返回。</span><span class="sxs-lookup"><span data-stu-id="96dc9-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="96dc9-174">它們不能是類的靜態或實例成員或正常結構。</span><span class="sxs-lookup"><span data-stu-id="96dc9-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="96dc9-175">它們不能被任何閉包構造（`async`方法或 lambda 運算式）捕獲。</span><span class="sxs-lookup"><span data-stu-id="96dc9-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="96dc9-176">它們不能用作泛型參數。</span><span class="sxs-lookup"><span data-stu-id="96dc9-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="96dc9-177">最後一點對於 F# 管道樣式程式設計至關重要，用於`|>`參數化其輸入類型的泛型函數也是如此。</span><span class="sxs-lookup"><span data-stu-id="96dc9-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="96dc9-178">將來可能會放寬`|>`此限制，因為它是內聯的，並且不會對其正文中的非內聯泛型函數進行任何調用。</span><span class="sxs-lookup"><span data-stu-id="96dc9-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="96dc9-179">儘管這些規則嚴格限制使用，但它們這樣做是為了以安全的方式實現高性能計算的承諾。</span><span class="sxs-lookup"><span data-stu-id="96dc9-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="96dc9-180">Byref 返回</span><span class="sxs-lookup"><span data-stu-id="96dc9-180">Byref returns</span></span>

<span data-ttu-id="96dc9-181">可以生成和使用 F# 函數或成員的 Byref 返回。</span><span class="sxs-lookup"><span data-stu-id="96dc9-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="96dc9-182">使用`byref`-返回方法時，將隱式取消引用該值。</span><span class="sxs-lookup"><span data-stu-id="96dc9-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="96dc9-183">例如：</span><span class="sxs-lookup"><span data-stu-id="96dc9-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="96dc9-184">要傳回值 byref，包含該值的變數必須比當前作用域長。</span><span class="sxs-lookup"><span data-stu-id="96dc9-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="96dc9-185">此外，要返回 byref，`&value`請使用 （其中值是比當前作用域長的變數）。</span><span class="sxs-lookup"><span data-stu-id="96dc9-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="96dc9-186">為了避免隱式取消引用（例如通過多個連結調用傳遞引用），請使用`&x`（值在哪裡）。 `x`</span><span class="sxs-lookup"><span data-stu-id="96dc9-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="96dc9-187">您也可以直接分配給返回`byref`。</span><span class="sxs-lookup"><span data-stu-id="96dc9-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="96dc9-188">請考慮以下（高度必要）計畫：</span><span class="sxs-lookup"><span data-stu-id="96dc9-188">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="96dc9-189">此為輸出：</span><span class="sxs-lookup"><span data-stu-id="96dc9-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="96dc9-190">位元組範圍</span><span class="sxs-lookup"><span data-stu-id="96dc9-190">Scoping for byrefs</span></span>

<span data-ttu-id="96dc9-191">`let`綁定值不能使其引用超過定義該值的範圍。</span><span class="sxs-lookup"><span data-stu-id="96dc9-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="96dc9-192">例如，不允許使用以下內容：</span><span class="sxs-lookup"><span data-stu-id="96dc9-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="96dc9-193">這可以防止您獲得不同的結果，具體取決於是否使用優化進行編譯。</span><span class="sxs-lookup"><span data-stu-id="96dc9-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
