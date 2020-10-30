---
title: 儲存和還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET], time zones
- serialization [.NET], time zones
- time zone objects [.NET], restoring
- saving time zones
- time zone objects [.NET], deserializing
- time zones [.NET], saving
- time zones [.NET], restoring
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
ms.openlocfilehash: 6a05bf4ce062a3f4e539e9b89779cb468b9782a6
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063387"
---
# <a name="saving-and-restoring-time-zones"></a>儲存和還原時區

<xref:System.TimeZoneInfo>類別會依賴登錄來取得預先定義的時區資料。 但是，登錄是動態結構。 此外，作業系統會使用登錄所包含的時區資訊，主要是用來處理目前年度的時間調整和轉換。 對於依賴精確時區資料的應用程式，這有兩個主要的含意：

- 應用程式所需的時區可能不會定義于登錄中，也可能已重新命名或從登錄中移除。

- 在登錄中定義的時區可能缺少歷程記錄時區轉換所需之特定調整規則的相關資訊。

<xref:System.TimeZoneInfo>類別透過其序列化支援來解決這些限制 (儲存) 和還原序列化 (還原時區資料) 。

## <a name="time-zone-serialization-and-deserialization"></a>時區序列化和還原序列化

藉由將時區資料序列化和還原序列化來儲存和還原時區，只需要兩個方法呼叫：

- 您可以藉 <xref:System.TimeZoneInfo> 由呼叫物件的方法來序列化物件 <xref:System.TimeZoneInfo.ToSerializedString%2A> 。 方法不接受任何參數，而且會傳回包含時區資訊的字串。

- 您可以將 <xref:System.TimeZoneInfo> 該字串傳遞至 `static` `Shared` Visual Basic) 方法中的 (，以從序列化字串還原序列化物件 <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> 。

## <a name="serialization-and-deserialization-scenarios"></a>序列化和還原序列化案例

可以儲存 (或將物件序列化) <xref:System.TimeZoneInfo> 至字串，以及還原 (或還原序列化) 以供稍後使用，以同時提高類別的公用程式和彈性 <xref:System.TimeZoneInfo> 。 本節將探討序列化和還原序列化最有用的部分情況。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>序列化和還原序列化應用程式中的時區資料

您可以視需要從字串還原序列化的時區。 如果從登錄取出的時區無法正確轉換特定日期範圍內的日期和時間，應用程式可能會這樣做。 例如，Windows XP 登錄區中的時區資料支援單一調整規則，而 Windows Vista 登錄中定義的時區通常會提供兩個調整規則的相關資訊。 這表示歷程記錄時間轉換可能不正確。 時區資料的序列化和還原序列化可以處理這項限制。

在下列範例中，所定義的自訂 <xref:System.TimeZoneInfo> 類別沒有調整規則，該類別代表從 1883 到 1917 年，日光節約時間推行之前的美國東部標準時間時區。 自訂時區會在具有全域範圍的變數中序列化。 時區轉換方法 `ConvertUtcTime` 會傳遞國際標準時間 (UTC) 次轉換。 如果日期和時間發生在1917或更早版本中，自訂的東部標準時區會從序列化字串還原，並取代從登錄取出的時區。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>處理時區例外狀況

由於登錄是動態結構，因此其內容可能會遭到意外或刻意修改。 這表示應該在登錄中定義，而且應用程式順利執行所需的時區可能不存在。 如果不支援時區序列化和還原序列化，您就不需要進行任何選擇，而是藉 <xref:System.TimeZoneNotFoundException> 由結束應用程式來處理結果。 不過，藉由使用時區序列化和還原序列化，您可以 <xref:System.TimeZoneNotFoundException> 從序列化字串還原所需的時區，以處理非預期的，應用程式將會繼續執行。

下列範例會建立並序列化自訂中央標準時區。 然後，它會嘗試從登錄中取出中央標準時區。 如果抓取作業擲回 <xref:System.TimeZoneNotFoundException> 或 <xref:System.InvalidTimeZoneException> ，則例外狀況處理常式會將時區還原序列化。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>儲存序列化字串並在需要時還原

先前的範例將時區資訊儲存至字串變數，並在需要時加以還原。 不過，包含序列化時區資訊的字串本身可以儲存在某些儲存媒體中，例如外部檔案、內嵌于應用程式中的資源檔或登錄。  (請注意，自訂時區的相關資訊應該與登錄中系統的時區金鑰分開儲存。 ) 

以這種方式儲存序列化的時區字串也會將時區建立常式與應用程式本身分開。 例如，時區建立常式可以執行和建立資料檔，其中包含應用程式可使用的歷史時區資訊。 然後，您可以使用應用程式來安裝資料檔案，而且可以在應用程式需要時加以開啟，並且可以將它的一個或多個時區還原序列化。

如需使用內嵌資源儲存序列化時區資料的範例，請參閱 [如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md) 和 [如何：從內嵌資源還原時區](restore-time-zones-from-an-embedded-resource.md)。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
