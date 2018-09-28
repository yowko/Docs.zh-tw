---
title: 如何： 從內嵌資源還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99d38b336b5e655dd1c96682eec90c5fbe8469d6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421212"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>如何： 從內嵌資源還原時區

本主題描述如何還原已儲存在資源檔的時區。 如相關資訊與指示儲存時區，請參閱 <<c0> [ 如何： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)。

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>若要還原序列化從內嵌資源之 TimeZoneInfo 物件

1. 如果要擷取的時區不是自訂的時區，請試著它具現化使用<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法。

2. 具現化<xref:System.Resources.ResourceManager>物件，並傳遞的內嵌的資源檔和包含的資源檔的組件參考的完整限定的名稱。

   如果您無法判斷內嵌的資源檔的完整的名稱，請使用[Ildasm.exe （IL 反組譯工具）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)來檢查組件的資訊清單。 `.mresource`項目識別的資源。 在範例中，資源的完整的名稱是`SerializeTimeZoneData.SerializedTimeZones`。

   如果資源檔內嵌在相同的組件包含時區具現化程式碼中，您可以呼叫來擷取它的參考`static`(`Shared` Visual Basic 中)<xref:System.Reflection.Assembly.GetExecutingAssembly%2A>方法。

3. 如果在呼叫<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法失敗，或如果自訂的時區來具現化時，擷取字串，包含已序列化的時區，藉由呼叫<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>方法。

4. 時區資料還原序列化呼叫<xref:System.TimeZoneInfo.FromSerializedString%2A>方法。

## <a name="example"></a>範例

下列範例會還原序列化<xref:System.TimeZoneInfo>內嵌.NET XML 資源檔中儲存的物件。

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

此程式碼說明例外狀況處理，以確保<xref:System.TimeZoneInfo>應用程式所需的物件已存在。 它會先嘗試具現化<xref:System.TimeZoneInfo>物件擷取登錄使用<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法。 如果時區不能具現化，程式碼會擷取它從內嵌的資源檔。

因為資料的自訂時區 (具現化所使用的時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法) 不會儲存在登錄中，程式碼不會呼叫<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>來具現化時區 Palmer，南極大陸。 相反地，立即呈現內嵌的資源檔，來擷取字串，包含時區的資料，然後呼叫<xref:System.TimeZoneInfo.FromSerializedString%2A>方法。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* System.Windows.Forms.dll 和 System.Core.dll 的參考加入至專案。

* 下列命名空間會匯入：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>另請參閱

* [日期、時間和時區](../../../docs/standard/datetime/index.md)
* [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
* [操作說明：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
