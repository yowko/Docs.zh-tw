---
title: HOW TO：解決模稜兩可的時間
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106776"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="69269-102">作法：解決模稜兩可的時間</span><span class="sxs-lookup"><span data-stu-id="69269-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="69269-103">不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。</span><span class="sxs-lookup"><span data-stu-id="69269-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="69269-104">發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。</span><span class="sxs-lookup"><span data-stu-id="69269-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="69269-105">處理不明確的時間時，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="69269-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="69269-106">假設如何將時間對應至 UTC。</span><span class="sxs-lookup"><span data-stu-id="69269-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="69269-107">例如，您可以假設不明確的時間一律是以時區的標準時間表示。</span><span class="sxs-lookup"><span data-stu-id="69269-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="69269-108">如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。</span><span class="sxs-lookup"><span data-stu-id="69269-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="69269-109">本主題說明如何藉由假設它代表時區的標準時間來解決不明確的時間。</span><span class="sxs-lookup"><span data-stu-id="69269-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="69269-110">將不明確的時間對應至時區標準時間</span><span class="sxs-lookup"><span data-stu-id="69269-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="69269-111"><xref:System.TimeZoneInfo.IsAmbiguousTime%2A>呼叫方法來判斷時間是否不明確。</span><span class="sxs-lookup"><span data-stu-id="69269-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="69269-112">如果時間不明確, 請從時區的<xref:System.TimeSpan> <xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性所傳回的物件減去時間。</span><span class="sxs-lookup"><span data-stu-id="69269-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="69269-113"><xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.DateTime.Kind%2A> <xref:System.DateTime.SpecifyKind%2A>呼叫 (在`Shared` Visual Basic .net 中) 方法, 將 UTC 日期和時間值的屬性設定為。 `static`</span><span class="sxs-lookup"><span data-stu-id="69269-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="69269-114">範例</span><span class="sxs-lookup"><span data-stu-id="69269-114">Example</span></span>

<span data-ttu-id="69269-115">下列範例說明如何藉由假設它代表當地時區的標準時間, 將不明確的時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="69269-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="69269-116">此範例包含名為`ResolveAmbiguousTime`的方法, 可判斷傳遞給它的<xref:System.DateTime>值是否不明確。</span><span class="sxs-lookup"><span data-stu-id="69269-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="69269-117">如果此值不明確, 則方法<xref:System.DateTime>會傳回代表對應 UTC 時間的值。</span><span class="sxs-lookup"><span data-stu-id="69269-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="69269-118">方法會藉由從本地時間減去當地時區的<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性值來處理這項轉換。</span><span class="sxs-lookup"><span data-stu-id="69269-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="69269-119">通常不明確的時間是藉由呼叫<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>方法來抓取<xref:System.TimeSpan>物件陣列, 其中包含不明確時間的可能 UTC 位移。</span><span class="sxs-lookup"><span data-stu-id="69269-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="69269-120">不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。</span><span class="sxs-lookup"><span data-stu-id="69269-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="69269-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性會傳回 UTC 與時區標準時間之間的位移。</span><span class="sxs-lookup"><span data-stu-id="69269-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="69269-122">在此範例中, 會透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性來建立本機時區的所有參考, 而當地時區永遠不會指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="69269-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="69269-123">這是建議的作法, 因為呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法會使指派當地時區的任何物件失效。</span><span class="sxs-lookup"><span data-stu-id="69269-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="69269-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="69269-124">Compiling the code</span></span>

<span data-ttu-id="69269-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="69269-125">This example requires:</span></span>

- <span data-ttu-id="69269-126">使用語句匯入的<xref:System>命名空間 (在程式碼C#中為必要項)。 `using`</span><span class="sxs-lookup"><span data-stu-id="69269-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="69269-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69269-127">See also</span></span>

- [<span data-ttu-id="69269-128">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="69269-128">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="69269-129">如何：讓使用者解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="69269-129">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
