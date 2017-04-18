---
title: "dllMainReturnsFalse MDA | Microsoft Docs"
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
  - "managed debugging assistants (MDAs), DllMain returns false"
  - "DllMainReturnsFalse MDA"
  - "DllMain function"
  - "MDAs (managed debugging assistants), DllMain returns false"
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# dllMainReturnsFalse MDA
如果以 DLL\_PROCESS\_ATTACH 的原因呼叫使用者組件的 Managed `DllMain` 函式，並傳回 FALSE，`dllMainReturnsFalse` Managed 偵錯助理 \(MDA\) 就會啟動。  
  
## 症狀  
 `DllMain` 函式傳回 FALSE，表示此函式沒有適當執行。  這樣就會造成無法判斷的問題，因為 `DllMain` 函式通常都包含重要的初始化程式碼。  
  
## 原因  
 以 DLL\_PROCESS\_ATTACH 的原因呼叫 `DllMain` 函式，進行載入時的 DLL 初始化。  如果傳回 FALSE，就表示 DLL 初始化失敗。  
  
## 解決方式  
 分析失敗 DLL 之 `DllMain` 函式的程式碼，並識別初始化失敗的原因。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  此 MDA 只會報告關於 `DllMain` 傳回值的資料。  
  
## Output  
 訊息，表示以 DLL\_PROCESS\_ATTACH 原因呼叫的 `DllMain` 函式傳回了 FALSE。  請注意，唯有 `DllMain` 以 Managed 程式碼實作時，這個 MDA 才會啟動。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)