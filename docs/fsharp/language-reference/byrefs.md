---
title: 'Byref （F #）'
description: '深入了解 byref 和 F # 中的類似 byref 類型用於低層級的程式設計。'
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695958"
---
# <a name="byrefs"></a><span data-ttu-id="161e8-103">Byref</span><span class="sxs-lookup"><span data-stu-id="161e8-103">Byrefs</span></span>

<span data-ttu-id="161e8-104">F # 提供處理低階程式設計的空間中的兩個主要功能領域：</span><span class="sxs-lookup"><span data-stu-id="161e8-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="161e8-105">`byref` / `inref` / `outref`類型，也就是 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="161e8-106">它們有使用量限制，因此無法編譯程式時，會在執行階段無效。</span><span class="sxs-lookup"><span data-stu-id="161e8-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="161e8-107">A `byref`-與結構，也就是一樣[結構](structures.md)有類似的語意和相同的編譯時間限制`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="161e8-108">其中一個範例是<xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="161e8-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="161e8-109">語法</span><span class="sxs-lookup"><span data-stu-id="161e8-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="161e8-110">Byref、 inref 和 outref</span><span class="sxs-lookup"><span data-stu-id="161e8-110">Byref, inref, and outref</span></span>

<span data-ttu-id="161e8-111">有三種形式的`byref`:</span><span class="sxs-lookup"><span data-stu-id="161e8-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="161e8-112">`inref<'T>`用於讀取的基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="161e8-113">`outref<'T>`用於將寫入基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="161e8-114">`byref<'T>`用於讀取和寫入基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="161e8-115">A`byref<'T>`可以在其中傳遞`inref<'T>`預期。</span><span class="sxs-lookup"><span data-stu-id="161e8-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="161e8-116">同樣地，`byref<'T>`可以在其中傳遞`outref<'T>`預期。</span><span class="sxs-lookup"><span data-stu-id="161e8-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="161e8-117">使用 byref</span><span class="sxs-lookup"><span data-stu-id="161e8-117">Using byrefs</span></span>

<span data-ttu-id="161e8-118">若要使用`inref<'T>`，您需要取得的指標值`&`:</span><span class="sxs-lookup"><span data-stu-id="161e8-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="161e8-119">若要寫入使用指標`outref<'T>`或是`byref<'T>`，您也必須進行抓取的指標值`mutable`。</span><span class="sxs-lookup"><span data-stu-id="161e8-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="161e8-120">如果您只撰寫的指標，而不是讀取它，請考慮使用`outref<'T>`而不是`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="161e8-121">Inref 語意</span><span class="sxs-lookup"><span data-stu-id="161e8-121">Inref semantics</span></span>

<span data-ttu-id="161e8-122">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="161e8-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

<span data-ttu-id="161e8-123">語意上來說，這表示下列事項：</span><span class="sxs-lookup"><span data-stu-id="161e8-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="161e8-124">持有人`x`指標可能只使用它來讀取值。</span><span class="sxs-lookup"><span data-stu-id="161e8-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="161e8-125">若要取得的任何指標`struct`欄位內變成巢狀`SomeStruct`會提供型別`inref<_>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="161e8-126">下列條件也成立：</span><span class="sxs-lookup"><span data-stu-id="161e8-126">The following is also true:</span></span>

* <span data-ttu-id="161e8-127">沒有任何隱含的其他執行緒或別名並沒有寫入權限`x`。</span><span class="sxs-lookup"><span data-stu-id="161e8-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="161e8-128">沒有任何隱含的`SomeStruct`不可變之故`x`正在`inref`。</span><span class="sxs-lookup"><span data-stu-id="161e8-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="161e8-129">不過，F # 的實值型別，**都**不可變`this`指標被推斷為`inref`。</span><span class="sxs-lookup"><span data-stu-id="161e8-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="161e8-130">所有這些規則同時表示的持有人`inref`指標可能不會修改所指向的記憶體的即時內容。</span><span class="sxs-lookup"><span data-stu-id="161e8-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="161e8-131">Outref 語意</span><span class="sxs-lookup"><span data-stu-id="161e8-131">Outref semantics</span></span>

<span data-ttu-id="161e8-132">目的`outref<'T>`是指出只應該從讀取指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="161e8-133">意外`outref<'T>`讀取基礎的允許值，儘管其名稱。</span><span class="sxs-lookup"><span data-stu-id="161e8-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="161e8-134">這是基於相容性。</span><span class="sxs-lookup"><span data-stu-id="161e8-134">This is for compatibility purposes.</span></span> <span data-ttu-id="161e8-135">語意上來說，`outref<'T>`沒什麼兩樣`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="161e8-136">使用 C# 的 interop</span><span class="sxs-lookup"><span data-stu-id="161e8-136">Interop with C#</span></span> #

<span data-ttu-id="161e8-137">C# 支援`in ref`並`out ref`關鍵字，除了`ref`傳回。</span><span class="sxs-lookup"><span data-stu-id="161e8-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="161e8-138">下表顯示如何 F # 解譯什麼 C# 會發出：</span><span class="sxs-lookup"><span data-stu-id="161e8-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="161e8-139">C# 建構</span><span class="sxs-lookup"><span data-stu-id="161e8-139">C# construct</span></span>|<span data-ttu-id="161e8-140">F # 推斷</span><span class="sxs-lookup"><span data-stu-id="161e8-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="161e8-141">`ref` 傳回值</span><span class="sxs-lookup"><span data-stu-id="161e8-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="161e8-142">`ref readonly` 傳回值</span><span class="sxs-lookup"><span data-stu-id="161e8-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="161e8-143">`in ref` 參數</span><span class="sxs-lookup"><span data-stu-id="161e8-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="161e8-144">`out ref` 參數</span><span class="sxs-lookup"><span data-stu-id="161e8-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="161e8-145">下表顯示哪些 F # 發出：</span><span class="sxs-lookup"><span data-stu-id="161e8-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="161e8-146">F # 建構</span><span class="sxs-lookup"><span data-stu-id="161e8-146">F# construct</span></span>|<span data-ttu-id="161e8-147">發出的建構</span><span class="sxs-lookup"><span data-stu-id="161e8-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="161e8-148">`inref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="161e8-148">`inref<'T>` argument</span></span>|<span data-ttu-id="161e8-149">`[In]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="161e8-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="161e8-150">`inref<'T>` 傳回</span><span class="sxs-lookup"><span data-stu-id="161e8-150">`inref<'T>` return</span></span>|<span data-ttu-id="161e8-151">`modreq` 值的屬性</span><span class="sxs-lookup"><span data-stu-id="161e8-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="161e8-152">`inref<'T>` 抽象位置或實作中</span><span class="sxs-lookup"><span data-stu-id="161e8-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="161e8-153">`modreq` 在 引數或傳回</span><span class="sxs-lookup"><span data-stu-id="161e8-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="161e8-154">`outref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="161e8-154">`outref<'T>` argument</span></span>|<span data-ttu-id="161e8-155">`[Out]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="161e8-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="161e8-156">型別推斷 」 和 「 多載規則</span><span class="sxs-lookup"><span data-stu-id="161e8-156">Type inference and overloading rules</span></span>

<span data-ttu-id="161e8-157">`inref<'T>`類型由在下列情況下，F # 編譯器推斷：</span><span class="sxs-lookup"><span data-stu-id="161e8-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="161e8-158">.NET 參數或傳回型別具有`IsReadOnly`屬性。</span><span class="sxs-lookup"><span data-stu-id="161e8-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="161e8-159">`this`上沒有任何可變動的欄位的結構類型的指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="161e8-160">記憶體位置的位址衍生自另一個`inref<_>`指標。</span><span class="sxs-lookup"><span data-stu-id="161e8-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="161e8-161">當隱含位址`inref`抱，類型的引數的多載`SomeType`應優先於類型的引數的多載`inref<SomeType>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="161e8-162">例如: </span><span class="sxs-lookup"><span data-stu-id="161e8-162">For example:</span></span>

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

<span data-ttu-id="161e8-163">在這兩種情況下，多載採用`System.DateTime`而不是採用的多載解析`inref<System.DateTime>`。</span><span class="sxs-lookup"><span data-stu-id="161e8-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="161e8-164">類似 Byref 結構</span><span class="sxs-lookup"><span data-stu-id="161e8-164">Byref-like structs</span></span>

<span data-ttu-id="161e8-165">除了`byref` / `inref` / `outref`事，您可以定義您自己的結構，可以遵循`byref`-例如語意。</span><span class="sxs-lookup"><span data-stu-id="161e8-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="161e8-166">做法是使用<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性：</span><span class="sxs-lookup"><span data-stu-id="161e8-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="161e8-167">`IsByRefLike` 並不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="161e8-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="161e8-168">兩者都必須要有型別。</span><span class="sxs-lookup"><span data-stu-id="161e8-168">Both must be present on the type.</span></span>

<span data-ttu-id="161e8-169">「`byref`-例如"F # 中的結構是堆疊繫結值型別。</span><span class="sxs-lookup"><span data-stu-id="161e8-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="161e8-170">永遠不會在 managed 堆積上配置。</span><span class="sxs-lookup"><span data-stu-id="161e8-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="161e8-171">A `byref`-就像結構適用於高效能的程式設計，因為它會強制執行設定的強式存留期和非擷取相關的檢查。</span><span class="sxs-lookup"><span data-stu-id="161e8-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="161e8-172">規則包括：</span><span class="sxs-lookup"><span data-stu-id="161e8-172">The rules are:</span></span>

* <span data-ttu-id="161e8-173">它們可用來當做函式參數、 方法參數、 區域變數、 方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="161e8-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="161e8-174">它們不能是靜態或執行個體的類別或一般結構的成員。</span><span class="sxs-lookup"><span data-stu-id="161e8-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="161e8-175">它們無法擷取任何關閉的建構 (`async`方法或 lambda 運算式)。</span><span class="sxs-lookup"><span data-stu-id="161e8-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="161e8-176">它們不能當做泛型參數。</span><span class="sxs-lookup"><span data-stu-id="161e8-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="161e8-177">最後一點很重要的 F # 管線樣式程式設計中，為`|>`會參數化為其輸入的類型的泛型函式。</span><span class="sxs-lookup"><span data-stu-id="161e8-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="161e8-178">這項限制可能會放寬為`|>`未來，因為它是以內嵌方式，其主體中毫無任何非內嵌的泛型函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="161e8-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="161e8-179">雖然很希望這些規則會限制使用方式，如此一來滿足承諾的高效能運算以安全的方式。</span><span class="sxs-lookup"><span data-stu-id="161e8-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="161e8-180">Byref 傳回</span><span class="sxs-lookup"><span data-stu-id="161e8-180">Byref returns</span></span>

<span data-ttu-id="161e8-181">Byref 傳回從 F # 函式或成員可以產生及取用。</span><span class="sxs-lookup"><span data-stu-id="161e8-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="161e8-182">使用時`byref`-傳回方法，這個值是隱含已取值。</span><span class="sxs-lookup"><span data-stu-id="161e8-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="161e8-183">例如: </span><span class="sxs-lookup"><span data-stu-id="161e8-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="161e8-184">若要避免隱含取值，例如傳遞多個鏈結的呼叫，透過參考使用`&x`(其中`x`是值)。</span><span class="sxs-lookup"><span data-stu-id="161e8-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="161e8-185">您可以也可以直接指派給傳回`byref`。</span><span class="sxs-lookup"><span data-stu-id="161e8-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="161e8-186">請考慮下列 （高命令式） 的程式：</span><span class="sxs-lookup"><span data-stu-id="161e8-186">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

<span data-ttu-id="161e8-187">此為輸出：</span><span class="sxs-lookup"><span data-stu-id="161e8-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="161e8-188">範圍，將 byref</span><span class="sxs-lookup"><span data-stu-id="161e8-188">Scoping for byrefs</span></span>

<span data-ttu-id="161e8-189">A `let`-繫結的值不能有超過的範圍定義其參考。</span><span class="sxs-lookup"><span data-stu-id="161e8-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="161e8-190">例如，下列是不允許：</span><span class="sxs-lookup"><span data-stu-id="161e8-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="161e8-191">這會讓您取得取決於不同的結果，如果您使用 開啟或關閉的最佳化。</span><span class="sxs-lookup"><span data-stu-id="161e8-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
