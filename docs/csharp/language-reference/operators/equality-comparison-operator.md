---
title: == 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655955"
---
# <a name="-operator-c-reference"></a>== 運算子 (C# 參考)

等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。

## <a name="value-types-equality"></a>實值型別相等

若他們的值相等時，[內建實值型別](../keywords/value-types-table.md)的運算元就會相等：

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> 對於關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若所有運算元皆為數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) 時，運算的結果就會是 `false`。 這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值。 如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。

若基礎整數型別的對應值相等時，相同[列舉](../keywords/enum.md)類型的兩個運算元就會相等。

根據預設，`==` 運算子不會定義為使用者定義 [struct](../keywords/struct.md) 類型。 使用者定義型別可以[多載](#operator-overloadability) `==` 運算子。

從 C# 7.3 說起，`==` 及 [`!=`](not-equal-operator.md) 運算子是由 C# [tuples](../../tuples.md) 所支援。 如需詳細資訊，請參閱 [C# Tuple 類型](../../tuples.md)一文中的[相等與 Tuple](../../tuples.md#equality-and-tuples)一節。

## <a name="string-equality"></a>字串相等

當兩個 [string](../keywords/string.md) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

其為區分大小寫的序數比較。 如需如何比較字串的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。

## <a name="reference-types-equality"></a>參考型別相等

當兩個不是 `string` 參考型別的運算元參考相同的物件時，兩者就會相等：

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

此範例顯示出使用者定義參考型別會支援 `==` 運算子。 不過，使用者定義參考型別可以多載 `==` 運算子。 若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `==` 運算子。 若類型多載等號比較運算子 `==`，其必須也多載[不等比較運算子](not-equal-operator.md) `!=`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [相等比較](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
