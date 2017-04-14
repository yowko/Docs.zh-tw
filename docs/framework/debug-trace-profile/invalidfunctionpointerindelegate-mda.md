---
title: "invalidFunctionPointerInDelegate MDA | Microsoft Docs"
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
  - "invalidFunctionPointerInDelegate MDA"
  - "managed debugging assistants (MDAs), invalid function pointer to delegates"
  - "MDAs (managed debugging assistants), invalid function pointer to delegates"
  - "function pointers, invalid"
  - "marshaling, run-time errors"
  - "managed debugging assistants (MDAs), marshaling"
  - "MDAs (managed debugging assistants), marshaling"
  - "invalid function pointers"
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# invalidFunctionPointerInDelegate MDA
當無效的函式指標傳入，以建構取代原生函式指標的委派時，就會啟用 `invalidFunctionPointerInDelegate` Managed 偵錯助理 \(MDA\)。  
  
## 徵兆  
 使用委派來取代函式指標時，發生存取違規或非預期的記憶體損毀。  
  
## 原因  
 所指定的函式指標無效。  
  
## 解決方式  
 指定有效的函式指標  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## 輸出  
 無效的函式指標。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)