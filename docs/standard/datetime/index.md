---
title: "日期、時間和時區 | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "日期和時間資料 [.NET Framework]"
  - "時間 [.NET Framework], 時區"
  - "時區物件 [.NET Framework]"
  - "時區 [.NET Framework]"
  - "時間 [.NET Framework], 時區"
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 日期、時間和時區
除了基本 <xref:System.DateTime> 結構之外，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 還提供下列支援使用時區的類別：  
  
-   <xref:System.TimeZone>  
  
     使用這個類別搭配系統的本地時區及 Coordinated Universal Time \(UTC\) 時區。<xref:System.TimeZone> 類別的功能大致上已由 <xref:System.TimeZoneInfo> 類別替代。  
  
-   <xref:System.TimeZoneInfo>  
  
     使用這個類別搭配系統上預先定義的任何時區、建立新時區，以及在各時區之間輕鬆轉換日期和時間。  在開發新程式時，請使用 <xref:System.TimeZoneInfo> 類別而非 <xref:System.TimeZone> 類別。  
  
-   <xref:System.DateTimeOffset>  
  
     使用這個結構搭配已知與 UTC 之間偏移 \(或差異\) 的日期和時間。  <xref:System.DateTimeOffset> 結構會將日期和時間值，以及該時間與 UTC 之間的偏移組合在一起。  基於該時間與 UTC 之間的關聯性，個別日期和時間值會明確識別單一時間點。  如此可讓 <xref:System.DateTimeOffset> 值比 <xref:System.DateTime> 值更容易在電腦之間移動。  
  
 本文這一節提供您使用時區和建立時區感知應用程式 \(即可在時區之間轉換日期和時間的應用程式\) 所需的資訊。  
  
## 在本節中  
 [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)  
 討論建立時區感知應用程式時涉及的術語、概念與問題。  
  
 [在 DateTime、DateTimeOffset、 TimeSpan 和  TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)  
 討論搭配日期和時間資料時，使用 <xref:System.DateTime>、<xref:System.DateTimeOffset> 和 <xref:System.TimeZoneInfo> 型別的時機。  
  
 [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)  
 描述如何列舉本機系統上找到的時區。  
  
 [如何：列舉電腦上展示的時區](../../../docs/standard/datetime/enumerate-time-zones.md)  
 提供範例，這些範例會列舉電腦登錄中定義的時區，並讓使用者從清單中選取預先定義的時區。  
  
 [如何：存取預先定義的 UTC 和本機時區物件](../../../docs/standard/datetime/access-utc-and-local.md)  
 描述如何存取 Coordinated Universal Time 和本機時區。  
  
 [如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)  
 描述如何從本機系統登錄中將 <xref:System.TimeZoneInfo> 物件執行個體化。  
  
 [具現化 DateTimeOffset 物件](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)  
 討論可執行個體化 <xref:System.DateTimeOffset> 物件的方式，以及可將 <xref:System.DateTime> 值轉換成 <xref:System.DateTimeOffset> 的方式。  
  
 [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)  
 描述如何建立不支援日光節約時間轉換的自訂時區。  
  
 [如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)  
 描述如何建立支援一個或多個日光節約時間轉換的自訂時區。  
  
 [儲存和還原時區](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)  
 描述 <xref:System.TimeZoneInfo> 對於序列化和還原序列化時區資料的支援，並說明一些可以使用這些功能的情節。  
  
 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)  
 描述如何建立自訂時區以及將其資訊儲存到資源檔中。  
  
 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)  
 描述如何執行個體化儲存到內嵌資源檔的自訂時區。  
  
 [使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md)  
 討論加、減及比較 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值涵蓋的問題。  
  
 [如何：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)  
 討論如何執行日期和時間算術，以反映出時區的調整規則。  
  
 [在 DateTime 和 DateTimeOffset 之間轉換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)  
 描述如何在 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值之間轉換。  
  
 [在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)  
 描述如何在時區之間轉換。  
  
 [如何：解決模稜兩可的時間](../../../docs/standard/datetime/resolve-ambiguous-times.md)  
 描述如何藉由對應時區的標準時間來解析不明確的時間。  
  
 [如何：讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)  
 描述如何讓使用者決定不明確的本機時間與 Coordinated Universal Time 之間的對應。  
  
## 參考  
 <xref:System.TimeZoneInfo?displayProperty=fullName>