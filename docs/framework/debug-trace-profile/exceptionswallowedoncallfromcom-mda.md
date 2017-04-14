---
title: "exceptionSwallowedOnCallFromCom MDA | Microsoft Docs"
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
  - "messages, informational"
  - "informational messages"
  - "managed debugging assistants (MDAs), exceptions"
  - "exception handling, managed debugging assistants"
  - "MDAs (managed debugging assistants), exceptions"
  - "ExceptionSwallowedOnCallFromCOM MDA"
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# exceptionSwallowedOnCallFromCom MDA
透過不含 Unmanaged HRESULT 傳回類型的方法，從 COM 呼叫的通用語言執行平台 \(CLR\) 擲回例外狀況時，就會啟用 `exceptionSwallowedOnCallFromCOM` Managed 偵錯助理 \(MDA\)。  
  
## 徵兆  
 從 COM 呼叫 Managed 元件時，傳回的值為 FALSE 或 0。  或者，如果方法具有 void 傳回類型，執行方法期間可能不會指出已擲回例外狀況。  在這種情況下，會以無訊息模式攔截例外狀況，而執行作業會返回 COM 呼叫端。  
  
## 原因  
 已擲回例外狀況，但沒有有效的方式來進行提報。  
  
## 解決方式  
 僅供參考，不一定表示有 Bug。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  它只會提報以無訊息模式攔截例外狀況的相關資料。  
  
## 輸出  
 告知性訊息，包含方法名稱、類型名稱和例外狀況訊息。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)