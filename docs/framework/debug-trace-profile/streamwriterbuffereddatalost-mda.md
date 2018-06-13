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
ms.openlocfilehash: 15957ce03925d75021d88bc81d12809c3fe31c2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389937"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="5e1a5-102">streamWriterBufferedDataLost MDA</span><span class="sxs-lookup"><span data-stu-id="5e1a5-102">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="5e1a5-103">`streamWriterBufferedDataLost` Managed 偵錯助理 (MDA) 會在寫入 <xref:System.IO.StreamWriter> 時啟動，但在終結 <xref:System.IO.StreamWriter> 的執行個體之前，不會接著呼叫 <xref:System.IO.StreamWriter.Flush%2A> 或 <xref:System.IO.StreamWriter.Close%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-103">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="5e1a5-104">此 MDA 啟用時，執行階段會判斷在 <xref:System.IO.StreamWriter> 內是否仍有任何緩衝資料存在。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-104">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="5e1a5-105">如果緩衝資料不存在，則會啟動 MDA。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-105">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="5e1a5-106">呼叫 <xref:System.GC.Collect%2A> 和 <xref:System.GC.WaitForPendingFinalizers%2A> 方法可以強制執行完成項。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-106">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="5e1a5-107">否則完成項會在任意時間執行，並且可能根本不是在處理序結束時。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-107">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="5e1a5-108">明確執行完成項並啟用這個 MDA，可協助您更可靠地重現這種類型的問題。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-108">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5e1a5-109">徵兆</span><span class="sxs-lookup"><span data-stu-id="5e1a5-109">Symptoms</span></span>  
 <span data-ttu-id="5e1a5-110"><xref:System.IO.StreamWriter> 不會將資料的最後 1–4 KB 寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-110">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5e1a5-111">原因</span><span class="sxs-lookup"><span data-stu-id="5e1a5-111">Cause</span></span>  
 <span data-ttu-id="5e1a5-112"><xref:System.IO.StreamWriter> 會在內部緩衝處理資料，這樣需要呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A> 方法以將緩衝資料寫入基礎資料存放區。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-112">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="5e1a5-113">如果 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A> 未適當地呼叫，則 <xref:System.IO.StreamWriter> 執行個體中的緩衝資料可能不會如預期般寫入。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-113">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="5e1a5-114">以下是此 MDA 應該攔截、撰寫不夠周全的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-114">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="5e1a5-115">如果觸發記憶體回收且然後暫止，直到完成項完成，上述程式碼會更可靠地啟動此 MDA。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-115">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="5e1a5-116">若要追蹤這種類型的問題，您可以將下列程式碼新增在偵錯組建中前述方法的結尾。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-116">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="5e1a5-117">這將有助於可靠地啟用 MDA，但當然無法修正問題的原因。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-117">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="5e1a5-118">解決方式</span><span class="sxs-lookup"><span data-stu-id="5e1a5-118">Resolution</span></span>  
 <span data-ttu-id="5e1a5-119">請確定您對 <xref:System.IO.StreamWriter> 呼叫 <xref:System.IO.StreamWriter.Close%2A> 或 <xref:System.IO.StreamWriter.Flush%2A>，然後才關閉具有 <xref:System.IO.StreamWriter> 執行個體的應用程式或任何程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-119">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="5e1a5-120">達到此目的的其中一個最佳機制，是使用 C# `using` 區塊 (在 Visual Basic 中為 `Using`) 建立執行個體，這可確保叫用寫入器的 <xref:System.IO.StreamWriter.Dispose%2A> 方法，導致執行個體正確關閉。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-120">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="5e1a5-121">下列程式碼會示範相同的解決方案，並且使用 `try/finally` 而不是 `using`。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-121">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
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
  
 <span data-ttu-id="5e1a5-122">如果這些解決方案都無法使用 (例如，如果 <xref:System.IO.StreamWriter> 儲存在靜態變數，而且您無法輕鬆地在其存留期即將結束執行程式碼)，那麼請在最後一次使用它之後對 <xref:System.IO.StreamWriter> 呼叫 <xref:System.IO.StreamWriter.Flush%2A>，或是在第一次使用之前將 <xref:System.IO.StreamWriter.AutoFlush%2A> 屬性設為 `true`，以避免此問題。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-122">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
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
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5e1a5-123">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="5e1a5-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="5e1a5-124">此 MDA 對執行階段沒有影響。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-124">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5e1a5-125">輸出</span><span class="sxs-lookup"><span data-stu-id="5e1a5-125">Output</span></span>  
 <span data-ttu-id="5e1a5-126">指出發生此違規的訊息。</span><span class="sxs-lookup"><span data-stu-id="5e1a5-126">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5e1a5-127">組態</span><span class="sxs-lookup"><span data-stu-id="5e1a5-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e1a5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1a5-128">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="5e1a5-129">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="5e1a5-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
