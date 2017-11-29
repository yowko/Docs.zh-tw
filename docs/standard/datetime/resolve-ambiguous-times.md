---
title: "如何： 解決模稜兩可的時間"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="4ff3e-102">如何： 解決模稜兩可的時間</span><span class="sxs-lookup"><span data-stu-id="4ff3e-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="4ff3e-103">不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="4ff3e-104">發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="4ff3e-105">處理不明確的時間時，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4ff3e-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="4ff3e-106">假設如何將時間對應至 UTC。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="4ff3e-107">例如，您可以假設不明確的時間一律是以時區的標準時間表示。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="4ff3e-108">如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="4ff3e-109">本主題說明如何解決模稜兩可的時間所假設代表時區的標準時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="4ff3e-110">將不明確的時間對應至時區標準時間</span><span class="sxs-lookup"><span data-stu-id="4ff3e-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="4ff3e-111">呼叫<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>方法，以判斷時間是否模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="4ff3e-112">如果模稜兩可的時間，減去的時間從<xref:System.TimeSpan>傳回時區的物件<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="4ff3e-113">呼叫`static`(`Shared`在 Visual Basic.NET)<xref:System.DateTime.SpecifyKind%2A>方法，以設定的 UTC 日期和時間值的<xref:System.DateTime.Kind%2A>屬性<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="4ff3e-114">範例</span><span class="sxs-lookup"><span data-stu-id="4ff3e-114">Example</span></span>

<span data-ttu-id="4ff3e-115">下列範例說明如何將模稜兩可的時間轉換成 UTC 的假設代表本地時區的標準時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="4ff3e-116">此範例包含名為的方法`ResolveAmbiguousTime`，決定是否<xref:System.DateTime>傳遞給它的值模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="4ff3e-117">如果值為模稜兩可，則方法會傳回<xref:System.DateTime>值，表示對應的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="4ff3e-118">方法會藉由減去本地時區的值來處理這項轉換<xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性從本地時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="4ff3e-119">一般情況下，模稜兩可的時間由呼叫<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>方法來擷取陣列<xref:System.TimeSpan>物件，其中包含可能模稜兩可的時間的 UTC 位移。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="4ff3e-120">不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="4ff3e-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>屬性傳回 UTC 時區的標準時間之間的位移。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="4ff3e-122">在此範例中，所有參考的當地時區都透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性; 區域永遠不會指派給物件變數的本機時間。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="4ff3e-123">這是建議的作法，因為呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法會導致無效的當地時區指派給任何物件。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="4ff3e-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4ff3e-124">Compiling the code</span></span>

<span data-ttu-id="4ff3e-125">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4ff3e-125">This example requires:</span></span>

* <span data-ttu-id="4ff3e-126">對 system.core.dll 的參考無法加入至專案。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="4ff3e-127">確認<xref:System>以匯入命名空間`using`陳述式 （C# 程式碼所需）。</span><span class="sxs-lookup"><span data-stu-id="4ff3e-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ff3e-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ff3e-128">See also</span></span>

<span data-ttu-id="4ff3e-129">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[如何： 讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="4ff3e-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
