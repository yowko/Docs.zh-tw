---
title: '什麼是 F #'
description: '了解什麼 F # 程式設計語言和 F # 程式設計的如下。 了解豐富的資料類型、 函式，以及它們如何相互配合。'
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863292"
---
# <a name="what-is-f"></a>什麼是 F # #

F # 是功能性程式設計語言，可讓您更輕鬆地撰寫正確且可維護的程式碼。

F # 程式設計主要牽涉到定義類型和函式型別推斷和自動一般化。 這可讓您專注在問題領域，以及管理其資料，而不是程式設計的詳細資料。

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

F # 提供許多功能，包括：

* 輕量型語法
* 不可變的預設值
* 型別推斷和自動一般化
* 第一級函式
* 功能強大的資料類型
* 模式比對
* 非同步程式設計

一組完整的功能都記載於[F # 語言參考](language-reference/index.md)。

## <a name="rich-data-types"></a>豐富的資料類型

資料類型，例如[記錄](language-reference/records.md)並[差別聯集](language-reference/discriminated-unions.md)可讓您表示複雜的資料和網域。

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

F # 記錄和差別聯的集為非 null、 不可變的和根據預設，使其非常容易使用的比較。

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>強制使用函式和模式比對的正確性

F # 函式會宣告簡單且功能強大，在實務上。 結合[模式比對](language-reference/pattern-matching.md)，它們可讓您定義其正確性，編譯器會強制執行的行為。

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

F # 函式也是第一級，表示它們可以做為參數傳遞，從其他函式傳回的。

## <a name="functions-to-define-operations-on-objects"></a>若要在物件上定義作業的函式

F # 提供物件，相當有用的資料類型，當您需要的資料與功能的 blend 的完整支援。 F # 函式用來操作物件。

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

而不是撰寫是物件導向，F # 中的程式碼，您將經常撰寫程式碼視為物件做為另一個資料類型的函式來操作。 這類功能[泛型介面](language-reference/interfaces.md)，[物件運算式](language-reference/object-expressions.md)，以及審慎善用[成員](language-reference/members/index.md)在較大的 F # 程式中很常見。

## <a name="next-steps"></a>後續步驟

若要深入了解將較大的 F # 功能，請參閱[F # 導覽](tour.md)。