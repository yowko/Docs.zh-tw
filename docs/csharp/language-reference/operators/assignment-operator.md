---
title: '指派運算子-c # 參考'
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916935"
---
# <a name="assignment-operators-c-reference"></a>指派運算子 (c # 參考) 

指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。 指派運算式的結果是指派給左方運算元的值。 右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。

指派運算子 `=` 是右向關聯，也就是表單的運算式

```csharp
a = b = c
```

會評估為

```csharp
a = (b = c)
```

下列範例示範將區域變數、屬性及索引子元素作為指派運算子左運算元的用法：

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref 指派運算子

從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。 下列範例示範 ref 指派運算子的用法：

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

在 ref 指派運算子的情況下，它的兩個運算元都必須是相同的類型。

## <a name="compound-assignment"></a>複合指派

若是二元運算子 `op`，表單的複合指派運算式

```csharp
x op= y
```

相當於

```csharp
x = x op y
```

但只會評估 `x` 一次。

[算數](arithmetic-operators.md#compound-assignment)、[布林邏輯](boolean-logical-operators.md#compound-assignment)和[位元邏輯與位移](bitwise-and-shift-operators.md#compound-assignment)運算子支援複合指派。

## <a name="null-coalescing-assignment"></a>Null 聯合指派

從 c # 8.0 開始，您可以使用 null 聯合指派運算子， `??=` 只有在左側運算元評估為時，才將其右運算元的值指派給其左邊的運算元 `null` 。 如需詳細資訊，請參閱[？？和？= 運算子](null-coalescing-operator.md)一文。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型[別無法多](operator-overloading.md)載指派運算子。 不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。 如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。 如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。

使用者定義型別無法明確地多載複合指派運算子。 不過，如果使用者定義型別多載二元運算子 `op` ，則 `op=` 運算子（如果存在的話）也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指派運算子](~/_csharplang/spec/expressions.md#assignment-operators)一節。

如需 ref 指派運算子的詳細資訊 `= ref` ，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [ref 關鍵字](../keywords/ref.md)
