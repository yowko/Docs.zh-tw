---
title: 結果
description: 了解如何使用F#'Result' 類型，可協助您撰寫錯誤容錯的程式碼。
ms.date: 04/24/2017
ms.openlocfilehash: 8b419412b406018a21f2c23103c8193fec8766f2
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612708"
---
# <a name="results"></a><span data-ttu-id="8fb5d-103">結果</span><span class="sxs-lookup"><span data-stu-id="8fb5d-103">Results</span></span>

<span data-ttu-id="8fb5d-104">開頭為F#4.1 沒有`Result<'T,'TFailure>`您可以用來撰寫可以組成-容錯的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="8fb5d-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fb5d-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="8fb5d-106">備註</span><span class="sxs-lookup"><span data-stu-id="8fb5d-106">Remarks</span></span>

<span data-ttu-id="8fb5d-107">請注意，結果型別是[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)，這另一項功能中導入F#4.1。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="8fb5d-108">結構相等語意適用於此處。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="8fb5d-109">`Result`型別通常用於單邊錯誤處理，這通常稱為[鐵路導向程式設計](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html)在F#社群。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="8fb5d-110">下列的簡單範例會示範這種方法。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-110">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="8fb5d-111">如您所見，它是很容易就能鏈結各種驗證函式，如果您強制它們全部傳回`Result`。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="8fb5d-112">這樣，您會分解成小片段，也就是當您需要的組合這類功能。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="8fb5d-113">這也具有附加價值*強制*善用[模式比對](pattern-matching.md)結尾的一輪的驗證，進而強制執行較高的程式正確性。</span><span class="sxs-lookup"><span data-stu-id="8fb5d-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fb5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb5d-114">See also</span></span>

- [<span data-ttu-id="8fb5d-115">差別聯集</span><span class="sxs-lookup"><span data-stu-id="8fb5d-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="8fb5d-116">模式比對</span><span class="sxs-lookup"><span data-stu-id="8fb5d-116">Pattern Matching</span></span>](pattern-matching.md)