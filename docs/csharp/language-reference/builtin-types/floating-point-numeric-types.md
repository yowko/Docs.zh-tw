---
title: 浮點數值型別 - C# 參考
description: 瞭解內建 C# 浮點型態:浮動點、雙數和十進制
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121474"
---
# <a name="floating-point-numeric-types-c-reference"></a>浮點數值型別 (C# 參考)

*浮點數值類型*表示實數。 所有浮點數值類型都是[值類型](value-types.md)。 它們也是[簡單的類型](value-types.md#built-in-value-types),可以使用[文本](#real-literals)初始化。 所有浮點數值類型都支援[算術](../operators/arithmetic-operators.md)、[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算符。

## <a name="characteristics-of-the-floating-point-types"></a>浮點數型別的特性

C# 支援下列預先定義的浮點數型別：
  
|C# 型別/關鍵字|大概範圍|Precision|大小|.NET 類型|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup>|~6-9 位數|4 個位元組|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup>|~15-17 位數|8 個位元組|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup>|28-29 位數|16 個位元組|<xref:System.Decimal?displayProperty=nameWithType>|

在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。 它們是可互換的。 例如，下列宣告會宣告相同型別的變數：

```csharp
double a = 12.3;
System.Double b = 12.3;
```

每個浮點數型別的預設值都是零 (`0`)。 每個浮點數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大有限值。 `float` 與 `double` 型別也提供表示不是數字和無限值的常數。 例如，`double` 型別提供下列常數：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 與 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。

相較於 `float` 與 `double`，因為 `decimal` 型別的精確度較高且範圍較小，所以非常適合財務與金融計算。

您可以在運算式中混合[積分](integral-numeric-types.md)類型和`float``double`和類型。 在這種情況下,積分類型將隱式轉換為其中一個浮點類型,如有必要,`float`該類型將隱式轉換為`double`。 運算式評估如下：

- 如果表示式中有`double`類型,則表示式在關係與相等`double`[`bool`](bool.md)比較 中計算到或 。
- 如果運算式中沒有`double`類型,則運算式將計算到`float``bool`或在關係和相等比較中。

您還可以在運算式中混合積分類型和`decimal`類型。 在這種情況下,積分類型隱式轉換為`decimal`類型,運算式在關係和相等比較`decimal``bool`中計算為或 。

不能將`decimal`類型與 運算式`float``double`中的和類型混合。 在這種情況下,如果要執行算術、比較或相等操作,則必須顯式將操作數從 類型轉換`decimal`為 類型,如下例所示:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。

## <a name="real-literals"></a>真實文字

真實文本的類型由其後綴決定,如下所示:

- 沒有尾尾或`d`包含`D`後的文字的類型`double`
- 以`f`文字`F`的文字的類型`float`
- 以`m`文字`M`的文字的類型`decimal`

以下代碼展示每個範例:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

前面的範例還顯示`_`用作*數位分隔符*的用途,該分隔符支援從 C# 7.0 開始。 您可以將數字分隔符用於所有類型的數字文本。

您還可以使用科學記數法,即指定真實文本的指數部分,如下例所示:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>轉換

浮點數值類型之間只有一個隱式轉換:從`float`到`double`。 但是,您可以將任何浮點類型轉換為具有[顯式強制轉換](../operators/type-testing-and-cast.md#cast-expression)的任何其他浮點類型。 有關詳細資訊,請參閱[內建數位轉換](numeric-conversions.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [浮點型態](~/_csharplang/spec/types.md#floating-point-types)
- [小數型別](~/_csharplang/spec/types.md#the-decimal-type)
- [真實文字](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [值類型](value-types.md)
- [整數型別](integral-numeric-types.md)
- [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET 中的數值](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
