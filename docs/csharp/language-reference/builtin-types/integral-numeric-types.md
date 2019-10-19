---
title: 整數的數字型別 - C# 參考
description: 了解每個整數數字型別的範圍、儲存體大小和用法。
ms.date: 10/18/2019
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
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579187"
---
# <a name="integral-numeric-types--c-reference"></a>整數的數字型別 (C# 參考)

**整數數字型別**是**簡單型別**的子集，且可使用[*常值*](#integer-literals)初始化。 所有的整數型別也都是實值型別。 所有整數數數值型別都支援[算術](../operators/arithmetic-operators.md)、[位邏輯](../operators/bitwise-and-shift-operators.md)、比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子。

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

整數常值可以是

- *decimal*：不含任何前置詞
- *十六進位*：使用 `0x` 或 `0X` 前置詞
- *binary*：具有 `0b` 或 `0B` 前置詞（可在C# 7.0 和更新版本中取得）

下列程式碼示範每個的範例：

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

上述範例也會示範如何使用 `_` 做為*數位分隔符號*，從C# 7.0 開始支援。 您可以使用數位分隔符號搭配所有類型的數值常值。

整數常值的類型是由其後綴決定，如下所示：

- 如果常值沒有後置詞，其類型會是下列類型中可表示其值的第一個型別： `int`、`uint`、`long`、`ulong`。
- 如果常值是以 `U` 或 `u` 為後置字元，則其類型會是下列類型中可表示其值的第一個型別： `uint`、`ulong`。
- 如果常值是以 `L` 或 `l` 為後置字元，則其類型會是下列類型中可表示其值的第一個型別： `long`、`ulong`。

  > [!NOTE]
  > 您可以使用小寫字母 `l` 做為尾碼。 不過，這會產生編譯器警告，因為字母 `l` 可以與數位 `1` 混淆。 為了清楚起見，請使用 `L`。

- 如果常值是以 `UL`、`Ul`、`uL`、`ul`、`LU`、`Lu`、`lU` 或 `lu` 為尾碼，則其類型為 `ulong`。

如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。

整數常值所代表的值可以隱含地轉換成範圍小於所決定之常數值型別的類型。 當此值在目的地類型的範圍內時，就可能發生這種情況：

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

在目的地型別可以儲存來源型別全部值的整數型別中，任兩者之間都具有隱含轉換 (稱為「擴展轉換」)。 例如，`int` 到 `long` 有隱含轉換，因為 `int` 值範圍是適當的 `long` 子集。 較小的不帶正負號整數型別可隱含轉換成較大帶正負號整數型別。 任一整數型別也皆可隱含轉換成任一浮點型別。  任一帶正負號的整數型別不會隱含轉換成任一不帶正負號的整數型別。

當來源型別未定義隱含轉換成目的地型別時，您必須使用明確轉換將一種整數型別轉換成另一種整數型別。 這稱為「縮小轉換」。 因為轉換會導致資料遺失，所以需要明確轉換。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [整數型別](~/_csharplang/spec/types.md#integral-types)
- [整數常值](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [浮點類型](floating-point-numeric-types.md)
- [預設值表](../keywords/default-values-table.md)
- [格式化數值結果表](../keywords/formatting-numeric-results-table.md)
- [內建型別表](../keywords/built-in-types-table.md)
- [.NET 中的數值](../../../standard/numerics.md)
