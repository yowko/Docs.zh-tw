---
title: F# 4.5 - F# 指南中的新增功能
description: 獲取 F# 4.5 中提供的新功能的概述。
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186128"
---
# <a name="whats-new-in-f-45"></a>F# 4.5 中的新增功能

F# 4.5 為 F# 語言添加了多項改進。 這些功能中有許多被添加到一起，使您能夠在 F# 中編寫高效的代碼，同時確保此代碼是安全的。 這樣做意味著在使用這些構造時向語言添加一些概念和大量編譯器分析。

## <a name="get-started"></a>開始使用

F# 4.5 在所有 .NET 核心發行版本和視覺化工作室工具中均可用。 [開始使用 F#](../get-started/index.md)瞭解更多資訊。

## <a name="span-and-byref-like-structs"></a>跨度和位元組式結構

.NET Core 中引入<xref:System.Span%601>的類型允許您以強型別的方式表示記憶體中的緩衝區，現在 F# 中允許使用 F# 4.5。 下面的示例演示如何使用具有不同緩衝區表示表示的 對 的<xref:System.Span%601>函數操作：

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

這方面的一個重要方面是，Span 和其他類似[byref 的構造](../language-reference/structures.md#byreflike-structs)具有由編譯器執行的非常嚴格的靜態分析，這些分析以您可能會發現意外的方式限制它們的使用。 這是 F# 4.5 中引入的性能、表現力和安全性之間的基本權衡。

## <a name="revamped-byrefs"></a>已改造的參考

在 F# 4.5 之前，F# 中的[Byrefs](../language-reference/byrefs.md)對許多應用程式不安全且不健全。 在 F# 4.5 中解決了 byrefs 周圍的聲音問題，並且還應用了對跨度和 byref 類似結構的相同靜態分析。

### <a name="inreft-and-outreft"></a>inref<'t't>和出<'t'>

為了表示唯讀、只寫和讀/寫託管指標的概念，F# 4.5 分別引入了`inref<'T>`表示唯讀`outref<'T>`指標和只寫指標的類型。 每個都有不同的語義。 例如，您不能寫入 ： `inref<'T>`

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

預設情況下，型別推斷將推斷託管指標`inref<'T>`與 F# 代碼的不可變性質一致，除非某些內容已聲明為可變指標。 要使某些內容具有可寫性，您需要在將類型位址傳遞給操作`mutable`它的函數或成員之前聲明類型。 要瞭解更多資訊，請參閱[Byrefs](../language-reference/byrefs.md)。

## <a name="readonly-structs"></a>唯讀結構

從 F# 4.5 開始，您可以用<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>這樣的來對結構進行加號：

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

這不允許您在結構中聲明可變成員，併發出中繼資料，允許 F# 和 C# 在從程式集使用時將其視為唯讀。 要瞭解更多資訊，請參閱[唯讀結構](../language-reference/structures.md#readonly-structs)。

## <a name="void-pointers"></a>虛空指標

類型`voidptr`將添加到 F# 4.5，以下函數也包括：

* `NativePtr.ofVoidPtr`將 void 指標轉換為本機 int 指標
* `NativePtr.toVoidPtr`將本機 int 指標轉換為空指標

當與使用 void 指標的本機組件進行交互操作時，這非常有用。

## <a name="the-match-keyword"></a>`match!` 關鍵字

關鍵字`match!`在計算運算式內增強模式匹配：

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

這允許您縮短通常涉及混合選項（或其他類型）的代碼與計算運算式（如非同步）。 要瞭解更多資訊，請參閱[匹配！](../language-reference/computation-expressions.md#match)

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>在陣列、清單和序列運算式中放寬了向上轉換要求

混合類型，其中一個類型可以從陣列、清單和序列運算式的另一個內部繼承，傳統上需要您將任何派生類型用`:>`或`upcast`將其父類型向上轉換。 這是現在放鬆，如下所示：

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>陣列和清單運算式的縮進放鬆

在 F# 4.5 之前，當作為參數傳遞給方法調用時，需要過度縮進陣列和清單運算式。 不再需要這一點：

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
