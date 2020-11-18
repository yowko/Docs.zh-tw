---
title: 作法：建立沒有調整規則的時區
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 411a0c0b581830a45a986216681ca2800a9a4c42
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817987"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="1eeae-102">作法：建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="1eeae-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="1eeae-103">應用程式所需的精確時區資訊可能不會出現在特定的系統上，有許多原因：</span><span class="sxs-lookup"><span data-stu-id="1eeae-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="1eeae-104">本機系統的登錄中從未定義過時區。</span><span class="sxs-lookup"><span data-stu-id="1eeae-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="1eeae-105">已從登錄中修改或移除有關時區的資料。</span><span class="sxs-lookup"><span data-stu-id="1eeae-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="1eeae-106">時區存在，但沒有特定歷程記錄期間時區調整的精確資訊。</span><span class="sxs-lookup"><span data-stu-id="1eeae-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="1eeae-107">在這些情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法來定義應用程式所需的時區。</span><span class="sxs-lookup"><span data-stu-id="1eeae-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="1eeae-108">您可以使用這個方法的多載，建立具有或不含調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="1eeae-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="1eeae-109">如果時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整。</span><span class="sxs-lookup"><span data-stu-id="1eeae-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="1eeae-110"> (如需這些詞彙的定義，請參閱 [時區總覽](time-zone-overview.md)中的「時區術語」一節。 ) </span><span class="sxs-lookup"><span data-stu-id="1eeae-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1eeae-111">藉由呼叫方法建立的自訂時區， <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會新增至登錄中。</span><span class="sxs-lookup"><span data-stu-id="1eeae-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="1eeae-112">相反地，只能透過方法呼叫所傳回的物件參考來存取它們 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1eeae-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="1eeae-113">本主題說明如何建立沒有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="1eeae-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="1eeae-114">若要建立支援日光節約時間調整規則的時區，請參閱 [如何：建立具有調整規則的時區](create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="1eeae-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="1eeae-115">建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="1eeae-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="1eeae-116">定義時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1eeae-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="1eeae-117">顯示名稱會遵循相當標準的格式，在此格式中，國際標準時間 (UTC) 的時區時差會以括弧括住，後面接著可識別時區的字串、時區中的一或多個城市，或時區中的一或多個國家或地區。</span><span class="sxs-lookup"><span data-stu-id="1eeae-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="1eeae-118">定義時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="1eeae-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="1eeae-119">一般而言，此字串也會當做時區的識別碼使用。</span><span class="sxs-lookup"><span data-stu-id="1eeae-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="1eeae-120">如果您想要使用與時區標準名稱不同的識別碼，請定義時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="1eeae-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="1eeae-121">具現化 <xref:System.TimeSpan> 物件，該物件定義時區與 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="1eeae-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="1eeae-122">時間晚于 UTC 的時區具有正數位移。</span><span class="sxs-lookup"><span data-stu-id="1eeae-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="1eeae-123">時間早于 UTC 時間的時區具有負位移。</span><span class="sxs-lookup"><span data-stu-id="1eeae-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="1eeae-124">呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> 方法，以將新的時區具現化。</span><span class="sxs-lookup"><span data-stu-id="1eeae-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="1eeae-125">範例</span><span class="sxs-lookup"><span data-stu-id="1eeae-125">Example</span></span>

<span data-ttu-id="1eeae-126">下列範例會定義茂遜，南極洲的自訂時區，此時區沒有調整規則。</span><span class="sxs-lookup"><span data-stu-id="1eeae-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="1eeae-127">指派給屬性的字串 <xref:System.TimeZoneInfo.DisplayName%2A> 會遵循標準格式，也就是時區與 UTC 之間的時差，後面接著時區的易記描述。</span><span class="sxs-lookup"><span data-stu-id="1eeae-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1eeae-128">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1eeae-128">Compiling the code</span></span>

<span data-ttu-id="1eeae-129">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1eeae-129">This example requires:</span></span>

- <span data-ttu-id="1eeae-130">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1eeae-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="1eeae-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="1eeae-131">See also</span></span>

- [<span data-ttu-id="1eeae-132">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="1eeae-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="1eeae-133">時區概觀</span><span class="sxs-lookup"><span data-stu-id="1eeae-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="1eeae-134">如何：建立具有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="1eeae-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
