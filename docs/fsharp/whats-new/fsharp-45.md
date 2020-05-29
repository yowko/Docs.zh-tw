---
title: 'F # 4.5 的新功能-F # 指南'
description: '取得 F # 4.5 中可用的新功能總覽。'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202357"
---
# <a name="whats-new-in-f-45"></a>F # 4.5 的新功能

F # 4.5 加入了多項 F # 語言的增強功能。 其中許多功能都已新增在一起，可讓您以 F # 撰寫有效率的程式碼，同時確保此程式碼是安全的。 這麼做表示在使用這些結構時，將幾個概念新增至語言，以及大量編譯器分析。

## <a name="get-started"></a>開始使用

F # 4.5 適用于所有 .NET Core 發行版本和 Visual Studio 工具。 [開始使用 F #](../get-started/index.md)以深入瞭解。

## <a name="span-and-byref-like-structs"></a>Span 和類似 byref 的結構

<xref:System.Span%601>.Net Core 中引進的類型可讓您以強型別方式表示記憶體中的緩衝區，而 f # 中現在允許使用 f # 4.5。 下列範例會示範如何在 <xref:System.Span%601> 具有不同緩衝區標記法的上重複使用函數：

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

其中一個重要的層面是，Span 和其他[byref 類似的結構](../language-reference/structures.md#byreflike-structs)都有非常嚴格的靜態分析，由編譯器執行，以限制其使用方式，因為您可能會發現非預期的情況。 這是在 F # 4.5 中引進的效能、表達和安全性之間的基本取捨。

## <a name="revamped-byrefs"></a>改頭換面 byref

在 F # 4.5 之前，F # 中的[byref](../language-reference/byrefs.md)對許多應用程式而言是不安全的，而是無效:。 Byref 的 Soundness 問題已在 F # 4.5 中解決，同時也套用了對 span 和類似 byref 的結構所做的相同靜態分析。

### <a name="inreft-and-outreft"></a>inref< 不> 和 outref< 不>

為了表示唯讀、僅限寫入和讀取/寫入受控指標的概念，F # 4.5 引進了 `inref<'T>` ， `outref<'T>` 分別代表唯讀和僅限寫入指標的類型。 每個都有不同的語義。 例如，您無法寫入 `inref<'T>` ：

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

根據預設，型別推斷會將 managed 指標推斷為與 `inref<'T>` F # 程式碼的不可變性質相同，除非已經將某些專案宣告為可變動。 若要使其成為可寫入的專案，您必須在將 `mutable` 其位址傳遞給操作它的函式或成員之前，宣告類型。 若要深入瞭解，請參閱[byref](../language-reference/byrefs.md)。

## <a name="readonly-structs"></a>Readonly 結構

從 F # 4.5 開始，您可以使用來標注結構， <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> 如下所示：

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

這不允許您在結構中宣告可變動的成員，並且會發出中繼資料，讓 F # 和 c # 從元件取用時，將它視為唯讀。 若要深入瞭解，請參閱[ReadOnly 結構](../language-reference/structures.md#readonly-structs)。

## <a name="void-pointers"></a>Void 指標

`voidptr`類型會加入 F # 4.5，如下列函數所示：

* `NativePtr.ofVoidPtr`將 void 指標轉換成原生 int 指標
* `NativePtr.toVoidPtr`若要將原生 int 指標轉換成 void 指標

當與使用 void 指標的原生元件互通時，這會很有説明。

## <a name="the-match-keyword"></a>`match!` 關鍵字

關鍵字會在 `match!` 計算運算式內時增強模式比對：

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

這可讓您縮短程式碼，這通常牽涉到混合選項（或其他類型）與計算運算式（例如 async）。 若要深入瞭解，請參閱[match！](../language-reference/computation-expressions.md#match)。

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>陣列、清單和順序運算式中的寬鬆 upcasting 需求

混合型別，其中一個可能繼承自陣列、清單和序列運算式內的另一個類型，傳統上會要求您使用或，將任何衍生的型別向上轉換成其父系型別 `:>` `upcast` 。 這現在是寬鬆的，如下所示：

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>陣列和清單運算式的縮排放寬

在 F # 4.5 之前，當陣列和清單運算式當做引數傳遞給方法呼叫時，您需要過度將它縮排。 已不再需要此動作：

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
