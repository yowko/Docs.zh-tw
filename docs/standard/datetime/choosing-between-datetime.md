---
title: 比較 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo
description: 瞭解 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 類型之間的差異，以在 .NET 中代表日期和時間資訊。
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
ms.openlocfilehash: 03d00fb802032b981a5ebe80f7166eba0fb54a60
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326057"
---
# <a name="choose-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間進行選擇

.NET 應用程式可以透過數種方式來使用日期和時間資訊。 日期和時間資訊的常見用法包括：

- 只反映日期，使時間資訊不重要。

- 只反映時間，使日期資訊不重要。

- 反映抽象的日期和時間，這些並不會和特定時間或位置密切相關 (例如大多數國際連鎖的商店在工作日上午 9 點開始營業)。

- 若要從 .NET 外部的來源抓取日期和時間資訊，通常會將日期和時間資訊儲存成簡單的資料類型。

- 若要唯一且明確地識別單一時間點。 有些應用程式只需要在主機系統上有明確的日期和時間。 其他應用程式要求它在系統之間是明確的（也就是說，在某個系統上序列化的日期可以有意義地還原序列化，並在世界各地的另一個系統上使用）。

- 若要保留多個相關時間 (例如要求者的當地時間和 Web 要求的回條之伺服器時間)。

- 若要執行日期和時間運算，且該運算可能有會唯一明確地識別單一時間點的結果。

.Net 包含 <xref:System.DateTime> 、 <xref:System.DateTimeOffset> 、 <xref:System.TimeSpan> 和 <xref:System.TimeZoneInfo> 類型，這些都可以用來建立使用日期和時間的應用程式。

> [!NOTE]
> 本主題不會討論， <xref:System.TimeZone> 因為它的功能幾乎已完全納入 <xref:System.TimeZoneInfo> 類別中。 盡可能使用 <xref:System.TimeZoneInfo> 類別，而不是 <xref:System.TimeZone> 類別。

## <a name="the-datetime-structure"></a>DateTime 結構

<xref:System.DateTime> 值會定義特定的日期和時間。 它包含 <xref:System.DateTime.Kind%2A> 屬性，提供有關該日期和時間所屬時區的有限資訊。 由 <xref:System.DateTimeKind> 屬性傳回的 <xref:System.DateTime.Kind%2A> 值，表示 <xref:System.DateTime> 值是否代表當地時間 (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>)、國際標準時間 (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) 或未指定的時間 (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>)。

<xref:System.DateTime>結構適用于具有下列一或多個特性的應用程式：

- 只使用日期。

- 只使用時間。

- 使用抽象的日期和時間。

- 使用遺漏時區資訊的日期和時間。

- 只使用 UTC 日期和時間。

- 從 .NET 外部的來源（例如 SQL 資料庫）取出日期和時間資訊。 一般而言，這些來源會將日期和時間資訊以和 <xref:System.DateTime> 結構相容的簡單格式儲存。

- 執行日期和時間運算，但關心其一般結果。 例如，在對特定日期和時間加入六個月的加法運算中，該結果是否對日光節約時間進行調整通常並不重要。

除非特定的 <xref:System.DateTime> 值代表 UTC，否則該日期和時間值的可攜性通常是模稜兩可或受限制的。 例如，如果 <xref:System.DateTime> 值代表當地時間，則在該當地時區是可攜式的 (也就是說，如果值在相同時區的另一個系統上還原序列化，則該值仍會明確地識別單一時間點)。 在當地時區外， <xref:System.DateTime> 的值可有多重解譯。 如果該值的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，則它的可攜性更差：現在它於相同的時區中模稜兩可，即使在第一次序列化的同一個系統上也可能如此。 只有當 <xref:System.DateTime> 值代表 UTC 時，該值才會明確地識別單一時間點，無論該值所使用的系統或時區為何。

> [!IMPORTANT]
> 當儲存或共用 <xref:System.DateTime> 資料時應該使用 UTC，且 <xref:System.DateTime> 值的 <xref:System.DateTime.Kind%2A> 屬性應該設為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset 結構

<xref:System.DateTimeOffset> 結構代表日期和時間值，以及表示該值與 UTC 差異大小的位移。 因此，該值一律明確地識別單一時間點。

<xref:System.DateTimeOffset> 類型包含 <xref:System.DateTime> 類型的所有功能並感知時區。 這適用于下列應用程式：

- 唯一且明確地識別單一時間點。 <xref:System.DateTimeOffset> 類型可用來明確定義「現在」的意義，以記錄交易的時間、記錄系統或應用程式事件的時間以及記錄檔案建立及修改的時間。

- 執行一般日期和時間運算。

- 只要時間已儲存為兩個不同的值或一個結構中的兩個成員，就可保留多個相關時間。

> [!NOTE]
> <xref:System.DateTimeOffset> 值的用途比 <xref:System.DateTime> 值的更為普遍。 因此，請考慮 <xref:System.DateTimeOffset> 作為應用程式開發的預設日期和時間類型。

<xref:System.DateTimeOffset>值未系結至特定時區，但可能來自各種不同的時間區域。 下列範例會列出一些 <xref:System.DateTimeOffset> 值（包括當地的太平洋標準時間）可以屬於的時區。

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

此輸出顯示在本範例中的每個日期和時間值可屬於至少三個不同時區。 <xref:System.DateTimeOffset>6/10/2007 的值顯示如果日期和時間值代表日光節約時間，則其與 utc 的時差不一定會對應至原始時區的基底 UTC 時差，或從其顯示名稱中找到的 UTC 位移。 因為單一 <xref:System.DateTimeOffset> 值不會與時區緊密結合，所以無法反映時區與日光節約時間的來回轉換。 當使用日期和時間運算來操作值時，這可能會造成問題 <xref:System.DateTimeOffset> 。 如需如何以考慮時區調整規則的方式來執行日期和時間運算的討論，請參閱[使用日期和時間執行算數運算](performing-arithmetic-operations.md)。

## <a name="the-timespan-structure"></a>TimeSpan 結構

<xref:System.TimeSpan> 結構表示時間間隔。 其兩個一般用法為：

- 反映出兩個日期和時間值之間的時間間隔。 例如，從另一個值中減去 <xref:System.DateTime> 值會傳回 <xref:System.TimeSpan> 值。

- 測量已耗用時間。 例如， <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> 屬性會傳回一個 <xref:System.TimeSpan> 值，反映從呼叫開始測量已耗用時間的其中一個方法以來所經過的時間間隔 <xref:System.Diagnostics.Stopwatch> 。

<xref:System.TimeSpan>值也可以做為值的取代 <xref:System.DateTime> ，而該值會反映沒有特定日期參考的時間。 這種用法類似于 <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> 屬性，其會傳回 <xref:System.TimeSpan> 代表不參考日期之時間的值。 例如， <xref:System.TimeSpan> 結構可用來反映商店每日開始營業或打烊的時間，或可用來代表任何有規律事件發生的時間。

下列範例會定義 `StoreInfo` 結構，其中包含用來儲存開始營業和打烊時間的 <xref:System.TimeSpan> 物件，以及代表商店所在時區的 <xref:System.TimeZoneInfo> 物件。 該結構也包含兩種方法， `IsOpenNow` 和 `IsOpenAt`，假定使用者處於當地時區，該結構會表示商店是否於使用者指定的時間開始營業。

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

然後 `StoreInfo` 結構可供用戶端程式碼使用，如下所示。

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo 類別

<xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone. <xref:System.TimeZoneInfo> 類別讓您能夠處理日期和時間，讓任何日期和時間值能明確地識別單一時間點。 <xref:System.TimeZoneInfo> 類別也可延伸。 雖然這取決於提供給 Windows 系統和定義於登錄中的時區資訊，但它支援建立自訂的時區。 它也支援時區資訊的序列化和還原序列化。

在某些情況下，欲充分利用 <xref:System.TimeZoneInfo> 類別可能需要進一步的開發工作。 如果日期和時間值未與它們所屬的時區緊密結合，則需要進一步的工作。 除非您的應用程式提供將日期和時間與相關聯時區連結的一些機制，否則特定日期和時間值很容易就會從其時區解除關聯。 連結此資訊的一種方法是定義類別或結構，其中包含日期和時間值，以及與其相關聯的時區物件。

若要利用 .NET 中的時區支援，您必須知道當日期和時間物件具現化時，日期和時間值所屬的時區。 時區通常不是已知的，特別是在 web 或網路應用程式中。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
