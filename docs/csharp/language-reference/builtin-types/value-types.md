---
title: 數值型別 - C# 引用
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399578"
---
# <a name="value-types-c-reference"></a>數值型別（C# 引用）

*數值型別*和[參考型別](../keywords/reference-types.md)是 C# 類型的兩個主要類別。 數值型別的變數包含類型的實例。 這與參考型別的變數不同，該變數包含對類型實例的引用。 預設情況下，在[賦值](../operators/assignment-operator.md)時，將參數傳遞給方法，並返回方法結果，將複製變數值。 對於數值型別變數，將複製相應的類型實例。 下列範例示範了該行為：

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

如前面的示例所示，數值型別變數上的操作僅影響存儲在變數中的數值型別的實例。

如果數值型別包含參考型別的資料成員，則在複製數值型別實例時，僅複製對參考型別實例的引用。 副本和原始數值型別實例都有權訪問同一參考型別實例。 下列範例示範了該行為：

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> 為了使代碼不易出錯且更健壯，請定義和使用不可變的數值型別。 本文僅出於演示目的使用可變數值型別。

## <a name="kinds-of-value-types"></a>數值型別

數值型別可以是以下兩種類型之一：

- 結構[類型](struct.md)，它封裝資料和相關功能
- [枚舉類型](enum.md)，由一組命名常量定義，表示選擇或選項群組合

[空數值型別](nullable-value-types.md)`T?`表示其基礎數值型別`T`的所有值和附加[空](../keywords/null.md)值。 不能分配給`null`數值型別的變數，除非它是一個空數值型別。

## <a name="built-in-value-types"></a>內置數值型別

C# 提供以下內置數值型別，也稱為*簡單類型*：

- [整數數值類型](integral-numeric-types.md)
- [浮點數值類型](floating-point-numeric-types.md)
- 代表布林值的[布林](bool.md)
- 表示 Unicode UTF-16 字元的[字元](char.md)

所有簡單類型都是結構類型，與其他結構類型不同，因為它們允許某些附加操作：

- 可以使用文本提供簡單類型的值。 例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。

- 您可以使用 [const](../keywords/const.md) 關鍵字來宣告簡單型別的常數。 不可能有其他結構類型的常量。

- 常量運算式（其運算元都是簡單類型的常量）在編譯時計算。

從 C# 7.0 開始，C# 支援[值 tups](../../tuples.md)。 值元組是數值型別，但不是簡單類型。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [實值型別](~/_csharplang/spec/types.md#value-types)
- [簡單型別](~/_csharplang/spec/types.md#simple-types)
- [變數](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [參考型別](../keywords/reference-types.md)
