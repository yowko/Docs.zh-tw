---
title: "日期、時間和時區"
description: "日期、時間和時區"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 76e6cacc-1c0c-4a71-8cb8-018c112385ba
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: a4d0a68ac32c3d722a1479ca2b067892fd88bf52

---

# <a name="dates-times-and-time-zones"></a>日期、時間和時區

除了基本 [System.DateTime](xref:System.DateTime) 結構之外，.NET 還會提供下列支援處理時區的類別：

* [System.TimeZoneInfo](xref:System.TimeZoneInfo)
    
  使用這個類別，以處理系統的當地時區和國際標準時間 (UTC) 區域。
  
* [System.DateTimeOffset](xref:System.DateTimeOffset)  

  使用這個結構，來處理與 UTC 的位移 (或差異) 已知的日期和時間。 [DateTimeOffset](xref:System.DateTimeOffset)] 結構會合併日期和時間值與該時間與 UTC 的位移。 基於其與 UTC 的關聯性，個別日期和時間值會明確地識別單一時間點。 這可讓 [DateTimeOffset](xref:System.DateTimeOffset)] 值從某部電腦到另一部電腦的可攜性優於 [DateTime](xref:System.DateTime)] 值。 
  
文件的這一節提供使用時區以及建立可轉換不同時區之日期和時間的時區感知應用程式所需的資訊。

## <a name="in-this-section"></a>本章節內容

[時區概觀](time-zone-overview.md) - 討論有關建立時區感知應用程式的術語、概念和問題。
    
[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](choosing-between-datetime.md) - 討論在處理日期和時間資料時何時使用 [System.DateTime](xref:System.DateTime)、[System.DateTimeOffset](xref:System.DateTimeOffset) 和 [System.TimeZoneInfo](xref:System.TimeZoneInfo) 類型。
    
[尋找定義於本機系統的時區](finding-the-time-zones-on-local-system.md) - 描述如何列舉本機系統上找到的時區。

[具現化 DateTimeOffset 物件](instantiating-a-datetimeoffset-object.md) - 討論可以具現化 [System.DateTimeOffset](xref:System.DateTimeOffset) 物件的方式，以及 [System.DateTime](xref:System.DateTime) 值可以轉換為 [System.DateTimeOffset](xref:System.DateTimeOffset) 值的方式。

[使用日期和時間執行算術運算](performing-arithmetic-operations.md) - 討論如何加上、減去和比較 [System.DateTime](xref:System.DateTime) 與 [System.DateTimeOffset](xref:System.DateTimeOffset) 值的相關問題。

[在 DateTime 與 DateTimeOffset 之間轉換](converting-between-datetime-and-offset.md) - 描述如何在 [System.DateTime](xref:System.DateTime) 與 [System.DateTimeOffset](xref:System.DateTimeOffset) 值之間轉換。

[在各時區間轉換時間](converting-between-time-zones.md) - 描述如何將時間從某個時區轉換為另一個時區。

[如何：列舉電腦上展示的時區](enumerate-time-zones.md) - 提供範例，以列舉電腦登錄中所定義的時區，並讓使用者從清單中選取預先定義的時區。

[如何：存取預先定義的 UTC 和當地時區物件](access-utc-and-local.md) - 描述如何存取國際標準時間和當地時區。

[如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md) - 描述如何從本機系統登錄具現化 [System.TimeZoneInfo](xref:System.TimeZoneInfo) 物件。

[如何：在日期和時間運算中使用時區](use-time-zones-in-arithmetic.md) - 討論如何執行反映時區調整規則的日期和時間運算。

[如何：解決模稜兩可的時間](resolve-ambiguous-times.md) - 描述如何將模稜兩可的時間對應至時區標準時間來解決模稜兩可的時間。

[如何：讓使用者解決模稜兩可的時間](let-users-resolve-ambiguous-times.md) - 描述如何讓使用者決定模稜兩可的當地時間與國際標準時間之間的對應。

## <a name="reference"></a>參考資料

[System.TimeZoneInfo](xref:System.TimeZoneInfo)

[System.DateTimeOffset](xref:System.DateTimeOffset)

[System.DateTime](xref:System.DateTime)



<!--HONumber=Nov16_HO1-->


