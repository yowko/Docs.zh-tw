---
title: "streamWriterBufferedDataLost MDA | Microsoft Docs"
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
  - "StreamWriter class, data buffering problems"
  - "managed debugging assistants (MDAs), StreamWriter data buffering"
  - "buffers, StreamWriter problems"
  - "MDAs (managed debugging assistants), StreamWriter data buffering"
  - "StreamWriter buffered data lost"
  - "data buffering problems"
  - "streamWriterBufferedDataLost MDA"
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# streamWriterBufferedDataLost MDA
在 <xref:System.IO.StreamWriter> 的執行個體毀壞之前，已寫入 <xref:System.IO.StreamWriter>，但是未接著呼叫 <xref:System.IO.StreamWriter.Flush%2A> 或 <xref:System.IO.StreamWriter.Close%2A> 方法時，即會啟動 `streamWriterBufferedDataLost` Managed 偵錯助理 \(MDA\)。  當這個 MDA 已啟用時，執行階段可判斷在 <xref:System.IO.StreamWriter> 中是否仍有任何緩衝的資料存在。  如果有緩衝的資料存在，則會啟用此 MDA。  呼叫 <xref:System.GC.Collect%2A> 和 <xref:System.GC.WaitForPendingFinalizers%2A> 方法可以強制完成項執行。  否則，完成項將會在任意時間執行，可能根本不會在處理序結束時執行。  在啟用這個 MDA 的情況下明確執行完成項，將有助於更可靠地重現這個問題類型。  
  
## 症狀  
 <xref:System.IO.StreamWriter> 不會將上一個 1–4 KB 的資料寫入到檔案中。  
  
## 原因  
 <xref:System.IO.StreamWriter> 會在內部緩衝資料，而這需要呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A> 方法，才能將緩衝的資料寫入到基礎資料存放區。  如果未適當呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A>，則緩衝於 <xref:System.IO.StreamWriter> 執行個體中的資料可能不會如預期般寫入。  
  
 下列是這個 MDA 應該攔截的編寫不良的程式碼範例。  
  
```  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 如果觸發了記憶體回收，然後暫止到完成項完成，則之前的程式碼將會以更可靠的方式啟動這個 MDA。  若要追蹤這個問題類型，您可以在偵錯組建中將下列程式碼加入到之前方法的結尾，  如此將會以可靠的方式啟動 MDA，但是，這樣當然不會修復問題的原因。  
  
```  
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## 解決方式  
 確定您在關閉具有 <xref:System.IO.StreamWriter> 執行個體的應用程式或任何程式碼區塊之前，已在 <xref:System.IO.StreamWriter> 上呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A>。  完成這項處理的一個最佳機制是使用 C\# `using` 區塊 \(Visual Basic 中為 `Using`\) 建立此執行個體，如此將可確保一定會叫用寫入器的 <xref:System.IO.StreamWriter.Dispose%2A> 方法，讓此執行個體正確關閉。  
  
```  
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 下列程式碼將示範相同的解決方法，其中會使用 `try/finally`，而非 `using`。  
  
```  
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 如果這兩個解決方法都不能使用 \(例如，當 <xref:System.IO.StreamWriter> 儲存在靜態變數中，而您無法輕易地在它的存留末期執行程式碼\)，則在最後一次使用它之後於 <xref:System.IO.StreamWriter> 上呼叫 <xref:System.IO.StreamWriter.Flush%2A>，或是在第一次使用它之前將 <xref:System.IO.StreamWriter.AutoFlush%2A> 屬性設定為 `true`，這樣應該可以避免這個問題的發生。  
  
```  
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## 對執行階段的影響  
 這個 MDA 對執行階段無效。  
  
## Output  
 一則訊息，表示已發生這項違規。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.IO.StreamWriter>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)