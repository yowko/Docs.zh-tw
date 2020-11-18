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
# <a name="nameof"></a>Nameof

運算式會產生比對來源中 `nameof` 幾乎任何 F # 結構之來源名稱的字串常數。

## <a name="syntax"></a>語法

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a>備註

`nameof` 的運作方式是解析傳遞給它的符號，並產生在原始程式碼中宣告的符號名稱。 這在各種情況下都很有用，例如記錄，並可保護您的記錄免于原始程式碼中的變更。

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

最後一行將擲回例外狀況，並 `"month"` 將在錯誤訊息中顯示。

您可以採用幾乎每個 F # 結構的名稱：

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

`nameof` 不是第一個類別的函式，因此無法使用。 這表示它無法部分套用，而且無法透過 F # 管線運算子將值輸送至其中。

## <a name="nameof-on-operators"></a>Nameof on 運算子

F # 中的運算子可以用兩種方式來使用，例如運算子文字本身或代表已編譯表單的符號。 `nameof` 在運算子上，將會產生在來源中宣告之運算子的名稱。 若要取得編譯的名稱，請在來源中使用編譯的名稱：

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a>泛型上的 Nameof

您也可以採用泛型型別參數的名稱，但語法不同：

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

`nameof<'TGeneric>` 將採用來源中所定義的符號名稱，而不是取代在呼叫位置的型別名稱。

語法不同的原因是要與其他 F # 內建運算子（例如和） `typeof<>` 對齊 `typedefof<>` 。 這使得 F # 與對泛型型別和來源中任何其他動作的運算子相對應。

## <a name="nameof-in-pattern-matching"></a>模式比對中的 Nameof

此[ `nameof` 模式](pattern-matching.md#nameof-pattern)可讓您 `nameof` 在模式比對運算式中使用，如下所示：

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
