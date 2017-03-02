---
title: ".NET Core 中的數值"
description: ".NET Core 中的數值"
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6b8696be-55f5-4b66-98f3-69ff827c2c49
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 8e2aad830bdaccad6e8184fa462dd0d3157fd6c9
ms.lasthandoff: 03/02/2017

---

# <a name="numerics-in-net-core"></a>.NET Core 中的數值

.NET Core 支援標準數值整數和浮點數基本類型，以及沒有理論上限或下限的 [System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger) 整數類型、表示複數的 [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex) 類型和 [System.Numerics](https://docs.microsoft.com/dotnet/core/api/System.Numerics) 命名空間中一組啟用單指令多資料 ([SIMD](https://en.wikipedia.org/wiki/SIMD)) 的向量類型。 

## <a name="integral-types"></a>整數類資料型別

.NET Core 支援帶正負號和不帶正負號的整數，其長度介於&1; 到&8; 個位元組。 下表列出整數類資料類型和其大小，並指出它們是否帶正負號或不帶正負號，並記錄其範圍。 所有整數都是實值類型。 

類型 | 帶正負號/不帶正負號 | 大小 (位元組) | 最小值 | 最大值
---- | --------------- | ------------ | ------------- | -------------
[System.Byte](https://docs.microsoft.com/dotnet/core/api/System.Byte) | 不帶正負號 | 1 | 0 | 255
[System.Int16](https://docs.microsoft.com/dotnet/core/api/System.Int16) | 簽署人 | 2 | -32,768 | 32,767
[System.Int32](https://docs.microsoft.com/dotnet/core/api/System.Int32) | 簽署人 | 4 | -2,147,483,648 | 2,147,483,647
[System.Int64](https://docs.microsoft.com/dotnet/core/api/System.Int64) | 簽署人 | 8 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807
[System.SByte](https://docs.microsoft.com/dotnet/core/api/System.SByte) | 簽署人 | 1 | -128 | 127
[System.UInt16](https://docs.microsoft.com/dotnet/core/api/System.UInt16) | 不帶正負號 | 2 | 0 | 65,535
[System.UInt32](https://docs.microsoft.com/dotnet/core/api/System.UInt32) | 不帶正負號 | 4 | 0 | 4,294,967,295
[System.UInt64](https://docs.microsoft.com/dotnet/core/api/System.UInt64) | 不帶正負號 | 8 | 0 | 18,446,744,073,709,551,615

每個整數類資料類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 每個整數也包含方法，用以執行相等比較和相對比較、轉換數字的字串表示法為整數以及轉換整數為字串表示法。 除了由標準運算子所處理以外的某些其他數學運算，例如四捨五入和識別兩個整數值的大小，在 [System.Math](https://docs.microsoft.com/dotnet/core/api/System.Math) 類別中都有提供。 藉由使用 [System.BitConverter](https://docs.microsoft.com/dotnet/core/api/System.BitConverter) 類別，您也可在整數值中使用個別位元。 
     
請注意不帶正負號的整數類資料類型並不符合 CLS 標準。 如需詳細資訊，請參閱 [.NET 一般類型系統和 Common Language Specification](common-type-system.md)。

## <a name="floating-point-types"></a>浮點類型

.NET Core 包含三個基本浮點類型，如下表所列。 

類型 | 大小 (位元組) | 最小值 | 最大值
---- | ------------ | ------------- | -------------
[System.Double](https://docs.microsoft.com/dotnet/core/api/System.Double) | 8 | -1.79769313486232e308 | 1.79769313486232e308
[System.Single](https://docs.microsoft.com/dotnet/core/api/System.Single) | 4 | -3.402823e38 | 3.402823e38
[System.Decimal](https://docs.microsoft.com/dotnet/core/api/System.Decimal) | 16 | -79,228,162,514,264,337,593,543,950,335 | 79,228,162,514,264,337,593,543,950,335
   
每個浮點類型支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子。 這每一個都包含方法，用以執行相等比較和相對比較、轉換浮點數的字串表示法以及轉換浮點數為字串表示法。 某些額外的數學、代數和三角函數運算都由 `Math` 類別提供。 藉由使用 `BitConverter` 類別，您也可使用 `Double` 和 `Single` 中的個別位元。 `Decimal` 結構有它自己的方法，為 `Decimal.GetBits` 和 `Decimal.Decimal(Int32())`，用於使用十進位值的個別位元，而且還有一組自己的方法，用於執行一些額外的數學運算。 

`Double` 和 `Single` 類型主要供本質上並不精確的值使用 (例如太陽系中兩顆星之間的距離)，並且供不需較高有效位數和較小進位誤差的應用程式使用。 在需要較高精確度且不想要進位誤差的情況下，您應該使用 `Decimal` 類型。

## <a name="biginteger"></a>BigInteger

[System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger) 是不可變的類型，表示任意大的整數，其值在理論上沒有上限或下限。 `BigInteger` 類型的方法與其他整數類資料類型的方法極為相似。  

## <a name="complex"></a>Complex

[System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex) 類型代表複數，也就是具有實數和虛數的數字。 它支援一組標準的算術、比較、等號比較、明確轉換和隱含轉換的運算子，以及數學、代數和三角函數方法。 

## <a name="simd-enabled-vector-types"></a>啟用 SIMD 的向量類型

`System.Numerics` 命名空間包含一組針對 .NET Core 的向量類型，該類型已啟用 SIMD 。 SIMD 允許在硬體層級上平行處理某些作業，因此會大幅提升對向量執行計算的數學、科學和圖形應用程式效能。 

以下是 .NET Core 中已啟用 SIMD 的向量類型： 

* [System.Numerics.Vector2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector2)、[System.Numerics.Vector3](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector3) 和 [System.Numerics.Vector4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector4) 類型是 `Single` 類型的二維、三維和四維向量。

* [向量&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector-1) 結構可讓您建立任何基本數值類型的向量。 (基本數值類型包含 System 命名空間中 Decimal 以外的所有數值類型)。

* 有兩個矩陣類型，代表 3x2 矩陣的 [System.Numerics.Matrix3x2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix3x2)，以及代表 4x4 矩陣的 [System.Numerics.Matrix4x4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix4x4)。 

* [System.Numerics.Plane](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Plane) 類型代表三維平面，而 [System.Numerics.Quaternion](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Quaternion) 類型代表用來編碼三維實體旋轉的向量。

