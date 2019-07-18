---
title: 浮點數值型別 - C# 參考
description: 內建 C# 浮點數型別的概觀
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664188"
---
# <a name="floating-point-numeric-types-c-reference"></a>浮點數值型別 (C# 參考)

**浮點數型別**是**簡單型別**的子集，並可使用[*常值*](#floating-point-literals)初始化。 所有浮點數型別也是實值型別。 所有浮點數型別都支援[算術](../operators/arithmetic-operators.md)、[比較和等號](../operators/equality-operators.md)運算子。

下表顯示浮點數型別的精確度和大概範圍：
  
|類型|大概範圍|精確度|  
|----------|-----------------------|---------------|  
|`float`|±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup>|~6-9 位數|  
|`double`|±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup>|~15-17 位數|  
|`decimal`|±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup>|28-29 位數|  

所有浮點數型別的預設值為 `0`。 每個浮點數型別都有名為 `MinValue` 和 `MaxValue` 的常數，為該型別的最小值和最大值。 `float` 和 `double` 型別還有 `PositiveInfinity`、`NegativeInfinity` 和 `NaN` (亦即「非數字」) 等額外常數。 `decimal` 型別包含 `Zero`、`One` 和 `MinusOne` 的常數。

相較於 `float` 和 `double`，`decimal` 型別的精確度較高且範圍較小，因此非常適合財務和金融計算。

您可以在運算式中混合使用整數型別和浮點數型別。 在此情況下，整數型別會轉換成浮點類型。 運算式的評估會根據下列規則來執行：

- 如果其中一個浮點數型別是 `double`，運算式會評估為 `double` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。
- 如果運算式中沒有 `double` 型別，則運算式會評估為 `float` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。

浮點運算式可以包含下列值的集合：

- 正零和負零
- 正無限大和負無限大
- 非數字值 (NaN)
- 非零值的有限集合

如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。

您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。

## <a name="floating-point-literals"></a>浮點數常值

預設會將指派運算子右邊的浮點數值常值視為 `double`。 您可以使用尾碼，將浮點數或整數常值轉換成特定型別：

- `d` 或 `D` 尾碼會將常值轉換為 `double`。
- `f` 或 `F` 尾碼會將常值轉換為 `float`。
- `m` 或 `M` 尾碼會將常值轉換為 `decimal`。

下列範例顯示每種尾碼：

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>轉換

從 `float` 到 `double` 有隱含轉換 (稱為「擴展轉換」  )，而由於 `float` 值的範圍是 `double` 的適當子集，因此從 `float` 至 `double` 不會失去精確度。 

如果未定義從來源型別到目的地型別的隱含轉換，則必須使用明確轉換，將某種浮點數型別轉換成另一種浮點數型別。 這稱為「縮小轉換」  。 因為轉換會導致資料遺失，所以需要明確轉換。 其他浮點數型別和 `decimal` 型別之間沒有隱含轉換，因為 `decimal` 型別的精確度較 `float` 或 `double` 來得高。

如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。

如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [整數型別](integral-numeric-types.md)
- [預設值表](../keywords/default-values-table.md)
- [格式化數值結果表](../keywords/formatting-numeric-results-table.md)
- [內建型別表](../keywords/built-in-types-table.md)
- [.NET 中的數值](../../../standard/numerics.md)
- [轉換和型別轉換](../../programming-guide/types/casting-and-type-conversions.md)
- [隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)
- [明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)
