---
title: = 運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 85182acb84ea79cb00a9edb315c3954f440305f4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758361"
---
# <a name="-operator-c-reference"></a>= 運算子 (C# 參考)

指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../../csharp/programming-guide/indexers/index.md)元素。 指派運算式的結果是指派給左方運算元的值。 右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。

指派運算子是右向關聯運算子，亦即，以下形式的運算式

```csharp
a = b = c
```

評估為

```csharp
a = (b = c)
```

下列範例示範如何使用指派運算子將值指派給區域變數、屬性及索引子元素：

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>ref 指派運算子

從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。 下列範例示範 ref 指派運算子的用法：

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

就 ref 指派運算子而言，左方運算元與右方運算元的型別必須相同。

如需詳細資訊，請參閱[功能提案注意事項](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md) \(英文\)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別無法多載指派運算子。 不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。 如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。 如需詳細資訊，請參閱 [implicit](../keywords/implicit.md) 關鍵字一文。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[簡單指派](~/_csharplang/spec/expressions.md#simple-assignment)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [ref 關鍵字](../keywords/ref.md)
