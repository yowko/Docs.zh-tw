---
title: F# 4.6 的新功能- F#指南
description: 取得4.6 中F#可用的新功能總覽。
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980388"
---
# <a name="whats-new-in-f-46"></a>4\.6 中F#的新功能

F#4.6 新增多項語言的F#增強功能。

## <a name="get-started"></a>開始使用

F#4.6 適用于所有 .NET Core 發行版本和 Visual Studio 工具。 [開始使用F# ](../get-started/index.md)以深入瞭解。

## <a name="anonymous-records"></a>匿名記錄

[匿名記錄](../language-reference/anonymous-records.md)是4.6 中F#引進的F#一種新類型。 它們是命名值的簡單匯總，不需要在使用之前宣告。 您可以將它們宣告為結構或參考型別。 它們預設是參考型別。

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

當您想要將實值型別分組，而且在效能相關的案例中運作時，它們也可以宣告為結構：

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

這些功能非常強大，可用於許多案例。 深入瞭解[匿名記錄](../language-reference/anonymous-records.md)。

## <a name="valueoption-functions"></a>ValueOption 函式

4\.5 中F#新增的 ValueOption 類型現在具有選項類型的「模組系結函式同位」。 一些較常使用的範例如下：

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

這可讓 ValueOption 在實數值型別改善效能的案例中使用，就像選項一樣。
