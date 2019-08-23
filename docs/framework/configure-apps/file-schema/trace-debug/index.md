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
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927125"
---
# <a name="trace-and-debug-settings-schema"></a>追蹤和偵錯設定結構描述
追蹤和偵錯設定會指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
 下表描述每個追蹤和偵錯設定項目的函式。  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|將接聽項新增至追蹤來源的 `Listeners` 集合。|  
|[\<add>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<add>](add-element-for-sharedlisteners.md)|將接聽項新增至 `sharedListeners` 集合。|  
|[\<add>](add-element-for-switches.md)|指定設定追蹤參數的層級。|  
|[\<assert>](assert-element.md)|指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。|  
|[\<clear>](clear-element-for-listeners-for-source.md)|清除追蹤來源的 `Listeners` 集合。|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|將篩選新增至追蹤之 `Listeners` 集合中的接聽項。|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|將篩選新增至 `sharedListeners` 集合中的接聽項。|  
|[\<listeners>](listeners-element-for-source.md)|為追蹤來源的 `Listeners` 集合指定接聽項。|  
|[\<listeners>](listeners-element-for-trace.md)|為追蹤的 `Listeners` 集合指定接聽項。|  
|[\<performanceCounters>](performancecounters-element.md)|指定效能計數器共用之全域記憶體的大小。|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|從追蹤的 `Listeners` 集合移除接聽項。|  
|[\<remove>](remove-element-for-listeners-for-source.md)|從追蹤來源的 `Listeners` 集合移除接聽項。|  
|[\<sharedListeners>](sharedlisteners-element.md)|包含任何來源或追蹤項目可參考的接聽項。|  
|[\<sources>](sources-element.md)|包含起始追蹤訊息的追蹤來源。|  
|[\<source>](source-element.md)|指定起始追蹤訊息的追蹤來源。|  
|[\<switches>](switches-element.md)|包含追蹤參數及設定追蹤參數的層級。|  
|[\<system.diagnostics>](system-diagnostics-element.md)|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|[\<trace>](trace-element.md)|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [組態檔結構描述](../index.md)
