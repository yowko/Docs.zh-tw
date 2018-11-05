---
title: .NET 中的數值
ms.date: 10/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f180e459764d6e8e4484072218f01c8bab8a3b5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50191144"
---
# <a name="numerics-in-net"></a>.NET 中的數值

.NET 除了提供一系列數值整數和浮點基本類型之外，也提供沒有理論上限或下限的整數類型 <xref:System.Numerics.BigInteger?displayProperty=nameWithType>、代表複數的 <xref:System.Numerics.Complex?displayProperty=nameWithType> 類型，以及 <xref:System.Numerics> 命名空間中一組支援 SIMD 的類型。
  
## <a name="integer-types"></a>整數類型

.NET 同時支援帶正負號和不帶正負號的 8、16、32 及 64 位元整數類型，其已列於下表之中：
  
|類型|帶正負號/不帶正負號|大小 (以位元組為單位)|最小值|最大值|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|不帶正負號|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|簽署人|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|簽署人|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|簽署人|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|簽署人|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|不帶正負號|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|不帶正負號|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|不帶正負號|8|0|18,446,744,073,709,551,615|  
  
每個整數類型皆支援一組標準算術運算子。 <xref:System.Math?displayProperty=nameWithType> 類別能提供適用於更廣泛數學函式的方法。

藉由使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別，您也可在整數值中使用個別位元。  

> [!NOTE]  
> 不帶正負號的整數類型並不符合 CLS 規範。 如需詳細資訊，請參閱 [Language Independence and Language-Independent Components](language-independence-and-language-independent-components.md)。

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構是不可變的類型，表示任意大的整數，其值在理論上沒有上限或下限。 <xref:System.Numerics.BigInteger> 類型的方法與其他整數類資料類型的方法極為相似。
  
## <a name="floating-point-types"></a>浮點類型

.NET 包含三個基本浮點類型，如下表所列：
  
|類型|大小 (以位元組為單位)|大概範圍|精確度|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup>|~6-9 位數|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup>|~15-17 位數|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup>|28-29 位數|  
  
<xref:System.Single> 和 <xref:System.Double> 類型皆支援代表非數字和無限大的特殊值。 例如，<xref:System.Double> 類型能提供下列值：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 及 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。 您會使用 <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>、<xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>、<xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType> 及 <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> 方法來測試這些特殊值。

每個浮點類型皆支援一組標準算術運算子。 <xref:System.Math?displayProperty=nameWithType> 類別能提供適用於更廣泛數學函式的方法。 .NET Core 2.0 和更新版本會包含 <xref:System.MathF?displayProperty=nameWithType> 類別，其能提供可以接受 <xref:System.Single> 類型之引數的方法。

藉由使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別，您也可使用 <xref:System.Double> 和 <xref:System.Single> 中的個別位元。 <xref:System.Decimal?displayProperty=nameWithType> 結構有它自己的方法，為 <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> 和 <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>，用於使用十進位值的個別位元，而且還有一組自己的方法，用於執行一些額外的數學運算。
  
<xref:System.Double> 和 <xref:System.Single> 類型主要供本質上並不精確的值使用 (例如兩個行星之間的距離)，並且供不需較高有效位數和較小進位誤差的應用程式使用。 在需要較高精確度並將進位誤差降到最低的情況下，您應該使用 <xref:System.Decimal?displayProperty=nameWithType> 類型。

> [!NOTE]
> <xref:System.Decimal> 類型並不會消除進位的需求。 它會將因進位而產生的錯誤降到最低。
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> 結構代表複數，也就是具有實部和虛部的數字。 它支援一組標準的算術、比較、等號比較、明確及隱含轉換的運算子，以及數學、代數和三角函數方法。  
  
## <a name="simd-enabled-types"></a>啟用 SIMD 的類型

<xref:System.Numerics> 命名空間包含一組 .NET 啟用 SIMD 的類型。 SIMD (單指令多資料) 作業可在硬體層級進行平行處理。 這能提升向量化運算 (常見於數學、科學及圖形應用程式中) 的輸送量。
  
.NET 啟用 SIMD 的類型包含下列項目：

- <xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 及 <xref:System.Numerics.Vector4> 類型，其代表具有 2、3 及 4 <xref:System.Single> 值的向量。

- 兩種矩陣型別：代表 3x2 矩陣的 <xref:System.Numerics.Matrix3x2>，以及代表 4x4 矩陣的 <xref:System.Numerics.Matrix4x4>。

- <xref:System.Numerics.Plane> 類型，其代表立體空間中的平面。

- <xref:System.Numerics.Quaternion> 類型，其代表用來編碼 3D 實體旋轉的向量。

- <xref:System.Numerics.Vector%601> 類型，其代表指定數值類型的向量，並能提供一組受益於 SIMD 支援的廣泛運算子。 <xref:System.Numerics.Vector%601> 執行個體的計數是固定的，但其值 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> 會相依於執行程式碼之電腦的 CPU。
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> 類型沒有包含至 .NET Framework 中。 您必須安裝 [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) \(英文\) NuGet 套件以存取這個類型。
  
啟用 SIMD 的類型的實作方式，使它們可以搭配未啟用 SIMD 的硬體或 JIT 編譯器使用。 若要運用 SIMD 指令，您的 64 位元應用程式必須由使用 RyuJIT 編譯器的執行階段執行，此編譯器已包含在 .NET Core 和 .NET Framework 4.6 及更新版本中。 它會在以 64 位元處理器為目標時加入 SIMD 支援。

## <a name="see-also"></a>另請參閱

- [應用程式基本概念](application-essentials.md)
- [Standard Numeric Format Strings](base-types/standard-numeric-format-strings.md)
