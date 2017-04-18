---
title: "追蹤和偵錯設定結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "組態結構描述 [.NET Framework], 追蹤和除錯設定"
  - "組態區段 [.NET Framework]"
  - "組態設定 [.NET Framework], 偵錯"
  - "組態設定 [.NET Framework], 追蹤"
  - "項目 [.NET Framework], 追蹤和除錯設定"
  - "結構描述組態設定"
  - "追蹤接聽項, 追蹤和偵錯設定結構描述"
  - "追蹤 [.NET Framework], 追蹤和偵錯設定結構描述"
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# 追蹤和偵錯設定結構描述
追蹤和偵錯設定指定了收集、存放及傳送訊息的追蹤接聽程式 \(Listener\)，以及設定追蹤參數的層級。  
  
 下表描述的是每一個追蹤和偵錯設定項目的功能。  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|將接聽程式加入至追蹤來源的 `Listeners` 集合。|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|將接聽程式加入至 `Listeners` 集合。|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|將接聽程式加入至 `sharedListeners` 集合。|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|指定設定追蹤參數的層級。|  
|[\<assert\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|指定您呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 方法時是否顯示訊息方塊，同時指定要寫入訊息的檔案名稱。|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|清除追蹤來源的 `Listeners` 集合。|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|清除用於追蹤的 `Listeners` 集合。|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|將篩選條件加入至追蹤來源的 `Listeners` 集合中的接聽程式。|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|將篩選條件加入至用於追蹤的 `Listeners` 集合中的接聽程式。|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|將篩選條件加入至 `sharedListeners` 集合中的接聽程式。|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|指定追蹤來源的 `Listeners` 集合的接聽程式。|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|指定用於追蹤的 `Listeners` 集合的接聽程式。|  
|[\<performanceCounters\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|指定效能計數器所共用的全域記憶體的大小。|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|從用於追蹤的 `Listeners` 集合移除接聽程式。|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|從追蹤來源的 `Listeners` 集合中移除接聽項。|  
|[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|包含任何來源或追蹤項目可以參考的接聽程式。|  
|[\<sources\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|包含會啟始追蹤訊息的追蹤來源。|  
|[\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|指定會啟始追蹤訊息的追蹤來源。|  
|[\<switches\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|包含追蹤參數和設定追蹤參數的層級。|  
|[\<system.diagnostics\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|[\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|包含收集、存放和傳送追蹤訊息的接聽程式。|  
  
## 請參閱  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.Debug>   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)