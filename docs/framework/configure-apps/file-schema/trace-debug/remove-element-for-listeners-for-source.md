---
title: "&lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;remove&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> 適用之 <listeners> 的 <remove> 項目"
  - "<source> 適用之 <listeners> 的 remove 項目"
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;source&gt; 的 &lt;listeners&gt; 適用之 &lt;remove&gt; 項目
從追蹤來源的 `Listeners` 集合中移除接聽項。  
  
## 語法  
  
```  
<remove name="listenerName" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要屬性。<br /><br /> 要從 `Listeners` 集合中移除的接聽項名稱。|  
  
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
 `<remove>` 項目會從追蹤來源的 `Listeners` 集合中移除指定的接聽項。  
  
 您可以程式方式從追蹤來源的 `Listeners` 集合中移除項目，透過的方式是呼叫 <xref:System.Diagnostics.TraceSource> 執行個體之 <xref:System.Diagnostics.TraceSource.Listeners%2A> 屬性上的 <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 方法。  
  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何先使用 `<remove>` 項目之後，再使用 `<add>` 項目將接聽項 `console` 加入到追蹤來源 `TraceSourceApp` 的 `Listeners` 集合中。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>   
 <xref:System.Diagnostics.TraceSource>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)