---
title: Managed 執行緒狀態
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55409cd2c3bed2bc09db10622de1cceab934112
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45624563"
---
# <a name="managed-thread-states"></a><span data-ttu-id="00d39-102">Managed 執行緒狀態</span><span class="sxs-lookup"><span data-stu-id="00d39-102">Managed Thread States</span></span>
<span data-ttu-id="00d39-103">屬性 <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> 提供位元遮罩，表示執行緒的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="00d39-104">執行緒一律是在 <xref:System.Threading.ThreadState> 列舉至少一個可能的狀態中，而且可能同時在多個狀態中。</span><span class="sxs-lookup"><span data-stu-id="00d39-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00d39-105">執行緒狀態只有在少數偵錯案例中有意義。</span><span class="sxs-lookup"><span data-stu-id="00d39-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="00d39-106">您的程式碼絕對不應該使用執行緒狀態來同步處理執行緒活動。</span><span class="sxs-lookup"><span data-stu-id="00d39-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="00d39-107">當您建立 Managed 執行緒時，它是在 <xref:System.Threading.ThreadState.Unstarted> 狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="00d39-108">執行緒會保留在 <xref:System.Threading.ThreadState.Unstarted> 狀態，直到它被作業系統移至啟動的狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="00d39-109">呼叫 <xref:System.Threading.Thread.Start%2A> 可讓作業系統知道，可以啟動執行緒，但不會變更執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="00d39-110">進入 Managed 環境的 Unmanaged 執行緒已經處於啟動狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="00d39-111">一旦執行緒處於啟動狀態，有數個動作可能會導致它變更狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="00d39-112">下表列出會導致變更狀態的動作，以及對應的新狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="00d39-113">動作</span><span class="sxs-lookup"><span data-stu-id="00d39-113">Action</span></span>|<span data-ttu-id="00d39-114">產生新狀態</span><span class="sxs-lookup"><span data-stu-id="00d39-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="00d39-115">呼叫 <xref:System.Threading.Thread> 類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="00d39-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="00d39-116">另一個執行緒呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="00d39-117">執行緒回應 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="00d39-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="00d39-118">執行緒呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="00d39-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="00d39-119">執行緒對另一個物件呼叫 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="00d39-120">執行緒對另一個執行緒呼叫 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="00d39-121">另一個執行緒呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="00d39-122">執行緒回應 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 要求。</span><span class="sxs-lookup"><span data-stu-id="00d39-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="00d39-123">另一個執行緒呼叫 <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="00d39-124">另一個執行緒呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="00d39-125">執行緒回應 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00d39-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="00d39-126"><xref:System.Threading.ThreadState.Aborted>，然後 <xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="00d39-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="00d39-127">因為 <xref:System.Threading.ThreadState.Running> 狀態的值為 0，不可能執行位元測試，以探索此狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="00d39-128">相反地，您可以使用下列測試 (在虛擬程式碼中)：</span><span class="sxs-lookup"><span data-stu-id="00d39-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="00d39-129">執行緒經常在任何指定時間處於多個狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="00d39-130">比方說，如果執行緒在 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 呼叫上被阻擋，而另一個執行緒對相同執行緒呼叫 <xref:System.Threading.Thread.Abort%2A>，執行緒就會同時處於 <xref:System.Threading.ThreadState.WaitSleepJoin> 和 <xref:System.Threading.ThreadState.AbortRequested> 狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="00d39-131">在此情況下，當執行緒從呼叫返回 <xref:System.Threading.Monitor.Wait%2A> 或是遭到中斷時，就會收到 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="00d39-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="00d39-132">一旦執行緒因為呼叫 <xref:System.Threading.ThreadState.Unstarted> 而離開 <xref:System.Threading.Thread.Start%2A>狀態，它便無法再回到 <xref:System.Threading.ThreadState.Unstarted> 狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="00d39-133">執行緒永遠無法離開 <xref:System.Threading.ThreadState.Stopped> 狀態。</span><span class="sxs-lookup"><span data-stu-id="00d39-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d39-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00d39-134">See also</span></span>

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadState>  
- [<span data-ttu-id="00d39-135">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="00d39-135">Threading</span></span>](../../../docs/standard/threading/index.md)
