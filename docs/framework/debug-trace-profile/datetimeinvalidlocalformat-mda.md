---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 380334dbe9b91ea369de6cbe58686a9a74254c2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148222"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
使用只能用於當地 <xref:System.DateTime> 執行個體的格式來格式化儲存為全球定位時間 (UTC) 的 <xref:System.DateTime> 執行個體時，會啟用 `dateTimeInvalidLocalFormat` MDA。 針對未指定或預設 <xref:System.DateTime> 執行個體，不會啟用此 MDA。  
  
## <a name="symptom"></a>徵兆  
 應用程式使用當地格式手動序列化 UTC <xref:System.DateTime> 執行個體：  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>原因  
 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 方法的 'z' 格式包含當地時區位移，例如，"+10:00" 表示雪梨時間。 因此，如果 <xref:System.DateTime> 的值是當地時間，則它只會產生有意義的結果。 如果值是 UTC 時間，則 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 會包含當地時區位移，但不會顯示或調整時區規範。  
  
### <a name="resolution"></a>解決方式  
 UTC <xref:System.DateTime> 執行個體應該使用指出它們為 UTC 的方式進行格式化。 UTC 時間的建議格式是使用 'Z' 表示 UTC 時間：  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 也有 "o" 格式可序列化利用正確序列化之 <xref:System.DateTime.Kind%2A> 屬性的 <xref:System.DateTime>，不論執行個體是當地時間、UTC 還是未指定都一樣：  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 不會影響執行階段。  
  
## <a name="output"></a>Output  
 此 MDA 啟用沒有任何特殊輸出。不過，呼叫堆疊可以用來決定已啟用 MDA 之 <xref:System.DateTime.ToString%2A> 呼叫的位置。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 請以下列方式考慮使用利用 <xref:System.Xml.XmlConvert> 或 <xref:System.Data.DataSet> 類別間接序列化 UTC <xref:System.DateTime> 值的應用程式。  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> 和 <xref:System.Data.DataSet> 序列化預設會使用當地格式進行序列化。 需要其他選項，才能序列化其他類型的 <xref:System.DateTime> 值，例如 UTC。  
  
 在此特定範例中，將 `XmlDateTimeSerializationMode.RoundtripKind` 傳入 `XmlConvert` 上的 `ToString` 呼叫。 這會將資料序列化為 UTC 時間。  
  
 如果使用 <xref:System.Data.DataSet>，請將 <xref:System.Data.DataColumn> 物件上的 <xref:System.Data.DataColumn.DateTimeMode%2A> 屬性設定為 <xref:System.Data.DataSetDateTime.Utc>。  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.DateTimeFormatInfo>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
