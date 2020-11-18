---
title: 作法：讓使用者解決模稜兩可的時間
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: d543db20161057764749210533f35f7c2a1ec81d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817792"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="67073-102">作法：讓使用者解決模稜兩可的時間</span><span class="sxs-lookup"><span data-stu-id="67073-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="67073-103">不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。</span><span class="sxs-lookup"><span data-stu-id="67073-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="67073-104">發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。</span><span class="sxs-lookup"><span data-stu-id="67073-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="67073-105">處理不明確的時間時，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="67073-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="67073-106">如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。</span><span class="sxs-lookup"><span data-stu-id="67073-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="67073-107">假設如何將時間對應至 UTC。</span><span class="sxs-lookup"><span data-stu-id="67073-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="67073-108">例如，您可以假設不明確的時間一律是以時區的標準時間表示。</span><span class="sxs-lookup"><span data-stu-id="67073-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="67073-109">本主題說明如何讓使用者解決不明確的時間。</span><span class="sxs-lookup"><span data-stu-id="67073-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="67073-110">讓使用者解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="67073-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="67073-111">取得使用者的時間和日期輸入。</span><span class="sxs-lookup"><span data-stu-id="67073-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="67073-112">呼叫 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法以判斷時間是否不明確。</span><span class="sxs-lookup"><span data-stu-id="67073-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="67073-113">如果時間不明確，請呼叫 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法來取出物件的陣列 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="67073-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="67073-114">陣列中的每個元素都包含不明確時間可以對應的 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="67073-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="67073-115">讓使用者選取想要的位移。</span><span class="sxs-lookup"><span data-stu-id="67073-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="67073-116">將當地時間減去使用者所選取的位移，以取得 UTC 日期和時間。</span><span class="sxs-lookup"><span data-stu-id="67073-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="67073-117">`static` `Shared` 在 Visual Basic .net) 方法中呼叫 (<xref:System.DateTime.SpecifyKind%2A> ，以將 UTC 日期和時間值的 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="67073-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="67073-118">範例</span><span class="sxs-lookup"><span data-stu-id="67073-118">Example</span></span>

<span data-ttu-id="67073-119">下列範例會提示使用者輸入日期和時間，若其不明確，可讓使用者選取不明確時間所對應的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="67073-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="67073-120">範例程式碼的核心會使用 <xref:System.TimeSpan> 物件陣列來指出不明確時間與 UTC 之間可能的位移。</span><span class="sxs-lookup"><span data-stu-id="67073-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="67073-121">不過，這些位移不可能對使用者具有任何意義。</span><span class="sxs-lookup"><span data-stu-id="67073-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="67073-122">若要釐清位移的意義，程式碼也會註明位移是否代表當地時區的標準時間或其日光節約時間。</span><span class="sxs-lookup"><span data-stu-id="67073-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="67073-123">此程式碼會藉由比較位移與屬性的值，來判斷哪一個時間是標準的，而哪個時間是日光節約時間 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 。</span><span class="sxs-lookup"><span data-stu-id="67073-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="67073-124">這個屬性指出 UTC 與時區標準時間的差異。</span><span class="sxs-lookup"><span data-stu-id="67073-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="67073-125">在此範例中，本地時區的所有參考都是透過屬性進行，而 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 本地時區絕不會指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="67073-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="67073-126">這是建議的作法，因為呼叫 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> 方法會讓本地時區指派的任何物件失效。</span><span class="sxs-lookup"><span data-stu-id="67073-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="67073-127">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="67073-127">Compiling the code</span></span>

<span data-ttu-id="67073-128">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="67073-128">This example requires:</span></span>

- <span data-ttu-id="67073-129"><xref:System>使用 `using` c # 程式碼) 所需的語句來匯入命名空間 (。</span><span class="sxs-lookup"><span data-stu-id="67073-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="67073-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="67073-130">See also</span></span>

- [<span data-ttu-id="67073-131">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="67073-131">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="67073-132">如何：解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="67073-132">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)
