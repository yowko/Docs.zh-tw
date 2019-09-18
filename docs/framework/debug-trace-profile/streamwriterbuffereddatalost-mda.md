---
title: streamWriterBufferedDataLost MDA
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3dcdd329318d48efa203d2b9dcbfe3501d94b3e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052274"
---
# <a name="streamwriterbuffereddatalost-mda"></a>streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` Managed 偵錯助理 (MDA) 會在寫入 <xref:System.IO.StreamWriter> 時啟動，但在終結 <xref:System.IO.StreamWriter> 的執行個體之前，不會接著呼叫 <xref:System.IO.StreamWriter.Flush%2A> 或 <xref:System.IO.StreamWriter.Close%2A> 方法。 此 MDA 啟用時，執行階段會判斷在 <xref:System.IO.StreamWriter> 內是否仍有任何緩衝資料存在。 如果緩衝資料不存在，則會啟動 MDA。 呼叫 <xref:System.GC.Collect%2A> 和 <xref:System.GC.WaitForPendingFinalizers%2A> 方法可以強制執行完成項。 否則完成項會在任意時間執行，並且可能根本不是在處理序結束時。 明確執行完成項並啟用這個 MDA，可協助您更可靠地重現這種類型的問題。  
  
## <a name="symptoms"></a>徵兆  
 <xref:System.IO.StreamWriter> 不會將資料的最後 1–4 KB 寫入至檔案。  
  
## <a name="cause"></a>原因  
 <xref:System.IO.StreamWriter> 會在內部緩衝處理資料，這樣需要呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A> 方法以將緩衝資料寫入基礎資料存放區。 如果 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A> 未適當地呼叫，則 <xref:System.IO.StreamWriter> 執行個體中的緩衝資料可能不會如預期般寫入。  
  
 以下是此 MDA 應該攔截、撰寫不夠周全的程式碼範例。  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 如果觸發記憶體回收且然後暫止，直到完成項完成，上述程式碼會更可靠地啟動此 MDA。 若要追蹤這種類型的問題，您可以將下列程式碼新增在偵錯組建中前述方法的結尾。 這將有助於可靠地啟用 MDA，但當然無法修正問題的原因。  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>解決方式  
 請確定您對 <xref:System.IO.StreamWriter> 呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A>，然後才關閉具有 <xref:System.IO.StreamWriter> 執行個體的應用程式或任何程式碼區塊。 達到此目的的其中一個最佳機制，是使用 C# `using` 區塊 (在 Visual Basic 中為 `Using`) 建立執行個體，這可確保叫用寫入器的 <xref:System.IO.StreamWriter.Dispose%2A> 方法，導致執行個體正確關閉。  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 下列程式碼會示範相同的解決方案，並且使用 `try/finally` 而不是 `using`。  
  
```csharp
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
  
 如果這些解決方案都無法使用 (例如，如果 <xref:System.IO.StreamWriter> 儲存在靜態變數，而且您無法輕鬆地在其存留期即將結束執行程式碼)，那麼請在最後一次使用它之後對 <xref:System.IO.StreamWriter> 呼叫 <xref:System.IO.StreamWriter.Flush%2A>，或是在第一次使用之前將 <xref:System.IO.StreamWriter.AutoFlush%2A> 屬性設為 `true`，以避免此問題。  
  
```csharp
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
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對執行階段沒有影響。  
  
## <a name="output"></a>Output  
 指出發生此違規的訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StreamWriter>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
