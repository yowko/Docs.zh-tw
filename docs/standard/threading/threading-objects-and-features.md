---
title: 執行緒物件和功能
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039325"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="a886d-102">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="a886d-102">Threading objects and features</span></span>

<span data-ttu-id="a886d-103">除了 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別以外，.NET 還會提供一些類別來協助您開發多執行緒應用程式。</span><span class="sxs-lookup"><span data-stu-id="a886d-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="a886d-104">下列文章概述這些類別：</span><span class="sxs-lookup"><span data-stu-id="a886d-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="a886d-105">標題</span><span class="sxs-lookup"><span data-stu-id="a886d-105">Title</span></span>|<span data-ttu-id="a886d-106">描述</span><span class="sxs-lookup"><span data-stu-id="a886d-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a886d-107">受控執行緒集區</span><span class="sxs-lookup"><span data-stu-id="a886d-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="a886d-108">描述 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別，這個類別提供 .NET 受控背景工作執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="a886d-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="a886d-109">計時器</span><span class="sxs-lookup"><span data-stu-id="a886d-109">Timers</span></span>](timers.md)|<span data-ttu-id="a886d-110">說明可用於多執行緒環境的計時器。</span><span class="sxs-lookup"><span data-stu-id="a886d-110">Describes timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="a886d-111">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="a886d-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="a886d-112">描述可用來同步對資料的存取或控制執行緒互動的類別。</span><span class="sxs-lookup"><span data-stu-id="a886d-112">Describes classes that can be used to synchronize access to data or control thread interaction.</span></span>|
|[<span data-ttu-id="a886d-113">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a886d-113">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|<span data-ttu-id="a886d-114">描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。</span><span class="sxs-lookup"><span data-stu-id="a886d-114">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>|
|[<span data-ttu-id="a886d-115">Mutex</span><span class="sxs-lookup"><span data-stu-id="a886d-115">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="a886d-116">說明如何使用 <xref:System.Threading.Mutex?displayProperty=nameWithType> 同步對物件的存取，或建置自己的同步處理機制。</span><span class="sxs-lookup"><span data-stu-id="a886d-116">Describes how to use a <xref:System.Threading.Mutex?displayProperty=nameWithType> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>|
|[<span data-ttu-id="a886d-117">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="a886d-117">Interlocked operations</span></span>](interlocked-operations.md)|<span data-ttu-id="a886d-118">描述 <xref:System.Threading.Interlocked?displayProperty=nameWithType> 類別，這個類別為多個執行緒共用的變數提供不可部分完成的作業。</span><span class="sxs-lookup"><span data-stu-id="a886d-118">Describes the <xref:System.Threading.Interlocked?displayProperty=nameWithType> class, which provides atomic operations for variables that are shared by multiple threads.</span></span>|
|[<span data-ttu-id="a886d-119">Reader-Writer 鎖定</span><span class="sxs-lookup"><span data-stu-id="a886d-119">Reader-Writer Locks</span></span>](reader-writer-locks.md)|<span data-ttu-id="a886d-120">描述 <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> 類別，這個類別提供單一寫入器/多個讀取器語意。</span><span class="sxs-lookup"><span data-stu-id="a886d-120">Describes the <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> class, which provides single-writer/multiple-reader semantics.</span></span>|
|[<span data-ttu-id="a886d-121">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a886d-121">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="a886d-122">描述 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 類別，並說明如何用以控制對有限資源的存取。</span><span class="sxs-lookup"><span data-stu-id="a886d-122">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class and explains how to use it to control access to limited resources.</span></span>|
|[<span data-ttu-id="a886d-123">barrier</span><span class="sxs-lookup"><span data-stu-id="a886d-123">Barrier</span></span>](barrier.md)|<span data-ttu-id="a886d-124">描述 <xref:System.Threading.Barrier?displayProperty=nameWithType> 類別，這個類別會實作屏障模式以便協調階段式作業中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a886d-124">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class that implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="a886d-125">SpinLock</span><span class="sxs-lookup"><span data-stu-id="a886d-125">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="a886d-126">描述 <xref:System.Threading.SpinLock?displayProperty=nameWithType> 類別，這是適用於特定低階案例之 <xref:System.Threading.Monitor?displayProperty=nameWithType> 類別的輕量型替代方案。</span><span class="sxs-lookup"><span data-stu-id="a886d-126">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> class, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level scenarios.</span></span>|
|[<span data-ttu-id="a886d-127">SpinWait</span><span class="sxs-lookup"><span data-stu-id="a886d-127">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="a886d-128">描述 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 類別，這是在起始核心架構等候之前，執行忙碌空轉的低階同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="a886d-128">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> class, which is a low-level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a886d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a886d-129">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="a886d-130">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="a886d-130">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="a886d-131">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="a886d-131">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="a886d-132">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="a886d-132">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="a886d-133">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="a886d-133">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
