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
# <a name="byrefs"></a>Byrefs

F # 有兩個主要的功能區，可應付低層級程式設計的空間：

* `byref` / `inref` / `outref` 類型，也就是 managed 指標。 它們具有使用方式的限制，因此您無法編譯在執行時間不正確程式。
* 類似的結構 `byref` ，也就是具有類似語義和相同編譯時間限制的 [結構](structures.md) `byref<'T>` 。 其中一個範例是 <xref:System.Span%601> 。

## <a name="syntax"></a>語法

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

## <a name="byref-inref-and-outref"></a>Byref、inref 和 outref

有三種形式 `byref` ：

* `inref<'T>`，用來讀取基礎值的 managed 指標。
* `outref<'T>`，用於寫入基礎值的 managed 指標。
* `byref<'T>`，用來讀取和寫入基礎值的 managed 指標。

`byref<'T>`可以傳遞至 `inref<'T>` 預期的。 同樣地，您 `byref<'T>` 可以在預期的位置傳遞 `outref<'T>` 。

## <a name="using-byrefs"></a>使用 byref

若要使用 `inref<'T>` ，您必須使用下列內容來取得指標值 `&` ：

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

若要使用或來寫入指標 `outref<'T>` `byref<'T>` ，您也必須將抓取指標的值設為 `mutable` 。

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

如果您只是要寫入指標，而不是讀取指標，請考慮使用 `outref<'T>` 而不是 `byref<'T>` 。

### <a name="inref-semantics"></a>Inref 語義

請考慮下列程式碼：

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

就語義而言，這表示下列各項：

* 指標的預留位置 `x` 只能用來讀取值。
* `struct`針對內嵌于中之欄位所取得的任何指標 `SomeStruct` 都會提供型別 `inref<_>` 。

以下也成立：

* 沒有任何暗示其他執行緒或別名沒有的寫入權限 `x` 。
* 沒有任何隱含的 `SomeStruct` 改變，因為這是的 `x` `inref` 。

但是，如果 **是** 不可變的 F # 實值型別，則會將 `this` 指標推斷為 `inref` 。

所有這些規則都表示指標的持有者 `inref` 可能不會修改所指向之記憶體的立即內容。

### <a name="outref-semantics"></a>Outref 語義

的目的 `outref<'T>` 是要指出指標只能寫入至。 非預期的情況下， `outref<'T>` 允許讀取基礎值（儘管其名稱）。 這是基於相容性的目的。 語義上， `outref<'T>` 與不同 `byref<'T>` 。

### <a name="interop-with-c"></a>Interop 與 C\#

`in ref`除了傳回之外，c # 也支援和 `out ref` 關鍵字 `ref` 。 下表顯示 F # 如何解讀 c # 發出的內容：

|C # 結構|F # 推斷|
|------------|---------|
|`ref` 傳回值|`outref<'T>`|
|`ref readonly` 傳回值|`inref<'T>`|
|`in ref` 參數|`inref<'T>`|
|`out ref` 參數|`outref<'T>`|

下表顯示 F # 發出的內容：

|F # 結構|發出的結構|
|------------|-----------------|
|`inref<'T>` 引數|`[In]` 引數上的屬性|
|`inref<'T>` 返回|`modreq` 值上的屬性|
|`inref<'T>` 在抽象插槽或執行中|`modreq` on 引數或 return|
|`outref<'T>` 引數|`[Out]` 引數上的屬性|

### <a name="type-inference-and-overloading-rules"></a>型別推斷和多載規則

`inref<'T>`在下列情況下，F # 編譯器會推斷型別：

1. 具有屬性的 .NET 參數或傳回型別 `IsReadOnly` 。
2. `this`結構類型上沒有可變動欄位的指標。
3. 衍生自另一個指標之記憶體位置的位址 `inref<_>` 。

當採用的隱含位址時 `inref` ，具有類型之引數的多載 `SomeType` 優先于具有類型之引數的多載 `inref<SomeType>` 。 例如：

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

在這兩種情況下， `System.DateTime` 會解析接受的多載，而不是採用多載 `inref<System.DateTime>` 。

## <a name="byref-like-structs"></a>類似 Byref 的結構

除了 `byref` / `inref` / `outref` 三個之外，您還可以定義自己的結構，這些結構可以遵循 `byref` 類似的語法。 這是使用屬性來完成的 <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 不表示 `Struct` 。 兩者都必須存在於類型上。

`byref`F # 中的「-like」結構是堆疊系結的實值型別。 它永遠不會在 managed 堆積上進行配置。 `byref`類似的結構適用于高效能程式設計，因為它會利用存留期和非捕捉的一組強大檢查來強制執行。 這些規則包括：

* 它們可用來作為函式參數、方法參數、區域變數、方法傳回。
* 它們不得為類別或一般結構的靜態或實例成員。
* `async`)  (方法或 lambda 運算式時，無法由任何關閉結構來捕捉它們。
* 它們不能用來做為泛型參數。

最後一點對於 F # 管線樣式程式設計很重要，因為它 `|>` 是參數化其輸入類型的泛型函式。 未來可能會放寬這 `|>` 項限制，因為它是內嵌的，而且不會對其主體中的非內嵌泛型函數進行任何呼叫。

雖然這些規則會嚴格限制使用方式，但它們會以安全的方式滿足高效能運算的承諾。

## <a name="byref-returns"></a>Byref 傳回

從 F # 函數或成員可以產生和取用的 Byref 傳回。 使用傳回的 `byref` 方法時，會隱含地取值值。 例如：

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

若要傳回值 byref，包含值的變數必須存留于目前範圍的時間。
此外，若要傳回 byref，請使用 `&value` (，其中 value 是長度超過目前範圍) 的變數。

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

若要避免隱含的取值，例如透過多個連結呼叫傳遞參考，請使用 `&x` (，其中 `x` 是) 的值。

您也可以直接指派給 return `byref` 。 請考慮下列 (高度命令式) 程式：

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

此為輸出：

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Byref 的範圍

系結 `let` 值不能有其參考超出定義的範圍。 例如，不允許下列情況：

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

這可防止您取得不同的結果，這取決於您是否使用優化進行編譯。
