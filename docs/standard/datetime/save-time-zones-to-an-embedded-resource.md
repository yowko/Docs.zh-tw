---
title: 作法：將時區儲存到內嵌資源
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], saving
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
ms.openlocfilehash: 23f86076b2858404f3dbc900d8c40a6509abe8db
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817597"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>作法：將時區儲存到內嵌資源

時區感知應用程式通常需要存在特定的時區。 不過，由於個別物件的可用性 <xref:System.TimeZoneInfo> 取決於儲存在本機系統登錄中的資訊，甚至可能不會有可能存在的可用時區。 此外，使用方法具現化之自訂時區的相關資訊 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會與登錄中的其他時區資訊一起儲存。 若要確保這些時區在需要時可供使用，您可以將它們序列化，並在稍後還原序列化它們來還原它們。

一般來說，將物件序列化是 <xref:System.TimeZoneInfo> 在時區感知應用程式以外的時間進行。 依據用來保存序列化物件的資料存放區 <xref:System.TimeZoneInfo> 而定，時區資料可能會在安裝或安裝常式中序列化 (例如，將資料儲存在登錄) 的應用程式索引鍵中，或做為在編譯最終應用程式之前執行的公用程式常式的一部分 (例如，當序列化資料儲存在 .NET XML 資源 ( .resx) 檔案) 時。

除了與應用程式一起編譯的資源檔之外，還有其他數個數據存放區可用於時區資訊。 其中包括下列各項：

- 登錄。 請注意，應用程式應該使用自己的應用程式金鑰的子機碼來儲存自訂的時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones 的子機碼。

- 設定檔案。

- 其他系統檔案。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>將時區序列化為 .resx 檔來儲存時區

1. 取出現有的時區，或建立新的時區。

   若要取出現有的時區，請參閱 [如何：存取預先定義的 UTC 和當地時區物件](access-utc-and-local.md) 和 [如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)。

   若要建立新的時區，請呼叫方法的其中一個多載 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。 如需詳細資訊，請參閱 [如何：建立沒有調整規則的時區](create-time-zones-without-adjustment-rules.md) 和 [如何：建立具有調整規則的](create-time-zones-with-adjustment-rules.md)時區。

2. 呼叫 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法，以建立包含時區資料的字串。

3. 將 .resx 檔案的 <xref:System.IO.StreamWriter> 名稱和選擇性路徑提供給類別的函式，以具現化物件 <xref:System.IO.StreamWriter> 。

4. 將 <xref:System.Resources.ResXResourceWriter> <xref:System.IO.StreamWriter> 物件傳遞給類別的函式，以具現化物件 <xref:System.Resources.ResXResourceWriter> 。

5. 將時區的序列化字串傳遞給 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法。

6. 呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。

7. 呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。

8. 藉 <xref:System.IO.StreamWriter> 由呼叫其方法來關閉物件 <xref:System.IO.StreamWriter.Close%2A> 。

9. 將產生的 .resx 檔加入至應用程式的 Visual Studio 專案。

10. 使用 Visual Studio 中的 [ **屬性** ] 視窗，確認 .resx 檔案的 [ **組建動作** ] 屬性設定為 [ **內嵌資源**]。

## <a name="example"></a>範例

下列範例 <xref:System.TimeZoneInfo> 會將代表中部標準時間的物件序列化，並將代表 <xref:System.TimeZoneInfo> Palmer 工作站的物件（南極洲 Time）序列化為 SerializedTimeZones .RESX 的 .net XML 資源檔。 中部標準時間通常定義于登錄中;Palmer 站，南極洲是自訂的時區。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

此範例 <xref:System.TimeZoneInfo> 會將物件序列化，讓它們在編譯時期可在資源檔中使用。

因為 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法會將完整的標頭資訊加入至 .NET XML 資源檔，所以無法用來將資源新增至現有的檔案。 此範例會藉由檢查 SerializedTimeZones .resx 檔案來處理此情況，如果存在，則會將其所有的資源（除了兩個序列化的時區以外）儲存至泛型 <xref:System.Collections.Generic.Dictionary%602> 物件。 然後會刪除現有的檔案，並將現有的資源新增至新的 SerializedTimeZones .resx 檔。 序列化的時區資料也會新增至此檔案。

資源的索引鍵 (或 **名稱**) 欄位不應包含內嵌空格。 在 <xref:System.String.Replace%28System.String%2CSystem.String%29> 指派給資源檔之前，會呼叫方法，以移除時區識別碼中的所有內嵌空格。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 將 System.Windows.Forms.dll 和 System.Core.dll 的參考新增至專案。

- 匯入下列命名空間：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>請參閱

- [日期、時間和時區](index.md)
- [時區概觀](time-zone-overview.md)
- [如何：從內嵌資源還原時區](restore-time-zones-from-an-embedded-resource.md)
