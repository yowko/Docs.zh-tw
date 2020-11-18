---
title: 插入字串
description: '瞭解內插字串，這是一種特殊形式的字串，可讓您直接在其中內嵌 F # 運算式。'
ms.date: 11/12/2020
ms.openlocfilehash: a49d4e743306fd9bdabb1e019ec4e6c77e0e1f5a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688596"
---
# <a name="interpolated-strings"></a>插入字串

內插字串是可讓您在其中內嵌 F # 運算式的 [字串](strings.md) 。 它們在各種案例中很有用，因為字串值可能會根據值或運算式的結果而變更。

## <a name="syntax"></a>語法

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a>備註

插補字串可讓您在字串常值內的「漏洞」內撰寫程式碼。 以下是基本範例：

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

每個 `{}` 大括弧配對之間的內容可以是任何 F # 運算式。

若要對大括弧組進行換用 `{}` ，請撰寫兩個括弧，如下所示：

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a>具類型的插入字串

內插字串也可以有 F # 格式規範，以強制執行型別 safey。

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

在上述範例中，程式碼會錯誤 `age` 地傳遞值 `name` ，其中應該是，反之亦然/反之亦然。 因為插入字串使用格式規範，所以這是編譯錯誤，而不是微妙的執行時間 bug。

[純文字格式](plaintext-formatting.md)中涵蓋的所有格式規範都是在插入字串內有效。

## <a name="verbatim-interpolated-strings"></a>逐字插補字串

F # 支援以三個引號括住的逐字字串，讓您可以內嵌字串常值。

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a>對齊內插字串中的運算式

您可以在插入字串內將運算式靠左對齊或靠右對齊 `|` ，以及指定多少空間。 下列插入字串會將左邊和右邊的運算式分別靠左和向右對齊7個空格。

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a>字串插值和 `FormattableString` 格式

您也可以套用遵守下列規則的格式 <xref:System.FormattableString> ：

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

此外，您也可以透過類型注釋，將插入字串 typechecked 為 <xref:System.FormattableString> ：

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

請注意，類型注釋必須在插入字串運算式本身。 F # 不會以隱含方式將內插字串轉換成 <xref:System.FormattableString> 。

## <a name="see-also"></a>另請參閱

* [字串](strings.md)
