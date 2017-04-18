---
title: ".NET Framework 中的類型轉換表 | Microsoft Docs"
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
  - "擴展轉換"
  - "縮小轉換"
  - "類型轉換，資料表"
  - "轉換類型，縮小轉換"
  - "轉換類型，放大轉換"
  - "基底類型，轉換"
  - "資料表 [.NET Framework]，類型轉換"
  - "資料類型 [.NET Framework]，轉換"
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework 中的類型轉換表
將一種型別的值轉換成另一種大小相等或較大型別的值時，會發生擴展轉換。  將一種型別的值轉換成另一種較小型別的值時，則會發生縮小轉換。  這個主題中的表格將說明這兩種轉換型別的行為。  
  
## 擴展轉換  
 下表說明不會造成資訊遺失的可執行擴展轉換。  
  
|型別|不會造成資料遺失的可轉換型別|  
|--------|--------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 有些擴展成 <xref:System.Single> 或 <xref:System.Double> 的轉換可能會造成精確度降低。  下表說明偶爾會造成資訊遺失的擴展轉換。  
  
|型別|可轉換型別|  
|--------|-----------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## 縮小轉換  
 縮小成 <xref:System.Single> 或 <xref:System.Double> 的轉換可能會造成資訊遺失。  如果目標型別無法正確表示來源的範圍，則結果型別會設定為常數 `PositiveInfinity` 或 `NegativeInfinity`。  `PositiveInfinity` 是將正數除以零的結果，而且當 <xref:System.Single> 或 <xref:System.Double> 的值超過 `MaxValue` 欄位的值時也會傳回此值。  `NegativeInfinity` 是將負數除以零的結果，而且當 <xref:System.Single> 或 <xref:System.Double> 的值低於 `MinValue` 欄位的值時，也會傳回此值。  從 <xref:System.Double> 轉換為 <xref:System.Single> 可能會導致 `PositiveInfinity` 或 `NegativeInfinity`。  
  
 對於其他資料型別而言，縮小轉換也可能造成資訊遺失。  但是，如果所轉換之型別的值超出目標型別的 `MaxValue` 和 `MinValue` 欄位所指定的範圍，而且執行階段已檢查轉換，確定目標型別的值未超過其 `MaxValue` 或 `MinValue`，則會擲回 <xref:System.OverflowException>。  使用 <xref:System.Convert?displayProperty=fullName> 類別執行的轉換永遠是以這種方式進行檢查。  
  
 下表列出使用 <xref:System.Convert?displayProperty=fullName> 時會擲回 <xref:System.OverflowException> 的轉換，或如果所轉換之型別的值超出結果型別所定義的範圍時的任何會檢查的轉換。  
  
|型別|可轉換型別|  
|--------|-----------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## 請參閱  
 <xref:System.Convert?displayProperty=fullName>   
 [.NET Framework 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)