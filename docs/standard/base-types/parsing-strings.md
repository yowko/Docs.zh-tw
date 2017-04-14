---
title: "在 .NET Framework 中剖析字串 | Microsoft Docs"
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
  - "剖析字串，關於剖析字串"
  - "IFormatProvider 介面，剖析字串"
  - "基底類型，剖析字串"
  - "Parse 方法"
  - "剖析字串"
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 在 .NET Framework 中剖析字串
剖析作業會將代表 .NET Framework 基底型別的字串轉換成該基底型別。  例如，剖析作業可用來將字串轉換成浮點數或日期和時間值。  最常用來執行剖析作業的方法是 `Parse` 方法。  因為剖析是格式化的相反操作 \(包含將基底型別轉換成其字串表示\)，所以很多相同的規則和慣例都適用。  就如同格式化使用實作 <xref:System.IFormatProvider> 介面的物件來提供區分文化特性的格式化資訊，剖析也會使用實作 <xref:System.IFormatProvider> 介面的物件來判斷解譯字串表示的方式。  如需詳細資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)。  
  
## 在本節中  
 [剖析數值字串](../../../docs/standard/base-types/parsing-numeric.md)  
 描述如何將字串轉換成 .NET Framework 實值型別 \(Numeric Type\)。  
  
 [剖析日期和時間字串](../../../docs/standard/base-types/parsing-datetime.md)  
 描述如何將字串轉換成 .NET Framework **DateTime** 型別。  
  
 [剖析其他字串](../../../docs/standard/base-types/parsing-other.md)  
 描述如何將字串轉換成 **Char**、**Boolean** 和 **Enum** 型別。  
  
## 相關章節  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 描述基本的格式化概念，例如格式規範和格式提供者 \(Format Provider\)。  
  
 [.NET Framework 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)  
 描述如何轉換型別。  
  
 [基底類型](../../../docs/standard/base-types/index.md)  
 描述可在 .NET Framework 基底型別上執行的常見作業。