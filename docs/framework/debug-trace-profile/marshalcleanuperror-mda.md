---
title: "marshalCleanupError MDA | Microsoft Docs"
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
  - "cleanup operations"
  - "marshaling, run-time errors"
  - "managed debugging assistants (MDAs), marshaling"
  - "MDAs (managed debugging assistants), marshaling"
  - "marshaling cleanup error"
  - "MarshalCleanupError MDA"
  - "memory, cleanup errors"
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# marshalCleanupError MDA
如果通用語言執行平台 \(CLR\) 在嘗試清除用來封送處理本機與 Managed 程式碼界限間之資料類型的暫存結構和記憶體時，發生錯誤，就會啟用 `marshalCleanupError` Managed 偵錯助理 \(MDA\)。  
  
## 徵兆  
 進行本機與 Managed 程式碼轉換時發生記憶體流失、執行緒文化特性之類的執行階段狀態未還原，或是 <xref:System.Runtime.InteropServices.SafeHandle> 清除發生錯誤。  
  
## 原因  
 清除暫存結構時，發生非預期的錯誤。  
  
## 解決方式  
 檢閱所有 <xref:System.Runtime.InteropServices.SafeHandle> 建構函式、完成項和自訂封送處理器實作是否有錯誤。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## 輸出  
 出現一則訊息，提報在清除期間失敗的作業。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)