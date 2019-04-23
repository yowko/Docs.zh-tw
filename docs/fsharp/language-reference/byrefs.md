---
title: Byref
description: 了解 byref 和中的類似 byref 類型F#，用來進行低層級的程式設計。
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055361"
---
# <a name="byrefs"></a><span data-ttu-id="2ef8c-103">Byref</span><span class="sxs-lookup"><span data-stu-id="2ef8c-103">Byrefs</span></span>

<span data-ttu-id="2ef8c-104">F#已處理的低階程式設計空間中的兩個主要功能領域：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="2ef8c-105">`byref` / `inref` / `outref`類型，也就是 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="2ef8c-106">它們有使用量限制，因此無法編譯程式時，會在執行階段無效。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="2ef8c-107">A `byref`-與結構，也就是一樣[結構](structures.md)有類似的語意和相同的編譯時間限制`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="2ef8c-108">其中一個範例是<xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ef8c-109">語法</span><span class="sxs-lookup"><span data-stu-id="2ef8c-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="2ef8c-110">Byref、 inref 和 outref</span><span class="sxs-lookup"><span data-stu-id="2ef8c-110">Byref, inref, and outref</span></span>

<span data-ttu-id="2ef8c-111">有三種形式的`byref`:</span><span class="sxs-lookup"><span data-stu-id="2ef8c-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="2ef8c-112">`inref<'T>`用於讀取的基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="2ef8c-113">`outref<'T>`用於將寫入基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="2ef8c-114">`byref<'T>`用於讀取和寫入基礎值的 managed 的指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="2ef8c-115">A`byref<'T>`可以在其中傳遞`inref<'T>`預期。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="2ef8c-116">同樣地，`byref<'T>`可以在其中傳遞`outref<'T>`預期。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="2ef8c-117">使用 byref</span><span class="sxs-lookup"><span data-stu-id="2ef8c-117">Using byrefs</span></span>

<span data-ttu-id="2ef8c-118">若要使用`inref<'T>`，您需要取得的指標值`&`:</span><span class="sxs-lookup"><span data-stu-id="2ef8c-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="2ef8c-119">若要寫入使用指標`outref<'T>`或是`byref<'T>`，您也必須進行抓取的指標值`mutable`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="2ef8c-120">如果您只撰寫的指標，而不是讀取它，請考慮使用`outref<'T>`而不是`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="2ef8c-121">Inref 語意</span><span class="sxs-lookup"><span data-stu-id="2ef8c-121">Inref semantics</span></span>

<span data-ttu-id="2ef8c-122">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="2ef8c-123">語意上來說，這表示下列事項：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="2ef8c-124">持有人`x`指標可能只使用它來讀取值。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="2ef8c-125">若要取得的任何指標`struct`欄位內變成巢狀`SomeStruct`會提供型別`inref<_>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="2ef8c-126">下列條件也成立：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-126">The following is also true:</span></span>

* <span data-ttu-id="2ef8c-127">沒有任何隱含的其他執行緒或別名並沒有寫入權限`x`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="2ef8c-128">沒有任何隱含的`SomeStruct`不可變之故`x`正在`inref`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="2ef8c-129">不過，對於F#實值型別所**會**不可變的`this`指標就會推斷`inref`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="2ef8c-130">所有這些規則同時表示的持有人`inref`指標可能不會修改所指向的記憶體的即時內容。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="2ef8c-131">Outref 語意</span><span class="sxs-lookup"><span data-stu-id="2ef8c-131">Outref semantics</span></span>

<span data-ttu-id="2ef8c-132">目的`outref<'T>`是指出只應該從讀取指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="2ef8c-133">意外`outref<'T>`讀取基礎的允許值，儘管其名稱。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="2ef8c-134">這是基於相容性。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-134">This is for compatibility purposes.</span></span> <span data-ttu-id="2ef8c-135">語意上來說，`outref<'T>`沒什麼兩樣`byref<'T>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="2ef8c-136">使用 c# 的 interop\#</span><span class="sxs-lookup"><span data-stu-id="2ef8c-136">Interop with C\#</span></span>

<span data-ttu-id="2ef8c-137">C# 支援`in ref`並`out ref`關鍵字，除了`ref`傳回。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="2ef8c-138">下表顯示F#會解譯項目C#發出：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="2ef8c-139">C# 建構</span><span class="sxs-lookup"><span data-stu-id="2ef8c-139">C# construct</span></span>|<span data-ttu-id="2ef8c-140">F#推斷</span><span class="sxs-lookup"><span data-stu-id="2ef8c-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="2ef8c-141">`ref` 傳回值</span><span class="sxs-lookup"><span data-stu-id="2ef8c-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="2ef8c-142">`ref readonly` 傳回值</span><span class="sxs-lookup"><span data-stu-id="2ef8c-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="2ef8c-143">`in ref` 參數</span><span class="sxs-lookup"><span data-stu-id="2ef8c-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="2ef8c-144">`out ref` 參數</span><span class="sxs-lookup"><span data-stu-id="2ef8c-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="2ef8c-145">下表顯示F#會發出：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="2ef8c-146">F#建構</span><span class="sxs-lookup"><span data-stu-id="2ef8c-146">F# construct</span></span>|<span data-ttu-id="2ef8c-147">發出的建構</span><span class="sxs-lookup"><span data-stu-id="2ef8c-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="2ef8c-148">`inref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="2ef8c-148">`inref<'T>` argument</span></span>|<span data-ttu-id="2ef8c-149">`[In]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="2ef8c-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="2ef8c-150">`inref<'T>` 傳回</span><span class="sxs-lookup"><span data-stu-id="2ef8c-150">`inref<'T>` return</span></span>|<span data-ttu-id="2ef8c-151">`modreq` 值的屬性</span><span class="sxs-lookup"><span data-stu-id="2ef8c-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="2ef8c-152">`inref<'T>` 抽象位置或實作中</span><span class="sxs-lookup"><span data-stu-id="2ef8c-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="2ef8c-153">`modreq` 在 引數或傳回</span><span class="sxs-lookup"><span data-stu-id="2ef8c-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="2ef8c-154">`outref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="2ef8c-154">`outref<'T>` argument</span></span>|<span data-ttu-id="2ef8c-155">`[Out]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="2ef8c-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="2ef8c-156">型別推斷 」 和 「 多載規則</span><span class="sxs-lookup"><span data-stu-id="2ef8c-156">Type inference and overloading rules</span></span>

<span data-ttu-id="2ef8c-157">`inref<'T>`推斷類型是F#編譯器在下列情況：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="2ef8c-158">.NET 參數或傳回型別具有`IsReadOnly`屬性。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="2ef8c-159">`this`上沒有任何可變動的欄位的結構類型的指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="2ef8c-160">記憶體位置的位址衍生自另一個`inref<_>`指標。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="2ef8c-161">當隱含位址`inref`抱，類型的引數的多載`SomeType`應優先於類型的引數的多載`inref<SomeType>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="2ef8c-162">例如: </span><span class="sxs-lookup"><span data-stu-id="2ef8c-162">For example:</span></span>

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

<span data-ttu-id="2ef8c-163">在這兩種情況下，多載採用`System.DateTime`而不是採用的多載解析`inref<System.DateTime>`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="2ef8c-164">類似 Byref 結構</span><span class="sxs-lookup"><span data-stu-id="2ef8c-164">Byref-like structs</span></span>

<span data-ttu-id="2ef8c-165">除了`byref` / `inref` / `outref`事，您可以定義您自己的結構，可以遵循`byref`-例如語意。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="2ef8c-166">做法是使用<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2ef8c-167">`IsByRefLike` 並不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="2ef8c-168">兩者都必須要有型別。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-168">Both must be present on the type.</span></span>

<span data-ttu-id="2ef8c-169">「`byref`-例如"中的結構F#堆疊繫結實值型別。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="2ef8c-170">永遠不會在 managed 堆積上配置。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="2ef8c-171">A `byref`-就像結構適用於高效能的程式設計，因為它會強制執行設定的強式存留期和非擷取相關的檢查。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="2ef8c-172">規則包括：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-172">The rules are:</span></span>

* <span data-ttu-id="2ef8c-173">它們可用來當做函式參數、 方法參數、 區域變數、 方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="2ef8c-174">它們不能是靜態或執行個體的類別或一般結構的成員。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="2ef8c-175">它們無法擷取任何關閉的建構 (`async`方法或 lambda 運算式)。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="2ef8c-176">它們不能當做泛型參數。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="2ef8c-177">最後一點很重要的F#管線樣式程式設計中，作為`|>`會將其輸入的類型的參數化的泛型函式。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="2ef8c-178">這項限制可能會放寬為`|>`未來，因為它是以內嵌方式，其主體中毫無任何非內嵌的泛型函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="2ef8c-179">雖然很希望這些規則會限制使用方式，如此一來滿足承諾的高效能運算以安全的方式。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="2ef8c-180">Byref 傳回</span><span class="sxs-lookup"><span data-stu-id="2ef8c-180">Byref returns</span></span>

<span data-ttu-id="2ef8c-181">Byref 傳回從F#函式或成員可以產生及取用。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="2ef8c-182">使用時`byref`-傳回方法，這個值是隱含已取值。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="2ef8c-183">例如：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="2ef8c-184">若要避免隱含取值，例如傳遞多個鏈結的呼叫，透過參考使用`&x`(其中`x`是值)。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="2ef8c-185">您可以也可以直接指派給傳回`byref`。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="2ef8c-186">請考慮下列 （高命令式） 的程式：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-186">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="2ef8c-187">此為輸出：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="2ef8c-188">範圍，將 byref</span><span class="sxs-lookup"><span data-stu-id="2ef8c-188">Scoping for byrefs</span></span>

<span data-ttu-id="2ef8c-189">A `let`-繫結的值不能有超過的範圍定義其參考。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="2ef8c-190">例如，下列是不允許：</span><span class="sxs-lookup"><span data-stu-id="2ef8c-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="2ef8c-191">這會讓您取得取決於不同的結果，如果您使用 開啟或關閉的最佳化。</span><span class="sxs-lookup"><span data-stu-id="2ef8c-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
