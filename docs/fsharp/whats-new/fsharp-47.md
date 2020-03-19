---
title: F# 4.7 - F# 指南中的新增功能
description: 獲取 F# 4.7 中提供的新功能的概述。
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185867"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="16399-103">F# 4.7 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="16399-103">What's new in F# 4.7</span></span>

<span data-ttu-id="16399-104">F# 4.7 為 F# 語言添加了多項改進。</span><span class="sxs-lookup"><span data-stu-id="16399-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="16399-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="16399-105">Get started</span></span>

<span data-ttu-id="16399-106">F# 4.7 在所有 .NET 核心發行版本和視覺化工作室工具中均可用。</span><span class="sxs-lookup"><span data-stu-id="16399-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="16399-107">[開始使用 F#](../get-started/index.md)瞭解更多資訊。</span><span class="sxs-lookup"><span data-stu-id="16399-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="16399-108">語言版本</span><span class="sxs-lookup"><span data-stu-id="16399-108">Language version</span></span>

<span data-ttu-id="16399-109">F# 4.7 編譯器引入了通過專案檔案中的屬性設置有效語言版本的能力：</span><span class="sxs-lookup"><span data-stu-id="16399-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="16399-110">可以將其`4.6`設置為 值 、`4.7``latest`和`preview`。</span><span class="sxs-lookup"><span data-stu-id="16399-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="16399-111">預設值為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="16399-111">The default is `latest`.</span></span>

<span data-ttu-id="16399-112">如果將其設置為`preview`，編譯器將啟動編譯器中實現的所有 F# 預覽功能。</span><span class="sxs-lookup"><span data-stu-id="16399-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="16399-113">隱式收益</span><span class="sxs-lookup"><span data-stu-id="16399-113">Implicit yields</span></span>

<span data-ttu-id="16399-114">不再需要在`yield`可以推斷類型的陣列、清單、序列或計算運算式中應用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="16399-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="16399-115">在下面的示例中，兩個運算式都需要 F# 4.7 之前每個條目的`yield`語句：</span><span class="sxs-lookup"><span data-stu-id="16399-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]
```

<span data-ttu-id="16399-116">如果引入單個`yield`關鍵字，則所有其他項也必須已`yield`應用於該關鍵字。</span><span class="sxs-lookup"><span data-stu-id="16399-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="16399-117">在運算式中使用時，隱式收益不會啟動，該運算式`yield!`還用於執行諸如拼平序列之類的操作。</span><span class="sxs-lookup"><span data-stu-id="16399-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="16399-118">在這些情況下，今天必須繼續`yield`使用。</span><span class="sxs-lookup"><span data-stu-id="16399-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="16399-119">萬用字元識別碼</span><span class="sxs-lookup"><span data-stu-id="16399-119">Wildcard identifiers</span></span>

<span data-ttu-id="16399-120">在涉及類的 F# 代碼中，自識別碼必須始終在成員聲明中顯式。</span><span class="sxs-lookup"><span data-stu-id="16399-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="16399-121">但是，在從未使用自識別碼的情況下，傳統上使用雙底線來指示無名的自識別碼是慣例。</span><span class="sxs-lookup"><span data-stu-id="16399-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="16399-122">現在可以使用單個底線：</span><span class="sxs-lookup"><span data-stu-id="16399-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="16399-123">這也適用于`for`迴圈：</span><span class="sxs-lookup"><span data-stu-id="16399-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="16399-124">縮進鬆弛</span><span class="sxs-lookup"><span data-stu-id="16399-124">Indentation relaxations</span></span>

<span data-ttu-id="16399-125">在 F# 4.7 之前，主建構函式和靜態成員參數的縮進要求要求過高的縮進。</span><span class="sxs-lookup"><span data-stu-id="16399-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="16399-126">它們現在只需要一個縮進範圍：</span><span class="sxs-lookup"><span data-stu-id="16399-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
