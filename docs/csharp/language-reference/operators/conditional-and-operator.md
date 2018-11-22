---
title: '&amp;&amp; 運算子 (C# 參考)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529231"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; 運算子 (C# 參考)

條件式邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其 [bool](../keywords/bool.md) 運算元的邏輯 AND。 若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。 否則，結果為 `false`。 若第一個運算元的值為 `false`，就不會求第二個運算元的值，而運算結果會是 `false`。 下列範例示範了該行為：

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

[邏輯 AND 運算子](and-operator.md) `&`也會計算其 `bool` 運算元的邏輯 AND，但一律會求兩個運算元的值。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別無法多載條件式邏輯 AND 運算子。 不過，若使用者定義型別以某種方式多載[邏輯 AND](and-operator.md)、[true](../keywords/true-operator.md) 和 [false](../keywords/false-operator.md) 運算子，就可以為該類型運算元求 `&&` 運算的值。 如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件式邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [|| 運算子](conditional-or-operator.md)
- [\! 運算子](logical-negation-operator.md)
- [& 運算子](and-operator.md)
