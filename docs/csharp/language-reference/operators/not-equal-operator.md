---
title: '!= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610173"
---
# <a name="-operator-c-reference"></a>!= 運算子 (C# 參考)

不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。 對於[內建類型](../keywords/built-in-types-table.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。 如需詳細資訊，請參閱 [== 運算子](equality-comparison-operator.md)一文。

下列範例示範 `!=` 運算子的用法：

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `!=` 運算子。 若類型多載不等比較運算子 `!=`，其必須也多載[等號比較運算子](equality-comparison-operator.md) `==`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [相等比較](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
