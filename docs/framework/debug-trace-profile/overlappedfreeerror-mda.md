---
title: "overlappedFreeError MDA | Microsoft Docs"
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
  - "OverlappedFreeError MDA"
  - "overlapped free method call error"
  - "managed debugging assistants (MDAs), overlapped structures"
  - "overlapped structures"
  - "MDAs (managed debugging assistants), overlapped structures"
  - "freeing overlapped structures"
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# overlappedFreeError MDA
如果在重疊的作業完成之前呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=fullName> 方法，`overlappedFreeError` Managed 偵錯助理 \(MDA\) 就會啟動。  
  
## 症狀  
 存取違規或記憶體回收的堆積損毀。  
  
## 原因  
 在作業完成之前就釋放了 Overlapped 結構，  釋放此結構之後，使用重疊指標的函式稍後可能寫入了此結構。  這可能會造成堆積損毀，因為當時可能有另一個物件佔用該區域。  
  
 如果重疊的作業沒有啟動成功，這個 MDA 可能不會顯示錯誤。  
  
## 解決方式  
 呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> 方法之前，請先確保使用 Overlapped 結構的 I\/O 作業已經完成。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 下列是這個 MDA 的輸出範例。  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'.  If the AppDomain is shut down, this can cause heap corruption when the async I/O completes.  The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack().  If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)