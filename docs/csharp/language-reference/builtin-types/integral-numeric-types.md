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
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739011"
---
# <a name="integral-numeric-types--c-reference"></a>整數的數字型別 (C# 參考)

*積分數值類型*表示整數。 所有積分數值類型都是[值型](value-types.md)態 。 它們也是[簡單的類型](value-types.md#built-in-value-types),可以使用[文本](#integer-literals)初始化。 所有積分數值類型都支援[算術](../operators/arithmetic-operators.md)、[位邏輯](../operators/bitwise-and-shift-operators.md)、[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算元。

## <a name="characteristics-of-the-integral-types"></a>整數型別的特性

C# 支援下列預先定義的整數型別：

|C# 型別/關鍵字|範圍|大小|.NET 類型|
|----------|-----------|----------|-------------|
|`sbyte`|-128 到 127|帶正負號的 8 位元整數|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 至 255|不帶正負號的 8 位元整數|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32,768 至 32,767|帶正負號的 16 位元整數|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 到 65,535|不帶正負號的 16 位元整數|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2,147,483,648 至 2,147,483,647|帶正負號的 32 位元整數|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 到 4,294,967,295|不帶正負號的 32 位元整數|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807|帶正負號的 64 位元整數|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 到 18,446,744,073,709,551,615|不帶正負號的 64 位元整數|<xref:System.UInt64?displayProperty=nameWithType>|

在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。 它們是可互換的。 例如，下列宣告會宣告相同型別的變數：

```csharp
int a = 123;
System.Int32 b = 123;
```

每個整數型別的預設值都是零 (`0`)。 每個整數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大值。

使用 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構來表示帶正負號的整數，無上下限。

## <a name="integer-literals"></a>整數常值

整數文字可以是

- *十進位*:沒有任何前置字串
- *十六進位*:`0x`帶`0X`或 前置字
- *二進位* `0b` `0B`: 帶 或 前置字串(在 C# 7.0 及更高版本中提供 )

以下代碼展示每個範例:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

前面的範例還顯示`_`用作*數位分隔符*的用途,該分隔符支援從 C# 7.0 開始。 您可以將數字分隔符用於所有類型的數字文本。

整數文字的類型由其後綴確定,如下所示:

- 如果文字`int`沒有後綴,則其類型是可以表示其值的以下類型中的第一個: `uint` `long`、 `ulong`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、
- 如果文字`U`後置字`u`串或或 ,其類型是可以表示其值的以下類型中的`uint`第`ulong`一個: 。
- 如果文字`L`後置字`l`串或或 ,其類型是可以表示其值的以下類型中的`long`第`ulong`一個: 。

  > [!NOTE]
  > 您可以將小寫字母`l`用作後綴。 但是,這將生成編譯器警告,因為字母`l`可能會與`1`數位 混淆。 用於`L`清楚。

- 如果文字`UL`後置置為`Ul`, `uL``ul``LU``Lu``lU`、、、、、、、、、 的`lu`一`ulong`個類型為 。

如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。

如果整數文字的確定類型為`int`,並且文字表示的值在目標類型的範圍內,則可以隱式轉換`sbyte`為`short``ushort``uint``ulong``byte`、、、、、、、、、、、、、 或 :

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

如前面的示例所示,如果文本的值不在目標類型範圍內,則會發生編譯器錯誤[CS0031。](../../misc/cs0031.md)

您可以使用強制轉換將整數文字表示的值轉換為文字的決定類型以外的類型:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>轉換

您可以將任何積分數值類型轉換為任何其他積分數值類型。 如果目標類型可以儲存源類型的所有值,則轉換是隱式轉換。 否則,您需要使用[強制轉換表達式](../operators/type-testing-and-cast.md#cast-expression)執行顯式轉換。 有關詳細資訊,請參閱[內建數位轉換](numeric-conversions.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [整數型別](~/_csharplang/spec/types.md#integral-types)
- [整數常值](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [值類型](value-types.md)
- [浮點型態](floating-point-numeric-types.md)
- [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET 中的數值](../../../standard/numerics.md)
