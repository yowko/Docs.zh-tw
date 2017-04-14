---
title: "&lt;sharedListeners&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> 項目"
  - "接聽項"
  - "共用接聽項"
  - "sharedListeners 項目"
  - "追蹤接聽項, <sharedListeners> 項目"
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;sharedListeners&gt; 項目
包含任何來源或追蹤項目可以參考的接聽程式。這些接聽項預設不會接收任何追蹤，而且不可能在執行階段擷取這些接聽項。  識別為共用接聽項的接聽項可以根據名稱加入到來源或追蹤。  
  
## 語法  
  
```  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|將接聽程式加入至 `sharedListeners` 集合。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`Configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
  
## 備註  
 將接聽項加入到共用接聽項集合時，並不會讓它成為使用中的接聽項。  它仍必須加入到追蹤來源或追蹤，其方式是將它加入到該追蹤項目的 `Listeners` 集合中。  .NET Framework 內的接聽項類別是衍生自 <xref:System.Diagnostics.TraceListener> 類別。  
  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何使用 `<sharedListeners>` 項目將接聽項 `console` 加入到 <xref:System.Diagnostics.TraceSource> 和 <xref:System.Diagnostics.Trace> 類別的 `Listeners` 集合中。  主控台追蹤接聽項會透過 <xref:System.Diagnostics.TraceSource> 或 <xref:System.Diagnostics.Trace> 的呼叫，將追蹤資訊寫入到主控台。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceListener>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)