---
title: "&lt;system.diagnostics&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.diagnostics> 項目"
  - "system.diagnostics 項目"
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;system.diagnostics&gt; 項目
指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。  
  
## 語法  
  
```  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<assert\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|指定您呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 方法時是否顯示訊息方塊，同時指定要寫入訊息的檔案名稱。|  
|[\<performanceCounters\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|指定效能計數器所共用的全域記憶體的大小。|  
|[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|包含任何來源或追蹤項目可以參考的接聽程式。  識別為共用接聽項的接聽項可以根據名稱加入到來源或追蹤。|  
|[\<來源\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|指定啟始追蹤訊息的追蹤來源。|  
|[\<參數\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|包含追蹤參數和設定追蹤參數的層級。|  
|[\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|包含收集、存放和傳送追蹤訊息的接聽程式。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 範例  
 以下範例示範如何在 **\<system.diagnostics\>** 項目中內嵌一個追蹤參數和一個追蹤接聽程式。  `General` 追蹤參數設定為 [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) 層級。  追蹤接聽程式 `myListener` 會建立一個名為 `MyListener.log` 的檔案，並且將輸出寫入檔案。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。  例如，您可以為 <xref:System.Diagnostics.BooleanSwitch> 指定 `true`，或是使用代表列舉值的文字，例如，為 <xref:System.Diagnostics.TraceSwitch> 指定 `Error`。  `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)