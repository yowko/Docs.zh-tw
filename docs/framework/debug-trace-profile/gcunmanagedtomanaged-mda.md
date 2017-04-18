---
title: "gcUnmanagedToManaged MDA | Microsoft Docs"
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
  - "GC unmanaged to managed"
  - "transitioning threads unmanaged to managed code"
  - "GcUnmanagedToManaged MDA"
  - "threading [.NET Framework], garbage collection"
  - "managed debugging assistants (MDAs), garbage collection"
  - "threading [.NET Framework], managed debugging assistants"
  - "garbage collection, run-time errors"
  - "unmanaged to managed garbage collection"
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# gcUnmanagedToManaged MDA
每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，`gcUnmanagedToManaged` Managed 偵錯助理 \(MDA\) 會造成記憶體回收。  
  
## 徵兆  
 使用 COM 和平台叫用執行 Unmanaged 使用者元件的應用程式在 CLR 中造成不具決定性的存取違規。  
  
## 原因  
 如果應用程式正在執行 Unmanaged 使用者元件，那麼這些元件可能已損毀記憶體回收的堆積。  在 CLR 中，當記憶體回收行程嘗試查核物件圖形時，這會造成存取違規。  
  
## 解決方式  
 在每次 Managed 轉換之前，啟用此助理會減少從 Unmanaged 元件損毀記憶體回收的堆積到強制執行記憶體回收而發生存取違規的間隔時間。  
  
## 對執行階段的影響  
 每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，會造成記憶體回收。  
  
## 輸出  
 此 MDA 不會產生輸出。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)