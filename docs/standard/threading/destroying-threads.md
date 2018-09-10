---
title: 終結執行緒
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a243c95aff77a5de2b3af15542c0bcc44870333
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205967"
---
# <a name="destroying-threads"></a><span data-ttu-id="67ac7-102">終結執行緒</span><span class="sxs-lookup"><span data-stu-id="67ac7-102">Destroying threads</span></span>
<span data-ttu-id="67ac7-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法可用來永久停止受控執行緒。</span><span class="sxs-lookup"><span data-stu-id="67ac7-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="67ac7-104">當您呼叫 <xref:System.Threading.Thread.Abort%2A> 時，通用語言執行平台會在目標執行緒中擲回 <xref:System.Threading.ThreadAbortException>，而目標執行緒可加以攔截。</span><span class="sxs-lookup"><span data-stu-id="67ac7-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="67ac7-105">如需詳細資訊，請參閱<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67ac7-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ac7-106">如果執行緒在其 <xref:System.Threading.Thread.Abort%2A> 方法被呼叫時正在執行非受控碼，執行階段就會將它標示為 <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67ac7-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67ac7-107">當執行緒返回受控碼時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67ac7-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="67ac7-108">一旦中止執行緒之後，就無法重新啟動。</span><span class="sxs-lookup"><span data-stu-id="67ac7-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="67ac7-109"><xref:System.Threading.Thread.Abort%2A> 方法不會造成執行緒立即中止，因為目標執行緒可以攔截 <xref:System.Threading.ThreadAbortException> 並執行 `finally` 區塊中任意數量的程式碼。</span><span class="sxs-lookup"><span data-stu-id="67ac7-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="67ac7-110">如果您需要等候，直到執行緒結束，則可呼叫 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67ac7-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="67ac7-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 是一個封鎖呼叫，在執行緒實際停止執行或已經過選擇性的逾時間隔之後才會返回。</span><span class="sxs-lookup"><span data-stu-id="67ac7-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="67ac7-112">中止的執行緒可以呼叫 <xref:System.Threading.Thread.ResetAbort%2A> 方法，或在 `finally` 區塊中執行未繫結的處理，因此，如果您未指定逾時，則不保證會等候結束。</span><span class="sxs-lookup"><span data-stu-id="67ac7-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="67ac7-113">正在對 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 方法的呼叫中等候的執行緒可由呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 的其他執行緒來中斷。</span><span class="sxs-lookup"><span data-stu-id="67ac7-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="67ac7-114">處理 ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="67ac7-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="67ac7-115">如果您預期執行緒會中止，無論是從您自己的程式碼呼叫 <xref:System.Threading.Thread.Abort%2A>，還是卸載執行緒執行所在的應用程式定義域 (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 來終止執行緒)，您的執行緒都必須處理 <xref:System.Threading.ThreadAbortException> 並執行 `finally` 子句中的任何最終處理，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="67ac7-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="67ac7-116">清除程式碼必須位於 `catch` 子句或 `finally` 子句，因為系統必須在 `finally` 子句結尾處重新擲回 <xref:System.Threading.ThreadAbortException>，如果沒有 `finally` 子句，則會在 `catch` 子句結尾處重新擲回。</span><span class="sxs-lookup"><span data-stu-id="67ac7-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="67ac7-117">您可以呼叫 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> 方法來防止系統重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67ac7-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="67ac7-118">但是，只有當您自己的程式碼會造成 <xref:System.Threading.ThreadAbortException>，才應採取此作法。</span><span class="sxs-lookup"><span data-stu-id="67ac7-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ac7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67ac7-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- [<span data-ttu-id="67ac7-120">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="67ac7-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
