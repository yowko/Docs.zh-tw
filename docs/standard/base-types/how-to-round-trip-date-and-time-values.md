---
title: "如何：反覆存取日期和時間值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "反覆存取日期和時間值"
  - "日期 [.NET Framework]、反覆存取值"
  - "時區 [.NET Framework]、反覆存取日期和時間值"
  - "時間 [.NET Framework]、反覆存取值"
  - "格式化字串 [.NET Framework]、反覆存取值"
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：反覆存取日期和時間值
在許多應用程式中，日期和時間值是用來明確識別單一時間點。  本主題示範如何儲存和還原 <xref:System.DateTime> 值、<xref:System.DateTimeOffset> 值以及具備時區資訊的日期和時間值，如此一來，還原的值就可將相同的時間識別為儲存的值。  
  
### 若要反覆存取 DateTime 值  
  
1.  呼叫 <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> 方法加上 "o" 格式規範，將 <xref:System.DateTime> 值轉換成其字串表示。  
  
2.  將 <xref:System.DateTime> 值的字串表示儲存到檔案，或跨程序、應用程式定義域或電腦界限傳遞。  
  
3.  擷取表示 <xref:System.DateTime> 值的字串。  
  
4.  呼叫 <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> 方法，並將 <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> 當做 `styles` 參數的值傳遞。  
  
 下列範例示範如何反覆存取 <xref:System.DateTime> 值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 反覆存取 <xref:System.DateTime> 值時，此方式能成功保存所有本地和國際標準時間的時間。  例如，如果區域 <xref:System.DateTime> 值儲存在美國太平洋標準時區系統中，以及還原到美國中央標準時區的系統中，還原的日期和時間就會是原始時間再加上兩小時，反映出兩個時區之間的時差。  不過，這種方式對未指定的時間不一定精確。  <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind> 的所有 <xref:System.DateTime> 值都會視為是本地時間。  若非如此，<xref:System.DateTime> 將無法成功識別正確的時間點。  為解決此限制，在進行儲存和還原作業時，可以將日期和時間值與其時區緊密結合在一起。  
  
### 若要反覆存取 DateTimeOffset 值  
  
1.  呼叫 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=fullName> 方法加上 "o" 格式規範，將 <xref:System.DateTimeOffset> 值轉換成其字串表示。  
  
2.  將 <xref:System.DateTimeOffset> 值的字串表示儲存到檔案，或跨程序、應用程式定義域或電腦界限傳遞。  
  
3.  擷取表示 <xref:System.DateTimeOffset> 值的字串。  
  
4.  呼叫 <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> 方法，並將 <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> 當做 `styles` 參數的值傳遞。  
  
 下列範例示範如何反覆存取 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 此方式永遠能將 <xref:System.DateTimeOffset> 值明確識別為單一時間點。  此值接著可以藉由呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=fullName> 方法轉換為 Coordinated Universal Time \(UTC\)，或可以藉由呼叫 <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=fullName> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> 方法轉換為特定時區的時間。  此方式的主要限制在於，如果在表示特定時區時間的 <xref:System.DateTimeOffset> 值上執行日期和時間運算，可能不會產生該時區的精確結果。  這是因為當 <xref:System.DateTimeOffset> 值執行個體化時，會與其時區解除關聯。  因此，當您執行日期和時間計算時，就無法再套用該時區的調整規則。  要解決此問題，您可以定義自訂型別，將日期和時間值以及其伴隨的時區包含在內。  
  
### 若要反覆存取具有時區的日期和時間值  
  
1.  定義有兩個欄位的類別或結構。  第一個欄位是 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 物件，而第二個欄位是 <xref:System.TimeZoneInfo> 物件。  下列範例是這種型別的簡單版本。  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  以 <xref:System.SerializableAttribute> 屬性標記類別。  
  
3.  使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName> 方法序列化物件。  
  
4.  使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> 方法還原物件。  
  
5.  將還原序列化的物件轉型 \(C\#\) 或轉換 \(Visual Basic\) 為適當型別的物件。  
  
 下列範例示範如何反覆存取同時儲存日期和時間以及時區資訊的物件。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 此方式應能永遠明確反映出正確的時間點，不論是在儲存和還原之前或之後，但前提是日期和時間以及時區合併物件的實作不允許日期值與時區值變成不同步。  
  
## 編譯程式碼  
 這些範例需要：  
  
-   使用 C\# `using` 陳述式或 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` 陳述式匯入下列命名空間：  
  
    -   <xref:System> \(僅限 C\#\)。  
  
    -   <xref:System.Globalization?displayProperty=fullName>.  
  
    -   <xref:System.IO?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=fullName>.  
  
-   System.Core.dll 的參考。  
  
-   每個程式碼範例 \(除 `DateInTimeZone` 類別外\) 都應包含在類別或 Visual Basic 模組中、包裝在方法中，以及從 `Main` 方法呼叫。  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [在 DateTime、DateTimeOffset、 TimeSpan 和  TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)   
 [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)