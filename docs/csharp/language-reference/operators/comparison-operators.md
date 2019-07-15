---
title: 比較運算子 - C#參考
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
ms.openlocfilehash: d3e9bf1356218f223f959b423dfc048972b075d3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661511"
---
# <a name="comparison-operators-c-reference"></a>比較運算子 (C#參考)

[`<` (小於)](#less-than-operator-)、[`>` (大於)](#greater-than-operator-)、[`<=` (小於或等於)](#less-than-or-equal-operator-)，以及 [`>=` (大於或等於)](#greater-than-or-equal-operator-) 比較 (也稱為關聯式) 運算子，會比較其運算元。 這些運算子可支援所有[整數](../builtin-types/integral-numeric-types.md)和[浮點](../builtin-types/floating-point-numeric-types.md)數字型別。

> [!NOTE]
> 針對 `==`、`<`、`>`、`<=` 和 `>=` 運算子，如果任何運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，則作業的結果是 `false`。 這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。 如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。

列舉類型也支援比較運算子。 相同[列舉](../keywords/enum.md)類型的運算元會比較基礎整數型別的對應值。

[`==` 和 `!=` 運算子](equality-operators.md) 會檢查其運算元是否相等。

## <a name="less-than-operator-"></a>小於運算子 \<

`<` 運算子會傳回 `true` (如果其左邊運算元小於第右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>大於運算子 >

`>` 運算子會傳回 `true` (如果其左邊運算元大於第右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>小於或等於運算子 \<=

`<=` 運算子會傳回 `true` (如果其左邊運算元小於或等於右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>大於或等於運算子 >=

`>=` 運算子會傳回 `true` (如果其左邊運算元大於或等於右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義類型可以[多載](operator-overloading.md) `<`、`>`、`<=` 及 `>=` 運算子。

如果類型多載 `<` 或 `>` 運算子之一，則也必須多載 `<` 和 `>`。 如果類型多載 `<=` 或 `>=` 運算子之一，則也必須多載 `<=` 和 `>=`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [等號比較運算子](equality-operators.md)
