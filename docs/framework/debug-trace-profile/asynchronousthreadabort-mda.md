---
title: "asynchronousThreadAbort MDA | Microsoft Docs"
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
  - "asynchronous thread aborts"
  - "AsynchronousThreadAbort MDA"
  - "managed debugging assistants (MDAs), asynchronous thread aborts"
  - "threading [.NET Framework], managed debugging assistants"
  - "MDAs (managed debugging assistants), asynchronous thread aborts"
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# asynchronousThreadAbort MDA
當執行緒嘗試對另一個執行緒引入非同步中止時，`asynchronousThreadAbort` Managed 偵錯助理 \(MDA\) 就會啟動。  同步執行緒中止並不會啟動 `asynchronousThreadAbort` MDA。  
  
## 症狀  
 當主應用程式執行緒中止時，應用程式會損毀，並且出現未處理的 <xref:System.Threading.ThreadAbortException>。  如果當時要繼續執行應用程式，可能會出現比應用程式損毀更糟的結果，甚至還會造成資料損毀。  
  
 原本該自動進行的作業，很可能在部分完成後遭到中斷，使得應用程式資料處於無法預期的狀態。  <xref:System.Threading.ThreadAbortException> 可以從程式碼執行中似乎是隨機點產生，這些通常預期都不會引發例外狀況。  程式碼可能無法處理這種例外狀況，因而造成損毀。  
  
 由於這個問題原有的隨機性，症狀可能會有很大的不同。  
  
## 原因  
 一個執行緒中的程式碼呼叫了目標執行緒上的 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 方法，造成非同步執行緒中止。  由於對 <xref:System.Threading.Thread.Abort%2A> 發出呼叫的程式碼，不是在中止作業目標 \(Target\) 的執行緒上，因此，執行緒中止是非同步的。  同步執行緒中止應該不會造成問題，因為執行 <xref:System.Threading.Thread.Abort%2A> 的程式碼，應該已經只在應用程式狀態一致的安全檢查點上執行過。  
  
 由於非同步執行緒中止是在目標執行緒執行中的不可預期點進行，因而出現問題。  若要避免發生這種情形，請撰寫程式碼，並在可能以這種方式中止的執行緒上執行該程式碼，以便在程式碼的幾乎每一行處理 <xref:System.Threading.ThreadAbortException>，讓應用程式資料能夠回到一致的狀態。  期待在撰寫程式碼時會設想這個問題，或是撰寫出能夠防護各種可能情況的程式碼，都是不切實際的。  
  
 呼叫進入 Unmanaged 程式碼和 `finally` 區塊，並不會非同步地中止，而是會立即從這些分類的其中一個分類中結束。  
  
 由於本問題原有的隨機性，可能會難以判定原因。  
  
## 解決方式  
 避免需要使用非同步執行緒中止的程式碼設計。  有數種處理方法更適合用來中斷不需要呼叫 <xref:System.Threading.Thread.Abort%2A> 的目標執行緒。  最安全的方法就是採用一種機制，例如通用的屬性，對目標執行緒發出信號以要求中斷。  目標執行緒會在特定的安全檢查點檢查信號。  如果注意到已經要求中斷，目標執行緒就會順利地關閉。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  它只會報告有關非同步執行緒中止的資料。  
  
## Output  
 這個 MDA 會報告執行中止之執行緒的 ID，以及做為中止目標之執行緒的 ID。  由於僅限於非同步中止，因此，這兩者絕對不會相同。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <asynchronousThreadAbort />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 要啟動 `asynchronousThreadAbort` MDA，只需要呼叫個別執行地執行緒上的 <xref:System.Threading.Thread.Abort%2A>。  請考慮如果執行緒的內容啟動函式是一組更為複雜的作業，而那些作業可能會在任意一點因為中止而中斷的後果。  
  
```  
using System.Threading;  
void FireMda()  
{  
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Abort();   
    t.Join();  
}  
```  
  
## 請參閱  
 <xref:System.Threading.Thread>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)