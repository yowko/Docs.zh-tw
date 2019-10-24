---
title: 浮點數值型別 - C# 參考
description: 內建 C# 浮點數型別的概觀
ms.date: 10/22/2019
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
ms.openlocfilehash: 4d71f7eea3f574e483dc4250f5c87e1ffd551f2f
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771896"
---
# <a name="floating-point-numeric-types-c-reference"></a>浮點數值型別 (C# 參考)

**浮點數型別**是**簡單型別**的子集，並可使用[*常值*](#real-literals)初始化。 所有浮點數型別也是實值型別。 所有浮點數數值型別都支援[算術](../operators/arithmetic-operators.md)、比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子。

## <a name="characteristics-of-the-floating-point-types"></a>浮點數型別的特性

C# 支援下列預先定義的浮點數型別：
  
|C# 型別/關鍵字|大概範圍|精確度|大小|.NET 型別|
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

您可以在運算式中混合使用[整數](integral-numeric-types.md)型別與浮點數型別。 在此情況下，整數型別會轉換成浮點類型。 運算式的評估會根據下列規則來執行：

- 如果其中一個浮點類型是 `double`，則運算式會評估為 `double`，或在關聯式和相等比較中為[bool](../keywords/bool.md) 。
- 如果運算式中沒有 `double` 類型，則運算式會評估為 `float`，或在關聯式和相等比較中為[bool](../keywords/bool.md) 。

浮點運算式可以包含下列值的集合：

- 正零和負零
- 正無限大和負無限大
- 非數字值 (NaN)
- 非零值的有限集合

如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。

您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。

## <a name="real-literals"></a>實際常值

實際常值的類型取決於其後置詞，如下所示：

- 不含尾碼或具有 `d` 或 `D` 尾碼的常值屬於類型 `double`
- 具有 `f` 或 `F` 尾碼的常值屬於類型 `float`
- 具有 `m` 或 `M` 尾碼的常值屬於類型 `decimal`

下列程式碼示範每個的範例：

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

上述範例也會示範如何使用 `_` 做為*數位分隔符號*，從C# 7.0 開始支援。 您可以使用數位分隔符號搭配所有類型的數值常值。

您也可以使用科學記號標記法，也就是指定實際常值的指數部分，如下列範例所示：

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>轉換

浮點數數值型別之間只有一個隱含轉換：從 `float` 到 `double`。 不過，您可以使用[明確轉換](../operators/type-testing-and-cast.md#cast-operator-)，將任何浮點類型轉換成任何其他浮點類型。 如需詳細資訊，請參閱[內建數值轉換](numeric-conversions.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [浮點類型](~/_csharplang/spec/types.md#floating-point-types)
- [Decimal 類型](~/_csharplang/spec/types.md#the-decimal-type)
- [實際常值](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [內建型別表](../keywords/built-in-types-table.md)
- [整數型別](integral-numeric-types.md)
- [格式化數值結果表](../keywords/formatting-numeric-results-table.md)
- [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET 中的數值](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
