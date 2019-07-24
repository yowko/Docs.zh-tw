---
title: 整數的數字型別 - C# 參考
description: 了解每個整數數字型別的範圍、儲存體大小和用法。
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236081"
---
# <a name="integral-numeric-types--c-reference"></a>整數的數字型別 (C# 參考)

**整數數字型別**是**簡單型別**的子集，且可使用[*常值*](#integral-literals)初始化。 所有的整數型別也都是實值型別。 所有整數的數字型別都支援[算術](../operators/arithmetic-operators.md)、[位元邏輯](../operators/bitwise-and-shift-operators.md)、[比較和等號](../operators/equality-operators.md)運算子。

## <a name="characteristics-of-the-integral-types"></a>整數型別的特性

C# 支援下列預先定義的整數型別：

|C# 型別/關鍵字|範圍|大小|.NET 型別|
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

## <a name="integral-literals"></a>整數常值

整數常值可指定為*十進位常值*、*十六進位常值*或*二進位常值*。 各自的範例如下所示：

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

十進位常值不需要任何前置詞。 `x` 或 `X` 前置詞表示*十六進位常值*。 `b` 或 `B` 前置詞表示*二進位常值*。 `binaryLiteral` 宣告示範使用 `_` 作為*數字分隔符號*。 數字分隔符號可搭配所有數字常值使用。 自 C# 7.0 開始，支援二進位常值和數字分隔符號 `_`。

### <a name="literal-suffixes"></a>常值後置詞

`l` 或 `L` 後置詞會指定整數常值應為 `long` 型別。 `ul` 或 `UL` 後置詞指定 `ulong` 型別。 如果大於 9,223,372,036,854,775,807 的常值使用 `L` 後置詞 (`long` 的最大值)，則該值會轉換成 `ulong` 型別。 如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。 

> [!NOTE]
> 您可以使用小寫字母 "l" 作為後置詞。 不過，因為字母 "l" 很容易與數字 "1" 混淆，所以這會產生編譯器警告。 為了清楚起見，請使用 "L"。

### <a name="type-of-an-integral-literal"></a>整數常值的型別

如果整數常值沒有後置詞，則其型別會是下列可表示值型別中的第一個：

1. `int`
1. `uint`
1. `long`
1. `ulong`

您可以使用指派或轉換，將整數常值轉換成範圍比預設小的型別：

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

您可以使用指派、轉換或常數後置詞，將整數常值轉換成範圍比預設大的型別：

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>轉換

在目的地型別可以儲存來源型別全部值的整數型別中，任兩者之間都具有隱含轉換 (稱為「擴展轉換」  )。 例如，`int` 到 `long` 有隱含轉換，因為 `int` 值範圍是適當的 `long` 子集。 較小的不帶正負號整數型別可隱含轉換成較大帶正負號整數型別。 任一整數型別也皆可隱含轉換成任一浮點型別。  任一帶正負號的整數型別不會隱含轉換成任一不帶正負號的整數型別。

當來源型別未定義隱含轉換成目的地型別時，您必須使用明確轉換將一種整數型別轉換成另一種整數型別。 這稱為「縮小轉換」  。 因為轉換會導致資料遺失，所以需要明確轉換。

## <a name="see-also"></a>另請參閱

- [C# 語言規格 - 整數型別](~/_csharplang/spec/types.md#integral-types)
- [C# 參考](../index.md)
- [浮點類型](floating-point-numeric-types.md)
- [預設值表](../keywords/default-values-table.md)
- [格式化數值結果表](../keywords/formatting-numeric-results-table.md)
- [內建型別表](../keywords/built-in-types-table.md)
- [.NET 中的數值](../../../standard/numerics.md)
