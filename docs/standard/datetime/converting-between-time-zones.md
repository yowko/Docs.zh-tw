---
title: 在各時區間轉換時間
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c77832a4c578ddb2c8a427b133e53ab4ab5c5e3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595622"
---
# <a name="converting-times-between-time-zones"></a>在各時區間轉換時間

對於使用日期和時間來處理時區差異的任何應用程式，它會變得越來越重要。 應用程式不會再假設，隨時可以是以當地時間表示，這是時間可從<xref:System.DateTime>結構。 例如，顯示美國東部目前時間的網頁對東亞地區的客戶不具公信力。 本主題說明如何將時間從某個時區轉換到另一個，以及如何將轉換<xref:System.DateTimeOffset>具有有限時區感知的值。

## <a name="converting-to-coordinated-universal-time"></a>轉換為國際標準時間

國際標準時間 (UTC) 是高精確度且不可部分完成的時間標準。 全世界的時區都會表示為與 UTC 的正或負位移。 因此，UTC 提供一種無時區或時區中性時間。 跨電腦的日期和時間可攜性十分重要時，建議使用 UTC 時間。 (如需詳細資料和其他使用日期和時間的最佳做法，請參閱[撰寫程式碼使用.NET Framework 中的日期時間的最佳做法](https://msdn.microsoft.com/library/ms973825.aspx)。)將個別時區轉換為 UTC 可輕鬆地比較時間。

> [!NOTE]
> 您也可以序列化<xref:System.DateTimeOffset>結構來明確代表單一點的時間。 因為<xref:System.DateTimeOffset>物件會儲存日期和時間的值，以及其與 UTC 的時差，所以它們一律代表特定點的關聯性中的時間為 UTC。

將時間轉換為 UTC 的最簡單方式是呼叫`static`(`Shared` Visual Basic 中)<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>方法。 方法所執行的確切轉換取決於 windows 7`dateTime`參數的<xref:System.DateTime.Kind%2A>屬性，如下表所示。

| `DateTime.Kind`            | 轉換                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | 將當地時間轉換為 UTC。                                                    |
| `DateTimeKind.Unspecified` | 假設 `dateTime` 參數是當地時間，並將當地時間轉換為 UTC。 |
| `DateTimeKind.Utc`         | 傳回未變更的 `dateTime` 參數。                                    |

下列程式碼會將目前當地時間轉換為 UTC，並將結果顯示到主控台。

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>方法不一定會產生相同的結果<xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType>和<xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType>方法。 如果主機系統的當地時區包含多個調整規則，<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>適當的規則適用於特定日期和時間。 另兩種方法一律會套用最新的調整規則。

如果日期和時間值不代表當地時間或 UTC，<xref:System.DateTime.ToUniversalTime%2A>方法可能會傳回錯誤結果。 不過，您可以使用<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>方法，以從指定的時區轉換的日期和時間。 (如需有關擷取<xref:System.TimeZoneInfo>物件，代表目的地時區中，請參閱[尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)。)下列程式碼會使用<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>方法將美加東部標準時間轉換為 UTC。

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

請注意，此方法會擲回<xref:System.ArgumentException>如果<xref:System.DateTime>物件的<xref:System.DateTime.Kind%2A>屬性和時區不相符。 如果發生不符的情形<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Local?displayProperty=nameWithType>但<xref:System.TimeZoneInfo>物件不代表當地時區，或如果<xref:System.DateTime.Kind%2A>屬性<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>但<xref:System.TimeZoneInfo>物件不等於<xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>。

所有這些方法採取<xref:System.DateTime>值做為參數和傳回<xref:System.DateTime>值。 針對<xref:System.DateTimeOffset>值，<xref:System.DateTimeOffset>結構具有<xref:System.DateTimeOffset.ToUniversalTime%2A>執行個體方法，將目前的執行個體的時間與日期轉換為 UTC。 下列範例會呼叫<xref:System.DateTimeOffset.ToUniversalTime%2A>方法，以將當地時間和數個其他時間轉換為 Coordinated Universal Time (UTC)。

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>將 UTC 轉換為指定的時區

若要將 UTC 轉換為當地時間，請參閱 「 轉換 UTC 到本地時間 」 一節。 若要將 UTC 轉換為您指定的任何時區的時間，呼叫<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>方法。 這個方法採用兩個參數：

* 要轉換的 UTC。 這必須是<xref:System.DateTime>值<xref:System.DateTime.Kind%2A>屬性設定為`Unspecified`或`Utc`。

* 要將 UTC 轉換為的時區。

下列程式碼會將 UTC 轉換為美加中部標準時間。

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>將 UTC 轉換為當地時間

若要將 UTC 轉換為當地時間，呼叫<xref:System.DateTime.ToLocalTime%2A>方法的<xref:System.DateTime>物件您想要轉換的時間。 方法的確切行為取決於物件的值<xref:System.DateTime.Kind%2A>屬性，如下表所示。

| `DateTime.Kind`            | 轉換                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | 傳回<xref:System.DateTime>保持不變的值。                                      |
| `DateTimeKind.Unspecified` | 假設<xref:System.DateTime>值為 UTC，並將 UTC 轉換為當地時間。 |
| `DateTimeKind.Utc`         | 將轉換<xref:System.DateTime>為當地時間的值。                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>方法的行為相同`DateTime.ToLocalTime`方法。 它會採用單一參數，這是要轉換的日期和時間值。

您也可以轉換為當地時間的時間，在任何指定的時區中，使用`static`(`Shared` Visual Basic 中)<xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType>方法。 這項技術會在下一節中討論。

## <a name="converting-between-any-two-time-zones"></a>在兩個時區之間轉換

您可以使用下列兩個的任兩個時區之間轉換`static`(`Shared` Visual Basic 中) 的方法<xref:System.TimeZoneInfo>類別：

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  此方法的參數是日期和時間值轉換時，`TimeZoneInfo`物件，表示日期和時間值的時區和`TimeZoneInfo`物件，表示要轉換的日期和時間值的時區。

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  此方法的參數是時區的日期和時間值轉換、 的日期和時間值的時區識別項以及日期和時間值轉換為識別項。

這兩種方法需要<xref:System.DateTime.Kind%2A>要轉換的日期和時間值的屬性和<xref:System.TimeZoneInfo>代表其時區的物件或時區的識別項對應至另一部。 否則會擲回 <xref:System.ArgumentException>。 例如，如果`Kind`屬性的日期和時間值是`DateTimeKind.Local`，如果擲回例外狀況`TimeZoneInfo`做為參數傳遞給方法的物件是否不等於`TimeZoneInfo.Local`。 例外狀況也會擲回做為參數傳遞給方法的識別項是否不等於`TimeZoneInfo.Local.Id`。

下列範例會使用<xref:System.TimeZoneInfo.ConvertTime%2A>方法，將夏威夷標準時間轉換為當地時間。

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>轉換 DateTimeOffset 值

所表示的日期和時間值<xref:System.DateTimeOffset>物件不是完全時區感知物件會與其時區解除關聯時，因為它具現化。 不過，在許多情況下，應用程式只需要根據與 UTC 的兩個不同位移來轉換日期和時間，而不是根據特定時區的時間。 若要執行這項轉換，您可以呼叫目前的執行個體<xref:System.DateTimeOffset.ToOffset%2A>方法。 方法的單一參數是新的日期和時間值，這個方法會傳回值的位移。

例如，如果網頁使用者要求的日期和時間已知且序列化為字串 (格式為 MM/dd/yyyy hh:mm:ss zzzz)，則下列 `ReturnTimeOnServer` 方法會將這個日期和時間值轉換為 Web 伺服器上的時間和日期。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

如果將字串 "9/1/2007 5:32:07 -05:00" 傳遞給這個方法，代表時區中的日期和時間比 UTC 早五個小時，就會傳回 9/1/2007 3:32:07 AM -07:00，代表伺服器位於美國太平洋標準時區。

<xref:System.TimeZoneInfo>類別也包含的多載<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法，會使用時區轉換<xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>值。 方法的參數是<xref:System.DateTimeOffset>值以及時區的時間要轉換的參考。 方法呼叫傳回<xref:System.DateTimeOffset>值。 例如，`ReturnTimeOnServer`可以如下所示改寫上一個範例中的方法，來呼叫<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>方法。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>另請參閱

* <xref:System.TimeZoneInfo>
* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [尋找本機系統上定義的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
