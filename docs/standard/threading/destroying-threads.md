---
title: "Destroying Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "destroying threads"
  - "threading [.NET Framework], destroying threads"
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Destroying Threads
<xref:System.Threading.Thread.Abort%2A> 方法是用來永久停止 Managed 執行緒。  當您呼叫 <xref:System.Threading.Thread.Abort%2A> 時，Common Language Runtime 會在目標執行緒中擲回 <xref:System.Threading.ThreadAbortException>，而目標執行緒可加以攔截。  如需詳細資訊，請參閱 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>。  
  
> [!NOTE]
>  如果在呼叫執行緒的 <xref:System.Threading.Thread.Abort%2A> 方法時，此執行緒正在執行 Unmanaged 程式碼，則執行階段會為它標記 <xref:System.Threading.ThreadState?displayProperty=fullName>。  當此執行緒返回 Managed 程式碼時，會擲回例外狀況。  
  
 一旦執行緒被中止，就無法重新啟動。  
  
 <xref:System.Threading.Thread.Abort%2A> 方法不會讓此執行緒立即中止，因為目標執行緒可以攔截 <xref:System.Threading.ThreadAbortException>，並執行 `finally` 區塊中任意數量的程式碼。  如果您需要等候到此執行緒結束，您可以呼叫 <xref:System.Threading.Thread.Join%2A?displayProperty=fullName>。  <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> 是一個封鎖的呼叫，此呼叫要等到此執行緒實際停止執行或經過了選擇性的逾時間隔之後，才會傳回。  中止的執行緒可能會呼叫 <xref:System.Threading.Thread.ResetAbort%2A> 方法，或是在 `finally` 區塊中執行無限制的處理；因此，如果您未指定逾時，不保證等候一定會結束。  
  
 等候 <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> 方法呼叫的執行緒可被其他呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 的執行緒所中斷。  
  
## 處理 ThreadAbortException  
 如果您預期執行緒要中止，不論其形式是當做從您自己的程式碼呼叫 <xref:System.Threading.Thread.Abort%2A> 的結果，或是當做執行緒執行所在的應用程式定義域卸載的結果 \(<xref:System.AppDomain.Unload%2A?displayProperty=fullName> 使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 來結束執行緒\)，則執行緒必須處理 <xref:System.Threading.ThreadAbortException>，並執行 `finally` 子句中的任何最終處理，如下列程式碼所示。  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 您的清除程式碼必須在 `catch` 子句或 `finally` 子句中，因為在沒有 `finally` 子句的情況下遇到 `finally` 子句結尾或 `catch` 子句結尾時，系統會重新擲回 <xref:System.Threading.ThreadAbortException>。  
  
 您可以藉由呼叫 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=fullName> 方法，防止系統重新擲回此例外狀況。  但是，只有當您的程式碼會造成 <xref:System.Threading.ThreadAbortException> 時，才應該這麼做。  
  
## 請參閱  
 <xref:System.Threading.ThreadAbortException>   
 <xref:System.Threading.Thread>   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)