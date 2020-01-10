---
title: Byrefs
description: 深入瞭解中F#的 byref 和 byref 型別，其適用于低層級的程式設計。
ms.date: 11/04/2019
ms.openlocfilehash: a6d3d69c4a163be9ecef7e33c284c4a73e800405
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545127"
---
# <a name="byrefs"></a>Byrefs

F#有兩個主要的功能領域，可應付低層級程式設計的空間：

* `byref`/`inref`/`outref` 類型，這是 managed 指標。 它們對使用方式有限制，因此您無法編譯在執行時間不正確程式。
* `byref`類似的結構，這是具有類似的語義和 `byref<'T>`的編譯時間限制的[結構](structures.md)。 其中一個範例是 <xref:System.Span%601>。

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

有三種形式的 `byref`：

* `inref<'T>`，這是用來讀取基礎值的 managed 指標。
* `outref<'T>`，用於寫入基礎值的 managed 指標。
* `byref<'T>`，這是用來讀取和寫入基礎值的 managed 指標。

`byref<'T>` 可以在預期 `inref<'T>` 的情況下傳遞。 同樣地，您可以在預期 `outref<'T>` 的位置傳遞 `byref<'T>`。

## <a name="using-byrefs"></a>使用 byref

若要使用 `inref<'T>`，您需要取得具有 `&`的指標值：

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

若要使用 `outref<'T>` 或 `byref<'T>`來寫入指標，您也必須將此值設為您抓取 `mutable`的指標。

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

如果您只是要撰寫指標，而不是讀取它，請考慮使用 `outref<'T>`，而不是 `byref<'T>`。

### <a name="inref-semantics"></a>Inref 的語義

請考慮下列程式碼：

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

就語義而言，這表示下列各項：

* `x` 指標的持有者可能只會使用它來讀取值。
* 取得至 `SomeStruct` 中的 `struct` 欄位的任何指標都會提供類型 `inref<_>`。

以下也是 true：

* 不會隱含其他執行緒或別名不具有 `x`的寫入存取權。
* 這並不表示 `SomeStruct` 不會因為 `inref``x` 而變。

不過，如果F# **是不**變的實值型別，則會將 `this` 指標推斷為 `inref`。

所有這些規則都表示 `inref` 指標的持有者可能不會修改所指向之記憶體的立即內容。

### <a name="outref-semantics"></a>Outref 的語義

`outref<'T>` 的目的是要指出指標應該只寫入至。 不預期地，`outref<'T>` 允許讀取基礎值，而不論其名稱。 這是為了相容性之故。 就語義而言，`outref<'T>` 與 `byref<'T>`不同。

### <a name="interop-with-c"></a>與 C\# 的 Interop

C#除了 `ref` 傳回以外，支援 `in ref` 和 `out ref` 關鍵字。 下表顯示如何F#解讀發出的C#內容：

|C#建構|F#推測|
|------------|---------|
|`ref` 傳回值|`outref<'T>`|
|`ref readonly` 傳回值|`inref<'T>`|
|`in ref` 參數|`inref<'T>`|
|`out ref` 參數|`outref<'T>`|

下表顯示發出的F#內容：

|F#建構|發出的結構|
|------------|-----------------|
|`inref<'T>` 引數|在引數上 `[In]` 屬性|
|`inref<'T>` 傳回|值 `modreq` 屬性|
|抽象位置或執行中的 `inref<'T>`|`modreq` 引數或傳回|
|`outref<'T>` 引數|在引數上 `[Out]` 屬性|

### <a name="type-inference-and-overloading-rules"></a>型別推斷和多載規則

在下列情況下， F#編譯器會推斷 `inref<'T>` 型別：

1. 具有 `IsReadOnly` 屬性的 .NET 參數或傳回型別。
2. 結構型別上沒有可變欄位的 `this` 指標。
3. 衍生自另一個 `inref<_>` 指標之記憶體位置的位址。

當取得 `inref` 的隱含位址時，會慣用具有類型 `SomeType` 引數的多載，而此多載具有類型 `inref<SomeType>`的引數。 例如，

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

在這兩種情況下，會解析採用 `System.DateTime` 的多載，而不是採用 `inref<System.DateTime>`的多載。

## <a name="byref-like-structs"></a>類似 Byref 的結構

除了 `byref`/`inref`/`outref` 三個以外，您還可以定義自己的結構，以符合類似 `byref`的語義。 這會透過 <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> 屬性來完成：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 不表示 `Struct`。 這兩者都必須存在於類型上。

中F#的「`byref`贊」結構是堆疊系結的實值型別。 它永遠不會在受控堆積上配置。 `byref`類似的結構對高效能程式設計很有用，因為它會強制執行一組有關存留期和非捕捉的強式檢查。 規則包括：

* 它們可用來做為函式參數、方法參數、區域變數、方法傳回。
* 它們不能是類別或一般結構的靜態或實例成員。
* 它們無法由任何結束結構（`async` 方法或 lambda 運算式）來捕捉。
* 它們不能用來做為泛型參數。

這最後一點對F#管線型程式設計很重要，因為 `|>` 是參數化其輸入類型的泛型函式。 這項限制可能會在未來 `|>` 放寬，因為它是內嵌的，而且不會對其主體中的非內嵌泛型函式進行任何呼叫。

雖然這些規則非常嚴格地限制使用方式，但它們會以安全的方式滿足高效能運算的承諾。

## <a name="byref-returns"></a>Byref 傳回

可以產生和F#取用來自函數或成員的 Byref 回傳。 使用 `byref`傳回的方法時，會隱含地取值此值。 例如，

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

若要避免隱含取值，例如透過多個連鎖呼叫傳遞參考，請使用 `&x` （其中 `x` 是值）。

您也可以直接指派給 return `byref`。 請考慮下列（高度命令式）程式：

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

此為輸出：

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Byref 的範圍

`let`系結的值不能有超過其定義範圍的參考。 例如，不允許下列情況：

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

這會根據您是否使用優化開啟或關閉來進行編譯，而無法取得不同的結果。
