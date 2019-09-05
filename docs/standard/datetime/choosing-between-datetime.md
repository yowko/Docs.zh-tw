---
title: 在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4eb8c174e70b6761784a5defe12dc8a8a1e42b
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107071"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="543dd-102">在 DateTime、DateTimeOffset、 TimeSpan 和  TimeZoneInfo 之間選擇</span><span class="sxs-lookup"><span data-stu-id="543dd-102">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="543dd-103">使用日期和時間資訊的 .NET 應用程式大不相同，並且可透過數種方式使用該資訊。</span><span class="sxs-lookup"><span data-stu-id="543dd-103">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="543dd-104">日期和時間資訊的較常見用法包含下列一或多項：</span><span class="sxs-lookup"><span data-stu-id="543dd-104">The more common uses of date and time information include one or more of the following:</span></span>

- <span data-ttu-id="543dd-105">只反映日期，使時間資訊不重要。</span><span class="sxs-lookup"><span data-stu-id="543dd-105">To reflect a date only, so that time information is not important.</span></span>

- <span data-ttu-id="543dd-106">只反映時間，使日期資訊不重要。</span><span class="sxs-lookup"><span data-stu-id="543dd-106">To reflect a time only, so that date information is not important.</span></span>

- <span data-ttu-id="543dd-107">反映抽象的日期和時間，這些並不會和特定時間或位置密切相關 (例如大多數國際連鎖的商店在工作日上午 9 點開始營業)。</span><span class="sxs-lookup"><span data-stu-id="543dd-107">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

- <span data-ttu-id="543dd-108">若要從 .NET 外部的來源抓取日期和時間資訊, 通常會將日期和時間資訊儲存成簡單的資料類型。</span><span class="sxs-lookup"><span data-stu-id="543dd-108">To retrieve date and time information from sources outside of .NET, typically where date and time information is stored in a simple data type.</span></span>

- <span data-ttu-id="543dd-109">若要唯一且明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="543dd-109">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="543dd-110">有些應用程式只在主機系統上需要明確的日期和時間；有些則需要在不同系統上都明確 (也就是一個系統上已序列化的日期可以有意義地還原序列化，並且在世界各地的另一個系統上使用)。</span><span class="sxs-lookup"><span data-stu-id="543dd-110">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span>

- <span data-ttu-id="543dd-111">若要保留多個相關時間 (例如要求者的當地時間和 Web 要求的回條之伺服器時間)。</span><span class="sxs-lookup"><span data-stu-id="543dd-111">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

- <span data-ttu-id="543dd-112">若要執行日期和時間運算，且該運算可能有會唯一明確地識別單一時間點的結果。</span><span class="sxs-lookup"><span data-stu-id="543dd-112">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="543dd-113">.Net 包含<xref:System.DateTime>、 <xref:System.DateTimeOffset>、 <xref:System.TimeSpan>和類型,這些都可以用來建立使用日期和時間的應用程式。<xref:System.TimeZoneInfo></span><span class="sxs-lookup"><span data-stu-id="543dd-113">.NET includes the <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, and <xref:System.TimeZoneInfo> types, all of which can be used to build applications that work with dates and times.</span></span>

> [!NOTE]
> <span data-ttu-id="543dd-114">本主題不會<xref:System.TimeZone>討論, 因為它的功能幾乎已完全<xref:System.TimeZoneInfo>納入類別中。</span><span class="sxs-lookup"><span data-stu-id="543dd-114">This topic doesn't discuss <xref:System.TimeZone> because its functionality is almost entirely incorporated in the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="543dd-115">盡可能使用<xref:System.TimeZoneInfo>類別, 而不是<xref:System.TimeZone>類別。</span><span class="sxs-lookup"><span data-stu-id="543dd-115">Whenever possible, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

## <a name="the-datetime-structure"></a><span data-ttu-id="543dd-116">DateTime 結構</span><span class="sxs-lookup"><span data-stu-id="543dd-116">The DateTime structure</span></span>

<span data-ttu-id="543dd-117"><xref:System.DateTime> 值會定義特定的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-117">A <xref:System.DateTime> value defines a particular date and time.</span></span> <span data-ttu-id="543dd-118">它包含<xref:System.DateTime.Kind%2A>屬性, 提供有關該日期和時間所屬時區的有限資訊。</span><span class="sxs-lookup"><span data-stu-id="543dd-118">It includes a <xref:System.DateTime.Kind%2A> property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="543dd-119">由 <xref:System.DateTimeKind> 屬性傳回的 <xref:System.DateTime.Kind%2A> 值，表示 <xref:System.DateTime> 值是否代表當地時間 (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>)、國際標準時間 (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) 或未指定的時間 (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="543dd-119">The <xref:System.DateTimeKind> value returned by the <xref:System.DateTime.Kind%2A> property indicates whether the <xref:System.DateTime> value represents the local time (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Coordinated Universal Time (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), or an unspecified time (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).</span></span>

<span data-ttu-id="543dd-120"><xref:System.DateTime> 結構適用於執行下列項目的應用程式：</span><span class="sxs-lookup"><span data-stu-id="543dd-120">The <xref:System.DateTime> structure is suitable for applications that do the following:</span></span>

- <span data-ttu-id="543dd-121">只使用日期。</span><span class="sxs-lookup"><span data-stu-id="543dd-121">Work with dates only.</span></span>

- <span data-ttu-id="543dd-122">只使用時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-122">Work with times only.</span></span>

- <span data-ttu-id="543dd-123">使用抽象的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-123">Work with abstract dates and times.</span></span>

- <span data-ttu-id="543dd-124">使用遺漏時區資訊的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-124">Work with dates and times for which time zone information is missing.</span></span>

- <span data-ttu-id="543dd-125">只使用 UTC 日期和時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-125">Work with UTC dates and times only.</span></span>

- <span data-ttu-id="543dd-126">從 .NET 外部的來源 (例如 SQL 資料庫) 取出日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="543dd-126">Retrieve date and time information from sources outside of .NET, such as SQL databases.</span></span> <span data-ttu-id="543dd-127">一般而言，這些來源會將日期和時間資訊以和 <xref:System.DateTime> 結構相容的簡單格式儲存。</span><span class="sxs-lookup"><span data-stu-id="543dd-127">Typically, these sources store date and time information in a simple format that is compatible with the <xref:System.DateTime> structure.</span></span>

- <span data-ttu-id="543dd-128">執行日期和時間運算，但關心其一般結果。</span><span class="sxs-lookup"><span data-stu-id="543dd-128">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="543dd-129">例如，在對特定日期和時間加入六個月的加法運算中，該結果是否對日光節約時間進行調整通常並不重要。</span><span class="sxs-lookup"><span data-stu-id="543dd-129">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="543dd-130">除非特定的 <xref:System.DateTime> 值代表 UTC，否則該日期和時間值的可攜性通常是模稜兩可或受限制的。</span><span class="sxs-lookup"><span data-stu-id="543dd-130">Unless a particular <xref:System.DateTime> value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="543dd-131">例如，如果 <xref:System.DateTime> 值代表當地時間，則在該當地時區是可攜式的 (也就是說，如果值在相同時區的另一個系統上還原序列化，則該值仍會明確地識別單一時間點)。</span><span class="sxs-lookup"><span data-stu-id="543dd-131">For example, if a <xref:System.DateTime> value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="543dd-132">在當地時區外， <xref:System.DateTime> 的值可有多重解譯。</span><span class="sxs-lookup"><span data-stu-id="543dd-132">Outside the local time zone, that <xref:System.DateTime> value can have multiple interpretations.</span></span> <span data-ttu-id="543dd-133">如果該值的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則它的可攜性更差：現在它於相同的時區中模稜兩可，即使在第一次序列化的同一個系統上也可能如此。</span><span class="sxs-lookup"><span data-stu-id="543dd-133">If the value's <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="543dd-134">只有當 <xref:System.DateTime> 值代表 UTC 時，該值才會明確地識別單一時間點，無論該值所使用的系統或時區為何。</span><span class="sxs-lookup"><span data-stu-id="543dd-134">Only if a <xref:System.DateTime> value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="543dd-135">當儲存或共用 <xref:System.DateTime> 資料時應該使用 UTC，且 <xref:System.DateTime> 值的 <xref:System.DateTime.Kind%2A> 屬性應該設為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="543dd-135">When saving or sharing <xref:System.DateTime> data, UTC should be used and the <xref:System.DateTime> value's <xref:System.DateTime.Kind%2A> property should be set to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="543dd-136">DateTimeOffset 結構</span><span class="sxs-lookup"><span data-stu-id="543dd-136">The DateTimeOffset structure</span></span>

<span data-ttu-id="543dd-137"><xref:System.DateTimeOffset> 結構代表日期和時間值，以及表示該值與 UTC 差異大小的位移。</span><span class="sxs-lookup"><span data-stu-id="543dd-137">The <xref:System.DateTimeOffset> structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="543dd-138">因此，該值一律明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="543dd-138">Thus, the value always unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="543dd-139"><xref:System.DateTimeOffset> 類型包含 <xref:System.DateTime> 類型的所有功能並感知時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-139">The <xref:System.DateTimeOffset> type includes all of the functionality of the <xref:System.DateTime> type along with time zone awareness.</span></span> <span data-ttu-id="543dd-140">這讓它適合執行下列動作的應用程式:</span><span class="sxs-lookup"><span data-stu-id="543dd-140">This makes it suitable for applications that do the following:</span></span>

- <span data-ttu-id="543dd-141">唯一且明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="543dd-141">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="543dd-142"><xref:System.DateTimeOffset> 類型可用來明確定義「現在」的意義，以記錄交易的時間、記錄系統或應用程式事件的時間以及記錄檔案建立及修改的時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-142">The <xref:System.DateTimeOffset> type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span>

- <span data-ttu-id="543dd-143">執行一般日期和時間運算。</span><span class="sxs-lookup"><span data-stu-id="543dd-143">Perform general date and time arithmetic.</span></span>

- <span data-ttu-id="543dd-144">只要時間已儲存為兩個不同的值或一個結構中的兩個成員，就可保留多個相關時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-144">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="543dd-145"><xref:System.DateTimeOffset> 值的用途比 <xref:System.DateTime> 值的更為普遍。</span><span class="sxs-lookup"><span data-stu-id="543dd-145">These uses for <xref:System.DateTimeOffset> values are much more common than those for <xref:System.DateTime> values.</span></span> <span data-ttu-id="543dd-146">因此對於應用程式開發，應該考慮將 <xref:System.DateTimeOffset> 做為預設的日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="543dd-146">As a result, <xref:System.DateTimeOffset> should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="543dd-147"><xref:System.DateTimeOffset> 值與特定的時區並沒有密切的關係，但可能來自各種不同的時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-147">A <xref:System.DateTimeOffset> value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="543dd-148">為了說明這點，下列範例會列出可和一些 <xref:System.DateTimeOffset> 的值有關的時區 (包括本機的太平洋標準時間)。</span><span class="sxs-lookup"><span data-stu-id="543dd-148">To illustrate this, the following example lists the time zones to which a number of <xref:System.DateTimeOffset> values (including a local Pacific Standard Time) can belong.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

<span data-ttu-id="543dd-149">此輸出顯示在本範例中的每個日期和時間值可屬於至少三個不同時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-149">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="543dd-150">2007 年 6 月 10 日的 <xref:System.DateTimeOffset> 值顯示出若日期和時間值代表日光節約時間，則其相對於 UTC 的位移甚至不一定會對應於起始時區的基底 UTC 位移，或對應於從它的顯示名稱中找到的相對於 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="543dd-150">The <xref:System.DateTimeOffset> value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="543dd-151">這表示因為單一 <xref:System.DateTimeOffset> 的值並不會和時區緊密結合，所以它無法反映與日光節約時間相互轉換的時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-151">This means that, because a single <xref:System.DateTimeOffset> value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="543dd-152">特別是當使用日期和時間運算來管理 <xref:System.DateTimeOffset> 值的時候，這會有問題。</span><span class="sxs-lookup"><span data-stu-id="543dd-152">This can be particularly problematic when date and time arithmetic is used to manipulate a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="543dd-153">(如需在考慮時區調整規則的方式下該如何執行日期和時間運算的討論，請參閱 [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)。)</span><span class="sxs-lookup"><span data-stu-id="543dd-153">(For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md).)</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="543dd-154">TimeSpan 結構</span><span class="sxs-lookup"><span data-stu-id="543dd-154">The TimeSpan structure</span></span>

<span data-ttu-id="543dd-155"><xref:System.TimeSpan> 結構表示時間間隔。</span><span class="sxs-lookup"><span data-stu-id="543dd-155">The <xref:System.TimeSpan> structure represents a time interval.</span></span> <span data-ttu-id="543dd-156">其兩個一般用法為：</span><span class="sxs-lookup"><span data-stu-id="543dd-156">Its two typical uses are:</span></span>

- <span data-ttu-id="543dd-157">反映出兩個日期和時間值之間的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="543dd-157">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="543dd-158">例如，從另一個值中減去 <xref:System.DateTime> 值會傳回 <xref:System.TimeSpan> 值。</span><span class="sxs-lookup"><span data-stu-id="543dd-158">For example, subtracting one <xref:System.DateTime> value from another returns a <xref:System.TimeSpan> value.</span></span>

- <span data-ttu-id="543dd-159">測量已耗用時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-159">Measuring elapsed time.</span></span> <span data-ttu-id="543dd-160">例如, <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType>屬性會傳回一個<xref:System.TimeSpan>值, 反映從<xref:System.Diagnostics.Stopwatch>呼叫開始測量已耗用時間的其中一個方法以來所經過的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="543dd-160">For example, the <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> property returns a <xref:System.TimeSpan> value that reflects the time interval that has elapsed since the call to one of the <xref:System.Diagnostics.Stopwatch> methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="543dd-161">值也可以做為<xref:System.DateTime>值的取代, 而該值會反映沒有特定日期參考的時間。 <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="543dd-161">A <xref:System.TimeSpan> value can also be used as a replacement for a <xref:System.DateTime> value when that value reflects a time without reference to a particular day.</span></span> <span data-ttu-id="543dd-162">這種用法類似<xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType>于和<xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> <xref:System.TimeSpan>屬性, 其會傳回代表不參考日期之時間的值。</span><span class="sxs-lookup"><span data-stu-id="543dd-162">This usage is similar to the <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> properties, which return a <xref:System.TimeSpan> value that represents the time without reference to a date.</span></span> <span data-ttu-id="543dd-163">例如， <xref:System.TimeSpan> 結構可用來反映商店每日開始營業或打烊的時間，或可用來代表任何有規律事件發生的時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-163">For example, the <xref:System.TimeSpan> structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="543dd-164">下列範例會定義 `StoreInfo` 結構，其中包含用來儲存開始營業和打烊時間的 <xref:System.TimeSpan> 物件，以及代表商店所在時區的 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="543dd-164">The following example defines a `StoreInfo` structure that includes <xref:System.TimeSpan> objects for store opening and closing times, as well as a <xref:System.TimeZoneInfo> object that represents the store's time zone.</span></span> <span data-ttu-id="543dd-165">該結構也包含兩種方法， `IsOpenNow` 和 `IsOpenAt`，假定使用者處於當地時區，該結構會表示商店是否於使用者指定的時間開始營業。</span><span class="sxs-lookup"><span data-stu-id="543dd-165">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

<span data-ttu-id="543dd-166">然後 `StoreInfo` 結構可供用戶端程式碼使用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="543dd-166">The `StoreInfo` structure can then be used by client code like the following.</span></span>

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="543dd-167">TimeZoneInfo 類別</span><span class="sxs-lookup"><span data-stu-id="543dd-167">The TimeZoneInfo class</span></span>

<span data-ttu-id="543dd-168"><xref:System.TimeZoneInfo> 類別代表地球的任何時區，並可讓一個時區中的任何日期和時間轉換成在另一個時區中對等的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="543dd-168">The <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="543dd-169"><xref:System.TimeZoneInfo> 類別讓您能夠處理日期和時間，讓任何日期和時間值能明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="543dd-169">The <xref:System.TimeZoneInfo> class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="543dd-170"><xref:System.TimeZoneInfo> 類別也可延伸。</span><span class="sxs-lookup"><span data-stu-id="543dd-170">The <xref:System.TimeZoneInfo> class is also extensible.</span></span> <span data-ttu-id="543dd-171">雖然這取決於提供給 Windows 系統和定義於登錄中的時區資訊，但它支援建立自訂的時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-171">Although it depends on time zone information provided for Windows systems and defined in the registry, it supports the creation of custom time zones.</span></span> <span data-ttu-id="543dd-172">它也支援時區資訊的序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="543dd-172">It also supports the serialization and deserialization of time zone information.</span></span>

<span data-ttu-id="543dd-173">在某些情況下，欲充分利用 <xref:System.TimeZoneInfo> 類別可能需要進一步的開發工作。</span><span class="sxs-lookup"><span data-stu-id="543dd-173">In some cases, taking full advantage of the <xref:System.TimeZoneInfo> class may require further development work.</span></span> <span data-ttu-id="543dd-174">如果日期和時間值未與它們所屬的時區緊密結合, 則需要進一步的工作。</span><span class="sxs-lookup"><span data-stu-id="543dd-174">If date and time values are not tightly coupled with the time zones to which they belong, further work is required.</span></span> <span data-ttu-id="543dd-175">除非您的應用程式提供將日期和時間與相關聯時區連結的一些機制, 否則特定日期和時間值很容易就會從其時區解除關聯。</span><span class="sxs-lookup"><span data-stu-id="543dd-175">Unless your application provides some mechanism for linking a date and time with its associated time zone, it's easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="543dd-176">連結此資訊的一種方法是定義類別或結構，其中包含日期和時間值，以及與其相關聯的時區物件。</span><span class="sxs-lookup"><span data-stu-id="543dd-176">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="543dd-177">當日期和時間物件已具現化後，僅當日期和時間值的所屬時區已知時，才有可能利用 .NET 支援的時區。</span><span class="sxs-lookup"><span data-stu-id="543dd-177">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="543dd-178">情況往往並非如此，特別是在 Web 或網路應用程式的情況下。</span><span class="sxs-lookup"><span data-stu-id="543dd-178">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="543dd-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="543dd-179">See also</span></span>

- [<span data-ttu-id="543dd-180">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="543dd-180">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
