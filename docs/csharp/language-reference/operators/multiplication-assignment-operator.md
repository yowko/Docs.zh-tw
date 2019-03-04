---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967382"
---
# <a name="-operator-c-reference"></a>\*= 運算子 (C# 參考)

乘法指派運算子。

使用 `*=` 運算子的運算式，例如

```csharp
x *= y
```

相當於

```csharp
x = x * y
```

但只會評估 `x` 一次。

針對數值類型，[\* 運算子](multiplication-operator.md)會計算其運算元的乘積。

下列範例示範 `*=` 運算子的用法：

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>運算子是否可多載

如果使用者定義類型將[乘法運算子](multiplication-operator.md) `*` [多載](../keywords/operator.md)，則乘法指派運算子 `*=` 會隱含地多載。 使用者定義類型無法明確地多載乘法指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
