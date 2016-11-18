---
title: "類型轉換表"
description: "類型轉換表"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d602f260-e7cf-49c8-a37f-731f40e4a538
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 16f38150f26b477de5685d2d3b0ef18afb94c236

---

# <a name="type-conversion-tables"></a>類型轉換表

將一種類型的值轉換成另一種大小相等或較大類型的值時，就會發生擴展轉換。 將一種類型的值轉換成另一種大小較小類型的值時，就會發生縮小轉換。 本主題中的表格將說明這兩種轉換類型的行為。

## <a name="widening-conversions"></a>擴展轉換

類型 | 不會造成資料遺失的可轉換類型
---- | -------------------------------------
[Byte](xref:System.Byte) | [UInt16](xref:System.UInt16)、[Int16](xref:System.Int16)、[UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[SByte](xref:System.SByte) | [Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int16](xref:System.Int16) | [Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[UInt16](xref:System.UInt16) | [UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Char](xref:System.Char) | [UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int32](xref:System.Int32) | [Int64](xref:System.Int64)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[UInt32](xref:System.UInt32) | [Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int64](xref:System.Int64) | [Decimal](xref:System.Decimal)
[UInt64](xref:System.UInt64) | [Decimal](xref:System.Decimal)
[Single](xref:System.Single) | [Double](xref:System.Double)

某些轉換成 [Single](xref:System.Single) 或 [Double](xref:System.Double) 的擴展轉換可能會導致失去精確度。 下表描述有時會導致資訊遺失的擴展轉換。

類型 | 可轉換類型
---- | -------------------
[Int32](xref:System.Int32) | [Single](xref:System.Single)
[UInt32](xref:System.UInt32) | [Single](xref:System.Single)
[Int64](xref:System.Int64) | [Single](xref:System.Single)、[Double](xref:System.Double)
[UInt64](xref:System.UInt64) | [Single](xref:System.Single)、[Double](xref:System.Double)
[Decimal](xref:System.Decimal) | [Single](xref:System.Single)、[Double](xref:System.Double)

## <a name="narrowing-conversions"></a>縮小轉換

某些轉換成 [Single](xref:System.Single) 或 [Double](xref:System.Double) 的縮小轉換可能會導致資訊遺失。 如果目標類型無法正確表示來源的範圍，產生的類型會設定為常數 `PositiveInfinity` 或 `NegativeInfinity`。 `PositiveInfinity` 是正數除以零所得的結果；當 [Single](xref:System.Single) 或 [Double](xref:System.Double) 的值超過 `MaxValue` 欄位的值時，也會傳回此值。 `NegativeInfinity`是負數除以零所得的結果；當 [Single](xref:System.Single) 或 [Double](xref:System.Double) 的值低於 `MinValue` 欄位的值時，也會傳回此值。 從 [Double](xref:System.Double) 轉換為 [Single](xref:System.Single) 可能會導致 `PositiveInfinity` 或 `NegativeInfinity`。

縮小轉換也可能會導致其他資料類型的資訊遺失。 不過，如果所轉換之類型的值超出目標類型的 `MaxValue` 和 `MinValue` 欄位所指定的範圍，而且執行階段已檢查轉換，確定目標類型的值未超過其 `MaxValue` 或 `MinValue`，則會擲回 [OverflowException](xref:System.OverflowException)。 使用 [System.Convert](xref:System.Convert) 類別執行的轉換永遠是以這種方式進行檢查。

下表列出使用 [System.Convert](xref:System.Convert) 時擲回 [OverflowException](xref:System.OverflowException) 的轉換，或所轉換之類型的值超出為產生類型所定義的範圍時的任何已檢查轉換。

類型 | 可轉換類型
---- | -------------------
[Byte](xref:System.Byte) | [SByte](xref:System.SByte)
[SByte](xref:System.SByte) | [Byte](xref:System.Byte)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)
[Int16](xref:System.Int16) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[UInt16](xref:System.UInt16)
[UInt16](xref:System.UInt16) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)
[Int32](xref:System.Int32) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)
[UInt32](xref:System.UInt32) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)
[Int64](xref:System.Int64) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)
[UInt64](xref:System.UInt64) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)
[Decimal](xref:System.Decimal) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)
[Single](xref:System.Single) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)
[Double](xref:System.Double) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)

## <a name="see-also"></a>另請參閱

[System.Convert](xref:System.Convert)

[類型轉換](type-conversion.md)




<!--HONumber=Nov16_HO3-->


