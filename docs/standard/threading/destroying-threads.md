---
title: "終結執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a><span data-ttu-id="a3dc1-102">終結執行緒</span><span class="sxs-lookup"><span data-stu-id="a3dc1-102">Destroying Threads</span></span>
<span data-ttu-id="a3dc1-103"><xref:System.Threading.Thread.Abort%2A>方法用來永久停止 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="a3dc1-104">當您呼叫<xref:System.Threading.Thread.Abort%2A>，common language runtime 會擲回<xref:System.Threading.ThreadAbortException>中，在此目標執行緒可能會攔截目標執行緒。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="a3dc1-105">如需詳細資訊，請參閱<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dc1-106">如果執行緒正在執行 unmanaged 程式碼時其<xref:System.Threading.Thread.Abort%2A>呼叫方法時，執行階段會將其標示<xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a3dc1-107">執行緒傳回給 managed 程式碼時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="a3dc1-108">一旦執行緒已中止時，它在重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="a3dc1-109"><xref:System.Threading.Thread.Abort%2A>方法不會造成執行緒中止，因為目標執行緒可能會攔截<xref:System.Threading.ThreadAbortException>並執行程式碼中的任意數量`finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="a3dc1-110">您可以呼叫<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>如果您需要等候，直到執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="a3dc1-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>封鎖呼叫執行緒已實際停止執行之前不會傳回或選用的逾時間隔已經耗盡。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="a3dc1-112">已中止的執行緒可以呼叫<xref:System.Threading.Thread.ResetAbort%2A>方法或執行中的未繫結的處理`finally`區塊中，因此如果您未指定逾時，不保證結束等候。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="a3dc1-113">等待在呼叫的執行緒<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>方法可以中斷由其他執行緒呼叫<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="a3dc1-114">處理 ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="a3dc1-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="a3dc1-115">如果您預期您的執行緒會中止，呼叫的結果為<xref:System.Threading.Thread.Abort%2A>從自己的程式碼或執行後卸載應用程式定義域的執行緒已執行 (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>使用<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>終止執行緒)，您的執行緒必須處理<xref:System.Threading.ThreadAbortException>並執行中的任何最終處理`finally`子句，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a3dc1-116">清除程式碼必須在`catch`子句或`finally`子句，因為<xref:System.Threading.ThreadAbortException>重新擲回由系統在結尾`finally`子句，或結尾處`catch`子句如果沒有任何`finally`子句。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="a3dc1-117">您可以防止重新例外狀況擲回藉由呼叫系統<xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a3dc1-118">但是，您應該採取此只有當您自己的程式碼造成<xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="a3dc1-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dc1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3dc1-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="a3dc1-120">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="a3dc1-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
