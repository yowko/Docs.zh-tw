---
title: '! 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/14/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 464bd658c9bf430191d84d3d5ad8d57173ab87c5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303708"
---
# <a name="-operator-c-reference"></a>! operator (C# 參考)

邏輯負運算子 `!` 是一元運算子，它會計算其 [bool](../keywords/bool.md) 運算元的邏輯負值。 也就是說，它會產生 `true` (若運算元是 `false`) 與 `false` (若運算元是 `true`)：

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalNegationExamples.cs#Example)]

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `!` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[邏輯負值運算子](~/_csharplang/spec/expressions.md#logical-negation-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)