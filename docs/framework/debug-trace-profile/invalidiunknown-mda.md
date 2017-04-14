---
title: "invalidIUnknown MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid IUnknown pointer"
  - "InvalidIUnknown MDA"
  - "invalid IUnknown pointers"
  - "IUnknown pointers"
  - "managed debugging assistants (MDAs), invalid IUnknown pointer"
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# invalidIUnknown MDA
當無效的 `IUnknown` 指標從原生程式碼傳遞至 Managed 程式碼時，會啟動 `invalidIUnknown` Managed 偵錯助理 \(MDA\)。  查詢 `IUnknown` 介面時，`IUnknown` 無法成功傳回。  
  
## 徵兆  
 引數封送處理期間，在封送處理 COM 介面指標時，發生未預期的錯誤。  
  
## 原因  
 對於傳遞至 CLR 的 COM 介面進行了不正確的 `QueryInterface` 實作。  
  
## 解決方式  
 更正 `QueryInterface` 實作。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## 輸出  
 錯誤的描述。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)