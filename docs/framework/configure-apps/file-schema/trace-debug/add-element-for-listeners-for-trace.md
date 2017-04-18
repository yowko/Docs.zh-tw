---
title: "&lt;trace&gt; 適用之 &lt;listeners&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<listeners> 的 <add> 項目"
  - "<listeners> 的 add 項目"
  - "initializeData 屬性"
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 24
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;trace&gt; 適用之 &lt;listeners&gt; 的 &lt;add&gt; 項目
將接聽程式加入至 **Listeners** 集合。  
  
## 語法  
  
```  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|**type**|必要屬性。<br /><br /> 指定接聽程式的類型。  您必須使用符合[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定之需求的字串。|  
|**initializeData**|選擇性屬性。<br /><br /> 傳遞至指定類別的建構函式的字串。|  
|**name**|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|將篩選條件加入到追蹤之 `Listeners` 集合的接聽項中。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定收集、存放及傳送訊息的接聽程式。  接聽程式將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含收集、存放和傳送追蹤訊息的接聽程式。|  
  
## 備註  
 <xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.Trace> 類別共用一個 **Listeners** 集合。  如果您將接聽程式物件加入至其中一個類別的集合，另一個類別會使用相同的接聽程式。  接聽程式類別是從 [TraceListener 類別](frlrfSystemDiagnosticsTraceListenerClassTopic)衍生而來。  
  
 如果您未指定追蹤接聽程式的 `nam`e 屬性，追蹤接聽程式的 <xref:System.Diagnostics.TraceListener.Name%2A> 預設為空字串 empty string \(""\)。  如果您的應用程式僅有一個接聽程式，可以不必指定名稱就新增，並為名稱指定空字串以移除。  然而，如果您的應用程式有超過一個接聽程式，則應為每個追蹤接聽程式指定唯一的名稱，此可讓您辨識並管理 <xref:System.Diagnostics.Debug.Listeners%2A> 和 <xref:System.Diagnostics.Trace.Listeners%2A> 集合中個別的追蹤接聽程式。  
  
> [!NOTE]
>  加入多個具有相同型別與相同名稱的追蹤接聽程式，結果只有一個該型別和名稱的追蹤接聽程式會加入至 `Listeners` 集合。  不過，您可以經由程式設計方式將多個完全相同的接聽程式加入至 `Listeners` 集合中。  
  
 **initializeData** 屬性的值視您建立的接聽程式類型而定。  並非所有的接聽程式都會要求您指定 **initializeData**。  
  
> [!NOTE]
>  當您使用 `initializeData` 屬性時，可能會收到下列編譯器警告訊息：「'initializeData' 屬性未宣告」。這項警告出現的原因是驗證組態設定時其對象是基底型別 <xref:System.Diagnostics.TraceListener>，但此基底型別無法識別 `initializeData` 屬性。  如果追蹤接聽程式實作中包含採用參數的建構函式，您通常可以忽略這項警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽程式，並描述其 **initializeData** 屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------|------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 建構函式的 `useErrorStream` 值。將 `initializeData` 屬性設成 "`true`"，可將追蹤及偵錯輸出寫入至 <xref:System.Console.Error%2A?displayProperty=fullName>；設成 "`false`" 則會寫入至 <xref:System.Console.Out%2A?displayProperty=fullName>。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.XmlWriterTraceListener> 寫入的檔案名稱。|  
  
## 範例  
 下列範例示範如何使用 **\<add\>**項目將接聽項 `MyListener` 和 `MyEventListener` 加入到追蹤來源 **Listeners** 集合中。  `MyListener` 會建立一個名為 `MyListener.log` 的檔案，並將輸出寫入至該檔案中。  `MyEventListener` 會在事件記錄檔中建立項目。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)