---
title: 尋找定義於本機系統的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65798c46b01bb7a702559d685590ecf7a6f2793
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098285"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="9c23a-102">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="9c23a-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="9c23a-103"><xref:System.TimeZoneInfo> 類別不會公開公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="9c23a-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="9c23a-104">如此一來，`new` 關鍵字不能用來建立新的 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="9c23a-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="9c23a-105">相反地，<xref:System.TimeZoneInfo> 物件可從登錄擷取預先定義時區的詳細資訊，或建立自訂的時區來具現化。</span><span class="sxs-lookup"><span data-stu-id="9c23a-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="9c23a-106">本主題討論從儲存在登錄中的資料具現化時區。</span><span class="sxs-lookup"><span data-stu-id="9c23a-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="9c23a-107">此外，<xref:System.TimeZoneInfo> 類別的 `static` (在 Visual Basic 中為 `shared`) 屬性提供國際標準時間 (UTC) 及當地時區的存取。</span><span class="sxs-lookup"><span data-stu-id="9c23a-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="9c23a-108">對於在登錄中未定義的時區，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法的多載來建立自訂時區。</span><span class="sxs-lookup"><span data-stu-id="9c23a-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="9c23a-109">建立自訂的時區中會討論[如何： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)並[如何： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9c23a-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="9c23a-110">此外，您可以在序列化字串中使用 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法還原 <xref:System.TimeZoneInfo> 物件，對其具現化。</span><span class="sxs-lookup"><span data-stu-id="9c23a-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="9c23a-111">序列化和還原序列化<xref:System.TimeZoneInfo>物件中所提及[如何： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)並[如何： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9c23a-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="9c23a-112">存取個別時區</span><span class="sxs-lookup"><span data-stu-id="9c23a-112">Accessing individual time zones</span></span>

<span data-ttu-id="9c23a-113"><xref:System.TimeZoneInfo> 類別提供兩個預先定義的時區物件，該物件代表 UTC 時間和當地時區。</span><span class="sxs-lookup"><span data-stu-id="9c23a-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="9c23a-114">它們分別由 <xref:System.TimeZoneInfo.Utc%2A> 和 <xref:System.TimeZoneInfo.Local%2A> 屬性所提供。</span><span class="sxs-lookup"><span data-stu-id="9c23a-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="9c23a-115">如需存取 UTC 或當地時區的指示，請參閱 <<c0> [ 如何： 存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)。</span><span class="sxs-lookup"><span data-stu-id="9c23a-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="9c23a-116">您也可以具現化 <xref:System.TimeZoneInfo> 物件，該物件代表在登錄中所定義的任何時區。</span><span class="sxs-lookup"><span data-stu-id="9c23a-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="9c23a-117">如需特定時區物件具現化的指示，請參閱 <<c0> [ 如何： 將 TimeZoneInfo 物件具現化](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="9c23a-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="9c23a-118">時區識別項</span><span class="sxs-lookup"><span data-stu-id="9c23a-118">Time zone identifiers</span></span>

<span data-ttu-id="9c23a-119">時區識別項是唯一識別時區的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="9c23a-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="9c23a-120">雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。</span><span class="sxs-lookup"><span data-stu-id="9c23a-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="9c23a-121">在大部分情況下，其值會對應到 <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> 屬性，用來提供時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c23a-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="9c23a-122">不過仍有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9c23a-122">However, there are exceptions.</span></span> <span data-ttu-id="9c23a-123">若要確定您提供了有效的識別項，最好是列舉系統上可用的時區，並記下其相關聯的識別項。</span><span class="sxs-lookup"><span data-stu-id="9c23a-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c23a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c23a-124">See also</span></span>

- [<span data-ttu-id="9c23a-125">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="9c23a-125">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="9c23a-126">操作說明：存取預先定義的 UTC 和當地時區物件</span><span class="sxs-lookup"><span data-stu-id="9c23a-126">How to: Access the predefined UTC and local time zone objects</span></span>](../../../docs/standard/datetime/access-utc-and-local.md)
- [<span data-ttu-id="9c23a-127">操作說明：將 TimeZoneInfo 物件具現化</span><span class="sxs-lookup"><span data-stu-id="9c23a-127">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [<span data-ttu-id="9c23a-128">在各時區間轉換時間</span><span class="sxs-lookup"><span data-stu-id="9c23a-128">Converting times between time zones</span></span>](../../../docs/standard/datetime/converting-between-time-zones.md)
