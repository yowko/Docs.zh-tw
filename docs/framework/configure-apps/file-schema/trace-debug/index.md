---
title: 追蹤和偵錯設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 0ea53f0c9a209d9bcbcc1e758cdcf957cde095dc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083492"
---
# <a name="trace-and-debug-settings-schema"></a>追蹤和偵錯設定結構描述
追蹤和偵錯設定會指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
 下表描述每個追蹤和偵錯設定項目的函式。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|將接聽項新增至追蹤來源的 `Listeners` 集合。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|將接聽項新增至 `sharedListeners` 集合。|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|指定設定追蹤參數的層級。|  
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|清除追蹤來源的 `Listeners` 集合。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|將篩選新增至追蹤之 `Listeners` 集合中的接聽項。|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|將篩選新增至 `sharedListeners` 集合中的接聽項。|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|為追蹤來源的 `Listeners` 集合指定接聽項。|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|為追蹤的 `Listeners` 集合指定接聽項。|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|指定效能計數器共用之全域記憶體的大小。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|從追蹤的 `Listeners` 集合移除接聽項。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|從追蹤來源的 `Listeners` 集合移除接聽項。|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|包含任何來源或追蹤項目可參考的接聽項。|  
|[\<sources>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|包含起始追蹤訊息的追蹤來源。|  
|[\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|指定起始追蹤訊息的追蹤來源。|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|包含追蹤參數及設定追蹤參數的層級。|  
|[\<system.diagnostics>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|[\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
