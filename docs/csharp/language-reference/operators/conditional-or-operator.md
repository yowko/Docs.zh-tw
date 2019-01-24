---
title: '|| 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415425"
---
# <a name="-operator-c-reference"></a>|| 運算子 (C# 參考)

條件式邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其 [bool](../keywords/bool.md) 運算元的邏輯 OR。 若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。 否則，結果為 `false`。 若第一個運算元的值為 `true`，就不會求第二個運算元的值，而運算結果會是 `true`。 下列範例示範了該行為：

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

[邏輯 OR 運算子](or-operator.md) `|` 也會計算其 `bool` 運算元的邏輯 OR，但一律會求兩個運算元的值。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別無法多載條件式邏輯 OR 運算子。 不過，若使用者定義型別以某種方式多載[邏輯 OR](or-operator.md) 及 [true 和 false 運算子](../keywords/true-false-operators.md)，就可以針對該類型的運算元評估 `||` 運算。 如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件式邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [&& 運算子](conditional-and-operator.md)
- [\! 運算子](logical-negation-operator.md)
- [| 運算子](or-operator.md)
