---
title: 什麼是 F#
description: 瞭解什麼是程式F#設計語言，以及程式F#設計的樣子。 瞭解豐富的資料類型、函式，以及它們如何彼此搭配運作。
ms.date: 08/03/2018
ms.openlocfilehash: 3cba509f59a8e81e1a0264de7451e9d80304d768
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332738"
---
# <a name="what-is-f"></a>什麼是 F @ no__t-0

F#是一種功能性程式設計語言，可讓您輕鬆地撰寫正確和可維護的程式碼。

F#程式設計主要牽涉到定義型別和函式，這些類型和函數會自動推斷和一般化。 這可讓您的焦點停留在問題網域並操作其資料，而不是程式設計的細節。

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

F#有許多功能，包括：

* 輕量語法
* 預設為不可變
* 型別推斷和自動一般化
* 一級函式
* 功能強大的資料類型
* 模式比對
* 非同步程式設計

一組完整的功能記載于[ F#語言參考](./language-reference/index.md)中。

## <a name="rich-data-types"></a>豐富的資料類型

資料類型（例如[記錄](./language-reference/records.md)和[區分](./language-reference/discriminated-unions.md)等位）可讓您代表複雜的資料和定義域。

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

F#記錄和差異聯集預設為非 null、不可變且可比較，因此非常容易使用。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>使用函數和模式比對強制執行正確性

F#函式在實務上很容易宣告且功能強大。 結合[模式](./language-reference/pattern-matching.md)比對時，可讓您定義編譯器強制執行正確性的行為。

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

F#函式也是第一個類別，這表示它們可以當做參數傳遞，並從其他函數傳回。

## <a name="functions-to-define-operations-on-objects"></a>定義物件作業的函數

F#具有物件的完整支援，當您需要 blend 資料和功能時，這是有用的資料類型。 F#函數是用來操作物件。

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

與其撰寫物件導向的程式碼，在中F#，您通常會撰寫程式碼，將物件視為另一個資料類型，以供操作。 [泛型介面](./language-reference/interfaces.md)、[物件運算式](./language-reference/object-expressions.md)，以及合理使用[成員](./language-reference/members/index.md)等功能，在較大F#的程式中很常見。

## <a name="next-steps"></a>後續步驟

若要深入瞭解更多的F#功能集，請參閱[ F#導覽](tour.md)。
