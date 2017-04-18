---
title: "&lt;trace&gt; 的 &lt;listeners&gt; 適用之 &lt;clear&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> 適用之 <listeners> 的 <clear> 項目"
  - "<trace> 適用之 <listeners> 的 clear 項目"
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;trace&gt; 的 &lt;listeners&gt; 適用之 &lt;clear&gt; 項目
清除用於追蹤的 `Listeners` 集合。  
  
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
|`trace`|包含收集、存放和傳送追蹤訊息的接聽程式。|  
|`listeners`|包含收集、儲存和傳送訊息的接聽程式。  接聽程式將追蹤輸出導向至適當的目標。|  
  
## 備註  
 `<clear>` 項目會從追蹤的 `Listeners` 集合中移除所有接聽項。  您可以在使用 `<add>` 項目之前先使用 `<clear>` 項目，以確定此集合中沒有其他使用中的接聽項。  
  
 您可以程式方式清除 `Listeners` 集合，其方式是呼叫 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName> 屬性上的 <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 方法 \(`System.Diagnostics.Trace.Listeners.Clear()`\)。  
  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
> [!NOTE]
>  `<clear>` 項目會從 `Listeners` 集合中移除 <xref:System.Diagnostics.DefaultTraceListener>，改變 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 方法的行為。  呼叫 `Assert` 或 `Fail` 方法通常會導致訊息方塊出現。  不過，如果 <xref:System.Diagnostics.DefaultTraceListener> 不在 `Listeners` 集合中，則不會顯示此訊息方塊。  
  
## 範例  
 下列範例將示範如何先使用 `<clear>` 項目之後，再使用 `<add>` 項目將接聽項 `console` 加入到追蹤的 `Listeners` 集合中。  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## 請參閱  
 <xref:System.Diagnostics.Trace.Listeners%2A>   
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.TraceSource>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)