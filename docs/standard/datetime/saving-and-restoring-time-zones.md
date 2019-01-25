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
ms.openlocfilehash: 9d783f9e0d098e472dcf67aea394804d6eef2662
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569452"
---
# <a name="saving-and-restoring-time-zones"></a>儲存和還原時區

<xref:System.TimeZoneInfo>依賴登錄，以擷取預先定義的時區資料的類別。 不過，登錄是動態的結構。 此外，登錄包含時區資訊是由作業系統主要用來處理目前年度的時間調整和轉換。 這有兩個主要的含意，依賴精確的時區資料的應用程式：

* 應用程式需要的時區可能未定義在登錄中，或已重新命名或從登錄中移除。

* 在登錄中定義的時區可能缺少所需的歷程記錄的時區轉換的特定的調整規則的相關資訊。

<xref:System.TimeZoneInfo>類別會處理這些限制透過支援 （儲存） 的序列化和還原序列化 （還原） 的時區的資料。

## <a name="time-zone-serialization-and-deserialization"></a>時區序列化和還原序列化

儲存和還原時區的序列化和還原時區資料的序列化牽涉到兩個方法呼叫：

* 您可以將序列化<xref:System.TimeZoneInfo>藉由呼叫該物件的物件<xref:System.TimeZoneInfo.ToSerializedString%2A>方法。 方法不採用任何參數，並傳回字串，包含時區資訊。

* 您可以還原序列化<xref:System.TimeZoneInfo>在序列化的字串傳遞到該字串中的物件`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>方法。

## <a name="serialization-and-deserialization-scenarios"></a>序列化和還原序列化的案例

儲存 （或序列化） 的能力<xref:System.TimeZoneInfo>字串，以還原 （或還原序列化） 它以供稍後使用的物件會增加此公用程式及的彈性<xref:System.TimeZoneInfo>類別。 本節將探討一些中序列化和還原序列化是最有用的情況。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>序列化和還原序列化應用程式中的時區資料

在需要時，可以從字串還原序列化的時區。 應用程式可能會執行這項操作無法正確轉換的日期和時間在特定日期範圍內從登錄擷取時區時。 比方說，在 Windows XP 登錄時區資料都支援單一的調整規則，而通常是在 Windows Vista 登錄中定義的時區提供資訊大約兩個調整規則。 這表示歷程記錄的時間轉換可能不正確。 序列化和還原序列化的時區資料可以處理這項限制。

在下列範例中，自訂<xref:System.TimeZoneInfo>沒有調整規則的類別定義來代表美國美加東部標準時間時區從 1883年到 1917，美國地區的日光節約時間的推出之前。 自訂的時區會序列化具有全域範圍的變數中。 時區轉換方法， `ConvertUtcTime`，傳遞至轉換 Coordinated Universal Time (UTC) 時間。 發生時的日期和時間在 1917 年或更早版本，自訂的美加東部標準時區會還原序列化的字串，並取代從登錄擷取時區。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>時區例外狀況處理

因為登錄是動態結構，其內容會受到意外或刻意修改。 這表示，應該在登錄中定義和必要應用程式順利執行的時區可能不存在。 如果不支援時區序列化和還原序列化，您會有太多的選擇，但若要處理產生<xref:System.TimeZoneNotFoundException>以結束應用程式的方式。 不過，藉由使用時區序列化和還原序列化，您可以處理未預期<xref:System.TimeZoneNotFoundException>藉由還原序列化的字串，與應用程式所需的時區將會繼續執行。

下列範例會建立，並將自訂的中央標準時區的序列化。 它接著會嘗試從登錄擷取中央標準時區的時間。 如果擷取作業會擲回其中一個<xref:System.TimeZoneNotFoundException>或<xref:System.InvalidTimeZoneException>，例外狀況處理常式會還原序列化的時區。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>儲存序列化的字串，並將它需要時還原

先前的範例有儲存為字串變數的時區資訊，並在需要時還原。 不過，包含區域資訊本身儲存在儲存媒體中，例如外部檔案，將資源檔的序列化的時間字串內嵌在應用程式或登錄中。 （請注意，應該與系統的時區的登錄機碼中儲存的自訂時區的相關資訊）。

將序列化的時區字串儲存在這種方式，也會將時區建立常式從應用程式本身。 比方說，時區建立常式可以執行，並建立包含應用程式可以使用的歷程時區資訊的資料檔案。 可以是資料檔，則安裝應用程式時，您可以開啟和一或多個時區可以還原序列化時應用程式需要它們。

如需用來儲存已序列化的時區資料的內嵌的資源的範例，請參閱[How to:將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to:從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
