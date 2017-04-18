---
title: "&lt;sharedListeners&gt; 適用之 &lt;add&gt; 的 &lt;filter&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> 適用之 <add> 的 <filter> 項目"
  - "<sharedListeners> 適用之 <add> 的 filter 項目"
  - "篩選條件, 追蹤接聽項"
  - "initializeData 屬性"
  - "追蹤接聽項, 篩選條件"
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;sharedListeners&gt; 適用之 &lt;add&gt; 的 &lt;filter&gt; 項目
將篩選條件加入至 `sharedListeners` 集合中的接聽程式。  
  
## 語法  
  
```  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**type**|必要屬性。<br /><br /> 指定篩選條件的型別。  您只能使用此型別的完整名稱 \(使用 <xref:System.Type.FullName%2A?displayProperty=fullName> 屬性的格式\)，或者可以使用包括此組件資訊的完整型別名稱 \(使用 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> 屬性的格式\)。  如需建立完整型別名稱的詳細資訊，請參閱 [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|**initializeData**|選擇性屬性。<br /><br /> 傳遞至指定類別的建構函式的字串。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`sharedListeners`|任何來源或追蹤項目可以參考之接聽項的集合。|  
|`add`|將接聽項加入至 **sharedListeners** 集合中。|  
  
## 備註  
 如果接聽項定義在 `<sharedListeners>` 項目的 `<add>` 項目中，則該接聽項的篩選條件應該定義在做為 `<add>` 項目之子系的 `<filter>` 項目中。  
  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何使用 `<filter>` 項目，將篩選條件加入到 `sharedListeners` 集合中的追蹤接聽項 `console`。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceFilter>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceSource>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)