---
title: 作法：反覆存取日期和時間值
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8f56fcad74287e260c2989534e6bd4931ad646a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590025"
---
# <a name="how-to-round-trip-date-and-time-values"></a>作法：反覆存取日期和時間值
在許多應用程式中，日期和時間值的用途都是要明確地識別單一時間點。 本主題說明如何儲存並還原 <xref:System.DateTime> 值、<xref:System.DateTimeOffset> 值，以及具有時區資訊的日期和時間值，讓還原值能夠識別出與儲存值相同的時間。  
  
### <a name="to-round-trip-a-datetime-value"></a>若要反覆存取 DateTime 值  
  
1. 搭配 "o" 格式規範呼叫 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 方法，以將 <xref:System.DateTime> 值轉換為其字串表示。  
  
2. 將 <xref:System.DateTime> 值的字串表示儲存至檔案，或跨處理序、應用程式定義域或電腦界限進行傳遞。  
  
3. 擷取代表 <xref:System.DateTime> 值的字串。  
  
4. 呼叫 <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> 方法，然後傳遞 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> 作為 `styles` 參數值。  
  
 下列範例說明如何反覆存取 <xref:System.DateTime> 值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 反覆存取 <xref:System.DateTime> 值時，這項技術可以成功保留所有當地和全球通用時間的時間。 例如，如果當地的 <xref:System.DateTime> 值儲存在美國太平洋標準時區的系統上，但該值在美國中央標準時區的系統上還原，則還原的日期和時間會比原始時間晚兩個小時，以反映出兩個時區之間的時間差異。 不過，針對未指定的時間，這項技術並不一定準確。 所有 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind.Unspecified> 的 <xref:System.DateTime> 值，都會被視為當地時間。 如果不是這種狀況，<xref:System.DateTime> 就無法成功識別出正確的時間點。 這項限制的因應措施，是將日期和時間值與其儲存和還原作業的時區緊密結合。  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>若要反覆存取 DateTimeOffset 值  
  
1. 搭配 "o" 格式規範呼叫 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> 方法，以將 <xref:System.DateTimeOffset> 值轉換為其字串表示。  
  
2. 將 <xref:System.DateTimeOffset> 值的字串表示儲存至檔案，或跨處理序、應用程式定義域或電腦界限進行傳遞。  
  
3. 擷取代表 <xref:System.DateTimeOffset> 值的字串。  
  
4. 呼叫 <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> 方法，然後傳遞 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> 作為 `styles` 參數值。  
  
 下列範例說明如何反覆存取 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 這項技術一律會明確地將 <xref:System.DateTimeOffset> 值識別為單一時間點。 接著可呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> 方法來將值轉換為國際標準時間 (UTC)，或者可以呼叫 <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> 或 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> 方法來將它轉換為特定時區的時間。 這項技術有個主要限制：在表示特定時區之時間的 <xref:System.DateTimeOffset> 值上執行日期和時間算術時，可能不會產生該時區的精確結果。 這是因為在將 <xref:System.DateTimeOffset> 值具現化時，就會解除它與其時區的關聯。 因此，當您執行日期和時間計算時，就無法再套用該時區的調整規則。 若要解決這個問題，您可以定義自訂類型，以包含日期與時間值及其隨附的時區。  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>使用其時區反覆存取日期和時間值  
  
1. 定義包含兩個欄位的類別或結構。 第一個欄位是 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 物件，而第二個是 <xref:System.TimeZoneInfo> 物件。 下列範例是這種類型的簡單版本。  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2. 使用 <xref:System.SerializableAttribute> 屬性來標示類別。  
  
3. 使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> 方法來將物件序列化。  
  
4. 使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> 方法來還原物件。  
  
5. 將還原序列化的物件轉型 (在 C# 中) 或轉換 (在 Visual Basic 中) 為適當類型的物件。  
  
 下列範例說明如何反覆存取會儲存日期和時間及時區資訊的物件。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 假如組合的日期和時間及時區物件的實作不允許日期值變得與時區值不同步，這項技術應該在其儲存和還原前後，一律明確地反映正確的時間點。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
- 使用 C# `using` 陳述式或 Visual Basic `Imports` 陳述式匯入下列命名空間：  
  
    - <xref:System> (僅限 C#)。  
  
    - <xref:System.Globalization?displayProperty=nameWithType>.  
  
    - <xref:System.IO?displayProperty=nameWithType>.  
  
    - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
- 每個程式碼範例 (`DateInTimeZone` 類別除外) 都應包含於類別或 Visual Basic 模組中，並從 `Main` 方法進行呼叫。  
  
## <a name="see-also"></a>另請參閱

- [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)
- [在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)
- [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
