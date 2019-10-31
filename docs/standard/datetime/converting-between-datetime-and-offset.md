---
title: 在 DateTime 與 DateTimeOffset 之間轉換
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
ms.openlocfilehash: 428553f75db2cca6705ac72873e86e120e94d134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132586"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>在 DateTime 與 DateTimeOffset 之間轉換

雖然 <xref:System.DateTimeOffset> 結構提供比 <xref:System.DateTime> 結構更大的時區感知，但 <xref:System.DateTime> 參數在方法呼叫中較常使用。 因此，將 <xref:System.DateTimeOffset> 值轉換成 <xref:System.DateTime> 值，反之亦然的功能特別重要。 本主題說明如何以盡可能保留最多時區資訊的方式來執行這些轉換。

> [!NOTE]
> 在以時區表示時間時，<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 類型都有一些限制。 有了其 <xref:System.DateTime.Kind%2A> 屬性，<xref:System.DateTime> 就能夠僅反映國際標準時間（UTC）和系統的當地時區。 <xref:System.DateTimeOffset> 反映時間與 UTC 的時差，但不會反映該位移所屬的實際時區。 如需時間值和時區支援的詳細資訊，請參閱[在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>從 DateTime 到 DateTimeOffset 的轉換

<xref:System.DateTimeOffset> 結構提供兩種對等的方式，來執行 <xref:System.DateTime> 來進行大部分轉換所適用的 <xref:System.DateTimeOffset> 轉換：

- <xref:System.DateTimeOffset.%23ctor%2A> 的函式，它會根據 <xref:System.DateTime> 值建立新的 <xref:System.DateTimeOffset> 物件。

- 隱含轉換運算子，可讓您將 <xref:System.DateTime> 值指派給 <xref:System.DateTimeOffset> 物件。

針對 UTC 和本機 <xref:System.DateTime> 值，所產生 <xref:System.DateTimeOffset> 值的 <xref:System.DateTimeOffset.Offset%2A> 屬性會精確地反映 UTC 或當地時區的時差。 例如，下列程式碼會將 UTC 時間轉換成其相等的 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

在此情況下，`utcTime2` 變數的位移是 00:00。 同樣地，下列程式碼會將當地時間轉換為其對等的 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

不過，針對 <xref:System.DateTime.Kind%2A> 屬性 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>的 <xref:System.DateTime> 值，這兩種轉換方法會產生其位移為本地時區的 <xref:System.DateTimeOffset> 值。 下列範例中將示範以美國太平洋標準時間時區執行的情況。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

如果 <xref:System.DateTime> 值會以本地時區或 UTC 以外的時間來反映日期和時間，您可以藉由呼叫多載的 <xref:System.DateTimeOffset.%23ctor%2A> 的函式，將它轉換成 <xref:System.DateTimeOffset> 值，並保留其時區資訊。 例如，下列範例會具現化反映中部標準時間的 <xref:System.DateTimeOffset> 物件。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

此函式多載的第二個參數（代表時間與 UTC 時差的 <xref:System.TimeSpan> 物件）應該藉由呼叫時間對應時區的 <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> 方法來抓取。 方法的單一參數是 <xref:System.DateTime> 值，表示要轉換的日期和時間。 如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>從 DateTimeOffset 到 DateTime 的轉換

<xref:System.DateTimeOffset.DateTime%2A> 屬性最常用於執行 <xref:System.DateTime> 轉換 <xref:System.DateTimeOffset>。 不過，它會傳回 <xref:System.DateTime.Kind%2A> 屬性 <xref:System.DateTimeKind.Unspecified>的 <xref:System.DateTime> 值，如下列範例所示。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

這表示當使用 <xref:System.DateTimeOffset.DateTime%2A> 屬性時，轉換會遺失 <xref:System.DateTimeOffset> 值與 UTC 的關聯性的任何相關資訊。 這會影響對應到 UTC 時間或系統當地時間的 <xref:System.DateTimeOffset> 值，因為 <xref:System.DateTimeOffset.DateTime%2A> 結構只會在其 <xref:System.DateTime.Kind%2A> 屬性中反映這兩個時區。

若要在將 <xref:System.DateTimeOffset> 轉換成 <xref:System.DateTime> 值時保留盡可能多的時區資訊，您可以使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性。

### <a name="converting-a-utc-time"></a>轉換 UTC 時間

若要指出轉換後的 <xref:System.DateTimeOffset.DateTime%2A> 值是 UTC 時間，您可以取出 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 屬性的值。 它與 <xref:System.DateTimeOffset.DateTime%2A> 屬性有兩種不同之處：

- 它會傳回 <xref:System.DateTime.Kind%2A> 屬性 <xref:System.DateTimeKind.Utc>的 <xref:System.DateTime> 值。

- 如果 <xref:System.DateTimeOffset.Offset%2A> 屬性值不等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType>，它會將時間轉換成 UTC。

> [!NOTE]
> 如果您的應用程式需要轉換的 <xref:System.DateTime> 值明確地識別單一時間點，您應該考慮使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 屬性來處理 <xref:System.DateTime> 轉換的所有 <xref:System.DateTimeOffset>。

下列程式碼會使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性，將其位移等於 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 的 <xref:System.DateTimeOffset> 值轉換為 <xref:System.DateTime> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

下列程式碼會使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性，在 <xref:System.DateTimeOffset> 值上執行時區轉換和類型轉換。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>轉換當地時間

若要表示 <xref:System.DateTimeOffset> 值代表當地時間，您可以將 <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> 屬性傳回的 <xref:System.DateTime> 值傳遞給 `static` （`Shared`） Visual Basic 方法。 方法會傳回傳遞給它的日期和時間做為其第一個參數，但會將 <xref:System.DateTime.Kind%2A> 屬性設為其第二個參數所指定的值。 下列程式碼會在轉換其位移對應至當地時區的 <xref:System.DateTimeOffset> 值時，使用 <xref:System.DateTime.SpecifyKind%2A> 方法。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

您也可以使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性，將 <xref:System.DateTimeOffset> 值轉換為本機 <xref:System.DateTime> 值。 傳回的 <xref:System.DateTime> 值的 <xref:System.DateTime.Kind%2A> 屬性會 <xref:System.DateTimeKind.Local>。 下列程式碼會在轉換其位移對應至當地時區的 <xref:System.DateTimeOffset> 值時，使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性。 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

當您使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性來抓取 <xref:System.DateTime> 值時，屬性的 `get` 存取子會先將 <xref:System.DateTimeOffset> 值轉換為 UTC，然後藉由呼叫 <xref:System.DateTimeOffset.ToLocalTime%2A> 方法將它轉換成當地時間。 這表示您可以從 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性抓取值，以在執行類型轉換時，同時執行時區轉換。 這也表示執行轉換時會套用當地時區的調整規則。 下列程式碼說明如何使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性來同時執行型別和時區轉換。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>一般用途的轉換方法

下列範例會定義名為 `ConvertFromDateTimeOffset` 的方法，將 <xref:System.DateTimeOffset> 值轉換成 <xref:System.DateTime> 值。 根據其位移，它會判斷 <xref:System.DateTimeOffset> 值是 UTC 時間、當地時間還是其他時間，並據以定義傳回的日期和時間值的 <xref:System.DateTime.Kind%2A> 屬性。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

下列範例會呼叫 `ConvertFromDateTimeOffset` 方法來轉換 <xref:System.DateTimeOffset> 値，這些値代表 UTC 時間、本地時間以及美國中央標準時間時區。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰

- 它假設其位移 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 的日期和時間值代表 UTC。 事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。 時間區域也可以有 <xref:System.TimeSpan.Zero>的位移。

- 它假設位移等於當地時區位移的日期和時間代表當地時區。 因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。

## <a name="see-also"></a>請參閱

- [日期、時間及時區](../../../docs/standard/datetime/index.md)
