---
title: unit 關鍵字 (C# 參考)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 86cbb216bd960251ebd78916fae7865aa10aa5fc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149688"
---
# <a name="uint-c-reference"></a>uint (C# 參考)

`uint` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數型別。

|類型|範圍|大小|.NET 型別|
|----------|-----------|----------|-------------------------|
|`uint`|0 到 4,294,967,295|不帶正負號的 32 位元整數|<xref:System.UInt32?displayProperty=nameWithType>|

**注意** `uint`類型不符合 CLS 規範。 請盡可能使用 `int`。

## <a name="literals"></a>常值

您可以針對 `uint` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。 如果整數常值超出 `uint` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `uint` 值。

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。

從 C# 7.0 開始，已新增一些功能來提升可讀性：

- C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。
- C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。 十進位常值不允許有前置底線。

一些範例如下所示。

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

整數常值亦可包含後置詞以表示類型。 `U` 或 'u' 後置詞表示 `uint` 或 `ulong`，視常值的數值而定。 下列範例會使用 `u` 後置詞來表示這兩種類型的不帶正負號整數。 請注意，第一個常值是 `uint`，因為其值小於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>而第二個是 `ulong`，因為其值大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>。

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：

1. [int](int.md)
2. `uint`
3. [long](long.md)
4. [ulong](ulong.md)

## <a name="conversions"></a>轉換

有一項從 `uint` 轉換為 [long](long.md)、[ulong](ulong.md)、[float](float.md)、[double](double.md) 或 [decimal](decimal.md) 之預先定義的隱含轉換。 例如：

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

有一項從 [byte](byte.md)、[ushort](ushort.md) 或 [char](char.md) 轉換為 `uint` 之預先定義的隱含轉換。 否則，您必須使用轉換。 例如，下列指派陳述式會在未進行轉換的情況下產生編譯錯誤：

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

另請注意，沒有從浮點類型轉換為 `uint` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](float.md) 和 [double](double.md)。

如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](implicit-numeric-conversions-table.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- <xref:System.UInt32>
- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [整數型別表](integral-types-table.md)
- [內建型別表](built-in-types-table.md)
- [隱含數值轉換表](implicit-numeric-conversions-table.md)
- [明確數值轉換表](explicit-numeric-conversions-table.md)