---
title: F# 4.6 的新功能- F#指南
description: 取得4.6 中F#可用的新功能總覽。
ms.date: 11/27/2019
ms.openlocfilehash: 81d3e988d044cb16f8ec079118fd0ede2dabc587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644079"
---
# <a name="whats-new-in-f-46"></a><span data-ttu-id="e0e7c-103">4\.6 中F#的新功能</span><span class="sxs-lookup"><span data-stu-id="e0e7c-103">What's new in F# 4.6</span></span>

<span data-ttu-id="e0e7c-104">F#4.6 新增多項語言的F#增強功能。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-104">F# 4.6 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="e0e7c-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="e0e7c-105">Get started</span></span>

<span data-ttu-id="e0e7c-106">F#4.6 適用于所有 .NET Core 發行版本和 Visual Studio 工具。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-106">F# 4.6 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="e0e7c-107">[開始使用F# ](../get-started/index.md)以深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="anonymous-records"></a><span data-ttu-id="e0e7c-108">匿名記錄</span><span class="sxs-lookup"><span data-stu-id="e0e7c-108">Anonymous records</span></span>

<span data-ttu-id="e0e7c-109">[匿名記錄](../language-reference/anonymous-records.md)是4.6 中F#引進的F#一種新類型。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-109">[Anonymous records](../language-reference/anonymous-records.md) are a new kind of F# type introduced in F# 4.6.</span></span> <span data-ttu-id="e0e7c-110">它們是命名值的簡單匯總，不需要在使用之前宣告。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-110">They are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="e0e7c-111">您可以將它們宣告為結構或參考型別。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-111">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="e0e7c-112">它們預設是參考型別。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-112">They're reference types by default.</span></span>

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

<span data-ttu-id="e0e7c-113">當您想要將實值型別分組，而且在效能相關的案例中運作時，它們也可以宣告為結構：</span><span class="sxs-lookup"><span data-stu-id="e0e7c-113">They can also be declared as structs for when you want to group value types and are operating in performance-sensitive scenarios:</span></span>

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

<span data-ttu-id="e0e7c-114">這些功能非常強大，可用於許多案例。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-114">They're quite powerful and can be used in numerous scenarios.</span></span> <span data-ttu-id="e0e7c-115">深入瞭解[匿名記錄](../language-reference/anonymous-records.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-115">Learn more at [Anonymous records](../language-reference/anonymous-records.md).</span></span>

## <a name="valueoption-functions"></a><span data-ttu-id="e0e7c-116">ValueOption 函式</span><span class="sxs-lookup"><span data-stu-id="e0e7c-116">ValueOption functions</span></span>

<span data-ttu-id="e0e7c-117">4\.5 中F#新增的 ValueOption 類型現在具有選項類型的「模組系結函式同位」。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-117">The ValueOption type added in F# 4.5 now has "module-bound function parity" with the Option type.</span></span> <span data-ttu-id="e0e7c-118">一些較常使用的範例如下：</span><span class="sxs-lookup"><span data-stu-id="e0e7c-118">Some of the more commonly-used examples are as follows:</span></span>

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> None
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> Some

let reversedString = strOpt |> Option.bind reverse
```

<span data-ttu-id="e0e7c-119">這可讓 ValueOption 在實數值型別改善效能的案例中使用，就像選項一樣。</span><span class="sxs-lookup"><span data-stu-id="e0e7c-119">This allows for ValueOption to be used just like Option in scenarios where having a value type improves performance.</span></span>
