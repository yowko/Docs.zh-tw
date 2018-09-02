---
title: '值的選項 （F #）'
description: '深入了解 F # 值選項類型，也就是結構類型版本的選項。'
ms.date: 06/16/2018
ms.openlocfilehash: 4c255cbbcfd9cb480230de09cd370a401c87343a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398024"
---
# <a name="value-options"></a>值的選項

在下列兩種情況下保存時，會使用 F # 中的值選項類型：

1. 案例是適用於[F # 選項](options.md)。
2. 使用結構可提供效能優勢，在您的案例。

並非所有效能敏感的狀況下會 「 都解決 」 使用結構。 您必須考慮複製時使用它們，而不參考類型的額外成本。 不過，大型的 F # 程式通常具現化許多選擇性類型流經忙碌的路徑，因為結構有時可以產生更好的整體效能程式存留期。

## <a name="definition"></a>定義

值選項指[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)類似參考選項類型：

```fsharp
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpValueOption`1")>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone: 'T voption
    | ValueSome: 'T -> 'T voption

    member Value : 'T

and 'T voption = ValueOption<'T>
```

結構化相等和比較符合值 選項。 主要差異在於編譯的名稱、 型別名稱和大小寫名稱所有指出它是實值型別。

## <a name="using-value-options"></a>使用值的選項

就像使用值選項[選項](options.md)。 `ValueSome` 用來表示值已存在，及`ValueNone`值不存在時，會使用：

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

如同[選項](options.md)，傳回的函式的命名慣例`ValueOption`會加上前置詞與`try`。

## <a name="value-option-properties-and-methods"></a>值選項屬性和方法

此時沒有一個屬性的值選項： `Value`。 <xref:System.InvalidOperationException>沒有值是否存在叫用這個屬性時引發。

## <a name="value-option-functions"></a>值選項函式

目前沒有一個模組繫結函式的值選項`defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

如同`defaultArg`函式，`defaultValueArg`傳回指定的 [值] 選項的基礎值，如果存在的話，否則會傳回指定的預設值。

在此階段中，沒有其他模組繫結函數的值選項。

## <a name="see-also"></a>另請參閱

[選項](options.md)