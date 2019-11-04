---
title: 結果
description: 瞭解如何使用F# 「結果」類型來協助您撰寫錯誤容錯程式碼。
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424843"
---
# <a name="results"></a><span data-ttu-id="631ef-103">結果</span><span class="sxs-lookup"><span data-stu-id="631ef-103">Results</span></span>

<span data-ttu-id="631ef-104">從F# 4.1 開始，有一個 `Result<'T,'TFailure>` 型別，您可以用它來撰寫可撰寫的容錯程式碼。</span><span class="sxs-lookup"><span data-stu-id="631ef-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="631ef-105">語法</span><span class="sxs-lookup"><span data-stu-id="631ef-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="631ef-106">備註</span><span class="sxs-lookup"><span data-stu-id="631ef-106">Remarks</span></span>

<span data-ttu-id="631ef-107">請注意，結果類型是[結構區分](discriminated-unions.md#struct-discriminated-unions)等位，這是4.1 中F#引進的另一項功能。</span><span class="sxs-lookup"><span data-stu-id="631ef-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="631ef-108">結構相等的語義適用于這裡。</span><span class="sxs-lookup"><span data-stu-id="631ef-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="631ef-109">`Result` 類型通常用於 monadic 錯誤處理，這通常稱為「在F#社區中以鐵路為[導向的程式設計](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html)」。</span><span class="sxs-lookup"><span data-stu-id="631ef-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="631ef-110">下列簡單範例示範這種方法。</span><span class="sxs-lookup"><span data-stu-id="631ef-110">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="631ef-111">如您所見，如果您強制所有的驗證函式都要傳回 `Result`，這會是很容易的。</span><span class="sxs-lookup"><span data-stu-id="631ef-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="631ef-112">這可讓您將這類功能分解成一小部分，如同您所需的可組合。</span><span class="sxs-lookup"><span data-stu-id="631ef-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="631ef-113">這也有額外的值，可在驗證回合結束時*強制*使用[模式](pattern-matching.md)比對，而這會強制執行較高程度的程式正確性。</span><span class="sxs-lookup"><span data-stu-id="631ef-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="631ef-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="631ef-114">See also</span></span>

- [<span data-ttu-id="631ef-115">差別聯集</span><span class="sxs-lookup"><span data-stu-id="631ef-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="631ef-116">模式比對</span><span class="sxs-lookup"><span data-stu-id="631ef-116">Pattern Matching</span></span>](pattern-matching.md)
