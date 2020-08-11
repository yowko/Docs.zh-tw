---
title: 'C # 運算子和運算式-c # 參考'
description: '瞭解 c # 運算子和運算式、運算子優先順序和運算子的關聯性'
ms.date: 08/04/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 854d7c1278319869104e1758ba91eb3594741126
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063181"
---
# <a name="c-operators-and-expressions-c-reference"></a>C # 運算子和運算式 (c # 參考) 

C # 提供一些運算子。 [內建類型](../builtin-types/built-in-types.md)支援其中許多，而且可讓您使用這些類型的值來執行基本作業。 這些運算子包含下列群組：

- 使用數值運算元執行算數運算的[算術運算子](arithmetic-operators.md)
- 比較數值運算元的[比較運算子](comparison-operators.md)
- 使用運算元執行邏輯運算的[布林邏輯運算子](boolean-logical-operators.md) [`bool`](../builtin-types/bool.md)
- 使用整數類型的運算元來執行位 or 移位運算的[位 and 移位運算子](bitwise-and-shift-operators.md)
- 檢查其運算元是否相等的[等號比較運算子](equality-operators.md)

一般來說，您可以多[載這些運算子，也就](operator-overloading.md)是指定使用者定義型別之運算元的運算子行為。

最簡單的 c # 運算式是常值 (例如，[整數](../builtin-types/integral-numeric-types.md#integer-literals)和[實數](../builtin-types/floating-point-numeric-types.md#real-literals)) 和變數的名稱。 您可以使用運算子將它們結合成複雜的運算式。 運算子[優先順序](#operator-precedence)和[關聯](#operator-associativity)性決定運算式中作業的執行順序。 您可以使用括弧來變更由運算子優先順序和關聯性強制執行的評估順序。

在下列程式碼中，運算式的範例位於指派的右手邊：

[!code-csharp[expression examples](snippets/shared/Overview.cs#Expressions)]

通常，運算式會產生結果，而且可以包含在另一個運算式中。 [`void`](../builtin-types/void.md)方法呼叫是不會產生結果之運算式的範例。 它只能當做[語句](../../programming-guide/statements-expressions-operators/statements.md)使用，如下列範例所示：

```csharp
Console.WriteLine("Hello, world!");
```

以下是 c # 提供的其他運算式類型：

- [插補字串運算式](../tokens/interpolated.md)，提供方便的語法來建立格式化的字串：

  [!code-csharp-interactive[interpolated string](snippets/shared/Overview.cs#InterpolatedString)]

- 可讓您建立匿名函數的[Lambda 運算式](lambda-expressions.md)：

  [!code-csharp-interactive[lambda expression](snippets/shared/Overview.cs#Lambda)]

- [查詢運算式](../keywords/query-keywords.md)可讓您直接在 c # 中使用查詢功能：

  [!code-csharp-interactive[query expression](snippets/shared/Overview.cs#Query)]

您可以使用[運算式主體定義](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)來提供方法、函式、屬性、索引子或完成項的簡潔定義。

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
| [x-y](member-access-operators.md#member-access-expression-)、 [f (x) ](member-access-operators.md#invocation-expression-)、 [&#91;i&#93;](member-access-operators.md#indexer-operator-)、 [`x?.y`](member-access-operators.md#null-conditional-operators--and-) 、 [`x?[y]`](member-access-operators.md#null-conditional-operators--and-) 、 [x + +](arithmetic-operators.md#increment-operator-)、 [x--](arithmetic-operators.md#decrement-operator---)、 [x！](null-forgiving.md)、 [new](new-operator.md)、 [typeof](type-testing-and-cast.md#typeof-operator)、 [checked](../keywords/checked.md)、 [unchecked](../keywords/unchecked.md)、 [default](default.md)、 [nameof](nameof.md)、 [delegate](delegate-operator.md)、 [sizeof](sizeof.md)、 [stackalloc](stackalloc.md)、 [x->y](pointer-related-operators.md#pointer-member-access-operator--) | 主要 |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators)， [-x](arithmetic-operators.md#unary-plus-and-minus-operators)， [ \! x](boolean-logical-operators.md#logical-negation-operator-)， [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-)， [+ + x](arithmetic-operators.md#increment-operator-)， [--x](arithmetic-operators.md#decrement-operator---)， [^ x](member-access-operators.md#index-from-end-operator-)， [ (T) x](type-testing-and-cast.md#cast-expression)， [await](await.md)， [&x](pointer-related-operators.md#address-of-operator-)， [* x](pointer-related-operators.md#pointer-indirection-operator-)， [true 和 false](true-false-operators.md) | 一元 (Unary) |
| [x.。y](member-access-operators.md#range-operator-) | 範圍 |
| [switch](switch-expression.md) | `switch` 運算式 |
| [x * y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-) | 乘法|
| [x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--) | 加法 |
| [x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-)， [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)，[是](type-testing-and-cast.md#is-operator)， [as](type-testing-and-cast.md#as-operator) | 關聯性和型別測試 |
| [x = = y](equality-operators.md#equality-operator-)， [x！ = y](equality-operators.md#inequality-operator-) | 等式 |
| `x & y` | [布林值邏輯 AND](boolean-logical-operators.md#logical-and-operator-) 或[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [布林值邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) 或[位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [布林值邏輯 OR](boolean-logical-operators.md#logical-or-operator-) 或[位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | 條件式 AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | 條件式 OR |
| [x ?? y](null-coalescing-operator.md) | Null 聯合運算子 |
| [c ? t : f](conditional-operator.md) | 條件運算子 |
| [x = y](assignment-operator.md)， [x + = y](arithmetic-operators.md#compound-assignment)， [x-= y](arithmetic-operators.md#compound-assignment)， [x * = y](arithmetic-operators.md#compound-assignment)， [x/= y](arithmetic-operators.md#compound-assignment)， [x% = y](arithmetic-operators.md#compound-assignment)， [x &= y](boolean-logical-operators.md#compound-assignment)， [x &#124;= y](boolean-logical-operators.md#compound-assignment)，x [^ =](boolean-logical-operators.md#compound-assignment)y，x [ <<= y](bitwise-and-shift-operators.md#compound-assignment)， [x >>= y](bitwise-and-shift-operators.md#compound-assignment)， [x？？= y](null-coalescing-operator.md)，[=>](lambda-operator.md) | 指派和 Lambda 宣告 |

## <a name="operator-associativity"></a>運算子關聯性

當運算子具有相同的優先順序時，運算子的關聯性會決定作業的執行順序：

- *左關聯*運算子會依序從左至右進行評估。 除了[指派運算子](assignment-operator.md)和[null 聯合運算子](null-coalescing-operator.md)以外，所有二元運算子都是靠左關聯。 例如，`a + b - c` 會判斷值為 `(a + b) - c`。
- *右向關聯*運算子會依序從右至左進行評估。 指派運算子、null 聯合運算子和[條件運算子 `?:` ](conditional-operator.md)是右向關聯。 例如，`x = y = z` 會判斷值為 `x = (y = z)`。

使用括弧來變更由運算子關聯性強制執行的評估順序：

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>運算元評估

與運算子優先順序和關聯性無關，運算式中的運算元會由左至右評估。 下列範例示範了運算子和運算元的評估順序：

| 運算式 | 評估順序 |
| ---------- | ------------------- |
|`a + b`|a，b，+|
|`a + b * c`|a，b，c，*，+|
|`a / b + c * d`|a，b，/，c，d，*，+|
|`a / (b + c) * d`|a，b，c，+，/，d，*|

通常會評估所有運算子運算元。 不過，有些運算子會有條件地評估運算元。 也就是說，這類運算子最左邊運算元的值會定義 (還是應該評估其他運算元) 。 這些運算子是條件式邏輯[AND (`&&`) ](boolean-logical-operators.md#conditional-logical-and-operator-)和[或 (`||`) ](boolean-logical-operators.md#conditional-logical-or-operator-)運算子、 [null 聯合運算子 `??` 和 `??=` ](null-coalescing-operator.md)、 [null 條件運算子 `?.` 和 `?[]` ](member-access-operators.md#null-conditional-operators--and-)和[條件運算子 `?:` ](conditional-operator.md)。 如需詳細資訊，請參閱每個運算子的說明。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [運算式](~/_csharplang/spec/expressions.md)
- [運算子](~/_csharplang/spec/expressions.md#operators)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [運算子多載](operator-overloading.md)
- [運算式樹狀架構](../../programming-guide/concepts/expression-trees/index.md)
