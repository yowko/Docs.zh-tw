---
title: 位元與移位運算子 - C# 參考
description: 了解針對整數型別運算元執行位元邏輯或移位作業的 C# 運算子。
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 87cfbf6d74b61b5485599afa7e0aff9ecccad9d4
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555418"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>位元與移位運算子 (C# 參考)

下列運算子會使用[整數數數值型別](../builtin-types/integral-numeric-types.md)或[char](../builtin-types/char.md)類型的運算元來執行位 or shift 運算：

- 一元[ `~` (位補數) ](#bitwise-complement-operator-)運算子
- 二進位[ `<<` (左移位) ](#left-shift-operator-)和[ `>>` (右移運算子) ](#right-shift-operator-)移位運算子
- Binary [ `&` (邏輯 AND) ](#logical-and-operator-)、 [ `|` (邏輯 OR) ](#logical-or-operator-)，以及[ `^` (邏輯互斥 OR) ](#logical-exclusive-or-operator-)運算子

這些運算子已針對 `int`、`uint`、`long` 和 `ulong` 型別進行定義。 當兩個運算元都是其他整數型別 (`sbyte`、`byte`、`short`、`ushort` 或 `char`) 時，它們的值會轉換成 `int` 型別，而這也是作業的結果型別。 當運算元屬於不同的整數型別時，它們的值都會轉換成範圍最接近的整數型別。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)一節。

`&`、 `|` 和 `^` 運算子也會針對類型的運算元定義 `bool` 。 如需詳細資訊，請參閱[布林邏輯運算子](boolean-logical-operators.md)。

位元和移位運算子一律不會導致溢位，並會在[受檢查內容及未受檢查](../keywords/checked-and-unchecked.md)內容中產生相同的結果。

## <a name="bitwise-complement-operator-"></a>位元補充運算子 ~

`~` 運算子會透過反轉每個位元，產生其運算元的位元補充：

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

您也可以使用 `~` 符號來宣告完成項。 如需詳細資訊，請參閱[完成項](../../programming-guide/classes-and-structs/destructors.md)。

## <a name="left-shift-operator-"></a>左移運算子 \<\<

運算子會將 `<<` 其左邊的運算元向[右運算元所定義的位數](#shift-count-of-the-shift-operators)左移。

左移作業會捨棄位於結果型別範圍外的高位位元，並將低位的空位元位置設為零，如下列範例所示：

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

由於移位運算子僅針對 `int`、`uint`、`long` 和 `ulong` 型別進行定義，所以作業的結果一律會包含至少 32 個位元。 左邊運算元是另一個整數型別 (`sbyte`、`byte`、`short`、`ushort` 或 `char`)，其值會轉換成 `int` 型別，如下列範例所示：

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

如需 `<<` 運算子右邊運算元如何定義移位計數的資訊，請參閱[移位運算子的移位計數](#shift-count-of-the-shift-operators)一節。

## <a name="right-shift-operator-"></a>右移運算子 >>

運算子會將 `>>` 其左邊的運算元右移到[其右邊運算元所定義的位數](#shift-count-of-the-shift-operators)。

右移作業會捨棄低位位元，如下列範例所示：

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

會根據左邊運算元的類型來設定高位空位元位置，如下所示：

- 如果左運算元的類型為 `int` 或 `long` ，則右移運算子會執行*算術*移位：左邊運算元 (正負號位) 最有效位的值會傳播到高序位的空白位位置。 也就是說，若左邊運算元不是負值且在為負值時被設定為一，則高位空位元位置會被設定為零。

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- 如果左運算元的類型為 `uint` 或 `ulong` ，則右移運算子會執行*邏輯*移位：高序位空白位位置一律會設定為零。

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

如需 `>>` 運算子右邊運算元如何定義移位計數的資訊，請參閱[移位運算子的移位計數](#shift-count-of-the-shift-operators)一節。

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>邏輯 AND 運算子&amp;

`&` 運算子會計算其運算元的位元邏輯 AND：

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

針對 `bool` 運算元， `&` 運算子會計算其運算元的[邏輯 AND](boolean-logical-operators.md#logical-and-operator-) 。 一元的 `&` 運算子是 [address-of 運算子](pointer-related-operators.md#address-of-operator-)。

## <a name="logical-exclusive-or-operator-"></a>邏輯互斥 OR 運算子 ^

`^` 運算子會計算其運算元的位元邏輯互斥 OR，也稱為位元邏輯 XOR：

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

針對 `bool` 運算元， `^` 運算子會計算其運算元的[邏輯互斥 OR](boolean-logical-operators.md#logical-exclusive-or-operator-) 。

## <a name="logical-or-operator-"></a>邏輯 OR 運算子 |

`|` 運算子會計算其運算元的位元邏輯 OR：

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

針對 `bool` 運算元， `|` 運算子會計算其運算元的[邏輯 OR](boolean-logical-operators.md#logical-or-operator-) 。

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

下列範例會示範使用位元及移位運算子進行複合指派的方式：

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

由於[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)的緣故，`op` 作業結果可能無法隱含轉換成 `x` 的 `T` 型別。 在此情況下，如果 `op` 是預先定義的運算子，且作業結果可以明確轉換成 `x` 的 `T` 型別，則形式 `x op= y` 的複合指派運算式相等於 `x = (T)(x op y)`，唯一的不同在於 `x` 只會評估一次。 下列範例示範了該行為：

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>運算子優先順序

下列清單會從優先順序最高位元及移位運算子依序排序到優先順序最低的運算子：

- 位元補充運算子 `~`
- 移位運算子 `<<` 和 `>>`
- 邏輯 AND 運算子 `&`
- 邏輯互斥 OR 運算子 `^`
- 邏輯 OR 運算子 `|`

使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

如需依優先順序層級排序之 c # 運算子的完整清單，請參閱[c # 運算子](index.md)一文的[運算子優先順序](index.md#operator-precedence)一節。

## <a name="shift-count-of-the-shift-operators"></a>移位運算子的移位計數

對於移位運算子 `<<` 和 `>>` ，右運算元的類型必須是 `int` 或具有[預先定義的隱含數值轉換](../builtin-types/numeric-conversions.md#implicit-numeric-conversions)的類型 `int` 。

針對 `x << count` 和 `x >> count` 運算式，實際的移位計數取決於 `x` 的型別，如下所示：

- 如果的型別 `x` 是 `int` 或 `uint` ，則移位元數目是由右邊運算元的低序位*五*位所定義。 也就是說，位移計數是從 `count & 0x1F` (或 `count & 0b_1_1111`) 所計算。

- 如果的類型 `x` 是 `long` 或 `ulong` ，則移位元數目是由右邊運算元的低序位*六*位所定義。 也就是說，位移計數是從 `count & 0x3F` (或 `count & 0b_11_1111`) 所計算。

下列範例示範了該行為：

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> 如上述範例所示，即使右邊運算元的值大於左邊運算元中的位數，移位作業的結果也可以是非零，而是。

## <a name="enumeration-logical-operators"></a>列舉邏輯運算子

`~` `&` `|` `^` 任何[列舉](../builtin-types/enum.md)類型也支援、、和運算子。 對於相同列舉類型的運算元，會在基礎整數類型的對應值上執行邏輯運算。 例如，針對任何基礎型別為 `U` 列舉型別 `T` 的 `x` 和 `y`，`x & y` 運算式會產生與 `(T)((U)x & (U)y)` 運算式相同結果。

您通常會使用位邏輯運算子搭配使用[Flags](xref:System.FlagsAttribute)屬性所定義的列舉類型。 如需詳細資訊，請參閱[列舉型別](../builtin-types/enum.md)文章中的[作為位元旗標的列舉型別](../builtin-types/enum.md#enumeration-types-as-bit-flags)一節。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義型[別可以多](operator-overloading.md)載 `~` 、 `<<` 、、 `>>` 、 `&` `|` 和 `^` 運算子。 當二元運算子多載時，對應的複合指派運算子也會隱含地多載。 使用者定義型別無法明確地多載複合指派運算子。

若使用者定義型別 `T` 多載了 `<<` 或 `>>` 運算子，則左邊運算元的型別必須是 `T`，右邊運算元的型別必須是 `int`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [位補數運算子](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [移位運算子](~/_csharplang/spec/expressions.md#shift-operators)
- [邏輯運算子](~/_csharplang/spec/expressions.md#logical-operators)
- [複合指派](~/_csharplang/spec/expressions.md#compound-assignment)
- [數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [布林值邏輯運算子](boolean-logical-operators.md)
