---
title: 什麼是 F#
description: '瞭解 F # 程式設計語言為何，以及 F # 程式設計的樣子。 瞭解豐富的資料類型、函式，以及它們如何彼此配合。'
ms.date: 08/03/2018
ms.openlocfilehash: a6bad3e1db63c3fe948b5916925d5eb24a18a41c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739473"
---
# <a name="what-is-f"></a><span data-ttu-id="3251d-104">什麼是 F\#</span><span class="sxs-lookup"><span data-stu-id="3251d-104">What is F\#</span></span>

<span data-ttu-id="3251d-105">F # 是一種功能性程式設計語言，可讓您輕鬆地撰寫正確且可維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3251d-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="3251d-106">F # 程式設計主要牽涉到定義型別和函式，這些型別和函式會自動加以推斷。</span><span class="sxs-lookup"><span data-stu-id="3251d-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="3251d-107">這可讓您的焦點保持在問題領域並操作其資料，而不是程式設計的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3251d-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn $"{greeting}")

    0
```

<span data-ttu-id="3251d-108">F # 有許多功能，包括：</span><span class="sxs-lookup"><span data-stu-id="3251d-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="3251d-109">輕量語法</span><span class="sxs-lookup"><span data-stu-id="3251d-109">Lightweight syntax</span></span>
* <span data-ttu-id="3251d-110">預設為不可變</span><span class="sxs-lookup"><span data-stu-id="3251d-110">Immutable by default</span></span>
* <span data-ttu-id="3251d-111">型別推斷和自動一般化</span><span class="sxs-lookup"><span data-stu-id="3251d-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="3251d-112">一級函式</span><span class="sxs-lookup"><span data-stu-id="3251d-112">First-class functions</span></span>
* <span data-ttu-id="3251d-113">強大的資料類型</span><span class="sxs-lookup"><span data-stu-id="3251d-113">Powerful data types</span></span>
* <span data-ttu-id="3251d-114">模式比對</span><span class="sxs-lookup"><span data-stu-id="3251d-114">Pattern matching</span></span>
* <span data-ttu-id="3251d-115">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="3251d-115">Async programming</span></span>

<span data-ttu-id="3251d-116">[F # 語言參考](./language-reference/index.md)中記載了一組完整的功能。</span><span class="sxs-lookup"><span data-stu-id="3251d-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="3251d-117">豐富的資料類型</span><span class="sxs-lookup"><span data-stu-id="3251d-117">Rich data types</span></span>

<span data-ttu-id="3251d-118">資料類型（例如 [記錄](./language-reference/records.md) 和 [差異等位）可讓您](./language-reference/discriminated-unions.md) 代表複雜的資料和網域。</span><span class="sxs-lookup"><span data-stu-id="3251d-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

```fsharp
// Group data with Records
type SuccessfulWithdrawal =
    { Amount: decimal
      Balance: decimal }

type FailedWithdrawal =
    { Amount: decimal
      Balance: decimal
      IsOverdraft: bool }

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

<span data-ttu-id="3251d-119">F # 記錄和差異聯集預設為非 null、不變且可比較，因此很容易使用。</span><span class="sxs-lookup"><span data-stu-id="3251d-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="3251d-120">搭配函式和模式比對來強制執行正確性</span><span class="sxs-lookup"><span data-stu-id="3251d-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="3251d-121">F # 函式在實務上很容易宣告和強大。</span><span class="sxs-lookup"><span data-stu-id="3251d-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="3251d-122">結合 [模式](./language-reference/pattern-matching.md)比對時，它們可讓您定義編譯器強制執行其正確性的行為。</span><span class="sxs-lookup"><span data-stu-id="3251d-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f{s.Amount}"
    | InsufficientFunds f -> printfn "Failed: balance is %f{f.Balance}"
    | CardExpired d -> printfn "Failed: card expired on {d}"
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

<span data-ttu-id="3251d-123">F # 函式也是第一個類別，這表示它們可以作為參數傳遞，並從其他函式傳回。</span><span class="sxs-lookup"><span data-stu-id="3251d-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="3251d-124">定義物件作業的函數</span><span class="sxs-lookup"><span data-stu-id="3251d-124">Functions to define operations on objects</span></span>

<span data-ttu-id="3251d-125">F # 對物件有完整的支援，當您需要 blend 資料和功能時，這些物件是很有用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3251d-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="3251d-126">F # 函式是用來操作物件。</span><span class="sxs-lookup"><span data-stu-id="3251d-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="3251d-127">與其撰寫以物件為導向的程式碼，在 F # 中，您通常會撰寫程式碼，將物件視為另一種資料類型，以便處理函式。</span><span class="sxs-lookup"><span data-stu-id="3251d-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="3251d-128">[泛型介面](./language-reference/interfaces.md)、[物件運算式](./language-reference/object-expressions.md)和合理的[成員](./language-reference/members/index.md)用法等功能，在較大的 F # 程式中很常見。</span><span class="sxs-lookup"><span data-stu-id="3251d-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3251d-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3251d-129">Next steps</span></span>

<span data-ttu-id="3251d-130">若要深入瞭解一組較大的 F # 功能，請參閱 [F # 導覽](tour.md)。</span><span class="sxs-lookup"><span data-stu-id="3251d-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
