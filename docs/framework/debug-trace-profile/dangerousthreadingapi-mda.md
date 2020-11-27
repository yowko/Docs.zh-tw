---
title: dangerousThreadingAPI MDA
description: 請參閱 dangerousThreadingAPI managed 偵錯工具 (MDA) ，它會線上程暫止時啟動，而不是在目前線程以外的執行緒上呼叫暫止。
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 707e3e339cb8a692f862afc15328eef53f0547e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286080"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="b3d88-103">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="b3d88-103">dangerousThreadingAPI MDA</span></span>

<span data-ttu-id="b3d88-104">在目前執行緒以外的執行緒上呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 方法時，會啟用 `dangerousThreadingAPI` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="b3d88-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b3d88-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="b3d88-105">Symptoms</span></span>  

 <span data-ttu-id="b3d88-106">應用程式沒有回應或無限期停止回應。</span><span class="sxs-lookup"><span data-stu-id="b3d88-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="b3d88-107">系統或應用程式資料可能會暫時處於無法預測的狀態，或甚至已關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3d88-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="b3d88-108">某些作業未如預期完成。</span><span class="sxs-lookup"><span data-stu-id="b3d88-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="b3d88-109">由於這個問題原有的隨機性，徵兆可能會有很大的不同。</span><span class="sxs-lookup"><span data-stu-id="b3d88-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b3d88-110">原因</span><span class="sxs-lookup"><span data-stu-id="b3d88-110">Cause</span></span>  

 <span data-ttu-id="b3d88-111">使用 <xref:System.Threading.Thread.Suspend%2A> 方法，將執行緒非同步取代為另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="b3d88-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="b3d88-112">沒有任何方法可判斷執行緒何時可以安全地暫止另一個執行緒，而後者可能正在進行。</span><span class="sxs-lookup"><span data-stu-id="b3d88-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="b3d88-113">暫止執行緒可能會導致資料損毀或非變異值中斷。</span><span class="sxs-lookup"><span data-stu-id="b3d88-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="b3d88-114">如果執行緒進入暫止狀態，而且絕不會繼續使用 <xref:System.Threading.Thread.Resume%2A> 方法，則應用程式可能會無限期停止回應，並且可能破壞應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="b3d88-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="b3d88-115">這些方法已標記為過時。</span><span class="sxs-lookup"><span data-stu-id="b3d88-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="b3d88-116">如果目標執行緒擁有同步處理原始物件，則在暫止期間仍會擁有它們。</span><span class="sxs-lookup"><span data-stu-id="b3d88-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="b3d88-117">如果另一個執行緒 (例如執行 <xref:System.Threading.Thread.Suspend%2A> 的執行緒) 嘗試取得原始物件的鎖定，則這可能會導致死結。</span><span class="sxs-lookup"><span data-stu-id="b3d88-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="b3d88-118">在此情況下，問題資訊清單本身會是死結。</span><span class="sxs-lookup"><span data-stu-id="b3d88-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b3d88-119">解決方法</span><span class="sxs-lookup"><span data-stu-id="b3d88-119">Resolution</span></span>  

 <span data-ttu-id="b3d88-120">請避免需要使用 <xref:System.Threading.Thread.Suspend%2A> 和 <xref:System.Threading.Thread.Resume%2A> 的設計。</span><span class="sxs-lookup"><span data-stu-id="b3d88-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="b3d88-121">對於執行緒之間的合作，請使用同步處理原始物件，例如 <xref:System.Threading.Monitor>、<xref:System.Threading.ReaderWriterLock>、<xref:System.Threading.Mutex> 或 C# `lock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3d88-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="b3d88-122">如果您必須使用這些方法，請減少時間範圍，並將執行緒處於暫止狀態時執行的程式碼數量降至最低。</span><span class="sxs-lookup"><span data-stu-id="b3d88-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b3d88-123">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="b3d88-123">Effect on the Runtime</span></span>  

 <span data-ttu-id="b3d88-124">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="b3d88-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="b3d88-125">它只會報告危險執行緒處理作業的資料。</span><span class="sxs-lookup"><span data-stu-id="b3d88-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b3d88-126">輸出</span><span class="sxs-lookup"><span data-stu-id="b3d88-126">Output</span></span>  

 <span data-ttu-id="b3d88-127">MDA 識別可啟用它的危險執行緒處理方法。</span><span class="sxs-lookup"><span data-stu-id="b3d88-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b3d88-128">設定</span><span class="sxs-lookup"><span data-stu-id="b3d88-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="b3d88-129">範例</span><span class="sxs-lookup"><span data-stu-id="b3d88-129">Example</span></span>  

 <span data-ttu-id="b3d88-130">下列程式碼範例示範如何呼叫 <xref:System.Threading.Thread.Suspend%2A> 方法，以啟用 `dangerousThreadingAPI`。</span><span class="sxs-lookup"><span data-stu-id="b3d88-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3d88-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d88-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="b3d88-132">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="b3d88-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b3d88-133">lock 陳述式</span><span class="sxs-lookup"><span data-stu-id="b3d88-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
