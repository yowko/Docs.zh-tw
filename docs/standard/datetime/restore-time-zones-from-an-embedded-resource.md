---
title: 如何：從內嵌資源還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: b1cece13c88b3a49c9c4c90045a07dd009d4282d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281319"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>如何：從內嵌資源還原時區

本主題描述如何還原已儲存在資源檔中的時區。 如需儲存時區的相關資訊和指示，請參閱[如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md)。

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>從內嵌資源還原序列化 TimeZoneInfo 物件

1. 如果要抓取的時區不是自訂時區，請嘗試使用方法具現化該時區 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 。

2. 藉 <xref:System.Resources.ResourceManager> 由傳遞內嵌資源檔的完整名稱，以及包含資源檔之元件的參考，來具現化物件。

   如果您無法判斷內嵌資源檔的完整名稱，請使用[Ildasm （IL](../../framework/tools/ildasm-exe-il-disassembler.md)解譯器）來檢查元件的資訊清單。 `.mresource`專案會識別資源。 在範例中，資源的完整名稱是 `SerializeTimeZoneData.SerializedTimeZones` 。

   如果資源檔內嵌在包含時區具現化程式碼的相同元件中，您可以藉由呼叫 `static` （ `Shared` 在 Visual Basic）方法來抓取它的參考 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 。

3. 如果方法的呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 失敗，或是要具現化自訂時區，請呼叫方法來抓取包含序列化時區的字串 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> 。

4. 藉由呼叫方法，將時區資料還原序列化 <xref:System.TimeZoneInfo.FromSerializedString%2A> 。

## <a name="example"></a>範例

下列範例會將 <xref:System.TimeZoneInfo> 儲存在內嵌 .NET XML 資源檔中的物件還原序列化。

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

這段程式碼說明例外狀況處理，以確保 <xref:System.TimeZoneInfo> 應用程式所需的物件存在。 它會先嘗試使用方法，從登錄中抓取物件，以將它具現化 <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 。 如果無法具現化時區，則程式碼會從內嵌的資源檔抓取該時區。

由於自訂時區的資料（使用方法具現化的時區 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ）不會儲存在登錄中，因此程式碼不會呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 來為 Palmer、南極洲具現化時區。 相反地，它會立即尋找內嵌資源檔，以在呼叫方法之前，先取出包含時區資料的字串 <xref:System.TimeZoneInfo.FromSerializedString%2A> 。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 系統會將對 System.web 和 system.string 的參考加入至專案中。

- 匯入下列命名空間：

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
- [時區總覽](time-zone-overview.md)
- [如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md)
