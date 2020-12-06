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
# <a name="what-is-f"></a>什麼是 F\#

F # 是一種功能性程式設計語言，可讓您輕鬆地撰寫正確且可維護的程式碼。

F # 程式設計主要牽涉到定義型別和函式，這些型別和函式會自動加以推斷。 這可讓您的焦點保持在問題領域並操作其資料，而不是程式設計的詳細資料。

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

F # 有許多功能，包括：

* 輕量語法
* 預設為不可變
* 型別推斷和自動一般化
* 一級函式
* 強大的資料類型
* 模式比對
* 非同步程式設計

[F # 語言參考](./language-reference/index.md)中記載了一組完整的功能。

## <a name="rich-data-types"></a>豐富的資料類型

資料類型（例如 [記錄](./language-reference/records.md) 和 [差異等位）可讓您](./language-reference/discriminated-unions.md) 代表複雜的資料和網域。

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

F # 記錄和差異聯集預設為非 null、不變且可比較，因此很容易使用。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>搭配函式和模式比對來強制執行正確性

F # 函式在實務上很容易宣告和強大。 結合 [模式](./language-reference/pattern-matching.md)比對時，它們可讓您定義編譯器強制執行其正確性的行為。

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

F # 函式也是第一個類別，這表示它們可以作為參數傳遞，並從其他函式傳回。

## <a name="functions-to-define-operations-on-objects"></a>定義物件作業的函數

F # 對物件有完整的支援，當您需要 blend 資料和功能時，這些物件是很有用的資料類型。 F # 函式是用來操作物件。

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

與其撰寫以物件為導向的程式碼，在 F # 中，您通常會撰寫程式碼，將物件視為另一種資料類型，以便處理函式。 [泛型介面](./language-reference/interfaces.md)、[物件運算式](./language-reference/object-expressions.md)和合理的[成員](./language-reference/members/index.md)用法等功能，在較大的 F # 程式中很常見。

## <a name="next-steps"></a>後續步驟

若要深入瞭解一組較大的 F # 功能，請參閱 [F # 導覽](tour.md)。
