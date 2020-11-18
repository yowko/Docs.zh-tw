---
title: 在 DateTime 與 DateTimeOffset 之間轉換
description: 在 .NET 中轉換 DateTimeOffset 值與日期時間值。 DateTimeOffset 結構提供比 DateTime 結構更多的時區感知。
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
ms.openlocfilehash: af75a467c344e299037dc6c2077e4a6ef6df2df9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818078"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>在 DateTime 與 DateTimeOffset 之間轉換

雖然 <xref:System.DateTimeOffset> 結構提供的時區感知程度比結構更高，但 <xref:System.DateTime> <xref:System.DateTime> 在方法呼叫中較常使用參數。 基於這個原因，將值轉換為值的能力（反之亦然） <xref:System.DateTimeOffset> <xref:System.DateTime> 特別重要。 本主題說明如何以盡可能保留最多時區資訊的方式來執行這些轉換。

> [!NOTE]
> <xref:System.DateTime>和 <xref:System.DateTimeOffset> 類型在代表時區的時間時會有一些限制。 使用它的 <xref:System.DateTime.Kind%2A> 屬性， <xref:System.DateTime> 只能反映國際標準時間 (UTC) 和系統的當地時區。 <xref:System.DateTimeOffset> 反映時間與 UTC 之間的時差，但不會反映該位移所屬的實際時區。 如需時間值和時區支援的詳細資訊，請參閱 [在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇](choosing-between-datetime.md)。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>從 DateTime 到 DateTimeOffset 的轉換

<xref:System.DateTimeOffset>結構提供兩種對等方式來 <xref:System.DateTime> 執行 <xref:System.DateTimeOffset> 轉換，適用于大部分的轉換：

- 此函式會 <xref:System.DateTimeOffset.%23ctor%2A> 根據值建立新的 <xref:System.DateTimeOffset> 物件 <xref:System.DateTime> 。

- 隱含轉換運算子，可讓您將 <xref:System.DateTime> 值指派給 <xref:System.DateTimeOffset> 物件。

針對 UTC 和區域 <xref:System.DateTime> 值， <xref:System.DateTimeOffset.Offset%2A> 所產生值的屬性會 <xref:System.DateTimeOffset> 精確地反映 utc 或當地時區位移。 例如，下列程式碼會將 UTC 時間轉換成其相等的 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

在此情況下，`utcTime2` 變數的位移是 00:00。 同樣地，下列程式碼會將當地時間轉換為其相等的 <xref:System.DateTimeOffset> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

不過，對於 <xref:System.DateTime> <xref:System.DateTime.Kind%2A> 屬性為的值 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ，這兩種轉換方法 <xref:System.DateTimeOffset> 會產生值，其位移是本地時區的值。 下列範例中將示範以美國太平洋標準時間時區執行的情況。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

如果此 <xref:System.DateTime> 值反映本地時區或 UTC 以外的日期和時間，您可以藉由呼叫多載的函式，將它轉換成 <xref:System.DateTimeOffset> 值，並保留其時區資訊 <xref:System.DateTimeOffset.%23ctor%2A> 。 例如，下列範例會具現化 <xref:System.DateTimeOffset> 反映中部標準時間的物件。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

這個函式多載的第二個參數（ <xref:System.TimeSpan> 代表時間與 UTC 時差的物件）應該藉由呼叫 <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> 時間對應時區的方法來加以取出。 方法的單一參數是 <xref:System.DateTime> 表示要轉換之日期和時間的值。 如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>從 DateTimeOffset 到 DateTime 的轉換

<xref:System.DateTimeOffset.DateTime%2A>屬性最常用來執行 <xref:System.DateTimeOffset> <xref:System.DateTime> 轉換。 但是，它會傳回 <xref:System.DateTime> <xref:System.DateTime.Kind%2A> 屬性為的值 <xref:System.DateTimeKind.Unspecified> ，如下列範例所示。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

這表示 <xref:System.DateTimeOffset> 當使用屬性時，轉換會遺失值與 UTC 之關聯性的任何資訊 <xref:System.DateTimeOffset.DateTime%2A> 。 這會影響 <xref:System.DateTimeOffset> 對應至 UTC 時間或系統當地時間的值，因為此 <xref:System.DateTimeOffset.DateTime%2A> 結構只會在其屬性中反映這兩個時區 <xref:System.DateTime.Kind%2A> 。

若要在將轉換成值時盡可能保留最多時區資訊 <xref:System.DateTimeOffset> <xref:System.DateTime> ，您可以使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性。

### <a name="converting-a-utc-time"></a>轉換 UTC 時間

若要指出轉換的 <xref:System.DateTimeOffset.DateTime%2A> 值是 UTC 時間，您可以取得屬性的值 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 。 它與屬性有兩種不同之處 <xref:System.DateTimeOffset.DateTime%2A> ：

- 它會傳回 <xref:System.DateTime> <xref:System.DateTime.Kind%2A> 屬性為的值 <xref:System.DateTimeKind.Utc> 。

- 如果 <xref:System.DateTimeOffset.Offset%2A> 屬性值不相等 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> ，則會將時間轉換為 UTC。

> [!NOTE]
> 如果您的應用程式要求轉換的 <xref:System.DateTime> 值明確地識別單一時間點，您應該考慮使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> 屬性來處理所有 <xref:System.DateTimeOffset> <xref:System.DateTime> 轉換。

下列程式碼會使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性，將 <xref:System.DateTimeOffset> 位移等於值的值轉換成 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTime> 值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

下列程式碼會使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性來執行時區轉換和值的型別轉換 <xref:System.DateTimeOffset> 。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>轉換當地時間

若要指出 <xref:System.DateTimeOffset> 值代表本地時間，您可以將 <xref:System.DateTime> 屬性所傳回的值傳遞 <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> 給 `static` `Shared` Visual Basic) 方法中的 (<xref:System.DateTime.SpecifyKind%2A> 。 方法會傳回傳遞給它的日期和時間做為它的第一個參數，但會將 <xref:System.DateTime.Kind%2A> 屬性設定為其第二個參數所指定的值。 下列程式碼會 <xref:System.DateTime.SpecifyKind%2A> 在轉換的值時使用方法， <xref:System.DateTimeOffset> 其位移會對應到本地時區的值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

您也可以使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 屬性，將值轉換 <xref:System.DateTimeOffset> 為區域 <xref:System.DateTime> 值。 <xref:System.DateTime.Kind%2A>傳回值的屬性 <xref:System.DateTime> 為 <xref:System.DateTimeKind.Local> 。 下列程式碼會在 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 轉換的值時使用屬性， <xref:System.DateTimeOffset> 其位移會對應到本地時區的值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

當您 <xref:System.DateTime> 使用屬性來抓取值時 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> ，屬性的存取子會 `get` 先將 <xref:System.DateTimeOffset> 值轉換成 UTC，然後藉由呼叫方法將它轉換為當地時間 <xref:System.DateTimeOffset.ToLocalTime%2A> 。 這表示您可以從屬性取出值， <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 以便在執行類型轉換時執行時區轉換。 這也表示執行轉換時會套用當地時區的調整規則。 下列程式碼說明 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 如何使用屬性來執行型別和時區轉換。 範例輸出適用于設定為太平洋時區 (美國和加拿大) 的電腦。 11月日期是太平洋標準時間（UTC-8），而六月日期則是日光節約時間，也就是 UTC-7。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>一般用途的轉換方法

下列範例會定義名為 `ConvertFromDateTimeOffset` 的方法，將 <xref:System.DateTimeOffset> 值轉換成 <xref:System.DateTime> 值。 它會根據其位移來判斷 <xref:System.DateTimeOffset> 值是 UTC 時間、本地時間或其他時間，並據以定義傳回的日期和時間值的 <xref:System.DateTime.Kind%2A> 屬性。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

下列範例會呼叫 `ConvertFromDateTimeOffset` 方法來轉換 <xref:System.DateTimeOffset> 値，這些値代表 UTC 時間、本地時間以及美國中央標準時間時區。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰

- 它會假設日期和時間值的位移 <xref:System.TimeSpan.Zero?displayProperty=nameWithType> 代表 UTC。 事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。 時區也可以有的位移 <xref:System.TimeSpan.Zero> 。

- 它假設位移等於當地時區位移的日期和時間代表當地時區。 因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。

## <a name="see-also"></a>請參閱

- [日期、時間和時區](index.md)
