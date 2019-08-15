---
title: C# 運算子 - C# 參考
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 0e49c28f05d52c704a46806559407381c7eb3530
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971256"
---
# <a name="c-operators-c-reference"></a>C# 運算子 (C# 參考)

C# 提供內建型別支援的數個預先定義運算子。 例如，[算術運算子](arithmetic-operators.md)會執行含內建數值型別運算元的算術運算，而[布林邏輯運算子](boolean-logical-operators.md)會執行含 [bool](../keywords/bool.md) 運算元的邏輯運算。

使用者定義型別可以多載特定運算子，以定義該型別運算元的對應行為。 如需詳細資訊，請參閱[運算子多載](operator-overloading.md)。

下表列出 C# 運算子，從最高優先順序開始到最低優先順序。 相同列內的所有運算子都會共用相同的優先順序層級。

| 運算子 | 類別或名稱 |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-)、[x?.y](member-access-operators.md#null-conditional-operators--and-)、[x?[y]](member-access-operators.md#null-conditional-operators--and-)、[f(x)](member-access-operators.md#invocation-operator-)、[a&#91;x&#93;](member-access-operators.md#indexer-operator-)、[x++](arithmetic-operators.md#increment-operator-)、[x--](arithmetic-operators.md#decrement-operator---)、[new](new-operator.md)、[typeof](type-testing-and-conversion-operators.md#typeof-operator)、[checked](../keywords/checked.md)、[unchecked](../keywords/unchecked.md)、[default](default.md)、[nameof](nameof.md)、[delegate](delegate-operator.md)、[sizeof](sizeof.md)、[stackalloc](stackalloc.md)、[->](pointer-related-operators.md#pointer-member-access-operator--) | 主要 |
| [+x](addition-operator.md)、[-x](subtraction-operator.md)、[\!x](boolean-logical-operators.md#logical-negation-operator-)、[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++x](arithmetic-operators.md#increment-operator-)、[--x](arithmetic-operators.md#decrement-operator---)、[(T)x](type-testing-and-conversion-operators.md#cast-operator-)、[await](../keywords/await.md)、[&x](pointer-related-operators.md#address-of-operator-)、[*x](pointer-related-operators.md#pointer-indirection-operator-)、[true and false](true-false-operators.md) | 一元 |
| [x * y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-) | 乘法類 (Multiplicative)|
| [x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--) | 加法類 (Additive) |
| [x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-)、[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | 移位 |
| [x \< y](comparison-operators.md#less-than-operator-)、[x > y](comparison-operators.md#greater-than-operator-)、[x \<= y](comparison-operators.md#less-than-or-equal-operator-)、[x >= y](comparison-operators.md#greater-than-or-equal-operator-)、[is](type-testing-and-conversion-operators.md#is-operator)、[as](type-testing-and-conversion-operators.md#as-operator) | 關聯性和型別測試 |
| [x == y](equality-operators.md#equality-operator-)、[x != y](equality-operators.md#inequality-operator-) | 相等 |
| `x & y` | [布林值邏輯 AND](boolean-logical-operators.md#logical-and-operator-) 或[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [布林值邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) 或[位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [布林值邏輯 OR](boolean-logical-operators.md#logical-or-operator-) 或[位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | 條件式 AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | 條件式 OR |
| [x ?? y](null-coalescing-operator.md) | Null 聯合運算子 |
| [t ? x : y](conditional-operator.md) | 條件運算子 |
| [x = y](assignment-operator.md)、[x += y](arithmetic-operators.md#compound-assignment)、[x -= y](arithmetic-operators.md#compound-assignment)、[x *= y](arithmetic-operators.md#compound-assignment)、[x /= y](arithmetic-operators.md#compound-assignment)、[x %= y](arithmetic-operators.md#compound-assignment)、[x &= y](boolean-logical-operators.md#compound-assignment)、[x &#124;= y](boolean-logical-operators.md#compound-assignment)、[x ^= y](boolean-logical-operators.md#compound-assignment)、[x <<= y](bitwise-and-shift-operators.md#compound-assignment)、[x >>= y](bitwise-and-shift-operators.md#compound-assignment)、[=>](lambda-operator.md) | 指派和 Lambda 宣告 |

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [運算子](../../programming-guide/statements-expressions-operators/operators.md)
