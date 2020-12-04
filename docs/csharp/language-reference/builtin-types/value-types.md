---
description: 深入瞭解 C 中的實值型別、類型和內建的型別#
title: '實值型別-c # 參考'
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599391"
---
# <a name="value-types-c-reference"></a>數值型別 (c # 參考) 

實 *數值型別* 和 [參考型別](../keywords/reference-types.md)是 c # 型別的兩個主要類別。 實值型別的變數包含型別的實例。 這與參考型別的變數不同，後者包含型別實例的參考。 根據預設，在 [指派](../operators/assignment-operator.md)時，將引數傳遞至方法，並傳回方法結果，會複製變數值。 在實數值型別變數的情況下，會複製對應的型別實例。 下列範例示範了該行為：

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

如先前的範例所示，實數值型別變數的作業只會影響儲存在變數中的實值型別實例。

如果實值型別包含參考型別的資料成員，則在複製值型別實例時，只會複製參考型別的實例參考。 複製和原始實數值型別實例都可以存取相同的參考型別實例。 下列範例示範了該行為：

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> 若要讓您的程式碼較不容易出錯且更健全，請定義和使用不可變的實數值型別。 本文僅針對示範目的使用可變的實數值型別。

## <a name="kinds-of-value-types-and-type-constraints"></a>實數值型別和類型條件約束的種類

實值型別可以是下列兩種類型之一：

- 封裝資料和相關功能的[結構類型](struct.md)
- [列舉型](enum.md)別，它是由一組命名常數所定義，代表一個選擇或一個選擇組合。

[可為 null](nullable-value-types.md)的實值型別 `T?` 代表其基礎實值型別的所有值 `T` ，以及一個額外的[null](../keywords/null.md)值。 您無法指派 `null` 給實值型別的變數，除非它是可為 null 的實值型別。

您可以使用[ `struct` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)來指定型別參數為不可為 null 的實值型別。 結構和列舉類型都符合 `struct` 條件約束。 從 c # 7.3 開始，您可以 `System.Enum` 在稱為 [列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints) 的基類條件約束 (中使用，) 指定型別參數為列舉型別。

## <a name="built-in-value-types"></a>內建實數值型別

C # 提供下列內建實數值型別，也稱為 *簡單類型*：

- [整數數值類型](integral-numeric-types.md)
- [浮點數值類型](floating-point-numeric-types.md)
- 表示布林值的[bool](bool.md)
- 代表 Unicode UTF-16 字元的[char](char.md)

所有簡單類型都是結構類型，而且與其他結構類型不同，因為它們允許某些額外的作業：

- 您可以使用常值提供簡單類型的值。 例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。

- 您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。 不可能有其他結構類型的常數。

- 常數運算式（其運算元都是簡單類型的常數）會在編譯時期評估。

從 c # 7.0 開始，c # 支援 [值元組](value-tuples.md)。 值元組是實數值型別，但不是簡單類型。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [值類型](~/_csharplang/spec/types.md#value-types)
- [簡單型別](~/_csharplang/spec/types.md#simple-types)
- [變數](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [參考型別](../keywords/reference-types.md)
