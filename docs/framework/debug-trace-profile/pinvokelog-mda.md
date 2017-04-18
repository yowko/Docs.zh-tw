---
title: "pInvokeLog MDA | Microsoft Docs"
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
  - "signatures, platform invoke"
  - "MDAs (managed debugging assistants), platform invoke"
  - "platform invoke, run-time errors"
  - "platform invoke log"
  - "PInvokeLog MDA"
  - "managed debugging assistants (MDAs), platform invoke"
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# pInvokeLog MDA
`pInvokeLog` Managed 偵錯助理 \(MDA\) 會針對執行中使用的每個唯一平台叫用 \(Invoke\) 簽章 \(Signature\) 啟動。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 表示在執行時使用平台叫用簽章的訊息。  
  
## 組態  
 每個符合項目都會篩選做為平台叫用呼叫對象的 .dll 檔案。  
  
```  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)