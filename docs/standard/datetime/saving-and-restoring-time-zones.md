---
title: 儲存和還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea44b29eaa0273baadbf02093108bc4da912a3e5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106736"
---
# <a name="saving-and-restoring-time-zones"></a>儲存和還原時區

<xref:System.TimeZoneInfo>類別依賴登錄來取出預先定義的時區資料。 不過, 登錄是動態結構。 此外, 作業系統會使用登錄所包含的時區資訊, 主要用來處理目前年份的時間調整和轉換。 這對於依賴正確時區資料的應用程式有兩個主要的含意:

- 應用程式所需的時區可能未定義于登錄中, 或可能已從登錄中重新命名或移除。

- 在登錄中定義的時區可能缺少歷程記錄時區轉換所需之特定調整規則的相關資訊。

<xref:System.TimeZoneInfo>類別透過支援序列化 (儲存) 和還原序列化 (還原) 時區資料, 來解決這些限制。

## <a name="time-zone-serialization-and-deserialization"></a>時區序列化和還原序列化

藉由序列化和還原序列化時區資料來儲存和還原時區, 只需要兩個方法呼叫:

- 您可以藉由<xref:System.TimeZoneInfo>呼叫該物件的<xref:System.TimeZoneInfo.ToSerializedString%2A>方法來序列化物件。 方法不接受任何參數, 而且會傳回包含時區資訊的字串。

- 您可以<xref:System.TimeZoneInfo>藉由將該字串傳遞`static`至 (`Shared`在 Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>方法中, 將物件從序列化的字串還原序列化。

## <a name="serialization-and-deserialization-scenarios"></a>序列化和還原序列化案例

能夠將<xref:System.TimeZoneInfo>物件儲存 (或序列化) 至字串, 並還原 (或還原序列化) 它以供稍後使用, 同時增加了公用程式和<xref:System.TimeZoneInfo>類別的彈性。 本節將探討序列化和還原序列化最有用的一些情況。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>序列化和還原序列化應用程式中的時區資料

您可以視需要從字串還原序列化的時區。 如果從登錄中抓取的時區無法正確轉換特定日期範圍內的日期和時間, 應用程式可能會這麼做。 例如, Windows XP 登錄中的時區資料支援單一調整規則, 而 Windows Vista 登錄中所定義的時間區域通常會提供兩個調整規則的相關資訊。 這表示歷程記錄時間轉換可能不正確。 時區資料的序列化和還原序列化可以處理這項限制。

在下列範例中, 未定義<xref:System.TimeZoneInfo>任何調整規則的自訂類別, 以代表美國美國東部標準時區 (從1883到 1917), 在日光節約時間推出之前。 自訂時區會在具有全域範圍的變數中序列化。 時區轉換方法`ConvertUtcTime`會傳遞國際標準時間 (UTC) 時間來進行轉換。 如果日期和時間發生在1917或更早的版本中, 自訂的東部標準時區會從序列化字串還原, 並取代從登錄中抓取的時區。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>處理時區例外狀況

由於登錄是動態結構, 因此其內容會受到意外或刻意的修改。 這表示應該在登錄中定義且應用程式成功執行所需的時區不存在。 不支援時區序列化和還原序列化, 您只需要進行一些選擇, 但要處理<xref:System.TimeZoneNotFoundException>藉由結束應用程式所產生的。 不過, 藉由使用時區序列化和還原序列化, 您可以藉由<xref:System.TimeZoneNotFoundException>從序列化字串還原所需的時區來處理非預期的, 應用程式將會繼續執行。

下列範例會建立並序列化自訂的中央標準時區。 然後, 它會嘗試從登錄中取出中央標準時區。 如果抓取作業擲回<xref:System.TimeZoneNotFoundException> <xref:System.InvalidTimeZoneException>或, 則例外狀況處理常式會將時區還原序列化。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>儲存序列化字串, 並在需要時進行還原

先前的範例將時區資訊儲存至字串變數, 並在需要時加以還原。 不過, 包含序列化時區資訊的字串本身可以儲存在某些儲存媒體中, 例如外部檔案、內嵌在應用程式中的資源檔, 或登錄。 (請注意, 自訂時區的相關資訊應該與登錄中系統的時區金鑰分開儲存)。

以此方式儲存序列化的時區字串也會將時區建立常式與應用程式本身分開。 例如, 時區建立常式可以執行並建立資料檔, 其中包含應用程式可使用的歷程記錄時區資訊。 然後, 您可以在應用程式中安裝資料檔案, 並且可以開啟它, 並在應用程式需要時, 將它的一個或多個時區還原序列化。

如需使用內嵌資源來儲存序列化的時區資料的範例, 請參閱[如何:將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) , 以及[如何:從內嵌資源](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)還原時區。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
