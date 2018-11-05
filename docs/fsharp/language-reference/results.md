---
title: 結果 （F#）
description: 了解如何使用 F# '造成' 型別，可協助您撰寫錯誤容錯的程式碼。
ms.date: 04/24/2017
ms.openlocfilehash: a7ce2e1f6b8c6a32d99a2feaf9547c4b67b152b8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44213036"
---
# <a name="results"></a>結果

從 F# 4.1 開始，沒有`Result<'T,'TFailure>`類型可用來撰寫可以組成-容錯的程式碼。

## <a name="syntax"></a>語法

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>備註

請注意，結果型別是[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)，這是另一個 F# 4.1 中所引進的功能。  結構相等語意適用於此處。

`Result`型別通常用於單邊錯誤處理，這通常稱為[鐵路導向程式設計](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html)F# 社群中。  下列的簡單範例會示範這種方法。

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

如您所見，它是很容易就能鏈結各種驗證函式，如果您強制它們全部傳回`Result`。  這樣，您會分解成小片段，也就是當您需要的組合這類功能。  這也具有附加價值*強制*善用[模式比對](pattern-matching.md)結尾的一輪的驗證，進而強制執行較高的程式正確性。

## <a name="see-also"></a>另請參閱

- [差別聯集](discriminated-unions.md)
- [模式比對](pattern-matching.md)
