---
description: 瞭解 C 中的內建布林類型#
title: 'bool 型別-c # 參考'
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
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126459"
---
# <a name="bool-c-reference"></a>bool (c # 參考) 

`bool`Type 關鍵字是 <xref:System.Boolean?displayProperty=nameWithType> 代表布林值（可以是或）之 .net 結構類型的別名 `true` `false` 。

若要執行具有類型值的邏輯作業 `bool` ，請使用 [布林值邏輯](../operators/boolean-logical-operators.md) 運算子。 此 `bool` 類型是比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子的結果型別。 `bool`運算式可以是[if](../keywords/if-else.md)、 [do](../keywords/do.md)、 [while](../keywords/while.md)和[for](../keywords/for.md)語句和[條件運算子 `?:` ](../operators/conditional-operator.md)中的控制條件運算式。

此類型的預設值 `bool` 為 `false` 。

## <a name="literals"></a>常值

您可以使用 `true` 和 `false` 常值來初始化 `bool` 變數或傳遞 `bool` 值：

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>三值布林值邏輯

`bool?`如果您需要支援三值的邏輯（例如，當您使用支援三值布林類型的資料庫時），請使用可為 null 的型別。 針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。 如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

如需可為 null 實值型別的詳細資訊，請參閱[可為 null 的實數值型別](nullable-value-types.md)

## <a name="conversions"></a>轉換

C # 只會提供兩個牽涉到類型的轉換 `bool` 。 這些是對應至可為 null 之型別的隱含轉換 `bool?` ，以及來自型別的明確轉換 `bool?` 。 不過，.NET 提供其他方法，可讓您用來在類型之間進行轉換 `bool` 。 如需詳細資訊，請參閱 API 參考頁面的 [轉換為和來源布林值](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) 一節 <xref:System.Boolean?displayProperty=nameWithType> 。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[bool 類型](~/_csharplang/spec/types.md#the-bool-type)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [值類型](value-types.md)
- [true 和 false 運算子](../operators/true-false-operators.md)
