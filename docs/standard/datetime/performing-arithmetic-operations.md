---
title: "使用日期和時間執行算術運算"
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
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: edad8fc6643b90afc8327b574e19b178270829b3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>使用日期和時間執行算術運算

雖然同時<xref:System.DateTime>和<xref:System.DateTimeOffset>結構提供執行算術運算，其值的成員，算術運算的結果是非常不同。 本主題會檢查這些差異，與它們相關程度的時區感知日期和時間資料，並討論如何執行完整的時區感知的運算，使用日期和時間資料。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>比較和算術運算，含有 DateTime 值

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性可讓<xref:System.DateTimeKind>来指派給來指出它是代表本地時間、 國際標準時間 (UTC) 或未指定時區的時間的日期和時間值。 當比較，或執行日期和時間運算上時，不過，忽略此有限的時區資訊<xref:System.DateTimeKind>值。 下列範例會比較目前當地時間與目前 UTC 時間，以說明這點。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29>方法會報告本機時間早於 (或低於) 的 UTC 時間，且減法運算會指出在美國太平洋時區中 UTC 與本地時間，系統之間的差異太平洋標準時間時區系統來說相差七個小時。 但因為這兩個值提供單一時間點的不同表示，所以在此情況下，此時間間隔很明顯地完全歸因於當地時區與 UTC 的位移。

較常見地，<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性不會影響所傳回的結果<xref:System.DateTime.Kind>比較和算術方法 （如比較的兩個相同時間點表示），但是它可能會影響這些結果的解譯。 例如: 

* 任何算術運算的結果上執行兩個日期和時間值的<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性都等於<xref:System.DateTimeKind>反映出兩個值之間的實際時間間隔。 同樣地，兩個這類日期和時間值的比較會精確地反映時間的關聯性。

* 任何算術或比較運算的結果上執行兩個日期和時間值的<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性都等於<xref:System.DateTimeKind>或對兩個不同日期和時間值<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值會反映時鐘時間的差距兩個值。

* 當地日期和時間值的算術或比較作業不會考慮特定值是不明確或無效，也不會考慮當地時區與日光節約時間之轉換所產生的任何調整規則的影響。

* 任何比較或計算 UTC 與當地時間之差異的作業，都會在結果中包含等於當地時區與 UTC 之位移的時間間隔。

* 任何比較或計算未指定時間與 UTC 或當地時間之差異的作業，都會反映簡單時鐘時間。 不考慮時區差異，而且結果不會反映如何套用時區調整規則。

* 任何比較或計算兩個未指定時間之差異的作業都可能包含未知間隔，而未知間隔反映兩個不同時區的時間差異。

有許多案例中的時區差異並不會影響日期和時間計算 (其中有些的討論，請參閱[DateTime、 DateTimeOffset、 TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)) 或在其中的內容日期和時間資料會定義的比較或算術運算的意義。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>比較和 DateTimeOffset 值的算術運算

A<xref:System.DateTimeOffset>值包含不只一個日期和時間，還能明確定義該日期和時間相對於 UTC 的位移。 這樣做可定義的方式稍有不同於相等<xref:System.DateTimeOffset>值。 而<xref:System.DateTime>值是否相等，如果有相同的日期和時間值<xref:System.DateTimeOffset>值是否相等，如果它們都參考相同的點的時間。 這可讓<xref:System.DateTimeOffset>更精確且較不需要解譯時用於比較和大部分的算術運算，判斷兩個日期和時間之間的間隔中的值。 下列範例中，也就是<xref:System.DateTimeOffset>相當於上一個範例比較本機與 UTC<xref:System.DateTimeOffset>值，則將說明此行為差異。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

在此範例中，<xref:System.DateTimeOffset.CompareTo%2A>方法會指示目前的當地時間和目前的 UTC 時間為等於、 和減法<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>值，表示兩個時間之間的差異是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。

使用的主要限制<xref:System.DateTimeOffset>日期和時間運算中的值是，雖然<xref:System.DateTimeOffset>值有一些時區感知，他們並不完全感知時區。 雖然<xref:System.DateTimeOffset>值的位移會反映從 UTC 的時區位移時<xref:System.DateTimeOffset>變數會先指派值，它會變成解除關聯的時區時間之後。 因為它不再與可識別時間直接關聯，所以加上和減去日期和時間間隔不會視為時區的調整規則。

舉例而言，美國中央標準時間時區轉換成日光節約時間是在 2008 年 3 月 9 日的 凌晨 2:00 發生。 這表示，中央標準時間 2008 年 3 月 9 日上午 1:30 加上兩個半小時的間隔， 就會產生 2008 年 3 月 9 日凌晨 5:00 的 日期和時間。 不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日 凌晨 4:00。 請注意，雖然這並非我們感興趣的時區時間 (亦即，它沒有預期的時區位移)，但是這項作業的結果確實代表正確時間點。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>時區時間使用算術運算

<xref:System.TimeZoneInfo>類別包含數種轉換方法，它們將時間從一個時區轉換成另一個時，會自動套用調整。 這些需求包括下列各項：

* <xref:System.TimeZoneInfo.ConvertTime%2A>和<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>方法，將它轉換之間任何兩個時區的時間。

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>和<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>的方法，將特定時區的時間轉換成 UTC，或為特定時區的時間轉換成 UTC。

如需詳細資訊，請參閱[轉換的時區時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)>類別並未提供當您執行日期和時間運算時，會自動套用的調整規則的任何方法。 不過，作法是將時區時間轉換為 UTC，並執行算術運算，然後從 UTC 轉換回時區時間。 如需詳細資訊，請參閱[How to： 在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)。

例如，下列程式碼與前面的程式碼類似，也是將 2008 年 3 月 9 日 凌晨 2:00 加上兩個半小時。 不過，因為它會先將美加中部標準時間轉換為 UTC，再執行日期和時間運算，然後將 UTC 的結果轉換回美加中部標準時間，所以產生的時間會反映美加中部標準時區到日光節約時間的轉換。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[How to： 在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
