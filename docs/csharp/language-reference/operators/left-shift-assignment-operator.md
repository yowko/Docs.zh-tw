---
title: <<= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219445"
---
# <a name="-operator-c-reference"></a>\<\<= 運算子 (C# 參考)

左移指派運算子。

使用 `<<=` 運算子的運算式，例如

```csharp
x <<= y
```

相當於

```csharp
x = x << y
```

但只會評估 `x` 一次。

[`<<` 運算子](left-shift-operator.md)會向其第一個運算元左移第二個運算元所定義的位元數。

下列範例示範 `<<=` 運算子的用法：

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a>運算子是否可多載

若使用者定義型別[多載](../keywords/operator.md) [`<<` 運算子](left-shift-operator.md)，左移指派運算子 `<<=` 會隱含地多載。 使用者定義型別無法明確地多載左移指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
