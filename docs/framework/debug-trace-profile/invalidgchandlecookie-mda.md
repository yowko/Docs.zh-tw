---
title: "invalidGCHandleCookie MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid cookies"
  - "cookies, invalid"
  - "managed debugging assistants (MDAs), invalid cookies"
  - "InvalidGCHandleCookie MDA"
  - "invalid cookies"
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# invalidGCHandleCookie MDA
嘗試從無效的 <xref:System.IntPtr> Cookie 轉換至 <xref:System.Runtime.InteropServices.GCHandle> 時，`invalidGCHandleCookie` Managed 偵錯助理 \(MDA\) 就會啟動。  
  
## 症狀  
 嘗試從 <xref:System.IntPtr> 使用或擷取 <xref:System.Runtime.InteropServices.GCHandle> 時，發生未定義的行為，例如存取違規和記憶體損毀。  
  
## 原因  
 Cookie 可能是無效的，因為 Cookie 原先並非由 <xref:System.Runtime.InteropServices.GCHandle> 產生，它表示已經釋放的 <xref:System.Runtime.InteropServices.GCHandle>，並且也是不同應用程式定義域中 <xref:System.Runtime.InteropServices.GCHandle> 的 Cookie，或是做為 <xref:System.Runtime.InteropServices.GCHandle> 封送處理 \(Marshal\) 至機器碼，但卻傳遞回到 CLR 做為 <xref:System.IntPtr>，並在其中嘗試轉型 \(Cast\)。  
  
## 解決方式  
 為 <xref:System.Runtime.InteropServices.GCHandle> 指定有效的 <xref:System.IntPtr> Cookie。  
  
## 對執行階段的影響  
 在啟用這個 MDA 時，由於傳回的 Cookie 值不同於未啟用這個 MDA 時所傳回的值，偵錯工具不再能夠追蹤回到它們的物件。  
  
## Output  
 會報告無效的 <xref:System.IntPtr> Cookie 值。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>   
 <xref:System.Runtime.InteropServices.GCHandle>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)