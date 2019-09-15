---
title: 日期、時間和時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991278"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="d14ec-102">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="d14ec-102">Dates, times, and time zones</span></span>

<span data-ttu-id="d14ec-103">除了基本 <xref:System.DateTime> 結構之外，.NET 還會提供下列支援處理時區的類別：</span><span class="sxs-lookup"><span data-stu-id="d14ec-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="d14ec-104">使用這個類別，以處理系統的當地時區和國際標準時間 (UTC) 區域。</span><span class="sxs-lookup"><span data-stu-id="d14ec-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="d14ec-105">類別的功能<xref:System.TimeZone>大部分是<xref:System.TimeZoneInfo>由類別所取代。</span><span class="sxs-lookup"><span data-stu-id="d14ec-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="d14ec-106">使用此類別可搭配系統上預先定義的任何時區建立新的時區，以及將一個時區的日期和時間輕鬆轉換到另一個時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="d14ec-107">在開發新程式時，請使用 <xref:System.TimeZoneInfo> 類別而非 <xref:System.TimeZone> 類別。</span><span class="sxs-lookup"><span data-stu-id="d14ec-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="d14ec-108">使用這個結構，來處理與 UTC 的位移 (或差異) 已知的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="d14ec-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="d14ec-109"><xref:System.DateTimeOffset> 結構會合併日期和時間值與該時間與 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="d14ec-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="d14ec-110">基於其與 UTC 的關聯性，個別日期和時間值會明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="d14ec-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="d14ec-111">這可讓 <xref:System.DateTimeOffset> 值從某部電腦到另一部電腦的可攜性優於 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="d14ec-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="d14ec-112">文件的這一節提供使用時區以及建立可轉換不同時區之日期和時間的時區感知應用程式所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="d14ec-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d14ec-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="d14ec-113">In this section</span></span>

<span data-ttu-id="d14ec-114">[時區概觀](../../../docs/standard/datetime/time-zone-overview.md) - 討論有關建立時區感知應用程式的術語、概念和問題。</span><span class="sxs-lookup"><span data-stu-id="d14ec-114">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="d14ec-115">[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md) - 討論在處理日期和時間資料時何時使用 <xref:System.DateTime>、<xref:System.DateTimeOffset> 和 <xref:System.TimeZoneInfo> 類型。</span><span class="sxs-lookup"><span data-stu-id="d14ec-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="d14ec-116">[尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) - 描述如何列舉在本機系統上找到的時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-116">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="d14ec-117">[如何：列舉電腦](../../../docs/standard/datetime/enumerate-time-zones.md)上的時區提供範例，以列舉電腦登錄中所定義的時區，並讓使用者從清單中選取預先定義的時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-117">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="d14ec-118">[如何：存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)說明如何存取國際標準時間和當地時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-118">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="d14ec-119">[如何：具現化 TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)物件說明如何從本機<xref:System.TimeZoneInfo>系統登錄具現化物件。</span><span class="sxs-lookup"><span data-stu-id="d14ec-119">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="d14ec-120">[具現化 DateTimeOffset 物件](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) - 討論可以具現化 <xref:System.DateTimeOffset> 物件的方式，以及 <xref:System.DateTime> 值可以轉換為 <xref:System.DateTimeOffset> 值的方式。</span><span class="sxs-lookup"><span data-stu-id="d14ec-120">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="d14ec-121">[如何：建立沒有調整規則](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)的時區描述如何建立不支援日光節約時間轉換的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-121">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="d14ec-122">[如何：建立具有調整規則](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)的時區描述如何建立支援一或多個日光節約時間轉換的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-122">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="d14ec-123">[儲存和還原時區](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) - 描述 <xref:System.TimeZoneInfo> 對時區資料之序列化和還原序列化的支援，並說明可使用這些功能的一些案例。</span><span class="sxs-lookup"><span data-stu-id="d14ec-123">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="d14ec-124">[如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)說明如何建立自訂時區，並將其資訊儲存在資源檔中。</span><span class="sxs-lookup"><span data-stu-id="d14ec-124">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="d14ec-125">[如何：從內嵌資源](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)還原時區說明如何具現化已儲存至內嵌資源檔的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-125">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="d14ec-126">[使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md) - 討論如何加上、減去和比較 <xref:System.DateTime> 與 <xref:System.DateTimeOffset> 值的相關問題。</span><span class="sxs-lookup"><span data-stu-id="d14ec-126">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d14ec-127">[如何：使用日期和時間運算](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)中的時區討論如何執行反映時區調整規則的日期和時間運算。</span><span class="sxs-lookup"><span data-stu-id="d14ec-127">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="d14ec-128">[在 DateTime 和 DateTimeOffset 之間轉換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) - 描述如何在 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="d14ec-128">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d14ec-129">[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md) - 描述如何將時間從某個時區轉換為另一個時區。</span><span class="sxs-lookup"><span data-stu-id="d14ec-129">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="d14ec-130">[如何：解決不明確](../../../docs/standard/datetime/resolve-ambiguous-times.md)的時間描述如何藉由將不明確的時間對應至時區的標準時間來加以解決。</span><span class="sxs-lookup"><span data-stu-id="d14ec-130">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="d14ec-131">[如何：讓使用者解決不明確](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)的時間說明如何讓使用者判斷不明確當地時間與國際標準時間之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d14ec-131">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="d14ec-132">參考資料</span><span class="sxs-lookup"><span data-stu-id="d14ec-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
