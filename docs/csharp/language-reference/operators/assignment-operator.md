---
title: 指派運算子 - C# 引用
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399249"
---
# <a name="assignment-operators-c-reference"></a>分配運算子（C# 引用）

指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。 指派運算式的結果是指派給左方運算元的值。 右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。

指派運算子`=`是右關聯的，即表單的運算式

```csharp
a = b = c
```

會評估為

```csharp
a = (b = c)
```

下列範例示範將區域變數、屬性及索引子元素作為指派運算子左運算元的用法：

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref 指派運算子

從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。 下列範例示範 ref 指派運算子的用法：

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

在 ref 指派運算子中，其兩個運算元必須為同一類型。

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

## <a name="null-coalescing-assignment"></a>空合併分配

從 C# 8.0 開始，僅當左側運算元計算為`??=``null`時，可以使用空合併指派運算子將其右側運算元的值分配給其左側運算元。 有關詳細資訊，請參閱[？和？？• 運算子](null-coalescing-operator.md)文章。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義的類型不能[重載](operator-overloading.md)指派運算子。 不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。 如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。 如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。

使用者定義型別無法明確地多載複合指派運算子。 但是，如果使用者定義的類型重載二進位運算子`op`，`op=`則運算子（如果存在）也會隱式重載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指派運算子](~/_csharplang/spec/expressions.md#assignment-operators)一節。

有關 ref 指派運算子`= ref`的詳細資訊，請參閱[功能方案注釋](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [ref 關鍵字](../keywords/ref.md)
