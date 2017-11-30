---
title: "日期、時間和時區"
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e85fc8eac25cc6fdfb8cb3aaa77318019695c51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="e7dc4-102">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="e7dc4-102">Dates, times, and time zones</span></span>

<span data-ttu-id="e7dc4-103">除了基本 <xref:System.DateTime> 結構之外，.NET 還會提供下列支援處理時區的類別：</span><span class="sxs-lookup"><span data-stu-id="e7dc4-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="e7dc4-104">使用這個類別，以處理系統的當地時區和國際標準時間 (UTC) 區域。<xref:System.TimeZone> 類別的功能大部分都已被 <xref:System.TimeZoneInfo> 類別取代。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="e7dc4-105">使用此類別可搭配系統上預先定義的任何時區建立新的時區，以及將一個時區的日期和時間輕鬆轉換到另一個時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="e7dc4-106">在開發新程式時，請使用 <xref:System.TimeZoneInfo> 類別而非 <xref:System.TimeZone> 類別。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="e7dc4-107">使用這個結構，來處理與 UTC 的位移 (或差異) 已知的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="e7dc4-108"><xref:System.DateTimeOffset> 結構會合併日期和時間值與該時間與 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="e7dc4-109">基於其與 UTC 的關聯性，個別日期和時間值會明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="e7dc4-110">這可讓 <xref:System.DateTimeOffset> 值從某部電腦到另一部電腦的可攜性優於 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="e7dc4-111">文件的這一節提供使用時區以及建立可轉換不同時區之日期和時間的時區感知應用程式所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e7dc4-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7dc4-112">In this section</span></span>

<span data-ttu-id="e7dc4-113">[時區概觀](../../../docs/standard/datetime/time-zone-overview.md) - 討論有關建立時區感知應用程式的術語、概念和問題。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="e7dc4-114">[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md) - 討論在處理日期和時間資料時何時使用 <xref:System.DateTime>、<xref:System.DateTimeOffset> 和 <xref:System.TimeZoneInfo> 類型。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="e7dc4-115">[尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) - 描述如何列舉在本機系統上找到的時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="e7dc4-116">[如何：列舉電腦上既有的時區](../../../docs/standard/datetime/enumerate-time-zones.md)提供範例，以列舉電腦登錄中所定義的時區，並讓使用者從清單中選取預先定義的時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="e7dc4-117">[如何：存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md) - 描述如何存取國際標準時間和當地時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="e7dc4-118">[如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md) - 描述如何從本機系統登錄具現化 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="e7dc4-119">[具現化 DateTimeOffset 物件](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) - 討論可以具現化 <xref:System.DateTimeOffset> 物件的方式，以及 <xref:System.DateTime> 值可以轉換為 <xref:System.DateTimeOffset> 值的方式。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="e7dc4-120">[如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) - 描述如何建立不支援日光節約時間轉換的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="e7dc4-121">[如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) - 描述如何建立支援一或多種日光節約時間轉換的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="e7dc4-122">[儲存和還原時區](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) - 描述 <xref:System.TimeZoneInfo> 對時區資料之序列化和還原序列化的支援，並說明可使用這些功能的一些案例。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="e7dc4-123">[如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) - 描述如何建立自訂時區，並將它的資訊儲存在資源檔中。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="e7dc4-124">[如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) - 描述如何具現化已儲存至內嵌資源檔的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="e7dc4-125">[使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md) - 討論如何加上、減去和比較 <xref:System.DateTime> 與 <xref:System.DateTimeOffset> 值的相關問題。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="e7dc4-126">[如何：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) - 討論如何執行反映時區調整規則的日期和時間運算。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="e7dc4-127">[在 DateTime 和 DateTimeOffset 之間轉換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) - 描述如何在 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="e7dc4-128">[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md) - 描述如何將時間從某個時區轉換為另一個時區。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="e7dc4-129">[如何：解決不明確的時間](../../../docs/standard/datetime/resolve-ambiguous-times.md) - 描述如何將不明確的時間對應至時區的標準時間，來解決不明確的時間問題。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="e7dc4-130">[如何：讓使用者解決不明確的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) - 描述如何讓使用者決定不明確的當地時間與國際標準時間之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="e7dc4-131">參考資料</span><span class="sxs-lookup"><span data-stu-id="e7dc4-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
