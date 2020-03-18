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
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155928"
---
# <a name="destroying-threads"></a><span data-ttu-id="8f437-102">終結執行緒</span><span class="sxs-lookup"><span data-stu-id="8f437-102">Destroying threads</span></span>

<span data-ttu-id="8f437-103">要終止執行緒的執行，通常使用[協作取消模型](cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="8f437-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="8f437-104">有時無法以協作方式停止執行緒，因為它運行的協力廠商代碼不是為協作取消而設計的。</span><span class="sxs-lookup"><span data-stu-id="8f437-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="8f437-105">.NET 框架中<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>的方法可用於強制終止託管執行緒。</span><span class="sxs-lookup"><span data-stu-id="8f437-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="8f437-106">調用 時<xref:System.Threading.Thread.Abort%2A>調用 ，通用語言運行時在目標<xref:System.Threading.ThreadAbortException>執行緒中引發 一個，目標執行緒可以捕獲該執行緒。</span><span class="sxs-lookup"><span data-stu-id="8f437-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="8f437-107">如需詳細資訊，請參閱 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8f437-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f437-108">.NET Core 中不支援該方法<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8f437-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="8f437-109">如果需要在 .NET Core 中強制終止協力廠商代碼的執行，請在單獨的進程中運行它並使用<xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8f437-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="8f437-110">如果執行緒在其 <xref:System.Threading.Thread.Abort%2A> 方法被呼叫時正在執行非受控碼，執行階段就會將它標示為 <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8f437-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f437-111">當執行緒返回受控碼時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8f437-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="8f437-112">一旦中止執行緒之後，就無法重新啟動。</span><span class="sxs-lookup"><span data-stu-id="8f437-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="8f437-113"><xref:System.Threading.Thread.Abort%2A> 方法不會造成執行緒立即中止，因為目標執行緒可以攔截 <xref:System.Threading.ThreadAbortException> 並執行 `finally` 區塊中任意數量的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f437-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="8f437-114">如果您需要等候，直到執行緒結束，則可呼叫 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8f437-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="8f437-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 是一個封鎖呼叫，在執行緒實際停止執行或已經過選擇性的逾時間隔之後才會返回。</span><span class="sxs-lookup"><span data-stu-id="8f437-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="8f437-116">中止的執行緒可以呼叫 <xref:System.Threading.Thread.ResetAbort%2A> 方法，或在 `finally` 區塊中執行未繫結的處理，因此，如果您未指定逾時，則不保證會等候結束。</span><span class="sxs-lookup"><span data-stu-id="8f437-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="8f437-117">正在對 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 方法的呼叫中等候的執行緒可由呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 的其他執行緒來中斷。</span><span class="sxs-lookup"><span data-stu-id="8f437-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="8f437-118">處理 ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="8f437-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="8f437-119">如果您預期執行緒會中止，無論是從您自己的程式碼呼叫 <xref:System.Threading.Thread.Abort%2A>，還是卸載執行緒執行所在的應用程式定義域 (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 來終止執行緒)，您的執行緒都必須處理 <xref:System.Threading.ThreadAbortException> 並執行 `finally` 子句中的任何最終處理，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8f437-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8f437-120">清除程式碼必須位於 `catch` 子句或 `finally` 子句，因為系統必須在 `finally` 子句結尾處重新擲回 <xref:System.Threading.ThreadAbortException>，如果沒有 `finally` 子句，則會在 `catch` 子句結尾處重新擲回。</span><span class="sxs-lookup"><span data-stu-id="8f437-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="8f437-121">您可以呼叫 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> 方法來防止系統重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8f437-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8f437-122">但是，只有當您自己的程式碼會造成 <xref:System.Threading.ThreadAbortException>，才應採取此作法。</span><span class="sxs-lookup"><span data-stu-id="8f437-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f437-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f437-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="8f437-124">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="8f437-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
