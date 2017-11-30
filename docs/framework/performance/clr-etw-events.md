---
title: "CLR ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d0619388b429bd1824a62bc29ccb222eea1ffde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-events"></a>CLR ETW 事件
本節中的主題描述 Windows (ETW) 事件的事件追蹤。 每個事件都有相關聯的關鍵字和層級，如 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)主題中所述。 CLR 具有事件的兩個提供者：  
  
-   執行階段提供者，以根據啟用哪些關鍵字 (事件的類別) 來引發事件。 CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。  
  
-   具有特殊用途的取消提供者。 CLR 取消提供者 GUID 是 a669021c-c450-4609-a035-5af59af4df18。  
  
 如需提供者的詳細資訊，請參閱 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [執行階段資訊事件](../../../docs/framework/performance/runtime-information-etw-events.md)  
 擷取執行階段的相關資訊，包含 SKU、版本號碼、執行階段啟用方式、用來啟動它的命令列參數、GUID (適用時)，以及其他相關資訊。  
  
 [Exception Thrown_V1 事件](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 擷取所擲回例外狀況的相關資訊。  
  
 [爭用事件](../../../docs/framework/performance/contention-etw-events.md)  
 擷取爭用執行階段所使用之監視鎖定或原生鎖定的相關資訊。  
  
 [執行緒集區事件](../../../docs/framework/performance/thread-pool-etw-events.md)  
 擷取背景工作執行緒集區和 I/O 執行緒集區的相關資訊。  
  
 [載入器事件](../../../docs/framework/performance/loader-etw-events.md)  
 擷取載入和卸載應用程式定義域、組件和模組的相關資訊。  
  
 [方法事件](../../../docs/framework/performance/method-etw-events.md)  
 擷取進行符號解析之 CLR 方法的相關資訊。  
  
 [記憶體回收事件](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 擷取記憶體回收的相關資訊，以協助診斷和偵錯。  
  
 [JIT 追蹤事件](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 擷取 Just-In-Time (JIT) 內嵌和 tail 呼叫的相關資訊。  
  
 [Interop 事件](../../../docs/framework/performance/interop-etw-events.md)  
 擷取 Microsoft Intermediate Language (MSIL) Stub 產生和快取的相關資訊。  
  
 [ARM 事件](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 擷取應用程式定義域狀態的詳細診斷資訊。  
  
 [安全性事件](../../../docs/framework/performance/security-etw-events.md)  
 擷取強式名稱和 Authenticode 驗證的相關資訊。  
  
 [堆疊事件](../../../docs/framework/performance/stack-etw-event.md)  
 擷取與其他事件搭配使用以在引發事件之後產生堆疊追蹤的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [改善偵錯和效能調整使用 ETW](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Windows 效能部落格](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)  
 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)  
 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
