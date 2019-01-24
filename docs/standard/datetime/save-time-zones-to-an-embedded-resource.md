---
title: HOW TO：將時區儲存到內嵌資源
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592870"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>HOW TO：將時區儲存到內嵌資源

時區感知的應用程式通常需要為特定時區的目前狀態。 不過，因為個別的可用性<xref:System.TimeZoneInfo>物件取決於儲存在本機系統登錄中的資訊，甚至是通常可用的時區可能不存在。 此外，自訂時區的相關資訊，將使用具現化<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會儲存在登錄中的其他時區資訊。 若要確保的這些時間的時區都可在必要時，序列化，就可以將它儲存它們即可稍後再還原序列化其還原。

一般而言，序列化<xref:System.TimeZoneInfo>物件除了時區感知的應用程式，就會發生。 根據資料存放區用來保存序列化<xref:System.TimeZoneInfo>物件時，可能會序列化時區的資料，設定或安裝的常式 （例如，當資料儲存在登錄的應用程式金鑰），或執行公用程式常式之前 （例如，當序列化的資料儲存在.NET XML 資源 (.resx) 檔），最終的應用程式會編譯。

除了編譯與應用程式的資源檔，數個其他資料存放區可用的時區資訊。 這些需求包括下列各項：

* 登錄中。 請注意，應用程式應該使用它自己的應用程式金鑰的子機碼來儲存自訂的時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones 的子機碼。

* 組態檔。

* 其他系統檔案。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>序列化至.resx 檔案所儲存的時區

1. 擷取現有的時區，或建立新的時區。

   若要擷取現有的時區，請參閱[How to:存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)和[How to:將 TimeZoneInfo 物件具現化](../../../docs/standard/datetime/instantiate-time-zone-info.md)。

   若要建立新的時區，請呼叫其中一個多載<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法。 如需詳細資訊，請參閱[＜How to：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to:建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。

2. 呼叫<xref:System.TimeZoneInfo.ToSerializedString%2A>方法用來建立字串，包含時區的資料。

3. 具現化<xref:System.IO.StreamWriter>藉由提供名稱和選擇性的.resx 檔案的路徑物件<xref:System.IO.StreamWriter>類別建構函式。

4. 具現化<xref:System.Resources.ResXResourceWriter>物件，並傳遞<xref:System.IO.StreamWriter>物件到<xref:System.Resources.ResXResourceWriter>類別建構函式。

5. 傳遞時區的序列化字串<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>方法。

6. 呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。

7. 呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。

8. 關閉<xref:System.IO.StreamWriter>物件，藉由呼叫其<xref:System.IO.StreamWriter.Close%2A>方法。

9. 將產生的.resx 檔案新增至應用程式的 Visual Studio 專案。

10. 使用**屬性**視窗，在 Visual Studio 中，請確定.resx 檔**建置動作**屬性設定為**內嵌資源**。

## <a name="example"></a>範例

下列範例會序列化<xref:System.TimeZoneInfo>物件，表示中部標準時間和<xref:System.TimeZoneInfo>物件，表示.NET XML 資源檔名為 SerializedTimeZones.resx 帕麥站，南極大陸的時間。 中部標準時間通常被定義在登錄中;帕麥站，南極大陸是自訂的時區。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

此範例會序列化<xref:System.TimeZoneInfo>物件，讓它們可在資源檔編譯時期。

因為<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>方法將完整的標頭資訊新增至.NET XML 資源檔，它不能將資源新增至現有的檔案。 範例會處理這藉由檢查 SerializedTimeZones.resx 檔案，且若有的話，儲存其所有資源以外的其他兩個都序列化成泛型的時區<xref:System.Collections.Generic.Dictionary%602>物件。 現有的檔案會被刪除，現有的資源會新增至新的 SerializedTimeZones.resx 檔案。 序列化的時區資料也會加入至這個檔案。

索引鍵 (或**名稱**) 資源的欄位不應包含內嵌的空格。 <xref:System.String.Replace%28System.String%2CSystem.String%29>呼叫方法先指派給資源檔，時區識別項中移除所有內嵌的空格。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* System.Windows.Forms.dll 和 System.Core.dll 的參考加入至專案。

* 下列命名空間會匯入：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
- [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
