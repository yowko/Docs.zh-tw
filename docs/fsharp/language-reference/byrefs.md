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
# <a name="byrefs"></a>Byrefs

F# 具有在低級程式設計領域處理的兩個主要功能領域：

* `byref` /類型`inref`，/託管`outref`指標。 它們對使用有限制，因此您不能編譯在運行時不正確程式。
* 類似`byref`結構的結構，它是具有與 相似的語義和相同的編譯時間限制[的結構](structures.md)`byref<'T>`。 一個例子是<xref:System.Span%601>。

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

有三種形式： `byref`

* `inref<'T>`，用於讀取基礎值的託管指標。
* `outref<'T>`，用於寫入基礎值的託管指標。
* `byref<'T>`，用於讀取和寫入基礎值的託管指標。

`byref<'T>`可以傳遞預期 為`inref<'T>`的 。 同樣，`byref<'T>`可以傳遞預期 為`outref<'T>`的 。

## <a name="using-byrefs"></a>使用參考

要使用`inref<'T>`， 需要獲取具有 的`&`指標值：

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

要使用`outref<'T>`或`byref<'T>`寫入指標，還必須使獲取指向`mutable`的指標的值。

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

如果只編寫指標而不是讀取指標，請考慮使用`outref<'T>`而不是`byref<'T>`。

### <a name="inref-semantics"></a>Inref 語義

請考慮下列程式碼：

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

從語義上講，這意味著以下內容：

* 指標的`x`持有者只能使用它讀取該值。
* 任何獲取到`struct`嵌套在其中`SomeStruct`的欄位的指標都是`inref<_>`給定的類型。

以下內容也是如此：

* 其他執行緒或別名對 沒有寫入存取權限，這沒有任何含義`x`。
* 沒有任何暗示是`SomeStruct`不變的`x`，因為是一個。 `inref`

但是，**對於不可變**的 F# 數值型別，`this`將指標推斷為`inref`。

所有這些規則加在一`inref`起意味著指標的持有者不能修改指向的記憶體的即時內容。

### <a name="outref-semantics"></a>外部參照語義

的目的是`outref<'T>`指示指標應只寫入。 出乎意料的是`outref<'T>`，允許讀取基礎值，儘管它的名稱。 這是出於相容性目的。 從語義上講`outref<'T>`，與 沒有什麼`byref<'T>`不同。

### <a name="interop-with-c"></a>與 C 的互通\#

除了`in ref``ref`返回之外，C# 還支援 和`out ref`關鍵字。 下表顯示了 F# 如何解釋 C# 發出的內容：

|C# 構造|F# 推斷|
|------------|---------|
|`ref`傳回值|`outref<'T>`|
|`ref readonly`傳回值|`inref<'T>`|
|`in ref` 參數|`inref<'T>`|
|`out ref` 參數|`outref<'T>`|

下表顯示了 F# 發出的內容：

|F# 構造|已發出構造|
|------------|-----------------|
|`inref<'T>` 引數|`[In]`參數上的屬性|
|`inref<'T>`返回|`modreq`值的屬性|
|`inref<'T>`抽象插槽或實現|`modreq`在參數或返回|
|`outref<'T>` 引數|`[Out]`參數上的屬性|

### <a name="type-inference-and-overloading-rules"></a>型別推斷和重載規則

在`inref<'T>`以下情況下，F# 編譯器會推斷類型：

1. 具有`IsReadOnly`屬性的 .NET 參數或返回類型。
2. 沒有`this`可變欄位的結構類型的指標。
3. 從其他`inref<_>`指標派生的記憶體位置的位址。

當採用 隱式位址`inref`時，具有類型`SomeType`參數的重載優先于具有類型`inref<SomeType>`類型的重載。 例如：

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

在這兩種情況下，重`System.DateTime`載將得到解決，而不是重載。 `inref<System.DateTime>`

## <a name="byref-like-structs"></a>類似 Byref 的結構

`byref` /除了`outref``byref`三者組之外，您還可以定義自己的結構，這些結構可以遵循類似語義。 `inref` / 這與屬性一<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>起完成：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`並不意味著`Struct`. 兩者都必須存在於類型上。

F#`byref`中的"類似"結構是一種堆疊綁定數值型別。 它永遠不會在託管堆上分配。 `byref`類似結構對於高性能程式設計非常有用，因為它通過一組有關存留期和非捕獲的強檢查強制執行。 規則包括：

* 它們可用作函數參數、方法參數、區域變數、方法返回。
* 它們不能是類的靜態或實例成員或正常結構。
* 它們不能被任何閉包構造（`async`方法或 lambda 運算式）捕獲。
* 它們不能用作泛型參數。

最後一點對於 F# 管道樣式程式設計至關重要，用於`|>`參數化其輸入類型的泛型函數也是如此。 將來可能會放寬`|>`此限制，因為它是內聯的，並且不會對其正文中的非內聯泛型函數進行任何調用。

儘管這些規則嚴格限制使用，但它們這樣做是為了以安全的方式實現高性能計算的承諾。

## <a name="byref-returns"></a>Byref 返回

可以生成和使用 F# 函數或成員的 Byref 返回。 使用`byref`-返回方法時，將隱式取消引用該值。 例如：

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

要傳回值 byref，包含該值的變數必須比當前作用域長。
此外，要返回 byref，`&value`請使用 （其中值是比當前作用域長的變數）。

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

為了避免隱式取消引用（例如通過多個連結調用傳遞引用），請使用`&x`（值在哪裡）。 `x`

您也可以直接分配給返回`byref`。 請考慮以下（高度必要）計畫：

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

## <a name="scoping-for-byrefs"></a>位元組範圍

`let`綁定值不能使其引用超過定義該值的範圍。 例如，不允許使用以下內容：

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

這可以防止您獲得不同的結果，具體取決於是否使用優化進行編譯。
