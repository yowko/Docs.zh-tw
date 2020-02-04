---
title: 整數的數字型別 - C# 參考
description: 了解每個整數數字型別的範圍、儲存體大小和用法。
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 2fb4d7185ac85b29f2cc2d2e7a29e192f91a0868
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980141"
---
# <a name="integral-numeric-types--c-reference"></a>整數的數字型別 (C# 參考)

**整數數字型別**是**簡單型別**的子集，且可使用[*常值*](#integer-literals)初始化。 所有的整數型別也都是實值型別。 All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.

## <a name="characteristics-of-the-integral-types"></a>整數型別的特性

C# 支援下列預先定義的整數型別：

|C# 型別/關鍵字|Range|大小|.NET 型別|
|----------|-----------|----------|-------------|
|`sbyte`|-128 到 127|帶正負號的 8 位元整數|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 到 255|不帶正負號的 8 位元整數|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32,768 到 32,767|帶正負號的 16 位元整數|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 到 65,535|不帶正負號的 16 位元整數|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2,147,483,648 至 2,147,483,647|帶正負號的 32 位元整數|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 到 4,294,967,295|不帶正負號的 32 位元整數|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|帶正負號的 64 位元整數|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 到 18,446,744,073,709,551,615|不帶正負號的 64 位元整數|<xref:System.UInt64?displayProperty=nameWithType>|

在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。 它們是可互換的。 例如，下列宣告會宣告相同型別的變數：

```csharp
int a = 123;
System.Int32 b = 123;
```

每個整數型別的預設值都是零 (`0`)。 每個整數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大值。

使用 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構來表示帶正負號的整數，無上下限。

## <a name="integer-literals"></a>整數常值

Integer literals can be

- *decimal*: without any prefix
- *hexadecimal*: with the `0x` or `0X` prefix
- *binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)

下列程式碼示範每個的範例：

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

上述範例也會示範如何使用 `_` 做為*數位分隔符號*，從C# 7.0 開始支援。 您可以使用數位分隔符號搭配所有類型的數值常值。

The type of an integer literal is determined by its suffix as follows:

- If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.
- If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.
- If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.

  > [!NOTE]
  > You can use the lowercase letter `l` as a suffix. However, this generates a compiler warning because the letter `l` can be confused with the digit `1`. Use `L` for clarity.

- 如果常值是以 `UL`、`Ul`、`uL`、`ul`、`LU`、`Lu`、`lU`或 `lu`為尾碼，則其類型為 `ulong`。

如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。

如果 `int` 整數常值的判斷類型，而且常值所代表的值是在目的地類型的範圍內，則可以隱含地將該值轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint`或 `ulong`：

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

如上述範例所示，如果常值不在目的地類型的範圍內，就會發生編譯器錯誤[CS0031](../../misc/cs0031.md) 。

您也可以使用轉型，將整數常值所代表的值轉換為類型，而不是常值的判斷型別：

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>轉換

您可以將任何整數數數值型別轉換成任何其他整數數數值型別。 如果目的地類型可以儲存來源類型的所有值，則轉換是隱含的。 否則，您必須使用[cast 運算子 `()`](../operators/type-testing-and-cast.md#cast-operator-)來叫用明確轉換。 如需詳細資訊，請參閱[內建數值轉換](numeric-conversions.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [整數型別](~/_csharplang/spec/types.md#integral-types)
- [整數常值](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [內建型別表](../keywords/built-in-types-table.md)
- [浮點類型](floating-point-numeric-types.md)
- [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET 中的數值](../../../standard/numerics.md)
