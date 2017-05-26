---
title: "日期、時間和時區 | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a6e7e748f67cf9d2dbfe5dd9bb9b14ecf2d8c331
ms.contentlocale: zh-tw
ms.lasthandoff: 05/05/2017

---

# <a name="dates-times-and-time-zones"></a>日期、時間和時區

.NET 除了提供基本的 <xref:System.DateTime> 結構，還提供下列支援處理時區的類別：

* <xref:System.TimeZone>

  使用這個類別，以處理系統的當地時區和國際標準時間 (UTC) 區域。<xref:System.TimeZone> 類別的功能大部分都已被 <xref:System.TimeZoneInfo> 類別取代。

* <xref:System.TimeZoneInfo>

  使用此類別可搭配系統上預先定義的任何時區建立新的時區，以及將一個時區的日期和時間輕鬆轉換到另一個時區。 對於新的開發，請使用 <xref:System.TimeZoneInfo> 類別而不是 <xref:System.TimeZone> 類別。

* <xref:System.DateTimeOffset>

  使用這個結構，來處理與 UTC 的位移 (或差異) 已知的日期和時間。 <xref:System.DateTimeOffset> 結構會合併日期和時間值和該時間與 UTC 的位移。 基於其與 UTC 的關聯性，個別日期和時間值會明確地識別單一時間點。 這可讓 <xref:System.DateTimeOffset> 值從某部電腦到另一部電腦的可攜性優於 <xref:System.DateTime> 值。

文件的這一節提供使用時區以及建立可轉換不同時區之日期和時間的時區感知應用程式所需的資訊。

## <a name="in-this-section"></a>本節內容

[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
 討論有關建立時區感知應用程式的術語、概念和問題。

[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)
 討論在處理日期和時間資料時，使用 <xref:System.DateTime>、<xref:System.DateTimeOffset> 和 <xref:System.TimeZoneInfo> 類型的時機。

[尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
 描述如何列舉在本機系統上找到的時區。

[操作說明：列舉電腦上既有的時區](../../../docs/standard/datetime/enumerate-time-zones.md)
 提供列舉電腦登錄中所定義的時區，以及讓使用者從清單中選取預先定義時區的範例。

[操作說明：存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)
 描述如何存取國際標準時間和當地時區。

[操作說明：將 TimeZoneInfo 物件具現化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
 描述如何從本機系統登錄具現化 <xref:System.TimeZoneInfo> 物件。

[具現化 DateTimeOffset 物件](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)
 討論可以具現化 <xref:System.DateTimeOffset> 物件的方式，以及 <xref:System.DateTime> 值可以轉換為 <xref:System.DateTimeOffset> 值的方式。

[操作說明：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
 描述如何建立不支援日光節約時間轉換的自訂時區。

[操作說明：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
 描述如何建立支援一或多種日光節約時間轉換的自訂時區。

[儲存和還原時區](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)
 描述 <xref:System.TimeZoneInfo> 對時區資料之序列化和還原序列化的支援，並說明可使用這些功能的一些案例。

[操作說明：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
 描述如何建立自訂時區，並將它的資訊儲存在資源檔中。

[操作說明：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
 描述如何具現化已儲存至內嵌資源檔的自訂時區。

[使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md)
 討論如何加上、減去和比較 <xref:System.DateTime> 與 <xref:System.DateTimeOffset> 值的相關問題。

[操作說明：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
 討論如何執行反映時區調整規則的日期和時間運算。

[在 DateTime 與 DateTimeOffset 之間轉換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)
 描述如何在 <xref:System.DateTime> 與 <xref:System.DateTimeOffset> 值之間轉換。

[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)
 描述如何將時間從某個時區轉換為另一個時區。

[操作說明：解決模稜兩可的時間](../../../docs/standard/datetime/resolve-ambiguous-times.md)
 描述如何將模稜兩可的時間對應至時區標準時間來解決模稜兩可的時間。

[操作說明：讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
 描述如何讓使用者決定模稜兩可的當地時間與國際標準時間之間的對應。

## <a name="reference"></a>參考資料

<xref:System.TimeZoneInfo?displayProperty=fullName>
