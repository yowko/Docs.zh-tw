---
title: "儲存和還原時區"
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4e04de61ed5636d0102af694220dce06c256751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-restoring-time-zones"></a>儲存和還原時區

<xref:System.TimeZoneInfo>類別依賴登錄，以擷取預先定義的時區資料。 不過，登錄是動態的結構。 此外，登錄包含時區資訊會由作業系統主要用來處理時間調整並轉換為目前的年份。 這有兩個主要的含意，依賴精確的時區資料的應用程式：

* 不可定義為應用程式所需的時區，在登錄中，或已重新命名或從登錄中移除。

* 在登錄中定義的時區可能缺少所需的歷程記錄的時區轉換的特定的調整規則的相關資訊。

<xref:System.TimeZoneInfo>類別會處理這些限制透過其支援的序列化 （儲存） 和還原序列化 （還原） 的時區資料。

## <a name="time-zone-serialization-and-deserialization"></a>時區序列化和還原序列化

儲存和還原時區序列化和還原序列化的時區資料所牽涉到兩個方法呼叫：

* 您可以將序列化<xref:System.TimeZoneInfo>藉由呼叫該物件的物件<xref:System.TimeZoneInfo.ToSerializedString%2A>方法。 方法會採用任何參數，並傳回字串，包含時區資訊。

* 您可以還原序列化<xref:System.TimeZoneInfo>物件從已序列化的字串傳遞至該字串`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>方法。

## <a name="serialization-and-deserialization-scenarios"></a>序列化和還原序列化的案例

儲存 （或序列化） 的能力<xref:System.TimeZoneInfo>物件的字串和要還原 （或還原序列化） 它以供稍後使用增加的彈性和公用程式<xref:System.TimeZoneInfo>類別。 本節將說明部分的序列化和還原序列化是最有用的狀況。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>序列化和還原序列化應用程式中的時區資料

在需要時，可以從字串還原序列化的時區。 如果從登錄擷取時區是無法正確轉換的日期和時間的特定日期範圍內，應用程式可能此作業。 雖然通常是在 Windows Vista 登錄中定義的時區資訊提供兩種調整規則，例如，Windows XP 登錄中的時區資料支援單一的調整規則。 這表示歷程記錄的時間轉換可能不正確。 序列化和還原序列化的時區資料可以處理這項限制。

在下列範例中，自訂<xref:System.TimeZoneInfo>沒有調整規則的類別定義來代表美國美加東部標準時間區域從 1883年 1917 之前在美國境內的日光節約時間的簡介。 自訂的時區會序列化具有全域範圍的變數中。 時區轉換方法， `ConvertUtcTime`，傳遞至轉換 Coordinated Universal Time (UTC) 時間。 如果日期和時間發生在 1917 年或更早版本，自訂美加東部標準時間區域還原序列化字串，並取代從登錄擷取時區。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>時區例外狀況處理

由於登錄是動態的結構，其內容可能會有所意外或蓄意修改。 這表示時區，應該定義在登錄中，且成功執行應用程式需要可能不存在。 沒有時區序列化和還原序列化的支援，您有很少的選擇，但若要處理產生<xref:System.TimeZoneNotFoundException>藉由結束應用程式。 不過，藉由使用時區序列化和還原序列化，您可以處理未預期<xref:System.TimeZoneNotFoundException>藉由還原序列化的字串，與應用程式所需的時區將會繼續執行。

下列範例會建立，並序列化自訂中部標準時間區域。 它接著會嘗試從登錄擷取時區中部標準時間。 如果擷取作業會擲回其中<xref:System.TimeZoneNotFoundException>或<xref:System.InvalidTimeZoneException>，例外狀況處理常式會還原序列化的時區。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>儲存為序列化的字串，並將它在需要時還原

先前的範例有儲存為字串變數的時區資訊，而且需要時還原。 不過，包含序列化的時間區域資訊可以儲存在儲存媒體中，例如外部檔案，將資源檔中的字串會內嵌在應用程式或登錄。 （請注意自訂時區的相關資訊，應該儲存系統的時區為準的登錄機碼以外）。

將序列化的時區字串儲存在這種方式也會分隔時區建立常式與應用程式本身。 例如，時區建立常式可以執行，並建立資料檔案，其中包含應用程式可以使用的歷程時區資訊。 可以是資料檔，則安裝應用程式時，您可以開啟和一或多個時區可以還原序列化時應用程式需要它們。

如需用來儲存已序列化的時區資料的內嵌的資源的範例，請參閱[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

## <a name="see-also"></a>請參閱

[日期、時間和時區](../../../docs/standard/datetime/index.md)
