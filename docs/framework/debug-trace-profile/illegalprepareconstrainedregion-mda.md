---
title: "illegalPrepareConstrainedRegion MDA | Microsoft Docs"
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
  - "PrepareConstrainedRegions method"
  - "managed debugging assistants (MDAs), illegal PrepareConstrainedRegions"
  - "try/catch exception handling, managed debugging assistants"
  - "IllegalPrepareConstrainedRegions MDA"
  - "MDAs (managed debugging assistants), illegal PrepareConstrainedRegions"
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# illegalPrepareConstrainedRegion MDA
當 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=fullName> 方法呼叫沒有直接位於例外狀況處理常式的 `try` 陳述式前面時，`illegalPrepareConstrainedRegion` Managed 偵錯助理 \(MDA\) 就會啟動。  這項限制屬於 MSIL 層級，因此可以允許在呼叫和 `try` 之間具有不產生程式碼的來源 \(例如註解\)。  
  
## 症狀  
 一直不將限制的執行區域 \(CER\) 視為此種執行區域，而是當成簡單的例外狀況處理區塊 \(`finally` 或 `catch`\)。  因此，這個區域不會在記憶體不足狀況或執行緒中止的事件中執行。  
  
## 原因  
 未正確地遵循 CER 的準備模式。這是一個錯誤事件。  在例外狀況處理常式的 `catch`\/`finally`\/`fault`\/`filter` 區塊中引入 CER 時，用來標記例外狀況處理常式的 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法呼叫，必須在 `try` 陳述式之前直接使用。  
  
## 解決方式  
 確定對 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的呼叫會直接出現在 `try` ``  陳述式之前。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 這個 MDA 會顯示呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的方法名稱、MSIL 位移 \(Offset\)，以及指示呼叫沒有直接位於 try 區塊開始位置之前的訊息。  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例說明會使這個 MDA 啟動的模式。  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)