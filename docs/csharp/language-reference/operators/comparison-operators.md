---
title: 比較運算子 - C#參考
description: 深入了解可供您檢查數值順序的 C# 比較運算子。
ms.date: 05/11/2020
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
ms.openlocfilehash: d57f96b9c80bdc5f40169180b40326ffed91cf10
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555365"
---
# <a name="comparison-operators-c-reference"></a>比較運算子 (C#參考)

[ `<` (小於) ](#less-than-operator-)、 [ `>` (大於) ](#greater-than-operator-)、 [ `<=` (小於或等於) ](#less-than-or-equal-operator-)，而且[ `>=` (大於或等於) ](#greater-than-or-equal-operator-)比較（也稱為關聯式），運算子會比較其運算元。 所有[整數](../builtin-types/integral-numeric-types.md)和[浮點](../builtin-types/floating-point-numeric-types.md)數數值型別都支援這些運算子。

> [!NOTE]
> 針對 `==`、`<`、`>`、`<=` 和 `>=` 運算子，如果任何運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，則作業的結果是 `false`。 這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。 如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。

[Char](../builtin-types/char.md)類型也支援比較運算子。 在運算元的案例中 `char` ，會比較對應的字元碼。

列舉類型也支援比較運算子。 相同[列舉](../builtin-types/enum.md)類型的運算元會比較基礎整數型別的對應值。

[ `==` 和 `!=` 運算子](equality-operators.md)會檢查其運算元是否相等。

## <a name="less-than-operator-"></a>小於運算子 \<

`<` 運算子會傳回 `true` (如果其左邊運算元小於第右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>大於運算子 >

`>` 運算子會傳回 `true` (如果其左邊運算元大於第右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>小於或等於運算子 \<=

`<=` 運算子會傳回 `true` (如果其左邊運算元小於或等於右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>大於或等於運算子 >=

`>=` 運算子會傳回 `true` (如果其左邊運算元大於或等於右邊運算元)，否則會傳回 `false`：

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型[別可以多](operator-overloading.md)載 `<` 、 `>` 、 `<=` 和 `>=` 運算子。

如果類型多載 `<` 或 `>` 運算子之一，則也必須多載 `<` 和 `>`。 如果類型多載 `<=` 或 `>=` 運算子之一，則也必須多載 `<=` 和 `>=`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [等號比較運算子](equality-operators.md)
