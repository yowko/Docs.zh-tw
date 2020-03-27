---
title: 使用日期和時間執行算術運算
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344177"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>使用日期和時間執行算術運算

儘管<xref:System.DateTime>和<xref:System.DateTimeOffset>結構都提供對其值執行算數運算的成員，但算數運算的結果非常不同。 本主題將檢查這些差異，將它們與日期和時間資料中的時區感知度相關聯，並討論如何使用日期和時間資料執行完全時區感知操作。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>使用 DateTime 值的比較和算數運算

該<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性允許將<xref:System.DateTimeKind>值分配給日期和時間，以指示該值是表示本地時間、協調通用時間 （UTC） 還是未指定時區中的時間。 但是，在比較或執行值的<xref:System.DateTimeKind>日期和時間算術時，忽略此有限時區資訊。 下列範例會比較目前當地時間與目前 UTC 時間，以說明這點。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> 方法會報告本地時間早於 (或晚於) UTC 時間，接著減法運算會指出 UTC 與本地時間之間的時差，以美國太平洋標準時間時區系統來說相差七個小時。 但是，由於這兩個值提供單個時間點的不同表示形式，因此在這種情況下，時間間隔完全歸因於本地時區與 UTC 的偏移量。

更一般說<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>來，屬性不會影響通過<xref:System.DateTime.Kind>比較和算術方法返回的結果（如兩個相同時間點的比較所示），儘管它會影響這些結果的解釋。 例如：

- 對兩個日期和時間值執行的任何算數運算的結果，其<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性均相等<xref:System.DateTimeKind>，反映兩個值之間的實際時間間隔。 同樣地，兩個這類日期和時間值的比較會精確地反映時間的關聯性。

- 對兩個日期和時間值執行的任何算術或比較操作的結果，其<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性等於<xref:System.DateTimeKind>或兩個具有不同<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值的日期和時間值都反映了兩個值之間的時鐘時間差異。

- 當地日期和時間值的算術或比較作業不會考慮特定值是不明確或無效，也不會考慮當地時區與日光節約時間之轉換所產生的任何調整規則的影響。

- 任何比較或計算 UTC 與當地時間之差異的作業，都會在結果中包含等於當地時區與 UTC 之位移的時間間隔。

- 任何比較或計算未指定時間與 UTC 或當地時間之差異的作業，都會反映簡單時鐘時間。 不考慮時區差異，而且結果不會反映如何套用時區調整規則。

- 任何比較或計算兩個未指定時間之差異的作業都可能包含未知間隔，而未知間隔反映兩個不同時區的時間差異。

在很多方案中，時區差異不會影響日期和時間計算（有關其中一些計算的討論，請參閱[在日期時間、日期時間偏移、時間跨度和 TimeZoneInfo 之間進行選擇](../../../docs/standard/datetime/choosing-between-datetime.md)），或者日期和時間資料的上下文定義比較或算數運算的含義。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>使用 DateTimeOffset 值的比較和算數運算

<xref:System.DateTimeOffset>值不僅包括日期和時間，還包括明確定義相對於 UTC 的日期和時間的偏移量。 這使得定義相等性的方式與<xref:System.DateTimeOffset>值的相等性略有不同。 如果<xref:System.DateTime>值具有相同的日期和時間值，則值相等，<xref:System.DateTimeOffset>如果兩個值都引用同一時間點，則值相等。 這使得值在<xref:System.DateTimeOffset>比較和大多數確定兩個日期和時間間隔的算數運算中使用時更準確，也更不需要解釋。 下面的示例<xref:System.DateTimeOffset>與比較本地值和 UTC<xref:System.DateTimeOffset>值的上一個示例等效，說明了這種行為差異。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

在此示例中，<xref:System.DateTimeOffset.CompareTo%2A>該方法指示當前本地時間和當前 UTC 時間相等，並且值的<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>減法表示兩次之間的差異為<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。

在<xref:System.DateTimeOffset>日期和時間算術中使用值的主要限制是，雖然<xref:System.DateTimeOffset>值具有一定的時區感知，但它們並不完全瞭解時區。 儘管當<xref:System.DateTimeOffset><xref:System.DateTimeOffset>首次為變數分配值時，該值的偏移量反映了時區與 UTC 的偏移量，但它與之後的時區不同。 因為它不再與可識別時間直接關聯，所以加上和減去日期和時間間隔不會視為時區的調整規則。

為了說明，美國中央標準時區向夏令時的過渡發生在淩晨 2：00。 凌晨 2:00 加上兩個半小時。 這表示，中央標準時間 2008 年 3 月 9 日上午 1:30 加上兩個半小時的間隔， 就會產生 2008 年 3 月 9 日凌晨 5:00 的 凌晨 2:00 加上兩個半小時。 不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日 凌晨 2:00 加上兩個半小時。 請注意，此操作的結果確實表示正確的時間點，儘管它不是我們感興趣的時區中的時間（也就是說，它沒有預期的時區偏移）。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>在時區中隨時間的算數運算

該<xref:System.TimeZoneInfo>類包括許多轉換方法，這些方法在將時間從一個時區轉換為另一個時區時自動應用調整。 這些選項包括：

- <xref:System.TimeZoneInfo.ConvertTime%2A>和<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>方法，它們在任意兩個時區之間轉換時間。

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>和<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>方法，將特定時區中的時間轉換為 UTC，或將 UTC 轉換為特定時區中的時間。

有關詳細資訊，請參閱[在時區之間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

該<xref:System.TimeZoneInfo>類不提供在執行日期和時間算術時自動應用調整規則的任何方法。 不過，作法是將時區時間轉換為 UTC，並執行算術運算，然後從 UTC 轉換回時區時間。 有關詳細資訊，請參閱[：在日期和時間算術中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)。

例如，下列程式碼與前面的程式碼類似，也是將 2008 年 3 月 9 日 凌晨 2:00 加上兩個半小時。 不過，因為它會先將美加中部標準時間轉換為 UTC，再執行日期和時間運算，然後將 UTC 的結果轉換回美加中部標準時間，所以產生的時間會反映美加中部標準時區到日光節約時間的轉換。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [如何：在日期和時間算術中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
