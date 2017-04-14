---
title: ".NET Framework 中的數值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SIMD"
  - "System.Numerics.Vectors"
  - "向量"
  - "科學運算"
  - "Complex"
  - "數值"
  - "BigInteger"
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework 中的數值
.NET Framework 支援標準數值整數和浮點數基本類型，以及<xref:System.Numerics.BigInteger>，整數型別沒有理論上限或下限，<xref:System.Numerics.Complex>、 表示複數、 類型和一組啟用 SIMD 的向量中的型別<xref:System.Numerics>命名空間。  
  
 此外，System.Numerics.Vectors，啟用 SIMD 的文件庫的 vectory 型別，已發行的 NuGet 封裝。  
  
## <a name="integral-types"></a>整數類資料型別  
 .NET Framework 支援帶正負號和不帶正負號的整數，長度介於&1; 到&8; 個位元組。 下表列出整數類資料類型和其大小，並指出它們是否帶正負號或不帶正負號，並記錄其範圍。 所有整數都是實值類型。  
  
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
  
 每個整數類資料類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 每個整數也包含方法，用以執行相等比較和相對比較、轉換數字的字串表示法為整數以及轉換整數為字串表示法。 由標準的運算子，例如四捨五入和識別兩個整數的小或較大的值都是從處理的以外，其他數學運算<xref:System.Math>類別。 您也可以使用個別的位元整數值中使用<xref:System.BitConverter>類別。  
  
 請注意不帶正負號的整數類資料類型並不符合 CLS 規範。 如需詳細資訊，請參閱[語言獨立性以及與語言無關的元件](../../docs/standard/language-independence-and-language-independent-components.md)。  
  
## <a name="floating-point-types"></a>浮點類型  
 .NET Framework 包含三個基本浮點類型，如下表所列。  
  
|類型|大小 (以位元組為單位)|最低|最大值|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=fullName>|8|-1.79769313486232e308|1.79769313486232e308|  
|<xref:System.Single?displayProperty=fullName>|4|-3.402823e38|3.402823e38|  
|<xref:System.Decimal?displayProperty=fullName>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 每個浮點類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 這每一個都包含方法，用以執行相等比較和相對比較、轉換浮點數的字串表示法以及轉換浮點數為字串表示法。 某些額外的數學、 代數和三角函數運算都由<xref:System.Math>類別。 您也可以使用中的個別位元<xref:System.Double>和<xref:System.Single>藉由使用<xref:System.BitConverter>類別。 <xref:System.Decimal?displayProperty=fullName>結構有它自己的方法， <xref:System.Decimal.GetBits%2A?displayProperty=fullName>和[Decimal.Decimal (Int32\<xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=fullName>，用於使用十進位值的個別位元，還有它自己組方法執行一些額外的數學運算。  
  
 <xref:System.Double>和<xref:System.Single>類型主要用於值並不精確 （例如太陽系中兩顆星之間的距離） 的本質和應用程式是在不需要較高程度的有效位數和較小進位誤差。 您應該使用<xref:System.Decimal?displayProperty=fullName>類型中較高的情況下需要和捨入錯誤並不是，  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=fullName> 是不可變的類型，表示任意大的整數，其值在理論上沒有上限或下限。 方法的<xref:System.Numerics.BigInteger>類型極為相似的其他整數類資料類型。  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex>類型代表複數，也就是使用實數部分和虛數部分。 它支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子，以及數學、代數和三角函數方法。  
  
## <a name="simd-enabled-vector-types"></a>啟用 SIMD 的向量類型  
 <xref:System.Numerics>命名空間包含.NET Framework 的一組啟用 SIMD 的向量型別。 SIMD (Single Instruction Multiple Data 作業) 允許在硬體層級平行處理某些作業，因此會大幅提升對向量執行計算的數學、科學和圖形應用程式效能。  
  
 以下是 .NET Framework 之啟用 SIMD 的向量類型。  此外，System.Numerics.Vectors 還包含 Plane 類型和 Quaternion 類型。  
  
-   <xref:System.Numerics.Vector2>， <xref:System.Numerics.Vector3>，和<xref:System.Numerics.Vector4>類型，也就是 2、 3 和 4 維度類型的向量<xref:System.Single>。  
  
-   兩個矩陣類型<xref:System.Numerics.Matrix3x2>，用來表示一個 3x2 矩陣; 和<xref:System.Numerics.Matrix4x4>，用來表示一個 4x4 矩陣。  
  
-   <xref:System.Numerics.Plane>和<xref:System.Numerics.Quaternion>型別。  
  
 啟用 SimD 的向量類型會在 IL 中實作，使其能在未啟用 SimD 的硬體和 JIT 編譯器上使用。 若要利用 SIMD 指令，您必須使用 .NET Framework 4.6 隨附適用於 Managed 程式碼的新 64 位元 JIT 編譯器，來編譯 64 位元應用程式；當以 x64 處理器為目標時，它會加入 SIMD 支援。  
  
 SIMD 也能下載為[nuget](http://www.nuget.org/packages/System.Numerics.Vectors)。  NuGET 套件也包含泛型<xref:System.Numerics.Vector%601>結構，可讓您建立的任何基本數字型別向量。 (基本數字型別包含在所有數字型別<xref:System>以外的命名空間<xref:System.Decimal>。)此外，<xref:System.Numerics.Vector%601>結構提供便利的方法，您可以在使用向量時呼叫的程式庫。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式基本概念](../../docs/standard/application-essentials.md)