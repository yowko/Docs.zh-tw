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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107070"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>在 DateTime 與 DateTimeOffset 之間轉換

雖然結構提供的時區感知程度<xref:System.DateTime>比結構更高, <xref:System.DateTime>但參數在方法呼叫中較常使用。 <xref:System.DateTimeOffset> 因此, 將值轉換<xref:System.DateTimeOffset>成<xref:System.DateTime>值, 反之亦然的功能特別重要。 本主題說明如何以盡可能保留最多時區資訊的方式來執行這些轉換。

> [!NOTE]
> 在以時區表示<xref:System.DateTimeOffset>時間時,和類型都有一些限制。<xref:System.DateTime> 使用其<xref:System.DateTime.Kind%2A>屬性, <xref:System.DateTime>能夠只反映國際標準時間 (UTC) 和系統的當地時區。 <xref:System.DateTimeOffset>反映時間與 UTC 的位移, 但不會反映該位移所屬的實際時區。 如需時間值和時區支援的詳細資訊, 請參閱[在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>從 DateTime 到 DateTimeOffset 的轉換

結構會提供兩種對等方法<xref:System.DateTime> , <xref:System.DateTimeOffset>以執行轉換, 適用于大部分的轉換: <xref:System.DateTimeOffset>

- 此<xref:System.DateTimeOffset.%23ctor%2A>函式會根據<xref:System.DateTime>值建立<xref:System.DateTimeOffset>新的物件。

- 隱含轉換運算子, 可讓您將<xref:System.DateTime>值指派<xref:System.DateTimeOffset>給物件。

針對 utc 和區域<xref:System.DateTime>值, 所<xref:System.DateTimeOffset.Offset%2A>產生<xref:System.DateTimeOffset>值的屬性會精確反映 utc 或當地時區的時差。 例如, 下列程式碼會將 UTC 時間轉換為其對<xref:System.DateTimeOffset>等的值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

在此情況下，`utcTime2` 變數的位移是 00:00。 同樣地, 下列程式碼會將當地時間轉換為<xref:System.DateTimeOffset>其對等的值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

不過, 對於<xref:System.DateTime>其<xref:System.DateTime.Kind%2A>屬性為<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>的值, 這兩種轉換方法<xref:System.DateTimeOffset>會產生一個值, 其位移為本地時區的時差。 下列範例會示範以下列時區執行的情況：太平洋標準時區。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

如果該值反映當地時區或 UTC 以外的日期和時間, 您可以藉由呼叫多載的<xref:System.DateTimeOffset.%23ctor%2A>函式將它<xref:System.DateTimeOffset>轉換成值, 並保留其時區資訊。 <xref:System.DateTime> 例如, 下列範例會具現化<xref:System.DateTimeOffset>反映中部標準時間的物件。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

此函式多載的第二個<xref:System.TimeSpan>參數 (代表時間與 UTC 時差的物件) 應藉由<xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType>呼叫時間對應時區的方法來抓取。 方法的單一參數是表示要<xref:System.DateTime>轉換之日期和時間的值。 如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>從 DateTimeOffset 到 DateTime 的轉換

屬性最常用來<xref:System.DateTime>執行<xref:System.DateTimeOffset>轉換。 <xref:System.DateTimeOffset.DateTime%2A> 不過, 它<xref:System.DateTime>會傳回<xref:System.DateTime.Kind%2A>屬性為<xref:System.DateTimeKind.Unspecified>的值, 如下列範例所示。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

這表示<xref:System.DateTimeOffset> <xref:System.DateTimeOffset.DateTime%2A>當使用屬性時, 轉換會遺失與 UTC 的值關聯性的任何相關資訊。 這會<xref:System.DateTimeOffset>影響對應到 UTC 時間或系統本地時間的值, <xref:System.DateTimeOffset.DateTime%2A>因為結構只會反映其<xref:System.DateTime.Kind%2A>屬性中的兩個時區。

若<xref:System.DateTimeOffset>要在將轉換<xref:System.DateTime>成值時保留盡可能多的時區資訊<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> , 您可以使用和<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性。

### <a name="converting-a-utc-time"></a>轉換 UTC 時間

若要指出轉換<xref:System.DateTimeOffset.DateTime%2A>的值是 UTC 時間, 您可以取出<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>屬性的值。 它與<xref:System.DateTimeOffset.DateTime%2A>屬性有兩種不同之處:

- 它會傳回<xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc>值, 其屬性為。 <xref:System.DateTime>

- 如果屬性值不相等<xref:System.TimeSpan.Zero?displayProperty=nameWithType>, 則會將時間轉換成 UTC。 <xref:System.DateTimeOffset.Offset%2A>

> [!NOTE]
> 如果您的應用程式要求<xref:System.DateTime>轉換的值明確地識別單一時間點, 您應該考慮<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>使用屬性來處理所有<xref:System.DateTimeOffset>的<xref:System.DateTime>轉換。

下列<xref:System.DateTimeOffset.UtcDateTime%2A>程式碼使用屬性, <xref:System.DateTimeOffset>將位移等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTime>值的值轉換為。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

下列程式碼會使用<xref:System.DateTimeOffset.UtcDateTime%2A>屬性來對<xref:System.DateTimeOffset>值執行時區轉換和類型轉換。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>轉換當地時間

若要指出某個<xref:System.DateTimeOffset>值代表當地時間, 您可以將<xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType>屬性所<xref:System.DateTime>傳回的值傳遞至`static` (`Shared`在 Visual Basic) <xref:System.DateTime.SpecifyKind%2A>方法中。 方法會傳回傳遞給它的日期和時間做為其第一個參數, 但<xref:System.DateTime.Kind%2A>會將屬性設定為其第二個參數所指定的值。 下列程式碼會在<xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTimeOffset>轉換其位移對應至當地時區的值時, 使用方法。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

您也可以使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性, 將<xref:System.DateTimeOffset>值轉換成區域<xref:System.DateTime>值。 <xref:System.DateTimeKind.Local>傳回<xref:System.DateTime.Kind%2A> 值<xref:System.DateTime>的屬性是。 下列程式碼會在<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset>轉換其位移對應至當地時區的值時, 使用屬性。 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<xref:System.DateTime>當您`get` <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToLocalTime%2A>使用屬性來抓取值時, 屬性的存取子會先將值轉換成 UTC, 然後藉由呼叫方法將它轉換成當地時間。 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 這表示您可以從<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性取得值, 以在執行類型轉換的同時執行時區轉換。 這也表示執行轉換時會套用當地時區的調整規則。 下列程式碼說明如何使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性來執行類型和時區轉換。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>一般用途的轉換方法

下列範例會定義名為`ConvertFromDateTimeOffset`的方法, 將值轉換<xref:System.DateTimeOffset>成<xref:System.DateTime>值。 它會根據其位移, 判斷<xref:System.DateTimeOffset>值是 UTC 時間、當地時間還是其他時間, 並據以定義傳回的日期和時間值的<xref:System.DateTime.Kind%2A>屬性。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

下列範例會呼叫`ConvertFromDateTimeOffset`方法, 將代表 UTC 時間、當地時間和時間的值轉換成美國<xref:System.DateTimeOffset>中央標準時區時間。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰

- 它假設其位移<xref:System.TimeSpan.Zero?displayProperty=nameWithType>的日期和時間值代表 UTC。 事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。 時間區域也可以有的<xref:System.TimeSpan.Zero>位移。

- 它假設位移等於當地時區位移的日期和時間代表當地時區。 因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
