---
title: "尋找定義於本機系統的時區"
description: "尋找定義於本機系統的時區"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="72e65-104">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="72e65-104">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="72e65-105">[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別不會公開公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="72e65-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not expose a public constructor.</span></span> <span data-ttu-id="72e65-106">如此一來，`new` 關鍵字不能用來建立新的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="72e65-106">As a result, the `new` keyword cannot be used to create a new [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="72e65-107">相反地，[TimeZoneInfo](xref:System.TimeZoneInfo) 物件的具現化方式是從作業系統擷取預先定義時區的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="72e65-107">Instead, [TimeZoneInfo](xref:System.TimeZoneInfo) objects are instantiated by retrieving information on predefined time zones from the operating system.</span></span> <span data-ttu-id="72e65-108">本主題討論如何從作業系統所儲存的資料來具現化時區。</span><span class="sxs-lookup"><span data-stu-id="72e65-108">This topic discusses instantiating a time zone from data stored by the operating system.</span></span> <span data-ttu-id="72e65-109">此外，[TimeZoneInfo](xref:System.TimeZoneInfo) 類別的 `static` (在 Visual Basic 中為 `Shared`) 屬性提供國際標準時間 (UTC) 及當地時區的存取。</span><span class="sxs-lookup"><span data-stu-id="72e65-109">In addition, `static` (`Shared` in Visual Basic) properties of the [TimeZoneInfo](xref:System.TimeZoneInfo) class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="72e65-110">存取個別時區</span><span class="sxs-lookup"><span data-stu-id="72e65-110">Accessing Individual Time Zones</span></span>

<span data-ttu-id="72e65-111">[TimeZoneInfo](xref:System.TimeZoneInfo) 類別提供兩個預先定義的時區物件，該物件代表 UTC 時間和當地時區。</span><span class="sxs-lookup"><span data-stu-id="72e65-111">The [TimeZoneInfo](xref:System.TimeZoneInfo) class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="72e65-112">它們分別從 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 和 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性所提供。</span><span class="sxs-lookup"><span data-stu-id="72e65-112">They are available from the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) and [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) properties, respectively.</span></span> <span data-ttu-id="72e65-113">如需存取 UTC 或當地時區的指示，請參閱[如何：存取預先定義的 UTC 和當地時區物件](access-utc-and-local.md)。</span><span class="sxs-lookup"><span data-stu-id="72e65-113">For instructions on accessing the UTC or local time zones, see [How to: access the predefined UTC and local time zone objects](access-utc-and-local.md).</span></span> 

<span data-ttu-id="72e65-114">您也可以具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，該物件代表作業系統所定義的任何時區。</span><span class="sxs-lookup"><span data-stu-id="72e65-114">You can also instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents any time zone defined by the operating system.</span></span> <span data-ttu-id="72e65-115">如需特定時區物件具現化的指示，請參閱[如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="72e65-115">For instructions on instantiating a specific time zone object, see [How to: instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="72e65-116">時區識別項</span><span class="sxs-lookup"><span data-stu-id="72e65-116">Time Zone Identifiers</span></span>

<span data-ttu-id="72e65-117">時區識別項是唯一識別時區的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="72e65-117">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="72e65-118">雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。</span><span class="sxs-lookup"><span data-stu-id="72e65-118">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="72e65-119">在大部分情況下，其值會對應到 [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) 屬性，用來提供時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="72e65-119">In most cases, its value corresponds to the [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="72e65-120">不過仍有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="72e65-120">However, there are exceptions.</span></span> <span data-ttu-id="72e65-121">若要確定您提供了有效的識別項，最好是列舉系統上可用的時區，並記下其相關聯的識別項。</span><span class="sxs-lookup"><span data-stu-id="72e65-121">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span> <span data-ttu-id="72e65-122">如需列舉時區的指示，請參閱[如何：列舉電腦上展示的時區](enumerate-time-zones.md)。</span><span class="sxs-lookup"><span data-stu-id="72e65-122">For instructions on enumerating time zones, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72e65-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72e65-123">See Also</span></span>

[<span data-ttu-id="72e65-124">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="72e65-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="72e65-125">如何：存取預先定義的 UTC 及當地時區物件</span><span class="sxs-lookup"><span data-stu-id="72e65-125">How to: access the predefined UTC and local time zone objects</span></span>](access-utc-and-local.md)

[<span data-ttu-id="72e65-126">如何：具現化 TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="72e65-126">How to: instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)

[<span data-ttu-id="72e65-127">如何：列舉電腦上既有的時區</span><span class="sxs-lookup"><span data-stu-id="72e65-127">How to: enumerate time zones present on a computer</span></span>](enumerate-time-zones.md)

[<span data-ttu-id="72e65-128">轉換各時區的時間</span><span class="sxs-lookup"><span data-stu-id="72e65-128">Converting times between time zones</span></span>](converting-between-time-zones.md)
