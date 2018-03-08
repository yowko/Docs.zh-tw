---
title: ".NET 中的類型轉換表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e741de47fec5f0ed607bba33b963d449c5c51cce
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="type-conversion-tables-in-net"></a>.NET 中的類型轉換表
將一種類型的值轉換成另一種大小相等或較大類型的值時，就會發生擴展轉換。 將一種類型的值轉換成另一種大小較小類型的值時，就會發生縮小轉換。 本主題中的表格將說明這兩種轉換類型的行為。  
  
## <a name="widening-conversions"></a>擴展轉換  
 下表描述可執行且不會導致資訊遺失的擴展轉換。  
  
|類型|不會造成資料遺失的可轉換類型|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>、<xref:System.UInt64>、<xref:System.Double><xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 某些轉換成 <xref:System.Single> 或 <xref:System.Double> 的擴展轉換可能會導致失去精確度。 下表描述有時會導致資訊遺失的擴展轉換。  
  
|類型|可轉換類型|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 某些轉換成 <xref:System.Single> 或 <xref:System.Double> 的縮小轉換可能會導致資訊遺失。 如果目標類型無法正確表示來源的範圍，產生的類型會設定為常數 `PositiveInfinity` 或 `NegativeInfinity`。 `PositiveInfinity` 是正數除以零所得的結果；當 <xref:System.Single> 或 <xref:System.Double> 的值超過 `MaxValue` 欄位的值時，也會傳回此值。 `NegativeInfinity` 是負數除以零所得的結果；當 <xref:System.Single> 或 <xref:System.Double> 的值低於 `MinValue` 欄位的值時，也會傳回此值。 從 <xref:System.Double> 轉換為 <xref:System.Single> 可能會導致 `PositiveInfinity` 或 `NegativeInfinity`。  
  
 縮小轉換也可能會導致其他資料類型的資訊遺失。 不過，如果所轉換類型的值超出目標類型的 `MaxValue` 和 `MinValue` 欄位所指定的範圍，而且執行階段已檢查轉換，確定目標類型的值未超過其 `MaxValue` 或 `MinValue`，則會擲回 <xref:System.OverflowException>。 使用 <xref:System.Convert?displayProperty=nameWithType> 類別執行的轉換永遠都會以這種方式進行檢查。  
  
 下表列出使用 <xref:System.Convert?displayProperty=nameWithType> 擲回 <xref:System.OverflowException> 的轉換，或所轉換類型的值超出為產生類型所定義的範圍時的任何已檢查轉換。  
  
|類型|可轉換類型|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>、<xref:System.UInt16>、<xref:System.UInt32><xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Convert?displayProperty=nameWithType>  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
