---
title: 執行緒物件和功能
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 745cd1e17e2c06a513c6fdafe8f6b5f464b95d5f
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479655"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="f192b-102">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="f192b-102">Threading objects and features</span></span>

<span data-ttu-id="f192b-103">除了 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別以外，.NET 還會提供一些類別來協助您開發多執行緒應用程式。</span><span class="sxs-lookup"><span data-stu-id="f192b-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="f192b-104">下列文章概述這些類別：</span><span class="sxs-lookup"><span data-stu-id="f192b-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="f192b-105">標題</span><span class="sxs-lookup"><span data-stu-id="f192b-105">Title</span></span>|<span data-ttu-id="f192b-106">描述</span><span class="sxs-lookup"><span data-stu-id="f192b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f192b-107">受控執行緒集區</span><span class="sxs-lookup"><span data-stu-id="f192b-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="f192b-108">描述 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別，這個類別提供 .NET 受控背景工作執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="f192b-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="f192b-109">計時器</span><span class="sxs-lookup"><span data-stu-id="f192b-109">Timers</span></span>](timers.md)|<span data-ttu-id="f192b-110">說明可用於多執行緒環境的 .NET 計時器。</span><span class="sxs-lookup"><span data-stu-id="f192b-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="f192b-111">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="f192b-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="f192b-112">描述可用來同步對共用資源的存取或控制執行緒互動的類型。</span><span class="sxs-lookup"><span data-stu-id="f192b-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="f192b-113">EventWaitHandle、CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="f192b-113">EventWaitHandle, CountdownEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|<span data-ttu-id="f192b-114">描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。</span><span class="sxs-lookup"><span data-stu-id="f192b-114">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>|
|[<span data-ttu-id="f192b-115">Mutex</span><span class="sxs-lookup"><span data-stu-id="f192b-115">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="f192b-116">描述 <xref:System.Threading.Mutex?displayProperty=nameWithType>，它能授與對共用資源的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="f192b-116">Describes <xref:System.Threading.Mutex?displayProperty=nameWithType>, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="f192b-117">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="f192b-117">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="f192b-118">描述 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 類別，它能限制可以同時存取共用資源或資源集區的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="f192b-118">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="f192b-119">barrier</span><span class="sxs-lookup"><span data-stu-id="f192b-119">Barrier</span></span>](barrier.md)|<span data-ttu-id="f192b-120">描述 <xref:System.Threading.Barrier?displayProperty=nameWithType> 類別，這個類別會實作屏障模式以便協調階段式作業中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f192b-120">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class that implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="f192b-121">SpinLock</span><span class="sxs-lookup"><span data-stu-id="f192b-121">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="f192b-122">描述 <xref:System.Threading.SpinLock?displayProperty=nameWithType> 結構，這是適用於特定低階鎖定案例之 <xref:System.Threading.Monitor?displayProperty=nameWithType> 類別的輕量型替代方案。</span><span class="sxs-lookup"><span data-stu-id="f192b-122">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="f192b-123">SpinWait</span><span class="sxs-lookup"><span data-stu-id="f192b-123">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="f192b-124">描述 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 結構，它能提供微調式等候的支援。</span><span class="sxs-lookup"><span data-stu-id="f192b-124">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f192b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f192b-125">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="f192b-126">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="f192b-126">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="f192b-127">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="f192b-127">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="f192b-128">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="f192b-128">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="f192b-129">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="f192b-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
