---
title: "fatalExecutionEngineError MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "corrupted CLR"
  - "fatal execution error"
  - "terminated processes"
  - "unexpected terminations"
  - "fatal errors"
  - "MDAs (managed debugging assistants), fatal errors"
  - "process termination"
  - "FatalExecutionEngineError MDA"
  - "managed debugging assistants (MDAs), fatal errors"
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# fatalExecutionEngineError MDA
在 Common Language Runtime \(CLR\) 中偵測到嚴重錯誤時，`fatalExecutionEngine``Error` Managed 偵錯助理 \(MDA\) 就會啟動。  處理序將會結束。  
  
## 症狀  
 未預期的處理序終止。  由於可能因為不同的原因發生 CLR 失敗，因此無法判斷其他症狀。  
  
## 原因  
 CLR 已經嚴重損毀。  這最常是由資料損毀造成，諸如對錯誤平台叫用 \(Invoke\) 函式的呼叫，以及將無效的資料傳遞至 CLR 等問題都可能造成資料損毀。  
  
## 解決方式  
 啟用額外的 MDA 可能有助於識別問題。  下列 MDA 尤其能夠有助於診斷問題：  
  
-   [invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## 對執行階段的影響  
 這個 MDA 對執行階段的行為無效。  
  
## Output  
 造成嚴重錯誤之 CLR 函式的位址、發生錯誤所在執行緒的 ID 以及錯誤碼。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution.Cer>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)