---
title: /= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286516"
---
# <a name="-operator-c-reference"></a>/= 運算子 (C# 參考)

除法指派運算子。

使用 `/=` 運算子的運算式，例如

```csharp
x /= y
```

相當於

```csharp
x = x / y
```

但只會評估 `x` 一次。

[除法運算子](division-operator.md) `/` 會將它的第一個運算元除以第二個運算元。 所有數值型別都支援。

下列範例示範 `/=` 運算子的用法：

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a>運算子是否可多載

如果使用者定義的型別將[除法運算子](division-operator.md) `/` [多載](../keywords/operator.md)，則除法指派運算子 `/=` 會隱含地多載。 使用者定義型別無法明確地多載除法指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
