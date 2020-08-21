---
title: 結果
description: '瞭解如何使用 F # 的「結果」類型，協助您撰寫容錯程式碼。'
ms.date: 08/13/2020
ms.openlocfilehash: d69e6ddc37bcf5cb5fc28644d59a11a822b83faa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656914"
---
# <a name="results"></a>結果

此 `Result<'T,'TFailure>` 類型可讓您撰寫可組合的容錯程式碼。

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

請參閱的 [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) 內建組合器模組 `Result` 。 類型。

請注意，結果型別是 [結構](discriminated-unions.md#struct-discriminated-unions)差異聯集。 結構相等語義適用于此處。

此 `Result` 類型通常用於 monadic 錯誤處理，在 F # 社區中通常稱為 [鐵路導向程式設計](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) 。  下列簡單的範例示範這種方法。

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

如您所見，如果您強制將各種驗證函式全部傳回，就很容易將它們連結在一起 `Result` 。  這可讓您將像這樣的功能分解成可組合的小部分，就像您需要的一樣。  這也具有在往返驗證的結尾 *強制* 使用 [模式](pattern-matching.md) 比對的額外值，進而強制執行較高程度的程式正確性。

## <a name="see-also"></a>請參閱

- [已區分的聯集](discriminated-unions.md)
- [模式比對](pattern-matching.md)
