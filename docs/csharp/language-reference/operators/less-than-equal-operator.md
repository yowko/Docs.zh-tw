---
title: <= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: cb11a746d36cc22ab2341e28a7efba3c0b3510eb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257001"
---
# <a name="-operator-c-reference"></a>\<= 運算子 (C# 參考)

若「小於或等於」關係運算子的第一個運算元小於或等於其第二個運算元，其 `<=` 會傳回 `true`，否則為 `false`。 所有數值及列舉類型都支援 `<=` 運算子。 相同[列舉](../keywords/enum.md)類型的運算元會比較基礎整數型別的對應值。

> [!NOTE]
> 對於關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若所有運算元皆為數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) 時，運算的結果就會是 `false`。 這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值。 如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。

下列範例示範 `<=` 運算子的用法：

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `<=` 運算子。 若類型多載「少於或等於」運算子 `<=`，其也必須多載[「大於或等於」運算子](greater-than-equal-operator.md) `>=`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [< 運算子](less-than-operator.md)
- [== 運算子](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
