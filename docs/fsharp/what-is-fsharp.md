---
title: 什麼是F#
description: 了解F#程式語言是以及F#程式設計如下。 了解豐富的資料類型、 函式，以及它們如何相互配合。
ms.date: 08/03/2018
ms.openlocfilehash: ea82147e4e6d3c980fb224eeafd805c7ed53f8f2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966954"
---
# <a name="what-is-f"></a><span data-ttu-id="1a8c5-104">F 是什麼\#</span><span class="sxs-lookup"><span data-stu-id="1a8c5-104">What is F\#</span></span>

<span data-ttu-id="1a8c5-105">F#是功能的程式設計語言，可讓您更輕鬆地撰寫正確且可維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="1a8c5-106">F#主要程式設計需要定義類型和函式型別推斷和自動一般化。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="1a8c5-107">這可讓您專注在問題領域，以及管理其資料，而不是程式設計的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

<span data-ttu-id="1a8c5-108">F#有數種功能，包括：</span><span class="sxs-lookup"><span data-stu-id="1a8c5-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="1a8c5-109">輕量型語法</span><span class="sxs-lookup"><span data-stu-id="1a8c5-109">Lightweight syntax</span></span>
* <span data-ttu-id="1a8c5-110">不可變的預設值</span><span class="sxs-lookup"><span data-stu-id="1a8c5-110">Immutable by default</span></span>
* <span data-ttu-id="1a8c5-111">型別推斷和自動一般化</span><span class="sxs-lookup"><span data-stu-id="1a8c5-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="1a8c5-112">第一級函式</span><span class="sxs-lookup"><span data-stu-id="1a8c5-112">First-class functions</span></span>
* <span data-ttu-id="1a8c5-113">功能強大的資料類型</span><span class="sxs-lookup"><span data-stu-id="1a8c5-113">Powerful data types</span></span>
* <span data-ttu-id="1a8c5-114">模式比對</span><span class="sxs-lookup"><span data-stu-id="1a8c5-114">Pattern matching</span></span>
* <span data-ttu-id="1a8c5-115">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="1a8c5-115">Async programming</span></span>

<span data-ttu-id="1a8c5-116">一組完整的功能都記載於[F#語言參考](language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="1a8c5-117">豐富的資料類型</span><span class="sxs-lookup"><span data-stu-id="1a8c5-117">Rich data types</span></span>

<span data-ttu-id="1a8c5-118">資料類型，例如[記錄](language-reference/records.md)並[差別聯集](language-reference/discriminated-unions.md)可讓您表示複雜的資料和網域。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

<span data-ttu-id="1a8c5-119">F#記錄和差別聯的集為非 null、 不可變的和根據預設，使其非常容易使用的比較。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="1a8c5-120">強制使用函式和模式比對的正確性</span><span class="sxs-lookup"><span data-stu-id="1a8c5-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="1a8c5-121">F#函式會宣告簡單且功能強大，在實務上。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="1a8c5-122">結合[模式比對](language-reference/pattern-matching.md)，它們可讓您定義其正確性，編譯器會強制執行的行為。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

<span data-ttu-id="1a8c5-123">F#函式也是第一級，表示它們可以做為參數傳遞，從其他函式傳回的。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="1a8c5-124">若要在物件上定義作業的函式</span><span class="sxs-lookup"><span data-stu-id="1a8c5-124">Functions to define operations on objects</span></span>

<span data-ttu-id="1a8c5-125">F#提供物件，也就是有用的資料類型，當您需要的資料與功能的 blend 的完整的支援。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="1a8c5-126">F#函式用來操作物件。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="1a8c5-127">而不是撰寫程式碼，是物件導向、 在  F#，您通常會撰寫程式碼，會將物件做為另一個資料類型的函式來操作。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="1a8c5-128">這類功能[泛型介面](language-reference/interfaces.md)，[物件運算式](language-reference/object-expressions.md)，以及審慎使用[成員](language-reference/members/index.md)常見於較大F#程式。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1a8c5-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1a8c5-129">Next steps</span></span>

<span data-ttu-id="1a8c5-130">若要深入了解大的一組F#功能，請參閱[F#教學課程](tour.md)。</span><span class="sxs-lookup"><span data-stu-id="1a8c5-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>