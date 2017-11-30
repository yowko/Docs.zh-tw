---
title: "在.NET 中的類型轉換表"
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a>在.NET 中的類型轉換表
將一種類型的值轉換成另一種大小相等或較大類型的值時，就會發生擴展轉換。 將一種類型的值轉換成另一種大小較小類型的值時，就會發生縮小轉換。 本主題中的表格將說明這兩種轉換類型的行為。  
  
## <a name="widening-conversions"></a>擴展轉換  
 下表描述可以執行而不遺失資訊的擴展轉換。  
  
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
  
 某些擴展轉換為<xref:System.Single>或<xref:System.Double>可能會導致失去精確度。 下表描述有時會導致資訊遺失的擴展轉換。  
  
|類型|可轉換類型|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>縮小轉換  
 若要縮小轉換<xref:System.Single>或<xref:System.Double>可能會造成資訊遺失。 如果目標類型無法正確表示來源的範圍，產生的類型會設定為常數 `PositiveInfinity` 或 `NegativeInfinity`。 `PositiveInfinity`來自除以零的正數值的結果，並也會傳回時的值<xref:System.Single>或<xref:System.Double>超出值`MaxValue`欄位。 `NegativeInfinity`來自是負數值除以零的結果，並也會傳回時的值<xref:System.Single>或<xref:System.Double>低於的值`MinValue`欄位。 從轉換<xref:System.Double>至<xref:System.Single>可能會導致`PositiveInfinity`或`NegativeInfinity`。  
  
 縮小轉換也可能會導致其他資料類型的資訊遺失。 不過，<xref:System.OverflowException>如果正在轉換類型的值超出目標類型所指定的範圍，會擲回`MaxValue`和`MinValue`欄位，並轉換由要確保目標值的執行階段檢查型別不會超過其`MaxValue`或`MinValue`。 轉換執行之<xref:System.Convert?displayProperty=nameWithType>類別一律會以這種方式檢查。  
  
 下表列出會擲回的轉換<xref:System.OverflowException>使用<xref:System.Convert?displayProperty=nameWithType>或任何核取轉換轉換類型的值時產生的型別定義的範圍之外。  
  
|類型|可轉換類型|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>、<xref:System.UInt16>、<xref:System.UInt32><xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Convert?displayProperty=nameWithType>  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
