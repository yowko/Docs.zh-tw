---
title: 如何：將時區儲存到內嵌資源
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
ms.openlocfilehash: aaee4e82d09e8b604d06dadb5a5eefe8d2e1f307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123764"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>如何：將時區儲存到內嵌資源

時區感知應用程式通常需要有特定的時區。 不過，由於個別 <xref:System.TimeZoneInfo> 物件的可用性取決於儲存在本機系統登錄中的資訊，因此通常可能不會有可用的時區。 此外，使用 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法具現化之自訂時區的相關資訊不會與登錄中的其他時區資訊一起儲存。 若要確保這些時區在需要時可供使用，您可以藉由將它們序列化來加以儲存，並在稍後將它們還原序列化來加以還原。

一般來說，將 <xref:System.TimeZoneInfo> 物件序列化會與時區感知應用程式分開。 視用來保存序列化 <xref:System.TimeZoneInfo> 物件的資料存放區而定，可能會將時區資料序列化為安裝或安裝常式的一部分（例如，當資料儲存在登錄的應用程式索引鍵中），或做為之前執行之公用程式常式的一部分。最終的應用程式會經過編譯（例如，當序列化的資料儲存在 .NET XML 資源（.resx）檔案中時）。

除了以應用程式編譯的資源檔以外，還有其他幾個資料存放區可以用於時區資訊。 這些需求包括下列各項：

- 登錄。 請注意，應用程式應該使用自己的應用程式金鑰的子機碼來儲存自訂時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Nt\currentversion\time zones 區域的子機碼。

- 設定檔。

- 其他系統檔案。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>若要將時區序列化為 .resx 檔案來儲存該時區

1. 取出現有的時區或建立新的時區。

   若要取出現有的時區，請參閱[如何：存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)和[如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)。

   若要建立新的時區，請呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法的其中一個多載。 如需詳細資訊，請參閱[如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[如何：建立具有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。

2. 呼叫 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法，以建立包含時區資料的字串。

3. 將 .resx 檔案的名稱和（選擇性）路徑提供給 <xref:System.IO.StreamWriter> 類別的「函式」，以具現化 <xref:System.IO.StreamWriter> 物件。

4. 藉由將 <xref:System.IO.StreamWriter> 物件傳遞至 <xref:System.Resources.ResXResourceWriter> 類別的函式，以具現化 <xref:System.Resources.ResXResourceWriter> 物件。

5. 將時區的序列化字串傳遞至 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法。

6. 呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。

7. 呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。

8. 藉由呼叫它的 <xref:System.IO.StreamWriter.Close%2A> 方法來關閉 <xref:System.IO.StreamWriter> 物件。

9. 將產生的 .resx 檔案加入至應用程式的 Visual Studio 專案。

10. 使用 Visual Studio 中的 [**屬性**] 視窗，確保 .resx 檔案的 [**組建動作**] 屬性設定為 [**內嵌資源**]。

## <a name="example"></a>範例

下列範例會將代表中部標準時間的 <xref:System.TimeZoneInfo> 物件，以及代表 Palmer 站的 <xref:System.TimeZoneInfo> 物件序列化，並將時間南極洲至名為 SerializedTimeZones 的 .NET XML 資源檔。 中央標準時間通常會在登錄中定義;Palmer 站，南極洲是自訂的時區。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

這個範例會將 <xref:System.TimeZoneInfo> 物件序列化，使其可在編譯時期於資源檔中使用。

因為 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法會將完整的標頭資訊新增至 .NET XML 資源檔，所以不能用來將資源新增至現有的檔案。 這個範例會藉由檢查 SerializedTimeZones .resx 檔案來處理這項工作，如果存在的話，會將這兩個序列化時區以外的所有資源儲存至泛型 <xref:System.Collections.Generic.Dictionary%602> 物件。 然後會刪除現有的檔案，並將現有的資源新增至新的 SerializedTimeZones .resx 檔案。 序列化的時區資料也會新增至這個檔案。

資源的索引鍵（或**名稱**）欄位不應包含內嵌空格。 在將時區識別碼指派給資源檔之前，會呼叫 <xref:System.String.Replace%28System.String%2CSystem.String%29> 方法來移除所有內嵌空格。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 系統會將對 System.web 和 system.string 的參考加入至專案中。

- 匯入下列命名空間：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>請參閱

- [日期、時間及時區](../../../docs/standard/datetime/index.md)
- [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
- [操作說明：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
