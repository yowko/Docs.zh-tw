---
title: "&lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;add&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> 適用之 <listeners> 的 <add> 項目"
  - "<source> 適用之 <listeners> 的 add 項目"
  - "initializeData 屬性"
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;add&gt; 項目
將接聽程式加入至追蹤來源的 `Listeners` 集合。  
  
## 語法  
  
```  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`type`|必要屬性。<br /><br /> 指定接聽程式的類型。  您必須使用符合[指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定之要求的字串。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞至指定類別的建構函式的字串。  如果此類別並沒有接受字串的建構函式，則會擲回 <xref:System.Configuration.ConfigurationException>。|  
|`name`|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
|`traceOutputOptions`|選擇性屬性。<br /><br /> 為此追蹤接聽項指定 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 屬性值。|  
|\[自訂屬性\]|選擇性屬性。<br /><br /> 針對該接聽項指定 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 方法所識別的接聽項特定的屬性值。  <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 是 <xref:System.Diagnostics.DelimitedListTraceListener> 類別特有的額外屬性之範例。|  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|將篩選條件加入至追蹤來源的 `Listeners` 集合中的接聽程式。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`sources`|包含會啟始追蹤訊息的追蹤來源。|  
|`source`|指定會啟始追蹤訊息的追蹤來源。|  
|`listeners`|指定收集、存放和傳送訊息的接聽程式。|  
  
## 備註  
 .NET Framework 隨附的接聽程式類別是衍生自 <xref:System.Diagnostics.TraceListener> 類別。  
  
 如果您未指定追蹤接聽項的 `name` 屬性，則追蹤接聽項的 <xref:System.Diagnostics.TraceListener.Name%2A> 屬性會預設為空字串 \(""\)。  如果您的應用程式僅有一個接聽項，可以不必指定名稱就進行新增，也可以為該名稱指定空字串來進行移除。  然而，如果應用程式有一個以上的接聽項，則應該為每一個追蹤接聽項指定唯一的名稱，如此可讓您識別及管理 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=fullName> 集合中個別的追蹤接聽項。  
  
> [!NOTE]
>  加入多個具有相同型別與相同名稱的追蹤接聽程式，結果只有一個該型別和名稱的追蹤接聽程式會加入至 `Listeners` 集合。  不過，您可以經由程式設計方式將多個完全相同的接聽程式加入至 `Listeners` 集合中。  
  
 `initializeData` 屬性的值需視您建立的接聽項之型別而定，  並非所有的追蹤接聽項都會要求您指定 `initializeData`。  
  
> [!NOTE]
>  當您使用 `initializeData` 屬性時，可能會收到下列編譯器警告訊息：「'initializeData' 屬性未宣告」。這項警告出現的原因是驗證組態設定時其對象是基底型別 <xref:System.Diagnostics.TraceListener>，但此基底型別無法識別 `initializeData` 屬性。  如果追蹤接聽程式實作中包含採用參數的建構函式，您通常可以忽略這項警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其 `initializeData` 屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------|------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 建構函式的 `useErrorStream` 值。將 `initializeData` 屬性設定為 "`true`"，即可將追蹤和偵錯輸出寫入到標準錯誤資料流中；將它設定為 "`false`"，即可寫入到標準輸出資料流中。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.XmlWriterTraceListener> 寫入的檔案名稱。|  
  
## 組態檔  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何使用 `<add>` 項目將接聽項 `console` 和 `textListener` 加入到追蹤來源 `TraceSourceApp` 的 `Listeners` 集合中。  `textListener` 接聽項會將追蹤輸出寫入到 myListener.log 檔案中。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TraceListener>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)