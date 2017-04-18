---
title: "invalidOverlappedToPinvoke MDA | Microsoft Docs"
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
  - "overlapped pointers"
  - "managed debugging assistants (MDAs), overlapped pointers"
  - "invalid overlapped pointer to platform invoke"
  - "InvalidOverlappedToPinvoke MDA"
  - "MDAs (managed debugging assistants), overlapped pointers"
  - "pointers, overlapped"
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# invalidOverlappedToPinvoke MDA
當未在記憶體回收堆積上建立的重疊指標傳遞給特定的 Win32 函式時，會啟動 `invalidOverlappedToPinvoke` Managed 偵錯助理 \(MDA\)。  
  
> [!NOTE]
>  根據預設，只有當程式碼中定義了平台叫用呼叫，並且偵錯工具報告每一個方法的 JustMyCode 狀態，才會啟動這個 MDA。  不了解 JustMyCode \(例如沒有擴充功能的 MDbg.exe\) 的偵錯工具不會啟動這個 MDA，  您可以使用組態檔以及在 .mda.config 檔中明確設定 `justMyCode="false"`，以啟用這些偵錯工具的 MDA `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`\)。  
  
## 症狀  
 損毀或無法解釋的堆積損毀。  
  
## 原因  
 未在記憶體回收堆積上建立的重疊指標傳遞給特定的作業系統函式。  
  
 下表將顯示此 MDA 追蹤的函式。  
  
|模組|Function|  
|--------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2\_32.dll|`WSASend`|  
|WS2\_32.dll|`WSASendTo`|  
|WS2\_32.dll|`WSARecv`|  
|WS2\_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 在這個情況下，堆積損毀的可能性很高，因為進行呼叫的 <xref:System.AppDomain> 可能會卸載。  如果 <xref:System.AppDomain> 卸載，則應用程式的程式碼將會為重疊指標釋放記憶體 \(如此會在作業結束時造成損毀\)，或者程式碼將會遺漏記憶體 \(如此會在之後產生一些問題\)。  
  
## 解決方式  
 使用 <xref:System.Threading.Overlapped> 物件，並呼叫 <xref:System.Threading.Overlapped.Pack%2A> 方法來取得可傳遞給函式的 <xref:System.Threading.NativeOverlapped> 結構。  如果 <xref:System.AppDomain> 卸載，CLR 會等到非同步作業完成之後，再釋放指標。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 下列是來自這個 MDA 的輸出之範例。  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'.  If the AppDomain is shut down, this can cause heap corruption when the async I/O completes.  The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack().  If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)