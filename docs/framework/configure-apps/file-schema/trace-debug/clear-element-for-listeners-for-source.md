---
title: "&lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;clear&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> 適用之 <listeners> 的 <clear> 項目"
  - "<source> 適用之 <listeners> 的 clear 項目"
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;clear&gt; 項目
清除追蹤來源的 `Listeners` 集合。  
  
## 語法  
  
```  
<clear/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`sources`|包含會啟始追蹤訊息的追蹤來源。|  
|`source`|指定會啟始追蹤訊息的追蹤來源。|  
|`listeners`|指定收集、存放和傳送訊息的接聽程式。|  
  
## 備註  
 `<clear>` 項目會從追蹤來源的 `Listeners` 集合中移除所有的接聽項，包括 <xref:System.Diagnostics.DefaultTraceListener> 在內。  您可以在使用 `<add>` 項目之前先使用 `<clear>` 項目，以確定此集合中沒有其他使用中的接聽項。  
  
## 組態檔  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何先使用 `<clear>` 項目之後，再使用 `<add>` 項目，將接聽項 `console` 和 `textListener` 加入到追蹤來源 `TraceSourceApp` 的 `Listeners` 集合中。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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