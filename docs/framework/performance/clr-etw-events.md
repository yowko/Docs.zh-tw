---
title: "CLR ETW 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLR ETW 事件"
  - "ETW, CLR 事件"
  - "ETW, Common Language Runtime"
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: 45
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 45
---
# CLR ETW 事件
本節主題描述 Windows 事件追蹤 \(ETW\) 事件。  每個事件都有相關聯的關鍵字和層級，[CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)主題中會有相關說明。  CLR 有兩個事件提供者：  
  
-   執行階段提供者，會根據啟用的關鍵字 \(即事件的分類\) 引發事件。  CLR 執行階段提供者 GUID 為 e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4。  
  
-   取消提供者，具有特殊用途。  CLR 取消提供者 GUID 為 a669021c\-c450\-4609\-a035\-5af59af4df18。  
  
 如需提供者的詳細資訊，請參閱 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)。  
  
## 在本節中  
 [執行階段資訊事件](../../../docs/framework/performance/runtime-information-etw-events.md)  
 擷取執行階段的相關資訊，包括 SKU、版本號碼、執行階段的啟動方式、用來啟動執行階段的命令列參數、GUID \(如果適用的話\)，以及其他相關資訊。  
  
 [Exception Thrown\_V1 事件](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 擷取所擲回例外狀況的相關資訊。  
  
 [爭用事件](../../../docs/framework/performance/contention-etw-events.md)  
 擷取執行階段所使用之原生鎖定或監視器鎖定的爭用資訊。  
  
 [執行緒集區事件](../../../docs/framework/performance/thread-pool-etw-events.md)  
 擷取背景工作執行緒集區和 I\/O 緒行緒集區的相關資訊。  
  
 [載入器事件](../../../docs/framework/performance/loader-etw-events.md)  
 擷取與載入和卸載應用程式定義域、組件和模組有關的資訊。  
  
 [方法事件](../../../docs/framework/performance/method-etw-events.md)  
 擷取與符號解析的 CLR 方法有關的資訊。  
  
 [記憶體回收事件](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 擷取記憶體回收的相關資訊，以協助診斷和偵錯。  
  
 [JIT 追蹤事件](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 擷取 Just\-In\-Time \(JIT\) 內嵌和 tail 呼叫的相關資訊。  
  
 [Interop 事件](../../../docs/framework/performance/interop-etw-events.md)  
 擷取產生和快取 Microsoft Intermediate Language \(MSIL\) Stub 的相關資訊。  
  
 [ARM 事件](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 擷取應用程式定義域狀態的詳細診斷資訊。  
  
 [安全性事件](../../../docs/framework/performance/security-etw-events.md)  
 擷取強式名稱和 Authenticode 簽章驗證的相關資訊。  
  
 [堆疊事件](../../../docs/framework/performance/stack-etw-event.md)  
 擷取在事件引發之後，用來搭配其他事件以產生堆疊追蹤的資訊。  
  
## 請參閱  
 [改善 ETW 的偵錯和效能優化](http://go.microsoft.com/fwlink/?LinkId=179696)   
 [Windows 效能部落格](http://go.microsoft.com/fwlink/?LinkId=179509)   
 [控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)   
 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)   
 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)   
 [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)