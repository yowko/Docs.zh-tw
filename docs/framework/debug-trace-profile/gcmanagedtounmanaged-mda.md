---
title: "gcManagedToUnmanaged MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), garbage collection"
  - "GcManagedToUnmanaged MDA"
  - "GC managed to unmanaged"
  - "transitioning threads managed to unmanaged code"
  - "threading [.NET Framework], garbage collection"
  - "managed to unmanaged garbage collection"
  - "managed debugging assistants (MDAs), garbage collection"
  - "threading [.NET Framework], managed debugging assistants"
  - "garbage collection, run-time errors"
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# gcManagedToUnmanaged MDA
每當執行緒從 Managed 轉換到 Unmanaged 程式碼時，`gcManagedToUnmanaged` Managed 偵錯助理 \(MDA\) 會造成記憶體回收。  
  
## 徵兆  
 嘗試使用已公開至 COM 的 Managed 物件時，Unmanaged 使用者元件會擲回存取違規。  COM 物件似乎已發行。  存取違規不具決定性。  
  
## 原因  
 如果 Unmanaged 元件不是正確計算 Managed COM 物件的參考，執行階段可以收集已公開至 COM 的 Managed 物件，而 Unmanaged 元件仍會保存物件的參考。  執行階段會在記憶體回收期間呼叫 <xref:System.Runtime.InteropServices.Marshal.Release%2A>，因此如果使用者元件在發生記憶體回收之前使用物件，就不會被回收。  這是不具決定性的來源。  
  
## 解決方式  
 啟用此助理可減少從物件可供回收，到呼叫 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 之間的時間，有助於追蹤哪一個 Unmanaged 元件最先嘗試存取已收集的物件。  
  
## 對執行階段的影響  
 每當執行緒從 Managed 轉換到 Unmanaged 程式碼時，會造成記憶體回收。  
  
## 輸出  
 此 MDA 不會產生輸出。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)   
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)