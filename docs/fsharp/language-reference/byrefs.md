---
title: Byref （F#）
description: 深入了解 byref 和 F# 中的類似 byref 類型用於低層級的程式設計。
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "48836877"
---
# <a name="byrefs"></a>Byref

F# 提供處理低階程式設計的空間中的兩個主要功能領域：

* `byref` / `inref` / `outref`類型，也就是 managed 的指標。 它們有使用量限制，因此無法編譯程式時，會在執行階段無效。
* A `byref`-與結構，也就是一樣[結構](structures.md)有類似的語意和相同的編譯時間限制`byref<'T>`。 其中一個範例是<xref:System.Span%601>。

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

## <a name="byref-inref-and-outref"></a>Byref、 inref 和 outref

有三種形式的`byref`:

* `inref<'T>`用於讀取的基礎值的 managed 的指標。
* `outref<'T>`用於將寫入基礎值的 managed 的指標。
* `byref<'T>`用於讀取和寫入基礎值的 managed 的指標。

A`byref<'T>`可以在其中傳遞`inref<'T>`預期。 同樣地，`byref<'T>`可以在其中傳遞`outref<'T>`預期。

## <a name="using-byrefs"></a>使用 byref

若要使用`inref<'T>`，您需要取得的指標值`&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

若要寫入使用指標`outref<'T>`或是`byref<'T>`，您也必須進行抓取的指標值`mutable`。

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

如果您只撰寫的指標，而不是讀取它，請考慮使用`outref<'T>`而不是`byref<'T>`。

### <a name="inref-semantics"></a>Inref 語意

請考慮下列程式碼：

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

語意上來說，這表示下列事項：

* 持有人`x`指標可能只使用它來讀取值。
* 若要取得的任何指標`struct`欄位內變成巢狀`SomeStruct`會提供型別`inref<_>`。

下列條件也成立：

* 沒有任何隱含的其他執行緒或別名並沒有寫入權限`x`。
* 沒有任何隱含的`SomeStruct`不可變之故`x`正在`inref`。

不過，F# 的實值型別，**都**不可變`this`指標被推斷為`inref`。

所有這些規則同時表示的持有人`inref`指標可能不會修改所指向的記憶體的即時內容。

### <a name="outref-semantics"></a>Outref 語意

目的`outref<'T>`是指出只應該從讀取指標。 意外`outref<'T>`讀取基礎的允許值，儘管其名稱。 這是基於相容性。 語意上來說，`outref<'T>`沒什麼兩樣`byref<'T>`。

### <a name="interop-with-c"></a>使用 C# 的 interop #

C# 支援`in ref`並`out ref`關鍵字，除了`ref`傳回。 下表顯示如何 F# 解譯什麼 C# 會發出：

|C# 建構|F# 推斷|
|------------|---------|
|`ref` 傳回值|`outref<'T>`|
|`ref readonly` 傳回值|`inref<'T>`|
|`in ref` 參數|`inref<'T>`|
|`out ref` 參數|`outref<'T>`|

下表顯示哪些 F# 發出：

|F# 建構|發出的建構|
|------------|-----------------|
|`inref<'T>` 引數|`[In]` 引數上的屬性|
|`inref<'T>` 傳回|`modreq` 值的屬性|
|`inref<'T>` 抽象位置或實作中|`modreq` 在 引數或傳回|
|`outref<'T>` 引數|`[Out]` 引數上的屬性|

### <a name="type-inference-and-overloading-rules"></a>型別推斷 」 和 「 多載規則

`inref<'T>`類型由在下列情況下，F# 編譯器推斷：

1. .NET 參數或傳回型別具有`IsReadOnly`屬性。
2. `this`上沒有任何可變動的欄位的結構類型的指標。
3. 記憶體位置的位址衍生自另一個`inref<_>`指標。

當隱含位址`inref`抱，類型的引數的多載`SomeType`應優先於類型的引數的多載`inref<SomeType>`。 例如: 

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

在這兩種情況下，多載採用`System.DateTime`而不是採用的多載解析`inref<System.DateTime>`。

## <a name="byref-like-structs"></a>類似 Byref 結構

除了`byref` / `inref` / `outref`事，您可以定義您自己的結構，可以遵循`byref`-例如語意。 做法是使用<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 並不表示`Struct`。 兩者都必須要有型別。

「`byref`-例如"F# 中的結構是堆疊繫結值型別。 永遠不會在 managed 堆積上配置。 A `byref`-就像結構適用於高效能的程式設計，因為它會強制執行設定的強式存留期和非擷取相關的檢查。 規則包括：

* 它們可用來當做函式參數、 方法參數、 區域變數、 方法會傳回。
* 它們不能是靜態或執行個體的類別或一般結構的成員。
* 它們無法擷取任何關閉的建構 (`async`方法或 lambda 運算式)。
* 它們不能當做泛型參數。

最後一點很重要的 F# 管線樣式程式設計中，為`|>`會參數化為其輸入的類型的泛型函式。 這項限制可能會放寬為`|>`未來，因為它是以內嵌方式，其主體中毫無任何非內嵌的泛型函式的呼叫。

雖然很希望這些規則會限制使用方式，如此一來滿足承諾的高效能運算以安全的方式。

## <a name="byref-returns"></a>Byref 傳回

Byref 傳回從 F# 函式或成員可以產生及取用。 使用時`byref`-傳回方法，這個值是隱含已取值。 例如: 

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

若要避免隱含取值，例如傳遞多個鏈結的呼叫，透過參考使用`&x`(其中`x`是值)。

您可以也可以直接指派給傳回`byref`。 請考慮下列 （高命令式） 的程式：

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

此為輸出：

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>範圍，將 byref

A `let`-繫結的值不能有超過的範圍定義其參考。 例如，下列是不允許：

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

這會讓您取得取決於不同的結果，如果您使用 開啟或關閉的最佳化。
