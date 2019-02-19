---
title: '>>= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220909"
---
# <a name="-operator-c-reference"></a>>>= 運算子 (C# 參考)

右移指派運算子。

使用 `>>=` 運算子的運算式，例如

```csharp
x >>= y
```

相當於

```csharp
x = x >> y
```

但只會評估 `x` 一次。

[`>>` 運算子](right-shift-operator.md)會向其第一個運算元右移第二個運算元所定義的位元數。

下列範例示範 `>>=` 運算子的用法：

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a>運算子是否可多載

若使用者定義型別[多載](../keywords/operator.md) [`>>` 運算子](right-shift-operator.md)，右移指派運算子 `>>=` 會隱含地多載。 使用者定義型別無法明確地多載右移指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)