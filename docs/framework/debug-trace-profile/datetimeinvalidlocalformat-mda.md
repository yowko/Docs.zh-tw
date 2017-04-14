---
title: "dateTimeInvalidLocalFormat MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "dates [.NET Framework], formatting"
  - "invalid date time local format"
  - "invalid local formats"
  - "MDAs (managed debugging assistants), invalid local formats"
  - "managed debugging assistants (MDAs), invalid local formats"
  - "dateTimeInvalidLocalFormat MDA"
  - "date formatting"
  - "time formatting"
  - "UTC formatting"
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# dateTimeInvalidLocalFormat MDA
當以 Universal Coordinated Time \(UTC\) 格式儲存的 <xref:System.DateTime> 執行個體是利用僅供本地 <xref:System.DateTime> 執行個體使用的格式來進行格式化時，即會啟動 `dateTimeInvalidLocalFormat` MDA。  未指定或預設的 <xref:System.DateTime> 執行個體中，不會啟動這個 MDA。  
  
## 症狀  
 應用程式會利用本地格式，以手動方式序列化 UTC <xref:System.DateTime> 執行個體：  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### 原因  
 <xref:System.DateTime.ToString%2A?displayProperty=fullName> 方法的 'z' 格式包括本地時區位移，例如，"\+10:00" 表示澳洲雪梨時間。  就這一點而論，只有當 <xref:System.DateTime> 的值是本地時間時，它才會產生有意義的結果。  如果此值是 UTC 時間，<xref:System.DateTime.ToString%2A?displayProperty=fullName> 會包括本地時區位移，但是不會顯示或調整時區規範。  
  
### 解決方式  
 UTC <xref:System.DateTime> 執行個體應該以指示其為 UTC 的方式來進行格式化；  UTC 時間的建議格式是使用 'Z' 來表示 UTC 時間：  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 也有一個可序列化 <xref:System.DateTime> 的 "o" 格式，其會利用 <xref:System.DateTime.Kind%2A> 屬性，而此屬性可以正確地序列化，不論執行個體是否為本地、UTC 或未指定：  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## 對執行階段的影響  
 這個 MDA 不會影響執行階段。  
  
## Output  
 當這個 MDA 啟動後，不會產生任何特殊的輸出；但是，可使用呼叫堆疊來判斷啟動此 MDA 的 <xref:System.DateTime.ToString%2A> 呼叫位置。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 假設有一個應用程式依下列方式使用 <xref:System.Xml.XmlConvert> 或 <xref:System.Data.DataSet> 類別，以間接方式序列化 UTC <xref:System.DateTime> 值。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 根據預設，<xref:System.Xml.XmlConvert> 和 <xref:System.Data.DataSet> 序列化都會使用本地格式來進行序列化。  還需要其他選項，才能序列化其他類型的 <xref:System.DateTime> 值，例如 UTC。  
  
 就此特定範例而言，要將 `XmlDateTimeSerializationMode.RoundtripKind` 傳給 `XmlConvert` 上的 `ToString` 呼叫，  如此會將資料序列化成 UTC 時間。  
  
 如果是使用 <xref:System.Data.DataSet>，請將 <xref:System.Data.DataColumn> 物件上的 <xref:System.Data.DataColumn.DateTimeMode%2A> 屬性設定為 <xref:System.Data.DataSetDateTime>。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## 請參閱  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)