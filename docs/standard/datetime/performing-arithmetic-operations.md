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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2a50823b812541786cf1bebfd6b1262ce2e9314
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188095"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>使用日期和時間執行算術運算

雖然兩者<xref:System.DateTime>而<xref:System.DateTimeOffset>結構提供對其值執行算術運算的成員，算術運算的結果是非常不同。 本主題會檢查這些差異，與它們相關的日期和時間資料的時區感知程度，並討論如何執行完全時區感知運算使用日期和時間資料。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>比較和算術運算，與日期時間值

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性可讓<xref:System.DateTimeKind>值指派給日期和時間，以指出它是否代表當地時間、 Coordinated Universal Time (UTC) 或未指定時區的時間。 不過，這個有限的時區資訊會忽略比較或執行日期和時間運算時<xref:System.DateTimeKind>值。 下列範例會比較目前當地時間與目前 UTC 時間，以說明這點。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29>方法會報告本地時間早於 (或小於) UTC 時間，且減法運算會指出 UTC 與本地時間的系統之間的差異，在美國太平洋標準時間時區系統來說相差七個小時。 但因為這兩個值提供單一時間點的不同表示，所以在此情況下，此時間間隔很明顯地完全歸因於當地時區與 UTC 的位移。

更廣泛地<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性不會影響所傳回的結果<xref:System.DateTime.Kind>比較和算術方法 （如比較的兩個相同時間點表示），不過它可能會影響這些結果的解譯。 例如: 

* 任何算術運算的結果上執行兩個日期和時間值的<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性等於<xref:System.DateTimeKind>會反映兩個值之間的實際時間間隔。 同樣地，兩個這類日期和時間值的比較會精確地反映時間的關聯性。

* 任何算術或比較運算的結果上執行兩個日期和時間值的<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性等於<xref:System.DateTimeKind>或使用不同的兩個日期和時間值<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值會反映在時鐘時間差異兩個值。

* 當地日期和時間值的算術或比較作業不會考慮特定值是不明確或無效，也不會考慮當地時區與日光節約時間之轉換所產生的任何調整規則的影響。

* 任何比較或計算 UTC 與當地時間之差異的作業，都會在結果中包含等於當地時區與 UTC 之位移的時間間隔。

* 任何比較或計算未指定時間與 UTC 或當地時間之差異的作業，都會反映簡單時鐘時間。 不考慮時區差異，而且結果不會反映如何套用時區調整規則。

* 任何比較或計算兩個未指定時間之差異的作業都可能包含未知間隔，而未知間隔反映兩個不同時區的時間差異。

許多情況下，時區差異不會影響日期和時間計算 (其中部分項目的討論，請參閱[DateTime、 DateTimeOffset、 TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)) 或在其中的內容日期和時間資料會定義比較或算術運算的意義。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>比較和算術運算，使用 DateTimeOffset 值

A<xref:System.DateTimeOffset>值包含不只一個日期和時間，還能明確定義該日期和時間相對於 UTC 的位移。 這讓您能夠定義略有不同的等號比較，如<xref:System.DateTimeOffset>值。 然而<xref:System.DateTime>值是否相等，如果它們有相同的日期和時間值<xref:System.DateTimeOffset>值是否相等，如果它們都參考相同的點的時間。 這可讓<xref:System.DateTimeOffset>更精確且較不需要解譯時使用的比較和大部分算術運算，判斷兩個日期和時間之間隔的值。 下列範例中，也就是<xref:System.DateTimeOffset>相當於先前的範例，比較本機與 UTC<xref:System.DateTimeOffset>值，說明此行為差異。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

在此範例中，<xref:System.DateTimeOffset.CompareTo%2A>方法會指示目前的當地時間和目前的 UTC 時間為相等，而且減去<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>值，指出兩個時間之間的差異是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。

使用的主要限制<xref:System.DateTimeOffset>日期和時間運算中的值是，雖然<xref:System.DateTimeOffset>值具有一些時區感知，他們並不是完全時區感知。 雖然<xref:System.DateTimeOffset>值的位移會反映與 UTC 的時區時差時<xref:System.DateTimeOffset>變數第一次指派一個值，它會變成時區解除關聯之後。 因為它不再與可識別時間直接關聯，所以加上和減去日期和時間間隔不會視為時區的調整規則。

舉例而言，美國中央標準時間時區轉換成日光節約時間是在 2008 年 3 月 9 日的 凌晨 2:00 發生。 這表示，中央標準時間 2008 年 3 月 9 日上午 1:30 加上兩個半小時的間隔， 就會產生 2008 年 3 月 9 日凌晨 5:00 的 日期和時間。 不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日 凌晨 4:00。 請注意，雖然這並非我們感興趣的時區時間 (亦即，它沒有預期的時區位移)，但是這項作業的結果確實代表正確時間點。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>使用時區時間的算術運算

<xref:System.TimeZoneInfo>類別包含的數種轉換方法，它們將時間從某個時區轉換為另一個時，便會自動套用調整。 這些需求包括下列各項：

* <xref:System.TimeZoneInfo.ConvertTime%2A>和<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>將任何兩個時區之間的時間轉換的方法。

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>和<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>方法，將特定的時區時間轉換成 UTC，或將 UTC 轉換為特定時區的時間。

如需詳細資訊，請參閱 <<c0> [ 各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)>類別不提供任何自動套用調整規則，當您執行日期和時間運算的方法。 不過，作法是將時區時間轉換為 UTC，並執行算術運算，然後從 UTC 轉換回時區時間。 如需詳細資訊，請參閱 <<c0> [ 如何： 在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)。

例如，下列程式碼與前面的程式碼類似，也是將 2008 年 3 月 9 日 凌晨 2:00 加上兩個半小時。 不過，因為它會先將美加中部標準時間轉換為 UTC，再執行日期和時間運算，然後將 UTC 的結果轉換回美加中部標準時間，所以產生的時間會反映美加中部標準時區到日光節約時間的轉換。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [操作說明：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
