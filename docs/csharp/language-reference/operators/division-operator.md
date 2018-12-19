---
title: / 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286529"
---
# <a name="-operator-c-reference"></a>/ 運算子 (C# 參考)

除法運算子 `/` 會將它的第一個運算元除以第二個運算元。 所有數值類型皆支援除法運算子。

## <a name="integer-division"></a>整數除數

針對整數型別的運算元，`/` 運算子的結果會是整數型別，且等於兩個運算元捨入為零的商：

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

若要以浮點數的形式取得兩個運算元的商，請使用 `float`、`double` 或 `decimal` 型別：

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a>浮點除數

針對 `float`、`double` 和 `decimal` 型別，`/` 運算子的結果會是兩個運算元的商：

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

如果其中一個運算元是 `decimal`，則另一個運算元便不可以是 `float` 或 `double`，因為 `float` 或 `double` 都無法隱含轉換為 `decimal`。 您必須明確地將 `float` 或 `double` 運算元轉換為 `decimal` 型別。 如需在數值型別之間進行隱含轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md) `/` 運算子。 多載 `/` 運算子時，[除法指派運算子](division-assignment-operator.md) `/=` 也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[除法運算子](~/_csharplang/spec/expressions.md#division-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [% 運算子](remainder-operator.md)
