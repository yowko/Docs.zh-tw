---
title: 'bool 類型-c # 參考'
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 4623dc7d6c8c6c437c78aee45f0eeee8a92e3200
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854876"
---
# <a name="bool-c-reference"></a>bool (c # 參考) 

`bool`類型關鍵字是 .net 結構類型的別名， <xref:System.Boolean?displayProperty=nameWithType> 代表布林值，可以是 `true` 或 `false` 。

若要執行具有類型值的邏輯運算 `bool` ，請使用[布林邏輯](../operators/boolean-logical-operators.md)運算子。 `bool`類型是比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子的結果類型。 `bool`運算式可以是[if](../keywords/if-else.md)、 [do](../keywords/do.md)、 [while](../keywords/while.md)和[for](../keywords/for.md)語句中的控制條件運算式，以及[條件運算子 `?:` ](../operators/conditional-operator.md)中的。

此類型的預設值 `bool` 為 `false` 。

## <a name="literals"></a>常值

您可以使用 `true` 和 `false` 常值來初始化 `bool` 變數或傳遞 `bool` 值：

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>三值布林邏輯

`bool?`如果您需要支援三值邏輯（例如，當您使用支援三值布林值類型的資料庫時），請使用可為 null 的類型。 針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

如需可為 null 的實數值型別的詳細資訊，請參閱[nullable 實數值型別](nullable-value-types.md)。

## <a name="conversions"></a>轉換

C # 只提供兩個牽涉到 `bool` 類型的轉換。 這些是對應的可為 null 型別 `bool?` 和從型別明確轉換的隱含轉換 `bool?` 。 不過，.NET 提供了其他方法，可讓您用來轉換成或從 `bool` 類型轉換。 如需詳細資訊，請參閱 API 參考頁面的[轉換成和引數的布林值](/dotnet/api/system.boolean#converting-to-and-from-boolean-values)一節 <xref:System.Boolean?displayProperty=nameWithType> 。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[bool 類型](~/_csharplang/spec/types.md#the-bool-type)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [值類型](value-types.md)
- [true 和 false 運算子](../operators/true-false-operators.md)
