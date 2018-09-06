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
ms.openlocfilehash: 830e3e6e98be2eaaff2af6c0bdac650732833ab7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864417"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>在 DateTime 與 DateTimeOffset 之間轉換

雖然<xref:System.DateTimeOffset>結構提供更高的時區感知<xref:System.DateTime>結構，<xref:System.DateTime>更常在方法呼叫中使用參數。 因此，要轉換的能力<xref:System.DateTimeOffset>值來<xref:System.DateTime>值和相反作業特別重要。 本主題說明如何執行這些轉換會保留盡可能最多時區資訊的方式。

> [!NOTE]
> 同時<xref:System.DateTime>而<xref:System.DateTimeOffset>類型代表時區時間時，有一些限制。 使用其<xref:System.DateTime.Kind%2A>屬性，<xref:System.DateTime>能夠反映只有 Coordinated Universal Time (UTC) 和系統的當地時區。 <xref:System.DateTimeOffset> 會反映與 UTC 之位移的時間，但它不會反映屬於實際時區的時差。 如需時間值以及時區支援的詳細資訊，請參閱[選擇 DateTime、 DateTimeOffset、 TimeSpan 和 TimeZoneInfo 之間](../../../docs/standard/datetime/choosing-between-datetime.md)。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>從 DateTime 到 DateTimeOffset 的轉換

<xref:System.DateTimeOffset>結構提供兩個對等的方式來執行<xref:System.DateTime>到<xref:System.DateTimeOffset>適用於大部分轉換的轉換：

* <xref:System.DateTimeOffset.%23ctor%2A>建構函式，建立新<xref:System.DateTimeOffset>物件，根據<xref:System.DateTime>值。

* 隱含轉換運算子，可讓您指派<xref:System.DateTime>值<xref:System.DateTimeOffset>物件。

針對 UTC 和當地<xref:System.DateTime>值，<xref:System.DateTimeOffset.Offset%2A>屬性產生<xref:System.DateTimeOffset>精確地反映 UTC 或本地時間的時區時差。 例如，下列程式碼會將 UTC 時間轉換成其對等<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

在此情況下，`utcTime2` 變數的位移是 00:00。 同樣地，下列程式碼會將當地時間轉換成其對等<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

不過，為了<xref:System.DateTime>值的<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，這些兩種轉換方法會產生<xref:System.DateTimeOffset>位移為本地時區的值。 下列範例會示範以下列時區執行的情況：太平洋標準時區。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

如果<xref:System.DateTime>值的日期和時間的事物當地時區或 UTC 以外，您可以將它轉換成<xref:System.DateTimeOffset>值，並保留其時區資訊呼叫多載<xref:System.DateTimeOffset.%23ctor%2A>建構函式。 例如，下列範例會具現化<xref:System.DateTimeOffset>反映中部標準時間的物件。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

這個建構函式多載中，第二個參數<xref:System.TimeSpan>從其中擷取物件，表示 UTC 時間的位移，藉由呼叫<xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType>方法對應時區的時間。 方法的單一參數是<xref:System.DateTime>值，表示要轉換的日期和時間。 如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>從 DateTimeOffset 到 DateTime 的轉換

<xref:System.DateTimeOffset.DateTime%2A>屬性最常用來執行<xref:System.DateTimeOffset>到<xref:System.DateTime>轉換。 不過，它會傳回<xref:System.DateTime>值<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified>，如下列範例所示。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

這表示任何資訊的相關<xref:System.DateTimeOffset>轉換會遺失值的關聯性為 UTC 時<xref:System.DateTimeOffset.DateTime%2A>屬性使用。 這會影響<xref:System.DateTimeOffset>值，對應至 UTC 時間或系統的當地時間，因為<xref:System.DateTimeOffset.DateTime%2A>結構會反映只有這兩個時區中其<xref:System.DateTime.Kind%2A>屬性。

轉換時，保留最多時區資訊，盡可能<xref:System.DateTimeOffset>要<xref:System.DateTime>值，您可以使用<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>和<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性。

### <a name="converting-a-utc-time"></a>轉換 UTC 時間

表示已轉換<xref:System.DateTimeOffset.DateTime%2A>值是 UTC 時間，您可以擷取的值<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>屬性。 不同於<xref:System.DateTimeOffset.DateTime%2A>屬性有兩種：

* 它會傳回<xref:System.DateTime>值<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Utc>。

* 如果<xref:System.DateTimeOffset.Offset%2A>屬性值不等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>，它會將時間轉換為 UTC。

> [!NOTE]
> 如果您的應用程式需要轉換<xref:System.DateTime>值明確地識別單一點時間，您應該考慮使用<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>屬性來處理所有<xref:System.DateTimeOffset>到<xref:System.DateTime>轉換。

下列程式碼會使用<xref:System.DateTimeOffset.UtcDateTime%2A>要轉換的屬性<xref:System.DateTimeOffset>位移等於的值<xref:System.TimeSpan.Zero?displayProperty=nameWithType>到<xref:System.DateTime>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

下列程式碼會使用<xref:System.DateTimeOffset.UtcDateTime%2A>屬性上執行時區轉換和型別轉換<xref:System.DateTimeOffset>值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>轉換當地時間

表示<xref:System.DateTimeOffset>值代表當地時間，您可以傳遞<xref:System.DateTime>所傳回的值<xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType>屬性設`static`(`Shared`在 Visual Basic 中)<xref:System.DateTime.SpecifyKind%2A>方法。 此方法傳回的日期和時間做為其第一個參數，傳遞給它，但設定<xref:System.DateTime.Kind%2A>屬性設為其第二個參數所指定的值。 下列程式碼會使用<xref:System.DateTime.SpecifyKind%2A>方法轉換時<xref:System.DateTimeOffset>其位移對應至當地時區的值。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

您也可以使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>要轉換的屬性<xref:System.DateTimeOffset>值，以本機<xref:System.DateTime>值。 <xref:System.DateTime.Kind%2A>屬性傳回之<xref:System.DateTime>值是<xref:System.DateTimeKind.Local>。 下列程式碼會使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>轉換時的屬性<xref:System.DateTimeOffset>其位移對應至當地時區的值。 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

當您擷取<xref:System.DateTime>值使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性，屬性的`get`存取子會先轉換<xref:System.DateTimeOffset>值為 UTC，然後將它轉換為當地時間藉由呼叫<xref:System.DateTimeOffset.ToLocalTime%2A>方法。 這表示，您可以擷取值，以從<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>執行時區轉換，在此同時，您會執行類型轉換的屬性。 這也表示執行轉換時會套用當地時區的調整規則。 下列程式碼說明如何使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性，來執行類型和時區轉換。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>一般用途的轉換方法

下列範例會定義名為的方法`ConvertFromDateTimeOffset`以將轉換成<xref:System.DateTimeOffset>值來<xref:System.DateTime>值。 根據其位移，它會判斷是否<xref:System.DateTimeOffset>值為 UTC 時間、 當地時間或一些其他的時間，並定義傳回的日期和時間值的<xref:System.DateTime.Kind%2A>屬性據此。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

下列範例會呼叫`ConvertFromDateTimeOffset`方法，將轉換<xref:System.DateTimeOffset>值代表 UTC 時間、 當地時間，以及位於美國的時間中央標準時區時間。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰

* 它會假設日期和時間值的位移是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>代表 UTC。 事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。 時區也可以有的位移<xref:System.TimeSpan.Zero>。

* 它假設位移等於當地時區位移的日期和時間代表當地時區。 因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
