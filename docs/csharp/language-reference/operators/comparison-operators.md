---
title: 比較運算子 - C# 參考
description: 深入了解可供您檢查數值順序的 C# 比較運算子。
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 6d3751ff1ee2c6ee2f058eeda4ffd5db188a988e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633766"
---
# <a name="comparison-operators-c-reference"></a>比較運算子 (C#參考)

[`<` (小於)](#less-than-operator-)、[`>` (大於)](#greater-than-operator-)、[`<=` (小於或等於)](#less-than-or-equal-operator-)，以及 [`>=` (大於或等於)](#greater-than-or-equal-operator-) 比較 (也稱為關聯式) 運算子，會比較其運算元。 這些運算子可支援所有[整數](../keywords/integral-types-table.md)和[浮點](../keywords/floating-point-types-table.md)數字型別。

> [!NOTE]
> 針對 `==`、`<`、`>`、`<=` 和 `>=` 運算子，如果任何運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，則作業的結果是 `false`。 這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。 如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。

列舉類型也支援比較運算子。 相同[列舉](../keywords/enum.md)類型的運算元會比較基礎整數型別的對應值。

[`==` 和 `!=` 運算子](equality-operators.md) 會檢查其運算元是否相等。

## <a name="less-than-operator-"></a>小於運算子 \<

`<` 運算子會傳回 `true` (如果其第一個運算元小於第二個運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="greater-than-operator-"></a>大於運算子 >

`>` 運算子會傳回 `true` (如果其第一個運算元大於第二個運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>小於或等於運算子 \<=

`<=` 運算子會傳回 `true` (如果其第一個運算元小於或等於第二個運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>大於或等於運算子 >=

`>=` 運算子會傳回 `true` (如果其第一個運算元大於或等於第二個運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義類型可以[多載](../keywords/operator.md) `<`、`>`、`<=` 及 `>=` 運算子。

如果類型多載 `<` 或 `>` 運算子之一，則也必須多載 `<` 和 `>`。 如果類型多載 `<=` 或 `>=` 運算子之一，則也必須多載 `<=` 和 `>=`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [等號比較運算子](equality-operators.md)
