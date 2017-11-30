---
title: "如何：反覆存取日期和時間值"
ms.custom: 
ms.date: 03/30/2017
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>如何：反覆存取日期和時間值
在許多應用程式中，日期和時間值的用途都是要明確地識別單一時間點。 本主題說明如何儲存和還原<xref:System.DateTime>值<xref:System.DateTimeOffset>值和時間的日期和時間值區域資訊，以便還原的值識別儲存的值在同時間。  
  
### <a name="to-round-trip-a-datetime-value"></a>若要反覆存取 DateTime 值  
  
1.  轉換<xref:System.DateTime>值至它的字串表示，藉由呼叫<xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>使用"o"格式規範的方法。  
  
2.  儲存的字串表示<xref:System.DateTime>值至檔案，或跨處理序、 應用程式網域或電腦界限傳遞它。  
  
3.  擷取字串，代表<xref:System.DateTime>值。  
  
4.  呼叫<xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>方法，然後傳遞<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>做為值`styles`參數。  
  
 下列範例說明如何來回<xref:System.DateTime>值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 當往返<xref:System.DateTime>值，這項技術成功會保留所有本機和國際時間的時間。 例如，如果本機<xref:System.DateTime>在美國太平洋時區系統上儲存值太平洋標準時區的系統上，但該值在美國中央標準時區的系統上還原，則還原的日期和時間會比原始時間晚兩個小時，以反映出兩個時區之間的時間差異。 不過，針對未指定的時間，這項技術並不一定準確。 所有<xref:System.DateTime>值其<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified>會視為它們都是當地時間。 如果這不是如此，<xref:System.DateTime>不就會成功地識別正確的點的時間。 這項限制的因應措施，是將日期和時間值與其儲存和還原作業的時區緊密結合。  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>若要反覆存取 DateTimeOffset 值  
  
1.  轉換<xref:System.DateTimeOffset>值至它的字串表示，藉由呼叫<xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>使用"o"格式規範的方法。  
  
2.  儲存的字串表示<xref:System.DateTimeOffset>值至檔案，或跨處理序、 應用程式網域或電腦界限傳遞它。  
  
3.  擷取字串，代表<xref:System.DateTimeOffset>值。  
  
4.  呼叫<xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>方法，然後傳遞<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>做為值`styles`參數。  
  
 下列範例說明如何來回<xref:System.DateTimeOffset>值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 這項技術一律明確地識別<xref:System.DateTimeOffset>為單一時間點的值。 值可以再轉換為國際標準時間 (UTC) 藉由呼叫<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>方法，或它可以轉換為特定時區的時間呼叫<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType>或<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法。 這項技術的主要限制是該日期和時間執行算術、<xref:System.DateTimeOffset>值，表示為特定時區的時間可能不會產生精確的結果，該時區。 這是因為當<xref:System.DateTimeOffset>產生值時，它會與其時區解除關聯。 因此，當您執行日期和時間計算時，就無法再套用該時區的調整規則。 若要解決這個問題，您可以定義自訂類型，以包含日期與時間值及其隨附的時區。  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>反覆存取日期和時間值具有時區  
  
1.  定義類別或結構包含兩個欄位。 第一個欄位是<xref:System.DateTime>或<xref:System.DateTimeOffset>物件，而第二個是<xref:System.TimeZoneInfo>物件。 下列範例是這類類型的簡單版本。  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  將此類別標示與<xref:System.SerializableAttribute>屬性。  
  
3.  序列化物件使用<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>方法。  
  
4.  物件使用還原<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>方法。  
  
5.  轉型 （C# 中） 或者 （在 Visual Basic) 已還原序列化的物件轉換成適當型別的物件。  
  
 下列範例說明如何反覆存取的物件會儲存日期和時間以及時區資訊。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 這項技術應該一律明確地反映正確的時間兩者之前和之後儲存和還原，結合的日期和時間以及時區物件的實作不允許的日期值，成為與同步處理點時區值。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
-   使用 C# 匯入下列命名空間`using`陳述式或[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]`Imports`陳述式：  
  
    -   <xref:System>（僅限 C#)。  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   對 System.Core.dll 的參考。  
  
-   每個程式碼範例中，除了`DateInTimeZone`類別，應該包含在類別或 Visual Basic 的 module，包裝在方法中，並從呼叫`Main`方法。  
  
## <a name="see-also"></a>另請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
