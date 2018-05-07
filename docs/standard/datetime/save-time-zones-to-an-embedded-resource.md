---
title: 如何： 將時區儲存到內嵌資源
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
ms.openlocfilehash: 4dd7e6db78b76d737cb4646c2fad79d96fb60aee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>如何： 將時區儲存到內嵌資源

時區感知應用程式通常需要有特定的時區。 不過，因為個別的可用性<xref:System.TimeZoneInfo>物件相依於儲存在本機系統登錄中的資訊，甚至是通常可用的時區可能不存在。 此外，自訂時區的相關資訊，將使用具現化<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會儲存在登錄中的其他時區資訊。 若要確保這些時間區域，可在必要時，您可以序列化，將它們儲存，並稍後再還原其還原序列化。

一般來說，序列化<xref:System.TimeZoneInfo>物件除了時區感知的應用程式，就會發生。 根據用來保存已序列化的資料存放區<xref:System.TimeZoneInfo>物件，可能會序列化時區的資料，設定或安裝常式 （例如，當資料儲存在登錄的應用程式金鑰），或執行公用程式常式之前完成的應用程式會編譯 （例如，當序列化的資料儲存在.NET XML 資源 (.resx) 檔）。

除了與應用程式會編譯資源檔，數個其他資料存放區可以用於時區資訊。 這些需求包括下列各項：

* 登錄中。 請注意，應用程式應該使用它自己的應用程式金鑰的子機碼來儲存自訂的時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time 區域的子機碼。

* 組態檔。

* 其他系統檔案。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>要儲存時區序列化至.resx 檔案

1. 擷取現有的時區，或建立新的時區。

   若要擷取現有的時區，請參閱[如何： 存取預先定義的 UTC 與本地時間區域物件](../../../docs/standard/datetime/access-utc-and-local.md)和[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)。

   若要建立新的時區，請呼叫其中一個多載的<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法。 如需詳細資訊，請參閱[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。

2. 呼叫<xref:System.TimeZoneInfo.ToSerializedString%2A>方法來建立字串，包含時區的資料。

3. 具現化<xref:System.IO.StreamWriter>藉由提供名稱和選擇性的.resx 檔案的路徑物件<xref:System.IO.StreamWriter>類別建構函式。

4. 具現化<xref:System.Resources.ResXResourceWriter>物件，並傳遞<xref:System.IO.StreamWriter>物件<xref:System.Resources.ResXResourceWriter>類別建構函式。

5. 傳遞時區的序列化字串<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>方法。

6. 呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。

7. 呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。

8. 關閉<xref:System.IO.StreamWriter>物件藉由呼叫其<xref:System.IO.StreamWriter.Close%2A>方法。

9. 加入應用程式的 Visual Studio 專案中產生的.resx 檔。

10. 使用**屬性**視窗在 Visual Studio 中，請確定.resx 檔**建置動作**屬性設定為**內嵌資源**。

## <a name="example"></a>範例

下列範例會序列化<xref:System.TimeZoneInfo>中部標準時間表示的物件和<xref:System.TimeZoneInfo>物件，代表名為 SerializedTimeZones.resx.NET XML 資源檔 Palmer 站台、 目前時間。 中部標準時間通常被定義在登錄中。Palmer 站台目前是自訂的時區。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

這個範例會序列化<xref:System.TimeZoneInfo>物件，以便他們可以使用資源檔中在編譯時間。

因為<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>方法將完整的標頭資訊.NET XML 資源檔，但它不能將資源加入至現有的檔案。 此範例會藉由檢查 SerializedTimeZones.resx 檔案處理這，如果存在的話，其所有資源以外的儲存兩個都序列化泛型時區<xref:System.Collections.Generic.Dictionary%602>物件。 現有的檔案會被刪除，現有的資源新增至新的 SerializedTimeZones.resx 檔案。 已序列化的時區資料也會加入至這個檔案。

索引鍵 (或**名稱**) 的資源欄位不能包含內嵌的空格。 <xref:System.String.Replace%28System.String%2CSystem.String%29>方法呼叫之前就會指派給資源檔，時區識別項中移除所有內嵌的空格。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* System.Windows.Forms.dll 和 System.Core.dll 的參考加入專案。

* 應該是匯入下列命名空間：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
