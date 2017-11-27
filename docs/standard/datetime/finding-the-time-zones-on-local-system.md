---
title: "尋找定義於本機系統的時區"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="681a6-102">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="681a6-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="681a6-103"><xref:System.TimeZoneInfo> 類別不會公開公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="681a6-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="681a6-104">如此一來，`new` 關鍵字不能用來建立新的 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="681a6-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="681a6-105">相反地，<xref:System.TimeZoneInfo> 物件可從登錄擷取預先定義時區的詳細資訊，或建立自訂的時區來具現化。</span><span class="sxs-lookup"><span data-stu-id="681a6-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="681a6-106">本主題討論從儲存在登錄中的資料具現化時區。</span><span class="sxs-lookup"><span data-stu-id="681a6-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="681a6-107">此外，<xref:System.TimeZoneInfo> 類別的 `static` (在 Visual Basic 中為 `shared`) 屬性提供國際標準時間 (UTC) 及當地時區的存取。</span><span class="sxs-lookup"><span data-stu-id="681a6-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="681a6-108">對於在登錄中未定義的時區，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法的多載來建立自訂時區。</span><span class="sxs-lookup"><span data-stu-id="681a6-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="681a6-109">建立自訂時區中討論[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)主題。</span><span class="sxs-lookup"><span data-stu-id="681a6-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="681a6-110">此外，您可以在序列化字串中使用 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法還原 <xref:System.TimeZoneInfo> 物件，對其具現化。</span><span class="sxs-lookup"><span data-stu-id="681a6-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="681a6-111">序列化和還原序列化<xref:System.TimeZoneInfo>物件述[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)主題。</span><span class="sxs-lookup"><span data-stu-id="681a6-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="681a6-112">存取個別時區</span><span class="sxs-lookup"><span data-stu-id="681a6-112">Accessing individual time zones</span></span>

<span data-ttu-id="681a6-113"><xref:System.TimeZoneInfo> 類別提供兩個預先定義的時區物件，該物件代表 UTC 時間和當地時區。</span><span class="sxs-lookup"><span data-stu-id="681a6-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="681a6-114">它們分別由 <xref:System.TimeZoneInfo.Utc%2A> 和 <xref:System.TimeZoneInfo.Local%2A> 屬性所提供。</span><span class="sxs-lookup"><span data-stu-id="681a6-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="681a6-115">如需存取 UTC 或本地時區的指示，請參閱[如何： 存取預先定義的 UTC 與本地時間區域物件](../../../docs/standard/datetime/access-utc-and-local.md)。</span><span class="sxs-lookup"><span data-stu-id="681a6-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="681a6-116">您也可以具現化 <xref:System.TimeZoneInfo> 物件，該物件代表在登錄中所定義的任何時區。</span><span class="sxs-lookup"><span data-stu-id="681a6-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="681a6-117">如需特定時區物件具現化的指示，請參閱[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="681a6-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="681a6-118">時區識別項</span><span class="sxs-lookup"><span data-stu-id="681a6-118">Time zone identifiers</span></span>

<span data-ttu-id="681a6-119">時區識別項是唯一識別時區的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="681a6-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="681a6-120">雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。</span><span class="sxs-lookup"><span data-stu-id="681a6-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="681a6-121">在大部分情況下，其值會對應到 <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> 屬性，用來提供時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="681a6-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="681a6-122">不過仍有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="681a6-122">However, there are exceptions.</span></span> <span data-ttu-id="681a6-123">若要確定您提供了有效的識別項，最好是列舉系統上可用的時區，並記下其相關聯的識別項。</span><span class="sxs-lookup"><span data-stu-id="681a6-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="681a6-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="681a6-124">See also</span></span>

<span data-ttu-id="681a6-125">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[如何： 存取預先定義的 UTC 與本地時間區域物件](../../../docs/standard/datetime/access-utc-and-local.md)
[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[轉換時區之間的時間](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="681a6-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
