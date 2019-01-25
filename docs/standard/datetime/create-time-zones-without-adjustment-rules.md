---
title: HOW TO：建立沒有調整規則的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681712"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="3c280-102">HOW TO：建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3c280-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="3c280-103">應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：</span><span class="sxs-lookup"><span data-stu-id="3c280-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="3c280-104">永遠不會在本機系統登錄中定義時區。</span><span class="sxs-lookup"><span data-stu-id="3c280-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="3c280-105">已修改或從登錄中移除時區相關的資料。</span><span class="sxs-lookup"><span data-stu-id="3c280-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="3c280-106">時區存在，但並沒有特定的歷程記錄時間會調整時區的精確資訊。</span><span class="sxs-lookup"><span data-stu-id="3c280-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="3c280-107">在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。</span><span class="sxs-lookup"><span data-stu-id="3c280-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="3c280-108">您可以使用此方法的多載來建立時間的時區，或沒有調整規則。</span><span class="sxs-lookup"><span data-stu-id="3c280-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="3c280-109">如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。</span><span class="sxs-lookup"><span data-stu-id="3c280-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="3c280-110">(如需這些詞彙的定義，請參閱 < 時區詞彙 > 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)</span><span class="sxs-lookup"><span data-stu-id="3c280-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c280-111">藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="3c280-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="3c280-112">相反地，存取他們只能透過所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="3c280-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="3c280-113">本主題說明如何建立沒有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="3c280-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="3c280-114">若要建立支援日光節約時間調整規則的時區，請參閱[How to:建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="3c280-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="3c280-115">若要建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3c280-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="3c280-116">定義時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3c280-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="3c280-117">顯示名稱會遵循相當標準的格式 Coordinated Universal Time (UTC) 時區的位移以括弧括住且後面跟著識別時區，一或多個城市的時區，或其中一個或多個 cou 的字串ntries 或時區中的區域。</span><span class="sxs-lookup"><span data-stu-id="3c280-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="3c280-118">定義時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c280-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="3c280-119">一般而言，這個字串也做時區的識別項。</span><span class="sxs-lookup"><span data-stu-id="3c280-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="3c280-120">如果您想要使用不同的識別碼，與時區的標準名稱，定義的時區識別項。</span><span class="sxs-lookup"><span data-stu-id="3c280-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="3c280-121">具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。</span><span class="sxs-lookup"><span data-stu-id="3c280-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="3c280-122">時間會晚於 UTC 的時區有正面的位移。</span><span class="sxs-lookup"><span data-stu-id="3c280-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="3c280-123">與時間早於 UTC 的時區有負數位移。</span><span class="sxs-lookup"><span data-stu-id="3c280-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="3c280-124">呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>方法具現化新的時區。</span><span class="sxs-lookup"><span data-stu-id="3c280-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="3c280-125">範例</span><span class="sxs-lookup"><span data-stu-id="3c280-125">Example</span></span>

<span data-ttu-id="3c280-126">下列範例會定義茂遜，南極大陸，沒有調整規則的自訂時區。</span><span class="sxs-lookup"><span data-stu-id="3c280-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="3c280-127">將字串指派到<xref:System.TimeZoneInfo.DisplayName%2A>屬性會遵循標準格式與 UTC 的時區時差後面時區的好記的描述。</span><span class="sxs-lookup"><span data-stu-id="3c280-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3c280-128">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3c280-128">Compiling the code</span></span>

<span data-ttu-id="3c280-129">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3c280-129">This example requires:</span></span>

* <span data-ttu-id="3c280-130">對 System.Core.dll 的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="3c280-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="3c280-131">下列命名空間會匯入：</span><span class="sxs-lookup"><span data-stu-id="3c280-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="3c280-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c280-132">See also</span></span>

- [<span data-ttu-id="3c280-133">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="3c280-133">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="3c280-134">時區概觀</span><span class="sxs-lookup"><span data-stu-id="3c280-134">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="3c280-135">如何：建立有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3c280-135">How to: Create time zones with adjustment rules</span></span>](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
