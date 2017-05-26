---
title: ".NET Framework 中的數值 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 9b62cffb136abde67ab6952e7849e5681ec99a24
ms.contentlocale: zh-tw
ms.lasthandoff: 05/11/2017

---
# <a name="numerics-in-the-net-framework"></a>.NET Framework 中的數值
.NET Framework 除了沒有理論上限或下限的整數型別 <xref:System.Numerics.BigInteger>、代表複數的型別 <xref:System.Numerics.Complex>，以及 <xref:System.Numerics> 命名空間中一組支援 SIMD 的向量型別之外，也支援標準數值整數和浮點數基本型別。  
  
 此外，啟用 SIMD 的向量型別程式庫 System.Numerics.Vectors 會以 NuGet 套件形式發行。  
  
## <a name="integral-types"></a>整數類資料型別  
 .NET Framework 支援帶正負號和不帶正負號的整數，長度介於 1 到 8 個位元組。 下表列出整數類資料類型和其大小，並指出它們是否帶正負號或不帶正負號，並記錄其範圍。 所有整數都是實值類型。  
  
|類型|帶正負號/不帶正負號|大小 (位元組)|最小值|最大值|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=fullName>|不帶正負號|1|0|255|  
|<xref:System.Int16?displayProperty=fullName>|簽署人|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=fullName>|簽署人|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=fullName>|簽署人|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=fullName>|簽署人|1|-128|127|  
|<xref:System.UInt16?displayProperty=fullName>|不帶正負號|2|0|65,535|  
|<xref:System.UInt32?displayProperty=fullName>|不帶正負號|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=fullName>|不帶正負號|8|0|18,446,744,073,709,551,615|  
  
 每個整數類資料類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 每個整數也包含方法，用以執行相等比較和相對比較、轉換數字的字串表示法為整數以及轉換整數為字串表示法。 除了由標準的運算子所處理的以外，其他數學運算，例如四捨五入和識別兩個整數值的大小，在 <xref:System.Math> 類別中都有提供。 藉由使用 <xref:System.BitConverter> 類別，您也可在整數值中使用個別位元。  
  
 請注意不帶正負號的整數類資料類型並不符合 CLS 標準。 如需詳細資訊，請參閱[語言獨立性以及與語言無關的元件](../../docs/standard/language-independence-and-language-independent-components.md)。  
  
## <a name="floating-point-types"></a>浮點類型  
 .NET Framework 包含三個基本浮點類型，如下表所列。  
  
|類型|大小 (以位元組為單位)|最低|最大值|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=fullName>|8|-1.79769313486232e308|1.79769313486232e308|  
|<xref:System.Single?displayProperty=fullName>|4|-3.402823e38|3.402823e38|  
|<xref:System.Decimal?displayProperty=fullName>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 每個浮點類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 這每一個都包含方法，用以執行相等比較和相對比較、轉換浮點數的字串表示法以及轉換浮點數為字串表示法。 某些額外的數學、代數和三角函數運算都由 <xref:System.Math> 類別提供。 藉由使用 <xref:System.BitConverter> 類別，您也可使用 <xref:System.Double> 和 <xref:System.Single> 中的個別位元。 <xref:System.Decimal?displayProperty=fullName> 結構有它自己的方法，為 <xref:System.Decimal.GetBits%2A?displayProperty=fullName> 和 <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=fullName>，用於使用十進位值的個別位元，而且還有一組自己的方法，用於執行一些額外的數學運算。  
  
 <xref:System.Double> 和 <xref:System.Single> 類型主要供本質上並不精確的值使用 (例如太陽系中兩顆星之間的距離)，並且供不需較高有效位數和較小進位誤差的應用程式使用。 在需要較高精確度且不想要進位誤差的情況下，您應該使用 <xref:System.Decimal?displayProperty=fullName> 類型。  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=fullName> 是不可變的類型，表示任意大的整數，其值在理論上沒有上限或下限。 <xref:System.Numerics.BigInteger> 類型的方法與其他整數類資料類型的方法極為相似。  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex> 類型代表複數，也就是具有實部和虛部的數字。 它支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子，以及數學、代數和三角函數方法。  
  
## <a name="simd-enabled-vector-types"></a>啟用 SIMD 的向量類型  
 <xref:System.Numerics> 命名空間包含一組適用於 .NET Framework 之支援 SIMD 的向量型別。 SIMD (Single Instruction Multiple Data 作業) 允許在硬體層級平行處理某些作業，因此會大幅提升對向量執行計算的數學、科學和圖形應用程式效能。  
  
 以下是 .NET Framework 之啟用 SIMD 的向量類型。  此外，System.Numerics.Vectors 還包含 Plane 類型和 Quaternion 類型。  
  
-   <xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 及 <xref:System.Numerics.Vector4> 型別，這些是 <xref:System.Single> 類型的 2 維、3 維及 4 維向量。  
  
-   兩種矩陣型別：代表 3x2 矩陣的 <xref:System.Numerics.Matrix3x2> 和代表 4x4 矩陣的 <xref:System.Numerics.Matrix4x4>。  
  
-   <xref:System.Numerics.Plane> 和 <xref:System.Numerics.Quaternion> 型別。  
  
 啟用 SimD 的向量類型會在 IL 中實作，使其能在未啟用 SimD 的硬體和 JIT 編譯器上使用。 若要利用 SIMD 指令，您必須使用 .NET Framework 4.6 隨附適用於 Managed 程式碼的新 64 位元 JIT 編譯器，來編譯 64 位元應用程式；當以 x64 處理器為目標時，它會加入 SIMD 支援。  
  
 SIMD 也可做為 [NuGet 套件](http://www.nuget.org/packages/System.Numerics.Vectors)下載。  NuGet 套件也包含泛型 <xref:System.Numerics.Vector%601> 結構，此結構可讓您建立任何基本數值型別的向量。 (基本數值類型包含 <xref:System> 命名空間中 <xref:System.Decimal> 以外的所有數值類型)。此外，<xref:System.Numerics.Vector%601> 結構還提供可供您在使用向量時呼叫的便利方法程式庫。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式基本概念](../../docs/standard/application-essentials.md)
