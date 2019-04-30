---
title: 值的選項
description: 深入了解F#值的選項類型，這是結構類型版本的選項。
ms.date: 02/06/2019
ms.openlocfilehash: e1036c83189c853b3704d94ca245e4818acc98c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982575"
---
# <a name="value-options"></a>值的選項

中的值選項類型F#在下列兩種情況下保存時，會使用：

1. 案例是適用於[ F#  選項](options.md)。
2. 使用結構可提供效能優勢，在您的案例。

並非所有效能敏感的狀況下會 「 都解決 」 使用結構。 您必須考慮複製時使用它們，而不參考類型的額外成本。 不過，大型F#程式通常具現化的許多選擇性類型流經忙碌的路徑，並在這種情況下，結構通常可以產生更好的整體效能，程式的存留期。

## <a name="definition"></a>定義

值選項指[結構差別聯集](discriminated-unions.md#struct-discriminated-unions)類似參考選項類型。 如此一來您可以想像它的定義：

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
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

- [選項](options.md)
