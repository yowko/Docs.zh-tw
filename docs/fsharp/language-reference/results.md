---
title: '結果 （F #）'
description: "了解如何使用 F # '造成' 型別，可協助您撰寫容錯的程式碼。"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 35fd1d3b1590291e18aa28460cf5939606c21d3a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="results"></a><span data-ttu-id="4dd3f-103">結果</span><span class="sxs-lookup"><span data-stu-id="4dd3f-103">Results</span></span>

<span data-ttu-id="4dd3f-104">從 F # 4.1 開始，沒有`Result<'T,'TFailure>`類型可讓您撰寫容錯可撰寫其程式碼。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="4dd3f-105">語法</span><span class="sxs-lookup"><span data-stu-id="4dd3f-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="4dd3f-106">備註</span><span class="sxs-lookup"><span data-stu-id="4dd3f-106">Remarks</span></span>

<span data-ttu-id="4dd3f-107">請注意，結果型別是[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)，這是 F # 4.1 中導入的另一項功能。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="4dd3f-108">結構相等語意適用於此處。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="4dd3f-109">`Result`類型通常用於 monadic 錯誤處理，這通常稱為[鐵路導向程式設計](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html)F # 社群內。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="4dd3f-110">下列簡單範例會示範這種方法。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-110">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="4dd3f-111">如您所見，是很容易就能鏈結在一起各種驗證函式如果您強制全部傳回`Result`。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="4dd3f-112">此讓您分割成小片段，也就是當您需要的組合就像這樣的功能。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="4dd3f-113">這也具有附加價值*強制*使用[模式比對](pattern-matching.md)驗證的結尾，進而強制執行程式正確性較高。</span><span class="sxs-lookup"><span data-stu-id="4dd3f-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd3f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dd3f-114">See Also</span></span>

[<span data-ttu-id="4dd3f-115">差別聯集</span><span class="sxs-lookup"><span data-stu-id="4dd3f-115">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="4dd3f-116">模式比對</span><span class="sxs-lookup"><span data-stu-id="4dd3f-116">Pattern Matching</span></span>](pattern-matching.md)
