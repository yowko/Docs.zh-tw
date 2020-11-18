---
title: Nameof
description: 瞭解 nameof 運算子，這是可讓您在原始程式碼中產生任何符號名稱的中繼資料功能。
ms.date: 11/12/2020
ms.openlocfilehash: 9947d7172d1b73db5c181297ec8b1131382e1f5e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688605"
---
# <a name="nameof"></a><span data-ttu-id="6937e-103">Nameof</span><span class="sxs-lookup"><span data-stu-id="6937e-103">Nameof</span></span>

<span data-ttu-id="6937e-104">運算式會產生比對來源中 `nameof` 幾乎任何 F # 結構之來源名稱的字串常數。</span><span class="sxs-lookup"><span data-stu-id="6937e-104">The `nameof` expression produces a string constant that matches the name in source for nearly any F# construct in source.</span></span>

## <a name="syntax"></a><span data-ttu-id="6937e-105">語法</span><span class="sxs-lookup"><span data-stu-id="6937e-105">Syntax</span></span>

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a><span data-ttu-id="6937e-106">備註</span><span class="sxs-lookup"><span data-stu-id="6937e-106">Remarks</span></span>

<span data-ttu-id="6937e-107">`nameof` 的運作方式是解析傳遞給它的符號，並產生在原始程式碼中宣告的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="6937e-107">`nameof` works by resolving the symbol passed to it and produces the name of that symbol as it is declared in your source code.</span></span> <span data-ttu-id="6937e-108">這在各種情況下都很有用，例如記錄，並可保護您的記錄免于原始程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="6937e-108">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) ($"Value passed in was %d{month}.")

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="6937e-109">最後一行將擲回例外狀況，並 `"month"` 將在錯誤訊息中顯示。</span><span class="sxs-lookup"><span data-stu-id="6937e-109">The last line will throw an exception and `"month"` will be shown in the error message.</span></span>

<span data-ttu-id="6937e-110">您可以採用幾乎每個 F # 結構的名稱：</span><span class="sxs-lookup"><span data-stu-id="6937e-110">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

<span data-ttu-id="6937e-111">`nameof` 不是第一個類別的函式，因此無法使用。</span><span class="sxs-lookup"><span data-stu-id="6937e-111">`nameof` is not a first-class function and cannot be used as such.</span></span> <span data-ttu-id="6937e-112">這表示它無法部分套用，而且無法透過 F # 管線運算子將值輸送至其中。</span><span class="sxs-lookup"><span data-stu-id="6937e-112">That means it cannot be partially applied and values cannot be piped into it via F# pipeline operators.</span></span>

## <a name="nameof-on-operators"></a><span data-ttu-id="6937e-113">Nameof on 運算子</span><span class="sxs-lookup"><span data-stu-id="6937e-113">Nameof on operators</span></span>

<span data-ttu-id="6937e-114">F # 中的運算子可以用兩種方式來使用，例如運算子文字本身或代表已編譯表單的符號。</span><span class="sxs-lookup"><span data-stu-id="6937e-114">Operators in F# can be used in two ways, as an operator text itself, or a symbol representing the compiled form.</span></span> <span data-ttu-id="6937e-115">`nameof` 在運算子上，將會產生在來源中宣告之運算子的名稱。</span><span class="sxs-lookup"><span data-stu-id="6937e-115">`nameof` on an operator will produce the name of the operator as it is declared in source.</span></span> <span data-ttu-id="6937e-116">若要取得編譯的名稱，請在來源中使用編譯的名稱：</span><span class="sxs-lookup"><span data-stu-id="6937e-116">To get the compiled name, use the compiled name in source:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a><span data-ttu-id="6937e-117">泛型上的 Nameof</span><span class="sxs-lookup"><span data-stu-id="6937e-117">Nameof on generics</span></span>

<span data-ttu-id="6937e-118">您也可以採用泛型型別參數的名稱，但語法不同：</span><span class="sxs-lookup"><span data-stu-id="6937e-118">You can also take a name of a generic type parameter, but the syntax is different:</span></span>

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

<span data-ttu-id="6937e-119">`nameof<'TGeneric>` 將採用來源中所定義的符號名稱，而不是取代在呼叫位置的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6937e-119">`nameof<'TGeneric>` will take the name of the symbol as defined in source, not the name of the type substituted at a call site.</span></span>

<span data-ttu-id="6937e-120">語法不同的原因是要與其他 F # 內建運算子（例如和） `typeof<>` 對齊 `typedefof<>` 。</span><span class="sxs-lookup"><span data-stu-id="6937e-120">The reason why the syntax is different is to align with other F# intrinsic operators like `typeof<>` and `typedefof<>`.</span></span> <span data-ttu-id="6937e-121">這使得 F # 與對泛型型別和來源中任何其他動作的運算子相對應。</span><span class="sxs-lookup"><span data-stu-id="6937e-121">This makes F# consistent with respect to operators that act on generic types and anything else in source.</span></span>

## <a name="nameof-in-pattern-matching"></a><span data-ttu-id="6937e-122">模式比對中的 Nameof</span><span class="sxs-lookup"><span data-stu-id="6937e-122">Nameof in pattern matching</span></span>

<span data-ttu-id="6937e-123">此[ `nameof` 模式](pattern-matching.md#nameof-pattern)可讓您 `nameof` 在模式比對運算式中使用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6937e-123">The [`nameof` pattern](pattern-matching.md#nameof-pattern) lets you use `nameof` in a pattern match expression like so:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
