---
title: Byrefs
description: '深入瞭解以 F # 使用的 byref 和 byref 型別，這些類型用於低層級程式設計。'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740311"
---
# <a name="byrefs"></a><span data-ttu-id="fe067-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="fe067-103">Byrefs</span></span>

<span data-ttu-id="fe067-104">F # 有兩個主要的功能區，可應付低層級程式設計的空間：</span><span class="sxs-lookup"><span data-stu-id="fe067-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="fe067-105">`byref` / `inref` / `outref` 類型，也就是 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="fe067-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="fe067-106">它們具有使用方式的限制，因此您無法編譯在執行時間不正確程式。</span><span class="sxs-lookup"><span data-stu-id="fe067-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="fe067-107">類似的結構 `byref` ，也就是具有類似語義和相同編譯時間限制的 [結構](structures.md) `byref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="fe067-108">其中一個範例是 <xref:System.Span%601> 。</span><span class="sxs-lookup"><span data-stu-id="fe067-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe067-109">語法</span><span class="sxs-lookup"><span data-stu-id="fe067-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="fe067-110">Byref、inref 和 outref</span><span class="sxs-lookup"><span data-stu-id="fe067-110">Byref, inref, and outref</span></span>

<span data-ttu-id="fe067-111">有三種形式 `byref` ：</span><span class="sxs-lookup"><span data-stu-id="fe067-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="fe067-112">`inref<'T>`，用來讀取基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="fe067-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="fe067-113">`outref<'T>`，用於寫入基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="fe067-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="fe067-114">`byref<'T>`，用來讀取和寫入基礎值的 managed 指標。</span><span class="sxs-lookup"><span data-stu-id="fe067-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="fe067-115">`byref<'T>`可以傳遞至 `inref<'T>` 預期的。</span><span class="sxs-lookup"><span data-stu-id="fe067-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="fe067-116">同樣地，您 `byref<'T>` 可以在預期的位置傳遞 `outref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="fe067-117">使用 byref</span><span class="sxs-lookup"><span data-stu-id="fe067-117">Using byrefs</span></span>

<span data-ttu-id="fe067-118">若要使用 `inref<'T>` ，您必須使用下列內容來取得指標值 `&` ：</span><span class="sxs-lookup"><span data-stu-id="fe067-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="fe067-119">若要使用或來寫入指標 `outref<'T>` `byref<'T>` ，您也必須將抓取指標的值設為 `mutable` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="fe067-120">如果您只是要寫入指標，而不是讀取指標，請考慮使用 `outref<'T>` 而不是 `byref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="fe067-121">Inref 語義</span><span class="sxs-lookup"><span data-stu-id="fe067-121">Inref semantics</span></span>

<span data-ttu-id="fe067-122">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="fe067-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="fe067-123">就語義而言，這表示下列各項：</span><span class="sxs-lookup"><span data-stu-id="fe067-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="fe067-124">指標的預留位置 `x` 只能用來讀取值。</span><span class="sxs-lookup"><span data-stu-id="fe067-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="fe067-125">`struct`針對內嵌于中之欄位所取得的任何指標 `SomeStruct` 都會提供型別 `inref<_>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="fe067-126">以下也成立：</span><span class="sxs-lookup"><span data-stu-id="fe067-126">The following is also true:</span></span>

* <span data-ttu-id="fe067-127">沒有任何暗示其他執行緒或別名沒有的寫入權限 `x` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="fe067-128">沒有任何隱含的 `SomeStruct` 改變，因為這是的 `x` `inref` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="fe067-129">但是，如果 **是** 不可變的 F # 實值型別，則會將 `this` 指標推斷為 `inref` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="fe067-130">所有這些規則都表示指標的持有者 `inref` 可能不會修改所指向之記憶體的立即內容。</span><span class="sxs-lookup"><span data-stu-id="fe067-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="fe067-131">Outref 語義</span><span class="sxs-lookup"><span data-stu-id="fe067-131">Outref semantics</span></span>

<span data-ttu-id="fe067-132">的目的 `outref<'T>` 是要指出指標只能寫入至。</span><span class="sxs-lookup"><span data-stu-id="fe067-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="fe067-133">非預期的情況下， `outref<'T>` 允許讀取基礎值（儘管其名稱）。</span><span class="sxs-lookup"><span data-stu-id="fe067-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="fe067-134">這是基於相容性的目的。</span><span class="sxs-lookup"><span data-stu-id="fe067-134">This is for compatibility purposes.</span></span> <span data-ttu-id="fe067-135">語義上， `outref<'T>` 與不同 `byref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="fe067-136">Interop 與 C\#</span><span class="sxs-lookup"><span data-stu-id="fe067-136">Interop with C\#</span></span>

<span data-ttu-id="fe067-137">`in ref`除了傳回之外，c # 也支援和 `out ref` 關鍵字 `ref` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="fe067-138">下表顯示 F # 如何解讀 c # 發出的內容：</span><span class="sxs-lookup"><span data-stu-id="fe067-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="fe067-139">C # 結構</span><span class="sxs-lookup"><span data-stu-id="fe067-139">C# construct</span></span>|<span data-ttu-id="fe067-140">F # 推斷</span><span class="sxs-lookup"><span data-stu-id="fe067-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="fe067-141">`ref` 傳回值</span><span class="sxs-lookup"><span data-stu-id="fe067-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="fe067-142">`ref readonly` 傳回值</span><span class="sxs-lookup"><span data-stu-id="fe067-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="fe067-143">`in ref` 參數</span><span class="sxs-lookup"><span data-stu-id="fe067-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="fe067-144">`out ref` 參數</span><span class="sxs-lookup"><span data-stu-id="fe067-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="fe067-145">下表顯示 F # 發出的內容：</span><span class="sxs-lookup"><span data-stu-id="fe067-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="fe067-146">F # 結構</span><span class="sxs-lookup"><span data-stu-id="fe067-146">F# construct</span></span>|<span data-ttu-id="fe067-147">發出的結構</span><span class="sxs-lookup"><span data-stu-id="fe067-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="fe067-148">`inref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="fe067-148">`inref<'T>` argument</span></span>|<span data-ttu-id="fe067-149">`[In]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="fe067-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="fe067-150">`inref<'T>` 返回</span><span class="sxs-lookup"><span data-stu-id="fe067-150">`inref<'T>` return</span></span>|<span data-ttu-id="fe067-151">`modreq` 值上的屬性</span><span class="sxs-lookup"><span data-stu-id="fe067-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="fe067-152">`inref<'T>` 在抽象插槽或執行中</span><span class="sxs-lookup"><span data-stu-id="fe067-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="fe067-153">`modreq` on 引數或 return</span><span class="sxs-lookup"><span data-stu-id="fe067-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="fe067-154">`outref<'T>` 引數</span><span class="sxs-lookup"><span data-stu-id="fe067-154">`outref<'T>` argument</span></span>|<span data-ttu-id="fe067-155">`[Out]` 引數上的屬性</span><span class="sxs-lookup"><span data-stu-id="fe067-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="fe067-156">型別推斷和多載規則</span><span class="sxs-lookup"><span data-stu-id="fe067-156">Type inference and overloading rules</span></span>

<span data-ttu-id="fe067-157">`inref<'T>`在下列情況下，F # 編譯器會推斷型別：</span><span class="sxs-lookup"><span data-stu-id="fe067-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="fe067-158">具有屬性的 .NET 參數或傳回型別 `IsReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="fe067-159">`this`結構類型上沒有可變動欄位的指標。</span><span class="sxs-lookup"><span data-stu-id="fe067-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="fe067-160">衍生自另一個指標之記憶體位置的位址 `inref<_>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="fe067-161">當採用的隱含位址時 `inref` ，具有類型之引數的多載 `SomeType` 優先于具有類型之引數的多載 `inref<SomeType>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="fe067-162">例如：</span><span class="sxs-lookup"><span data-stu-id="fe067-162">For example:</span></span>

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

<span data-ttu-id="fe067-163">在這兩種情況下， `System.DateTime` 會解析接受的多載，而不是採用多載 `inref<System.DateTime>` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="fe067-164">類似 Byref 的結構</span><span class="sxs-lookup"><span data-stu-id="fe067-164">Byref-like structs</span></span>

<span data-ttu-id="fe067-165">除了 `byref` / `inref` / `outref` 三個之外，您還可以定義自己的結構，這些結構可以遵循 `byref` 類似的語法。</span><span class="sxs-lookup"><span data-stu-id="fe067-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="fe067-166">這是使用屬性來完成的 <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ：</span><span class="sxs-lookup"><span data-stu-id="fe067-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="fe067-167">`IsByRefLike` 不表示 `Struct` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="fe067-168">兩者都必須存在於類型上。</span><span class="sxs-lookup"><span data-stu-id="fe067-168">Both must be present on the type.</span></span>

<span data-ttu-id="fe067-169">`byref`F # 中的「-like」結構是堆疊系結的實值型別。</span><span class="sxs-lookup"><span data-stu-id="fe067-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="fe067-170">它永遠不會在 managed 堆積上進行配置。</span><span class="sxs-lookup"><span data-stu-id="fe067-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="fe067-171">`byref`類似的結構適用于高效能程式設計，因為它會利用存留期和非捕捉的一組強大檢查來強制執行。</span><span class="sxs-lookup"><span data-stu-id="fe067-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="fe067-172">這些規則包括：</span><span class="sxs-lookup"><span data-stu-id="fe067-172">The rules are:</span></span>

* <span data-ttu-id="fe067-173">它們可用來作為函式參數、方法參數、區域變數、方法傳回。</span><span class="sxs-lookup"><span data-stu-id="fe067-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="fe067-174">它們不得為類別或一般結構的靜態或實例成員。</span><span class="sxs-lookup"><span data-stu-id="fe067-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="fe067-175">`async`)  (方法或 lambda 運算式時，無法由任何關閉結構來捕捉它們。</span><span class="sxs-lookup"><span data-stu-id="fe067-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="fe067-176">它們不能用來做為泛型參數。</span><span class="sxs-lookup"><span data-stu-id="fe067-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="fe067-177">最後一點對於 F # 管線樣式程式設計很重要，因為它 `|>` 是參數化其輸入類型的泛型函式。</span><span class="sxs-lookup"><span data-stu-id="fe067-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="fe067-178">未來可能會放寬這 `|>` 項限制，因為它是內嵌的，而且不會對其主體中的非內嵌泛型函數進行任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe067-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="fe067-179">雖然這些規則會嚴格限制使用方式，但它們會以安全的方式滿足高效能運算的承諾。</span><span class="sxs-lookup"><span data-stu-id="fe067-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="fe067-180">Byref 傳回</span><span class="sxs-lookup"><span data-stu-id="fe067-180">Byref returns</span></span>

<span data-ttu-id="fe067-181">從 F # 函數或成員可以產生和取用的 Byref 傳回。</span><span class="sxs-lookup"><span data-stu-id="fe067-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="fe067-182">使用傳回的 `byref` 方法時，會隱含地取值值。</span><span class="sxs-lookup"><span data-stu-id="fe067-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="fe067-183">例如：</span><span class="sxs-lookup"><span data-stu-id="fe067-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

<span data-ttu-id="fe067-184">若要傳回值 byref，包含值的變數必須存留于目前範圍的時間。</span><span class="sxs-lookup"><span data-stu-id="fe067-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="fe067-185">此外，若要傳回 byref，請使用 `&value` (，其中 value 是長度超過目前範圍) 的變數。</span><span class="sxs-lookup"><span data-stu-id="fe067-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="fe067-186">若要避免隱含的取值，例如透過多個連結呼叫傳遞參考，請使用 `&x` (，其中 `x` 是) 的值。</span><span class="sxs-lookup"><span data-stu-id="fe067-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="fe067-187">您也可以直接指派給 return `byref` 。</span><span class="sxs-lookup"><span data-stu-id="fe067-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="fe067-188">請考慮下列 (高度命令式) 程式：</span><span class="sxs-lookup"><span data-stu-id="fe067-188">Consider the following (highly imperative) program:</span></span>

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
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

<span data-ttu-id="fe067-189">此為輸出：</span><span class="sxs-lookup"><span data-stu-id="fe067-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="fe067-190">Byref 的範圍</span><span class="sxs-lookup"><span data-stu-id="fe067-190">Scoping for byrefs</span></span>

<span data-ttu-id="fe067-191">系結 `let` 值不能有其參考超出定義的範圍。</span><span class="sxs-lookup"><span data-stu-id="fe067-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="fe067-192">例如，不允許下列情況：</span><span class="sxs-lookup"><span data-stu-id="fe067-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="fe067-193">這可防止您取得不同的結果，這取決於您是否使用優化進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fe067-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
