---
title: "&lt;sharedListeners&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> 的 <add> 項目"
  - "<sharedListeners> 的 add 項目"
  - "initializeData 屬性"
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;sharedListeners&gt; 的 &lt;add&gt; 項目
將接聽程式加入至 `sharedListeners` 集合。  `sharedListeners` 是任何 [\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) 或 [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) 可以參考之接聽項的集合。根據預設，`sharedListeners` 集合中的接聽項不會放置到 `Listeners` 集合中，  這些接聽項必須依據名稱加入到 [\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或 [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)中，  您無法在執行階段於程式碼中取得 `sharedListeners` 集合中的接聽項。  
  
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
|`name`|必要屬性。<br /><br /> 指定用來將共用接聽項加入到 `Listeners` 集合中的接聽項名稱。|  
|`type`|必要屬性。<br /><br /> 指定接聽程式的類型。  您必須使用符合 [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md) 中指定之要求的字串。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞至指定類別的建構函式的字串。|  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|將篩選條件加入至 `sharedListeners` 集合中的接聽程式。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`sharedListeners`|任何來源或追蹤項目可以參考之接聽項的集合。|  
  
## 備註  
 .NET Framework 隨附的接聽程式類別是衍生自 <xref:System.Diagnostics.TraceListener> 類別。  `name` 屬性的值是用來將共用接聽項加入到追蹤或追蹤來源的 `Listeners` 集合中。  `initializeData` 屬性的值需視您建立的接聽項之型別而定，  並非所有的追蹤接聽項都會要求您指定 `initializeData`。  
  
> [!NOTE]
>  當您使用 `initializeData` 屬性時，可能會收到下列編譯器警告訊息：「'initializeData' 屬性未宣告」。這項警告出現的原因是驗證組態設定時其對象是基底型別 <xref:System.Diagnostics.TraceListener>，但此基底型別無法識別 `initializeData` 屬性。  如果追蹤接聽程式實作中包含採用參數的建構函式，您通常可以忽略這項警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其 `initializeData` 屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------|------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 建構函式的 `useErrorStream` 值。將 `initializeData` 屬性設定為 "`true`"，即可將追蹤和偵錯輸出寫入到標準錯誤資料流中；將它設定為 "`false`"，即可寫入到標準輸出資料流中。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<xref:System.Diagnostics.XmlWriterTraceListener> 寫入的檔案名稱。|  
  
## 組態檔  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例示範如何使用 `<add>` 元素，將 <xref:System.Diagnostics.TextWriterTraceListener> `textListener` 加入至 `sharedListeners` 集合。`textListener` 是依照名稱加到追蹤來源`TraceSourceApp`的 `Listeners` 集合。  `textListener` 接聽項會將追蹤輸出寫入到 myListener.log 檔案中。  
  
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