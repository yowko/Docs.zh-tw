---
title: '&amp;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237021"
---
# <a name="amp-operator-c-reference"></a>&amp;= 運算子 (C# 參考)

AND 指派運算子。

使用 `&=` 運算子的運算式，例如

```csharp
x &= y
```

相當於

```csharp
x = x & y
```

但只會評估 `x` 一次。

若為整數運算元，[`&` 運算子](and-operator.md)會計算其運算元的位元邏輯 AND；若為 [bool](../keywords/bool.md) 運算元，則會計算其運算元的邏輯 AND。

下列範例示範 `&=` 運算子的用法：

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a>運算子是否可多載

若使用者定義型別[多載](../keywords/operator.md) [`&` 運算子](and-operator.md)，AND 指派運算子 `&=` 會隱含地多載。 使用者定義型別無法明確地多載 AND 指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
