---
title: '實數值型別-c # 參考'
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 0a05b2b0f3f2a8377fdba6144b8aeb12bdee1086
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86172947"
---
# <a name="value-types-c-reference"></a>數值型別 (c # 參考) 

實*數值型別*和[參考型別](../keywords/reference-types.md)是 c # 類型的兩個主要類別。 實值型別的變數包含型別的實例。 這與參考型別的變數不同，後者包含型別之實例的參考。 根據預設，在[指派](../operators/assignment-operator.md)時，將引數傳遞至方法，並傳回方法結果，會複製變數值。 在實數值型別變數的情況下，會複製對應的類型實例。 下列範例示範了該行為：

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

如上述範例所示，實數值型別變數上的作業只會影響實數值型別的實例，並儲存在變數中。

如果實值型別包含引用型別的資料成員，則在複製實值型別實例時，只會複製參考型別的實例參考。 複製和原始實數值型別實例都具有相同的參考類型實例的存取權。 下列範例示範了該行為：

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> 若要讓您的程式碼較不容易出錯且更健全，請定義和使用不可變的實數值型別。 本文只會針對示範用途使用可變的實值型別。

## <a name="kinds-of-value-types"></a>實數值型別的種類

實值型別可以是下列兩種類型的其中一種：

- 封裝資料和相關功能的[結構類型](struct.md)
- [列舉類型](enum.md)，這是由一組已命名的常數所定義，代表選擇或選擇的組合

[可為 null 的實數值型別](nullable-value-types.md) `T?` 代表其基礎數值型別的所有值 `T` ，以及額外的[null](../keywords/null.md)值。 您無法指派 `null` 給實數值型別的變數，除非它是可為 null 的實數值型別。

## <a name="built-in-value-types"></a>內建實數值型別

C # 提供下列內建實數值型別，也稱為*簡單類型*：

- [整數數值類型](integral-numeric-types.md)
- [浮點數值類型](floating-point-numeric-types.md)
- 表示布林值的[bool](bool.md)
- 代表 Unicode UTF-16 字元的[char](char.md)

所有簡單型別都是結構型別，而且與其他結構型別不同，因為它們允許特定的其他作業：

- 您可以使用常值來提供簡單類型的值。 例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。

- 您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。 不可能有其他結構類型的常數。

- 常數運算式（其運算元為簡單類型的所有常數）會在編譯時期進行評估。

從 c # 7.0 開始，c # 支援[值元組](value-tuples.md)。 值元組是實數值型別，但不是簡單類型。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [實值型別](~/_csharplang/spec/types.md#value-types)
- [簡單型別](~/_csharplang/spec/types.md#simple-types)
- [變數](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [參考型別](../keywords/reference-types.md)
