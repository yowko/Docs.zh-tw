---
title: 工作站與伺服器垃圾回收 (GC)
description: 在 .NET 中瞭解工作站和伺服器垃圾回收。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103552"
---
# <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="beca6-103">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="beca6-103">Workstation and server garbage collection</span></span>

<span data-ttu-id="beca6-104">記憶體回收行程會自行調整而且可在各種案例中運作。</span><span class="sxs-lookup"><span data-stu-id="beca6-104">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="beca6-105">但是,您可以根據工作負載的特徵[設定垃圾回收的類型](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="beca6-105">However, you can [set the type of garbage collection](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) based on the characteristics of the workload.</span></span> <span data-ttu-id="beca6-106">CLR 會提供下列記憶體回收類型：</span><span class="sxs-lookup"><span data-stu-id="beca6-106">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="beca6-107">工作站垃圾回收 (GC),專為用戶端應用設計。</span><span class="sxs-lookup"><span data-stu-id="beca6-107">Workstation garbage collection (GC), which is designed for client apps.</span></span> <span data-ttu-id="beca6-108">它是獨立應用的預設 GC 風格。</span><span class="sxs-lookup"><span data-stu-id="beca6-108">It's the default GC flavor for standalone apps.</span></span> <span data-ttu-id="beca6-109">對於託管應用(例如,由ASP.NET託管的應用,主機確定預設 GC 風格。</span><span class="sxs-lookup"><span data-stu-id="beca6-109">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="beca6-110">工作站記憶體回收可能是並行或非並行的。</span><span class="sxs-lookup"><span data-stu-id="beca6-110">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="beca6-111">併發 (或*後台*) 垃圾回收使託管線程能夠在垃圾回收期間繼續操作。</span><span class="sxs-lookup"><span data-stu-id="beca6-111">Concurrent (or *background*) garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="beca6-112">[後臺垃圾資源](background-gc.md)將取代 .NET 框架 4 和更高版本中[的併發垃圾回收](background-gc.md#concurrent-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="beca6-112">[Background garbage collection](background-gc.md) replaces [concurrent garbage collection](background-gc.md#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="beca6-113">伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="beca6-113">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="beca6-114">在 .NET Core 中,伺服器垃圾回收可以是非併發或後台。</span><span class="sxs-lookup"><span data-stu-id="beca6-114">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="beca6-115">在 .NET 框架 4.5 和更高版本中,伺服器垃圾回收可以是非併發或後臺。</span><span class="sxs-lookup"><span data-stu-id="beca6-115">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background.</span></span> <span data-ttu-id="beca6-116">在 .NET 框架 4 和早期版本中,伺服器垃圾回收是非併發的。</span><span class="sxs-lookup"><span data-stu-id="beca6-116">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="beca6-117">下圖顯示了在伺服器上執行垃圾回收的專用線程:</span><span class="sxs-lookup"><span data-stu-id="beca6-117">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![伺服器記憶體回收執行緒](./media/gc-server.png)

## <a name="performance-considerations"></a><span data-ttu-id="beca6-119">效能考量</span><span class="sxs-lookup"><span data-stu-id="beca6-119">Performance considerations</span></span>

### <a name="workstation-gc"></a><span data-ttu-id="beca6-120">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="beca6-120">Workstation GC</span></span>

<span data-ttu-id="beca6-121">以下是工作站記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="beca6-121">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="beca6-122">此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="beca6-122">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="beca6-123">因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="beca6-123">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="beca6-124">(運行本機代碼的線程不會在伺服器或工作站垃圾回收上掛起。</span><span class="sxs-lookup"><span data-stu-id="beca6-124">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="beca6-125">工作站垃圾資源的資源可以用於只有一個處理器的電腦,而不考慮[設定設定](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。</span><span class="sxs-lookup"><span data-stu-id="beca6-125">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

### <a name="server-gc"></a><span data-ttu-id="beca6-126">伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="beca6-126">Server GC</span></span>

<span data-ttu-id="beca6-127">以下是伺服器記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="beca6-127">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="beca6-128">此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。</span><span class="sxs-lookup"><span data-stu-id="beca6-128">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="beca6-129">執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。</span><span class="sxs-lookup"><span data-stu-id="beca6-129">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="beca6-130">每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="beca6-130">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="beca6-131">不同堆積上的物件可以彼此參考。</span><span class="sxs-lookup"><span data-stu-id="beca6-131">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="beca6-132">因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。</span><span class="sxs-lookup"><span data-stu-id="beca6-132">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="beca6-133">伺服器記憶體回收通常具有較大的區段。</span><span class="sxs-lookup"><span data-stu-id="beca6-133">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="beca6-134">但是,這隻是一個概括:段大小特定於實現,可能會發生變化。</span><span class="sxs-lookup"><span data-stu-id="beca6-134">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="beca6-135">調整應用時,不要對垃圾回收器分配的段大小進行假設。</span><span class="sxs-lookup"><span data-stu-id="beca6-135">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="beca6-136">伺服器記憶體回收可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="beca6-136">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="beca6-137">例如,假設有 12 個程序使用伺服器 GC 運行在具有四個處理器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="beca6-137">For example, imagine that there are 12 processes that use server GC running on a computer that has four processors.</span></span> <span data-ttu-id="beca6-138">如果所有進程都同時收集垃圾,它們就會相互干擾,因為同一處理器上將安排 12 個線程。</span><span class="sxs-lookup"><span data-stu-id="beca6-138">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="beca6-139">如果進程處於活動狀態,則讓所有進程都使用伺服器 GC 不是個好主意。</span><span class="sxs-lookup"><span data-stu-id="beca6-139">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="beca6-140">如果您正在運行應用程式的數百個實例,請考慮使用禁用併發垃圾回收的工作站垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="beca6-140">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="beca6-141">這樣會產生較少的內容切換，因此可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="beca6-141">This will result in less context switching, which can improve performance.</span></span>

## <a name="see-also"></a><span data-ttu-id="beca6-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beca6-142">See also</span></span>

- [<span data-ttu-id="beca6-143">後臺垃圾回收</span><span class="sxs-lookup"><span data-stu-id="beca6-143">Background garbage collection</span></span>](background-gc.md)
- [<span data-ttu-id="beca6-144">垃圾資源回收的執行時設定選項</span><span class="sxs-lookup"><span data-stu-id="beca6-144">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)
