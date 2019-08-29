---
title: 作法：建立沒有調整規則的時區
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
ms.openlocfilehash: 510112c8b19ec002d1dcf918eb983b55dee68fd0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106661"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="75da8-102">作法：建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="75da8-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="75da8-103">應用程式所需的精確時區資訊可能因下列幾個原因而不存在於特定系統上:</span><span class="sxs-lookup"><span data-stu-id="75da8-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="75da8-104">本機系統的登錄中從未定義過時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="75da8-105">已從登錄中修改或移除時區的相關資料。</span><span class="sxs-lookup"><span data-stu-id="75da8-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="75da8-106">時區存在, 但沒有特定歷程記錄期間之時區調整的精確資訊。</span><span class="sxs-lookup"><span data-stu-id="75da8-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="75da8-107">在這些情況下, 您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法來定義應用程式所需的時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="75da8-108">您可以使用這個方法的多載來建立具有或不含調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="75da8-109">如果時區支援日光節約時間, 您可以使用固定或浮動調整規則來定義調整。</span><span class="sxs-lookup"><span data-stu-id="75da8-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="75da8-110">(如需這些詞彙的定義, 請參閱時區[總覽](../../../docs/standard/datetime/time-zone-overview.md)中的「時區詞彙」一節)。</span><span class="sxs-lookup"><span data-stu-id="75da8-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75da8-111">藉由呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法所建立的自訂時間區域不會新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="75da8-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="75da8-112">相反地, 它們只能透過<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫所傳回的物件參考來存取。</span><span class="sxs-lookup"><span data-stu-id="75da8-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="75da8-113">本主題說明如何建立沒有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="75da8-114">若要建立支援日光節約時間調整規則的時區, 請參閱[如何:建立具有調整規則](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)的時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="75da8-115">建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="75da8-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="75da8-116">定義時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="75da8-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="75da8-117">顯示名稱遵循相當標準的格式, 其中時區與國際標準時間 (UTC) 的位移會括在括弧中, 後面接著可識別時區的字串、時區中的一或多個城市, 或一或多個 cou時區中的 ntries 或區域。</span><span class="sxs-lookup"><span data-stu-id="75da8-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="75da8-118">定義時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="75da8-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="75da8-119">通常, 這個字串也會當做時區的識別碼使用。</span><span class="sxs-lookup"><span data-stu-id="75da8-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="75da8-120">如果您想要使用與時區標準名稱不同的識別碼, 請定義時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="75da8-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="75da8-121">具現化物件, 其定義時區與 UTC 的位移。 <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="75da8-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="75da8-122">時間與 UTC 時間較晚的時區具有正位移。</span><span class="sxs-lookup"><span data-stu-id="75da8-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="75da8-123">具有早于 UTC 時間的時區具有負位移。</span><span class="sxs-lookup"><span data-stu-id="75da8-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="75da8-124"><xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>呼叫方法, 以具現化新的時區。</span><span class="sxs-lookup"><span data-stu-id="75da8-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="75da8-125">範例</span><span class="sxs-lookup"><span data-stu-id="75da8-125">Example</span></span>

<span data-ttu-id="75da8-126">下列範例會定義茂遜, 南極洲的自訂時區, 此時區沒有調整規則。</span><span class="sxs-lookup"><span data-stu-id="75da8-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="75da8-127">指派給<xref:System.TimeZoneInfo.DisplayName%2A>屬性的字串會遵循標準格式, 其中時區與 UTC 的位移後面會接著時區的易記描述。</span><span class="sxs-lookup"><span data-stu-id="75da8-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="75da8-128">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="75da8-128">Compiling the code</span></span>

<span data-ttu-id="75da8-129">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="75da8-129">This example requires:</span></span>

- <span data-ttu-id="75da8-130">匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="75da8-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="75da8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75da8-131">See also</span></span>

- [<span data-ttu-id="75da8-132">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="75da8-132">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="75da8-133">時區概觀</span><span class="sxs-lookup"><span data-stu-id="75da8-133">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="75da8-134">如何：建立具有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="75da8-134">How to: Create time zones with adjustment rules</span></span>](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
