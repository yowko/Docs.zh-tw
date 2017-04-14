---
title: "&lt;trace&gt; 的 &lt;listeners&gt; 適用之 &lt;add&gt; 的 &lt;filter&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> 的 <listeners> 適用之 <add> 的 <filter> 項目"
  - "<trace> 的 <listeners> 適用之 <add> 的 filter 項目"
  - "initializeData 屬性"
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;trace&gt; 的 &lt;listeners&gt; 適用之 &lt;add&gt; 的 &lt;filter&gt; 項目
將篩選條件加入到追蹤之 `Listeners` 集合的接聽項中。  
  
## 語法  
  
```  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`type`|必要屬性。<br /><br /> 指定篩選條件的型別，此型別應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。  您可使用此型別的符合命名空間之名稱，此名稱會對應到型別的 <xref:System.Type.FullName%2A> 屬性，或者可以使用包括組件資訊的完整型別名稱，此名稱會對應到 <xref:System.Type.AssemblyQualifiedName%2A> 屬性。  如需完整型別名稱的詳細資訊，請參閱 [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞至指定之篩選類別的建構函式之字串。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`trace`|包含收集、存放和傳送追蹤訊息的接聽程式。|  
|`listeners`|包含收集、儲存和傳送訊息的接聽程式。  接聽程式將追蹤輸出導向至適當的目標。|  
|`add`|將接聽程式加入至 `Listeners` 集合。|  
  
## 備註  
 `<filter>` 項目必須包含在追蹤接聽項的 `<add>` 項目中，該追踨接聽項不僅指定定義在 [\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md) 中的接聽項名稱，也指定其型別。  如果接聽項定義在 [\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md) 中，則該接聽項的篩選條件必須定義在該項目中。  
  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何使用 `<filter>`  項目，在追蹤的 `Listeners` 集合中，將篩選條件加入到接聽項 `console`，並將篩選條件事件層級指定為 `Error`。  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.TraceFilter>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)