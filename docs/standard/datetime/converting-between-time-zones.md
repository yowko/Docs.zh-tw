---
title: "在各時區間轉換時間"
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
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58ed01520a9bbed53d32fc10e48a479e68f6ef7c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="converting-times-between-time-zones"></a>在各時區間轉換時間

對於使用日期和時間來處理時區差異的任何應用程式，它會變得越來越重要。 應用程式不會再假設，隨時可以表示的當地時間，這是從可用的時間<xref:System.DateTime>結構。 例如，顯示美國東部目前時間的網頁對東亞地區的客戶不具公信力。 本主題說明如何將時間從一個時區轉換成另一個，以及如何將轉換<xref:System.DateTimeOffset>具有有限的時區感知的值。

## <a name="converting-to-coordinated-universal-time"></a>轉換為國際標準時間

國際標準時間 (UTC) 是高精確度且不可部分完成的時間標準。 全世界的時區都會表示為與 UTC 的正或負位移。 因此，UTC 提供一種無時區或時區中性時間。 跨電腦的日期和時間可攜性十分重要時，建議使用 UTC 時間。 (如詳細資訊和其他使用日期和時間的最佳作法，請參閱[撰寫程式碼使用.NET Framework 中的日期時間的最佳作法](http://go.microsoft.com/fwlink/?LinkId=92342)。)將個別時區轉換為 UTC 可輕鬆地比較時間。

> [!NOTE]
> 您也可以序列化<xref:System.DateTimeOffset>結構，以明確地代表單一點的時間。 因為<xref:System.DateTimeOffset>物件儲存以及其與 UTC 相差的日期和時間值，但是它們總是代表特定點的關聯性中的時間為 UTC。

將時間轉換成 UTC 的最簡單方式是呼叫`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>方法。 確切方法所執行的轉換取決於值`dateTime`參數的<xref:System.DateTime.Kind%2A>屬性，如下表所示。

| `DateTime.Kind`            | 轉換                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | 將當地時間轉換為 UTC。                                                    |
| `DateTimeKind.Unspecified` | 假設 `dateTime` 參數是當地時間，並將當地時間轉換為 UTC。 |
| `DateTimeKind.Utc`         | 傳回未變更的 `dateTime` 參數。                                    |

下列程式碼會將目前當地時間轉換為 UTC，並將結果顯示到主控台。

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>方法不一定會產生相同的結果<xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType>和<xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType>方法。 如果主機系統的本機時間區域包含多項調整規則，<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>適當的規則適用於特定日期和時間。 另兩種方法一律會套用最新的調整規則。

如果日期和時間值不代表當地時間或 UTC，<xref:System.DateTime.ToUniversalTime%2A>方法可能會傳回錯誤的結果。 不過，您可以使用<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>方法，從指定的時區將轉換的日期和時間。 (如需詳細資訊，擷取<xref:System.TimeZoneInfo>物件，表示目的地時區中，請參閱[尋找本機系統上所定義的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)。)下列程式碼會使用<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>方法，將美加東部標準時間轉換為 UTC。

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

請注意，這個方法會擲回<xref:System.ArgumentException>如果<xref:System.DateTime>物件的<xref:System.DateTime.Kind%2A>屬性與時區不相符。 如果發生不符的情形<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind?displayProperty=nameWithType>但<xref:System.TimeZoneInfo>物件不代表本地時區，或者如果<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind?displayProperty=nameWithType>但<xref:System.TimeZoneInfo>物件不等於<xref:System.DateTimeKind?displayProperty=nameWithType>。

所有這些方法需要<xref:System.DateTime>值做為參數和傳回<xref:System.DateTime>值。 如<xref:System.DateTimeOffset>值<xref:System.DateTimeOffset>結構有<xref:System.DateTimeOffset.ToUniversalTime%2A>執行個體方法，將日期和時間的目前執行個體轉換成 UTC。 下列範例會呼叫<xref:System.DateTimeOffset.ToUniversalTime%2A>方法，將本地時間和數個其他的時間轉換為國際標準時間 (UTC)。

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>將 UTC 轉換為指定的時區

若要轉換 UTC 到本地時間，請參閱 「 轉換 UTC 到本地時間 」 一節。 若要轉換的時間，以您指定任何時區 UTC，呼叫<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>方法。 這個方法採用兩個參數：

* 要轉換的 UTC。 這必須是<xref:System.DateTime>值其<xref:System.DateTime.Kind%2A>屬性設定為<xref:System.DateTimeKind?displayProperty=nameWithType>或<xref:System.DateTimeKind?displayProperty=nameWithType>。

* 要將 UTC 轉換為的時區。

下列程式碼會將 UTC 轉換為美加中部標準時間。

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>將 UTC 轉換為當地時間

若要轉換為本地時間的 UTC，呼叫<xref:System.DateTime.ToLocalTime%2A>方法<xref:System.DateTime>物件您想要轉換的時間。 方法的確切行為取決於物件的值<xref:System.DateTime.Kind%2A>屬性，如下表所示。

| `DateTime.Kind`            | 轉換                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | 傳回<xref:System.DateTime>值保持不變。                                      |
| `DateTimeKind.Unspecified` | 假設<xref:System.DateTime>值為 UTC，並將轉換為本地時間的 UTC。 |
| `DateTimeKind.Utc`         | 將轉換<xref:System.DateTime>值以本地時間。                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>方法的行為即會相同與`DateTime.ToLocalTime`方法。 它會採用單一參數，這是要轉換的日期和時間值。

您也可以轉換為本地時間中任何指定的時區的時間，使用`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType>方法。 這項技術會在下一節中討論。

## <a name="converting-between-any-two-time-zones"></a>在兩個時區之間轉換

您可以使用下列兩個其中任兩個時區之間進行轉換`static`(`Shared`在 Visual Basic 中) 的方法<xref:System.TimeZoneInfo>類別：

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  這個方法的參數是要轉換的日期和時間值`TimeZoneInfo`物件，表示日期和時間值的時區和`TimeZoneInfo`物件，表示要轉換的日期和時間值的時區。

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  這個方法的參數是要轉換的日期和時間值的日期和時間值轉換、 日期和時間值的時區的識別項和時區的識別項。

這兩種方法需要<xref:System.DateTime.Kind%2A>要轉換的日期和時間值的屬性和<xref:System.TimeZoneInfo>代表時區的物件或時區的識別項對應至另一個。 否則，<xref:System.ArgumentException>就會擲回。 例如，如果`Kind`的日期和時間值的屬性是`DateTimeKind.Local`，如果將會擲回例外狀況`TimeZoneInfo`做為參數傳遞給方法的物件是否不等於`TimeZoneInfo.Local`。 擲回例外狀況也做為參數傳遞給方法的識別項是否不等於`TimeZoneInfo.Local.Id`。

下列範例會使用<xref:System.TimeZoneInfo.ConvertTime%2A>方法，將從夏威夷標準時間轉換為本地時間。

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>轉換 DateTimeOffset 值

所表示的日期和時間值<xref:System.DateTimeOffset>物件並不完全時區感知，因為該物件會與其時區解除關聯時具現化。 不過，在許多情況下，應用程式只需要根據與 UTC 的兩個不同位移來轉換日期和時間，而不是根據特定時區的時間。 若要執行這項轉換，您可以呼叫目前的執行個體<xref:System.DateTimeOffset.ToOffset%2A>方法。 方法的參數，就是新的日期和時間值，這個方法會傳回值的位移。

例如，如果網頁使用者要求的日期和時間已知且序列化為字串 (格式為 MM/dd/yyyy hh:mm:ss zzzz)，則下列 `ReturnTimeOnServer` 方法會將這個日期和時間值轉換為 Web 伺服器上的時間和日期。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

如果將字串 "9/1/2007 5:32:07 -05:00" 傳遞給這個方法，代表時區中的日期和時間比 UTC 早五個小時，就會傳回 9/1/2007 3:32:07 AM -07:00，代表伺服器位於美國太平洋標準時區。

<xref:System.TimeZoneInfo>類別也包含的多載<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法，執行具有時區轉換<xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>值。 方法的參數是<xref:System.DateTimeOffset>值以及所要轉換的時間的時區的參考。 方法呼叫傳回<xref:System.DateTimeOffset>值。 例如，`ReturnTimeOnServer`前一個範例中的方法可以改寫，如下所示呼叫<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>方法。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>另請參閱

<xref:System.TimeZoneInfo>[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[尋找本機系統上所定義的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
