---
title: C# 運算子 - C# 參考
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 75697a7a52fbfb04e1b44ecf591e271217a69bf4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924657"
---
# <a name="c-operators-c-reference"></a>C# 運算子 (C# 參考)

C# 提供許多由內建類型支援的運算子。 舉例來說，以數值運算元執行算術運算的[算術運算子](arithmetic-operators.md)，以及以[布林](../keywords/bool.md)運算元執行邏輯運算的[布林值邏輯運算子](boolean-logical-operators.md)。 部分運算子可以[多載](operator-overloading.md)。 進行運算子多載時，您可以為使用者定義類型指定運算元的運算子行為。

再[運算式](../../programming-guide/statements-expressions-operators/expressions.md)中，運算子優先順序和關聯性會決定作業的執行順序。 您可以使用括弧來變更由運算子優先順序和關聯性強制執行的評估順序。

## <a name="operator-precedence"></a>運算子優先順序

在具有多個運算子的運算式中，具有較高優先順序的運算子會在優先順序較低的運算子之前進行評估。 在下列範例中，因為乘法的優先順序高於加法，所以會先執行乘法：

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

使用括弧變更由運算子優先順序強制執行的評估順序：

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

下表列出 C# 運算子，從最高優先順序開始到最低優先順序。 每個資料列中的運算子都具有相同的優先順序。

| 運算子 | 類別或名稱 |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-)、[x?.y](member-access-operators.md#null-conditional-operators--and-)、[x?[y]](member-access-operators.md#null-conditional-operators--and-)、[f(x)](member-access-operators.md#invocation-operator-)、[a&#91;i&#93;](member-access-operators.md#indexer-operator-)、[x++](arithmetic-operators.md#increment-operator-)、[x--](arithmetic-operators.md#decrement-operator---)、[new](new-operator.md)、[typeof](type-testing-and-cast.md#typeof-operator)、[checked](../keywords/checked.md)、[unchecked](../keywords/unchecked.md)、[default](default.md)、[nameof](nameof.md)、[delegate](delegate-operator.md)、[sizeof](sizeof.md)、[stackalloc](stackalloc.md)、[x->y](pointer-related-operators.md#pointer-member-access-operator--) | 主要 |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators)、[-x](arithmetic-operators.md#unary-plus-and-minus-operators)、[\!x](boolean-logical-operators.md#logical-negation-operator-)、[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++x](arithmetic-operators.md#increment-operator-)、[--x](arithmetic-operators.md#decrement-operator---)、[(T)x](type-testing-and-cast.md#cast-operator-)、[await](../keywords/await.md)、[&x](pointer-related-operators.md#address-of-operator-)、[*x](pointer-related-operators.md#pointer-indirection-operator-)、[true and false](true-false-operators.md) | 一元 |
| [x * y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-) | 乘法類 (Multiplicative)|
| [x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--) | 加法類 (Additive) |
| [x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-)、[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-)、[x > y](comparison-operators.md#greater-than-operator-)、[x \<= y](comparison-operators.md#less-than-or-equal-operator-)、[x >= y](comparison-operators.md#greater-than-or-equal-operator-)、[is](type-testing-and-cast.md#is-operator)、[as](type-testing-and-cast.md#as-operator) | 關聯性和型別測試 |
| [x == y](equality-operators.md#equality-operator-)、[x != y](equality-operators.md#inequality-operator-) | 相等 |
| `x & y` | [布林值邏輯 AND](boolean-logical-operators.md#logical-and-operator-) 或[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [布林值邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) 或[位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [布林值邏輯 OR](boolean-logical-operators.md#logical-or-operator-) 或[位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | 條件式 AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | 條件式 OR |
| [x ?? y](null-coalescing-operator.md) | Null 聯合運算子 |
| [c ? t : f](conditional-operator.md) | 條件運算子 |
| [x = y](assignment-operator.md)、[x += y](arithmetic-operators.md#compound-assignment)、[x -= y](arithmetic-operators.md#compound-assignment)、[x *= y](arithmetic-operators.md#compound-assignment)、[x /= y](arithmetic-operators.md#compound-assignment)、[x %= y](arithmetic-operators.md#compound-assignment)、[x &= y](boolean-logical-operators.md#compound-assignment)、[x &#124;= y](boolean-logical-operators.md#compound-assignment)、[x ^= y](boolean-logical-operators.md#compound-assignment)、[x <<= y](bitwise-and-shift-operators.md#compound-assignment)、[x >>= y](bitwise-and-shift-operators.md#compound-assignment)、[=>](lambda-operator.md) | 指派和 Lambda 宣告 |

## <a name="operator-associativity"></a>運算子關聯性

當運算子具有相同的優先順序時，運算子的關聯性會決定作業的執行順序：

- *左向關聯*運算子會依由左至右的順序進行評估。 除了[指派運算子](assignment-operator.md)和 [null 聯合運算子 `??`](null-coalescing-operator.md) 以外，所有二元運算子都是靠左關聯。 例如，`a + b - c` 會判斷值為 `(a + b) - c`。
- *右向關聯*運算子會依由右至左的順序進行評估。 指派運算子、null 聯合運算子 `??` 和[條件運算子 `?:`](conditional-operator.md) 是右向關聯。 例如，`x = y = z` 會判斷值為 `x = (y = z)`。

使用括弧來變更由運算子關聯性強制執行的評估順序：

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>運算元評估

與運算子優先順序和關聯性無關，運算式中的運算元會由左至右評估。 下列範例示範了運算子和運算元的評估順序：

| 運算式 | 評估的順序 |
| ---------- | ------------------- |
|`a + b`|a，b，+|
|`a + b * c`|a，b，c，*，+|
|`a / b + c * d`|a，b，/，c，d，*，+|
|`a / (b + c) * d`|a，b，c，+，/，d，*|

通常會評估所有運算子運算元。 有些運算子會視條件評估運算元。 也就是說，這類運算子第一個運算元的值會定義是否應該評估 (或要評估的) 其他運算元。 這些運算子包括條件式邏輯 [AND (`&&`)](boolean-logical-operators.md#conditional-logical-and-operator-) 和 [OR (`||`)](boolean-logical-operators.md#conditional-logical-or-operator-) 運算子、[null 聯合運算子 `??`](null-coalescing-operator.md)、[null 條件式運算子 `?.``?[]`](member-access-operators.md#null-conditional-operators--and-)和[條件式運算子 `?:`](conditional-operator.md)。 如需更多詳細資料，請參閱每個運算子的說明。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[運算子](~/_csharplang/spec/expressions.md#operators)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [運算式](../../programming-guide/statements-expressions-operators/expressions.md)
