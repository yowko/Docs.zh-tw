---
title: F# 4.7 的新功能- F#指南
description: 取得4.7 中F#可用的新功能總覽。
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644065"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="9a984-103">4\.7 中F#的新功能</span><span class="sxs-lookup"><span data-stu-id="9a984-103">What's new in F# 4.7</span></span>

<span data-ttu-id="9a984-104">F#4.7 新增多項語言的F#增強功能。</span><span class="sxs-lookup"><span data-stu-id="9a984-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="9a984-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="9a984-105">Get started</span></span>

<span data-ttu-id="9a984-106">F#4.7 適用于所有 .NET Core 發行版本和 Visual Studio 工具。</span><span class="sxs-lookup"><span data-stu-id="9a984-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="9a984-107">[開始使用F# ](../get-started/index.md)以深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="9a984-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="9a984-108">語言版本</span><span class="sxs-lookup"><span data-stu-id="9a984-108">Language version</span></span>

<span data-ttu-id="9a984-109">F# 4.7 編譯器導入了透過專案檔中的屬性來設定有效語言版本的功能：</span><span class="sxs-lookup"><span data-stu-id="9a984-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9a984-110">您可以將它設定為 `4.6`、`4.7`、`latest`和 `preview`的值。</span><span class="sxs-lookup"><span data-stu-id="9a984-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="9a984-111">預設為 `latest`。</span><span class="sxs-lookup"><span data-stu-id="9a984-111">The default is `latest`.</span></span>

<span data-ttu-id="9a984-112">如果您將它設定為 `preview`，您的編譯器將F#會啟動在編譯器中執行的所有預覽功能。</span><span class="sxs-lookup"><span data-stu-id="9a984-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="9a984-113">隱含產生</span><span class="sxs-lookup"><span data-stu-id="9a984-113">Implicit yields</span></span>

<span data-ttu-id="9a984-114">您不再需要在可推斷類型的陣列、清單、序列或計算運算式中套用 `yield` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9a984-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="9a984-115">在下列範例中，兩個運算式都需要F# 4.7 之前每個專案的 `yield` 語句：</span><span class="sxs-lookup"><span data-stu-id="9a984-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="9a984-116">如果您引進單一 `yield` 關鍵字，則每個其他專案也必須套用 `yield`。</span><span class="sxs-lookup"><span data-stu-id="9a984-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="9a984-117">在運算式中使用時，隱含產生不會啟動，也會使用 `yield!` 來執行像是壓平定序序列等動作。</span><span class="sxs-lookup"><span data-stu-id="9a984-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="9a984-118">在這些情況下，您必須繼續使用 `yield`。</span><span class="sxs-lookup"><span data-stu-id="9a984-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="9a984-119">萬用字元識別碼</span><span class="sxs-lookup"><span data-stu-id="9a984-119">Wildcard identifiers</span></span>

<span data-ttu-id="9a984-120">在F#涉及類別的程式碼中，自我識別元在成員宣告中必須一律是明確的。</span><span class="sxs-lookup"><span data-stu-id="9a984-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="9a984-121">但在從未使用過自我識別碼的情況下，傳統上使用雙底線來表示不具有任何自我識別元的慣例。</span><span class="sxs-lookup"><span data-stu-id="9a984-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="9a984-122">您現在可以使用單一底線：</span><span class="sxs-lookup"><span data-stu-id="9a984-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="9a984-123">這也適用于 `for` 迴圈：</span><span class="sxs-lookup"><span data-stu-id="9a984-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="9a984-124">縮排 relaxations</span><span class="sxs-lookup"><span data-stu-id="9a984-124">Indentation relaxations</span></span>

<span data-ttu-id="9a984-125">在F# 4.7 之前，主要的函式和靜態成員引數的縮排需求需要過多的縮排。</span><span class="sxs-lookup"><span data-stu-id="9a984-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="9a984-126">它們現在只需要單一縮排範圍：</span><span class="sxs-lookup"><span data-stu-id="9a984-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
