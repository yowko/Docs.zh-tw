---
title: 算術運算子 - C# 參考
description: 了解可使用數字型別執行乘法、除法、餘數、加法和減法運算的 C# 運算子。
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 25f716084c489c834e9242800f4c7e341c41aa58
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880668"
---
# <a name="arithmetic-operators-c-reference"></a>算術運算子 (C# 參考)

下列運算子會使用數字型別執行算術運算：

- 一元 [`++` (遞增)](#increment-operator-)、[`--` (遞減)](#decrement-operator---)、[`+` (加號)](#unary-plus-and-minus-operators) 和 [`-` (減號)](#unary-plus-and-minus-operators) 運算子
- 二元 [`*` (乘法)](#multiplication-operator-)、[`/` (除法)](#division-operator-)、[`%` (餘數)](#remainder-operator-)、[`+` (加法)](#addition-operator-) 和 [`-` (減法)](#subtraction-operator--) 運算子

這些運算子可支援所有[整數](../keywords/integral-types-table.md)和[浮點](../keywords/floating-point-types-table.md)數字型別。

## <a name="increment-operator-"></a>遞增運算子 ++

一元遞增運算子 `++` 的運算元遞增量為 1。 運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../../csharp/programming-guide/indexers/index.md)存取。

遞增運算子支援兩種形式：後置遞增運算子 `x++` 和前置遞增運算子 `++x`。

### <a name="postfix-increment-operator"></a>後置遞增運算子

`x++` 的結果為運算「之前」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>前置遞增運算子

`++x` 的結果為運算「之後」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>遞減運算子 --

一元遞減運算子 (`--`) 的運算元遞減量為 1。 運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../../csharp/programming-guide/indexers/index.md)存取。

遞減運算子支援兩種形式：後置遞減運算子 `x--` 和前置遞減運算子 `--x`。

### <a name="postfix-decrement-operator"></a>後置遞減運算子

`x--` 的結果為運算「之前」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>前置遞減運算子

`--x` 的結果為運算「之後」的 `x` 值，如下列範例所示：

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>一元加號和減號運算子

一元 `+` 運算子會傳回其運算元的值。 一元 `-` 運算子會計算其運算元的負數值。

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

一元 `-` 運算子不支援 [ulong](../keywords/ulong.md) 型別。

## <a name="multiplication-operator-"></a>乘法運算子 *

乘法運算子 `*` 會計算其運算元的乘積：

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

一元 `*` 運算子是一個[指標間接運算子](pointer-related-operators.md#pointer-indirection-operator-)。

## <a name="division-operator-"></a>除法運算子 /

除法運算子 `/` 會將它的第一個運算元除以第二個運算元。

### <a name="integer-division"></a>整數除數

針對整數型別的運算元，`/` 運算子的結果會是整數型別，且等於兩個運算元捨入為零的商：

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

若要以浮點數的形式取得兩個運算元的商，請使用 `float`、`double` 或 `decimal` 型別：

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>浮點除數

針對 `float`、`double` 和 `decimal` 型別，`/` 運算子的結果會是兩個運算元的商：

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

如果其中一個運算元是 `decimal`，則另一個運算元便不可以是 `float` 或 `double`，因為 `float` 或 `double` 都無法隱含轉換為 `decimal`。 您必須明確地將 `float` 或 `double` 運算元轉換為 `decimal` 型別。 如需在數值型別之間進行隱含轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。

## <a name="remainder-operator-"></a>餘數運算子 %

餘數運算子 `%` 會計算其第一個運算元除以第二個運算元之後的餘數。

### <a name="integer-remainder"></a>整數餘數
  
對整數型別的運算元來說，`a % b` 的結果是 `a - (a / b) * b` 所產生的值。 非零餘數的正負號與第一個運算元的正負號相同，如下列範例所示：

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

使用 <xref:System.Math.DivRem%2A?displayProperty=nameWithType> 方法計算整數除法和餘數結果。

### <a name="floating-point-remainder"></a>浮點數餘數

對於 `float` 和 `double` 運算元，有限 `x` 和 `y` 的 `x % y` 結果是 `z` 值，像是

- 若 `z` 不是零，其正負號與 `x` 的正負號相同。
- `z` 的絕對值是由 `|x| - n * |y|` 產生的值，其中 `n` 為最大可能整數，小於或等於 `|x| / |y|`，而 `|x|`和 `|y|`則分別是 `x` 和 `y` 的絕對值。

> [!NOTE]
> 這項計算餘數的方法和用於整數運算元的方法類似，但不同於 IEEE 754。 如需符合 IEEE 754 的餘數運算，請使用 <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 方法。

如需在非有限運算元情況中 `%` 運算子的行為，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[餘數運算子](~/_csharplang/spec/expressions.md#remainder-operator)小節。

針對 `decimal` 運算元，餘數運算子 `%` 相當於 <xref:System.Decimal?displayProperty=nameWithType> 型別的[餘數運算子](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。

下列範例示範具有浮點運算元的餘數運算子行為：

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>加法運算子 +

加法運算子 `+` 會計算其運算元的總和：

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

您也可以使用 `+` 運算子進行字串串連和委派組合。 如需詳細資訊，請參閱 [`+` 運算子](addition-operator.md)一文。

## <a name="subtraction-operator--"></a>減法運算子 -

減法運算子 `-` 會從第一個運算元減去第二個運算元：

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

您也可以使用 `-` 運算子進行委派移除。 如需詳細資訊，請參閱 [`-` 運算子](subtraction-operator.md)一文。

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

下列範例示範如何搭配算術運算子使用複合指派：

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

由於[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)的緣故，`op` 作業的結果可能不會隱含轉換成 `x` 的 `T` 類型。 在此情況下，如果 `op` 是預先定義的運算子，且作業結果可以明確轉換成 `x` 的 `T` 型別，則形式 `x op= y` 的複合指派運算式相等於 `x = (T)(x op y)`，唯一的不同在於 `x` 只會評估一次。 下列範例示範了該行為：

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

您也可以使用 `+=` 和 `-=` 運算子訂閱及取消訂閱[事件](../keywords/event.md)。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="operator-precedence-and-associativity"></a>運算子優先順序和關聯性

下列清單會將算術運算子從最高優先順序開始排序到最低優先順序：

- 後置遞增 `x++` 和遞減 `x--` 運算子
- 前置遞增 `++x` 和遞減 `--x` 以及一元 `+` 和 `-` 運算子
- 乘法類 `*`、`/` 和 `%` 運算子
- 加法類 `+` 和 `-` 運算子

二元算術運算子都是左向關聯。 亦即，具有相同優先順序層級的運算子會由左至右進行評估。

使用括號 `()` 變更運算子優先順序和關聯性強制執行的評估順序。

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](index.md)。

## <a name="arithmetic-overflow-and-division-by-zero"></a>算術溢位和除數為零

當算術運算的結果超出可能相關數字型別有限值的範圍之外時，算術運算子的行為取決於其運算元的型別。

### <a name="integer-arithmetic-overflow"></a>整數算術溢位

整數除以零一定會擲回 <xref:System.DivideByZeroException>。

如果整數算術溢位，則溢位檢查內容 (可以是 [checked 或 unchecked](../keywords/checked-and-unchecked.md)) 可控制所產生的行為：

- 在 checked 內容中，如果常數運算式發生溢位，則會發生編譯時期錯誤。 否則，當運算是在執行階段執行時，就會擲回 <xref:System.OverflowException>。
- 在 unchecked 內容中，會捨棄目的型別不適用的高序位位元，以便將結果截斷。

除了 [checked 與 unchecked](../keywords/checked-and-unchecked.md) 陳述式之外，您還可以使用 `checked` 和 `unchecked` 運算子控制評估運算式的溢位檢查內容：

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

根據預設，*unchecked* 內容中會發生算術運算。

### <a name="floating-point-arithmetic-overflow"></a>浮點算術溢位

具有 `float` 和 `double` 型別的算術運算永遠不會擲回例外狀況。 具有這些型別之算術運算的結果可以是代表無限值和非數字的其中一個特殊值：

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

若是 `decimal` 型別的運算元，算術溢位一律會擲回 <xref:System.OverflowException>，且除數為零一定會擲回 <xref:System.DivideByZeroException>。

## <a name="round-off-errors"></a>四捨五入錯誤

由於實數和浮點算術的浮點數表示法的一般限制，使用浮點型別計算時可能會發生四捨五入錯誤。 亦即，運算式產生的結果可能不同於預期的數學結果。 下列範例將示範幾個這類案例：

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

如需詳細資訊，請參閱 [System.Double](/dotnet/api/system.double#remarks)、[System.Single](/dotnet/api/system.single#remarks) 或 [System.Decimal](/dotnet/api/system.decimal#remarks) 參考頁面的備註。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型別可以[多載](../keywords/operator.md)一元 (`++`、`--`、`+` 和 `-`) 和二元 (`*`、`/`、`%`、`+` 與 `-`) 算術運算子。 當二元運算子多載時，對應的複合指派運算子也會隱含地多載。 使用者定義型別無法明確地多載複合指派運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [後置遞增和遞減運算子](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [前置遞增和遞減運算子](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [一元減號運算子](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [乘法運算子](~/_csharplang/spec/expressions.md#multiplication-operator)
- [除法運算子](~/_csharplang/spec/expressions.md#division-operator)
- [餘數運算子](~/_csharplang/spec/expressions.md#remainder-operator)
- [加法運算子](~/_csharplang/spec/expressions.md#addition-operator)
- [減法運算子](~/_csharplang/spec/expressions.md#subtraction-operator)
- [複合指派](~/_csharplang/spec/expressions.md#compound-assignment)
- [checked 和 unchecked 運算子](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET 中的數值](../../../standard/numerics.md)
