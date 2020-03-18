---
title: 布林型 - C# 參考
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846441"
---
# <a name="bool-c-reference"></a>布林（C# 參考）

類型`bool`關鍵字是 .NET<xref:System.Boolean?displayProperty=nameWithType>結構類型的別名，表示布林值，可以是`true`或`false`。

要使用`bool`類型的值執行邏輯操作，請使用[布林邏輯](../operators/boolean-logical-operators.md)運算子。 類型`bool`是[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算子的結果類型。 運算式`bool`可以是[if](../keywords/if-else.md)中的控制條件運算式，在 中[執行](../keywords/do.md)，[對於](../keywords/while.md)[語句和](../keywords/for.md)條件[運算子`?:`](../operators/conditional-operator.md)。

`bool`類型的預設值為`false`。

## <a name="literals"></a>常值

可以使用`true`和`false`文本來初始化`bool`變數或傳遞`bool`值：

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>三值布林邏輯

如果需要支援三值`bool?`邏輯，請使用可 null 類型，例如，當您使用支援三值布林類型的資料庫時。 針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

有關空數值型別的詳細資訊，請參閱[空數值型別](nullable-value-types.md)。

## <a name="conversions"></a>轉換

C# 僅提供兩個涉及`bool`該類型的轉換。 這些是對相應空`bool?`類型的隱式轉換，是從`bool?`該類型的顯式轉換。 但是，.NET 提供了可用於轉換為`bool`類型或從類型轉換的其他方法。 有關詳細資訊，請參閱<xref:System.Boolean?displayProperty=nameWithType>API 參考頁的"[轉換到布林值"和"從布林值轉換"](/dotnet/api/system.boolean#converting-to-and-from-boolean-values)部分。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[Bool 類型](~/_csharplang/spec/types.md#the-bool-type)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [實值型別](value-types.md)
- [true 和 false 運算子](../operators/true-false-operators.md)
