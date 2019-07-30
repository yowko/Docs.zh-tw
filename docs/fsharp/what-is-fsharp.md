---
title: 什麼是 F#
description: 瞭解什麼是程式F#設計語言, 以及程式F#設計的樣子。 瞭解豐富的資料類型、函式, 以及它們如何彼此搭配運作。
ms.date: 08/03/2018
ms.openlocfilehash: 0c576fe49fadebd68e4fc9d2b20ea8f0cb991af5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630456"
---
# <a name="what-is-f"></a><span data-ttu-id="20507-104">什麼是 F\#</span><span class="sxs-lookup"><span data-stu-id="20507-104">What is F\#</span></span>

<span data-ttu-id="20507-105">F#是一種功能性程式設計語言, 可讓您輕鬆地撰寫正確和可維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="20507-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="20507-106">F#程式設計主要牽涉到定義型別和函式, 這些類型和函數會自動推斷和一般化。</span><span class="sxs-lookup"><span data-stu-id="20507-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="20507-107">這可讓您的焦點停留在問題網域並操作其資料, 而不是程式設計的細節。</span><span class="sxs-lookup"><span data-stu-id="20507-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="20507-108">F#有許多功能, 包括:</span><span class="sxs-lookup"><span data-stu-id="20507-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="20507-109">輕量語法</span><span class="sxs-lookup"><span data-stu-id="20507-109">Lightweight syntax</span></span>
* <span data-ttu-id="20507-110">預設為不可變</span><span class="sxs-lookup"><span data-stu-id="20507-110">Immutable by default</span></span>
* <span data-ttu-id="20507-111">型別推斷和自動一般化</span><span class="sxs-lookup"><span data-stu-id="20507-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="20507-112">一級函式</span><span class="sxs-lookup"><span data-stu-id="20507-112">First-class functions</span></span>
* <span data-ttu-id="20507-113">功能強大的資料類型</span><span class="sxs-lookup"><span data-stu-id="20507-113">Powerful data types</span></span>
* <span data-ttu-id="20507-114">模式比對</span><span class="sxs-lookup"><span data-stu-id="20507-114">Pattern matching</span></span>
* <span data-ttu-id="20507-115">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="20507-115">Async programming</span></span>

<span data-ttu-id="20507-116">一組完整的功能記載于[ F#語言參考](./language-reference/index.md)中。</span><span class="sxs-lookup"><span data-stu-id="20507-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="20507-117">豐富的資料類型</span><span class="sxs-lookup"><span data-stu-id="20507-117">Rich data types</span></span>

<span data-ttu-id="20507-118">資料類型 (例如[記錄](./language-reference/records.md)和[區分](./language-reference/discriminated-unions.md)等位) 可讓您代表複雜的資料和定義域。</span><span class="sxs-lookup"><span data-stu-id="20507-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="20507-119">F#記錄和差異聯集預設為非 null、不可變且可比較, 因此非常容易使用。</span><span class="sxs-lookup"><span data-stu-id="20507-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="20507-120">使用函數和模式比對強制執行正確性</span><span class="sxs-lookup"><span data-stu-id="20507-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="20507-121">F#函式在實務上很容易宣告且功能強大。</span><span class="sxs-lookup"><span data-stu-id="20507-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="20507-122">結合[模式](./language-reference/pattern-matching.md)比對時, 可讓您定義編譯器強制執行正確性的行為。</span><span class="sxs-lookup"><span data-stu-id="20507-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="20507-123">F#函式也是第一個類別, 這表示它們可以當做參數傳遞, 並從其他函數傳回。</span><span class="sxs-lookup"><span data-stu-id="20507-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="20507-124">定義物件作業的函數</span><span class="sxs-lookup"><span data-stu-id="20507-124">Functions to define operations on objects</span></span>

<span data-ttu-id="20507-125">F#具有物件的完整支援, 當您需要 blend 資料和功能時, 這是有用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="20507-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="20507-126">F#函數是用來操作物件。</span><span class="sxs-lookup"><span data-stu-id="20507-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<[<EqualityConditionOn>] 'T when 'T: comparison>(elements: seq<'T>) =
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

<span data-ttu-id="20507-127">與其撰寫物件導向的程式碼, 在中F#, 您通常會撰寫程式碼, 將物件視為另一個資料類型, 以供操作。</span><span class="sxs-lookup"><span data-stu-id="20507-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="20507-128">[泛型介面](./language-reference/interfaces.md)、[物件運算式](./language-reference/object-expressions.md), 以及合理使用[成員](./language-reference/members/index.md)等功能, 在較大F#的程式中很常見。</span><span class="sxs-lookup"><span data-stu-id="20507-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20507-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20507-129">Next steps</span></span>

<span data-ttu-id="20507-130">若要深入瞭解更多的F#功能集, 請參閱[ F#導覽](tour.md)。</span><span class="sxs-lookup"><span data-stu-id="20507-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
