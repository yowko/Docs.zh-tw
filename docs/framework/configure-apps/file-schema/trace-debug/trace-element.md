---
title: "&lt;trace&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#trace"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> 項目"
  - "接聽項"
  - "trace 項目"
  - "追蹤接聽項, <trace> 項目"
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;trace&gt; 項目
包含收集、存放和傳送追蹤訊息的接聽程式。  
  
## 語法  
  
```  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`autoflush`|選擇性屬性。<br /><br /> 指定每次寫入作業後，追蹤接聽程式是否會自動清除輸出緩衝區。|  
|`indentsize`|選擇性屬性。<br /><br /> 指定要縮排的空格數。|  
|`useGlobalLock`|選擇性屬性。<br /><br /> 指示是否應使用全域鎖定。|  
  
## Autoflush 屬性  
  
|值|描述|  
|-------|--------|  
|`false`|不自動清除輸出緩衝區。  這是預設值。|  
|`true`|自動清除輸出緩衝區。|  
  
## useGlobalLock 屬性  
  
|值|描述|  
|-------|--------|  
|`false`|如果接聽器是安全執行緒 \(Thread Safe\)，請勿使用全域鎖定，否則請使用全域鎖定。|  
|`true`|不論接聽器是否為安全執行緒，一律使用全域鎖定。  這是預設值。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|指定收集、存放及傳送訊息的接聽程式。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
  
## 範例  
 下列範例將示範如何使用 `<trace>` 項目，將接聽器 `MyListener` 加入至 `Listeners` 集合中。  `MyListener` 會建立一個名稱為 `MyListener.log` 的檔案，並將輸出寫入檔案。  將 `useGlobalLock` 屬性設定為 `false`，當追蹤接聽器是安全執行緒時，就不會使用全域鎖定。  將 `autoflush` 屬性設定為 `true`，會使追蹤接聽器寫入至檔案，不論是否呼叫 <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=fullName> 方法。  將 `indentsize` 屬性設定為 0 \(零\)，則呼叫 <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=fullName> 方法時，接聽器的縮排為零格。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.DefaultTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)