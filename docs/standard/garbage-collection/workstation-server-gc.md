---
title: 工作站與伺服器垃圾收集（GC）的比較
description: 瞭解 .NET 中的工作站和伺服器垃圾收集。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 5ff2b1fe2f997913e071f35ec5abb167ed757608
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306691"
---
# <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="ae2fe-103">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="ae2fe-103">Workstation and server garbage collection</span></span>

<span data-ttu-id="ae2fe-104">記憶體回收行程會自行調整而且可在各種案例中運作。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-104">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="ae2fe-105">不過，您可以根據工作負載的特性來[設定垃圾收集的類型](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-105">However, you can [set the type of garbage collection](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) based on the characteristics of the workload.</span></span> <span data-ttu-id="ae2fe-106">CLR 會提供下列記憶體回收類型：</span><span class="sxs-lookup"><span data-stu-id="ae2fe-106">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="ae2fe-107">工作站垃圾收集（GC），專為用戶端應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-107">Workstation garbage collection (GC), which is designed for client apps.</span></span> <span data-ttu-id="ae2fe-108">這是獨立應用程式的預設 GC 類別。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-108">It's the default GC flavor for standalone apps.</span></span> <span data-ttu-id="ae2fe-109">例如，針對裝載的應用程式（由 ASP.NET 所主控），主機會決定預設的 GC 類別。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-109">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="ae2fe-110">工作站記憶體回收可能是並行或非並行的。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-110">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="ae2fe-111">同時（或*背景*）垃圾收集可讓受控執行緒在垃圾收集期間繼續作業。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-111">Concurrent (or *background*) garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="ae2fe-112">[背景垃圾收集](background-gc.md)會取代 .NET Framework 4 和更新版本中的[並行垃圾收集](background-gc.md#concurrent-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-112">[Background garbage collection](background-gc.md) replaces [concurrent garbage collection](background-gc.md#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="ae2fe-113">伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-113">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="ae2fe-114">在 .NET Core 中，伺服器垃圾收集可以是非並行或背景。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-114">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="ae2fe-115">在 .NET Framework 4.5 和更新版本中，伺服器垃圾收集可以是非並行或背景。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-115">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background.</span></span> <span data-ttu-id="ae2fe-116">在 .NET Framework 4 和舊版中，伺服器垃圾收集為非並行的。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-116">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="ae2fe-117">下圖顯示在伺服器上執行垃圾收集的專用線程：</span><span class="sxs-lookup"><span data-stu-id="ae2fe-117">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![伺服器記憶體回收執行緒](media/gc-server.png)

## <a name="performance-considerations"></a><span data-ttu-id="ae2fe-119">效能考量</span><span class="sxs-lookup"><span data-stu-id="ae2fe-119">Performance considerations</span></span>

### <a name="workstation-gc"></a><span data-ttu-id="ae2fe-120">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="ae2fe-120">Workstation GC</span></span>

<span data-ttu-id="ae2fe-121">以下是工作站記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="ae2fe-121">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="ae2fe-122">此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-122">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="ae2fe-123">因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-123">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="ae2fe-124">（執行機器碼的執行緒在伺服器或工作站垃圾收集上不會暫停）。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-124">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="ae2fe-125">工作站垃圾收集一律會在只有一個處理器的電腦上使用，不論[設定](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)為何。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-125">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

### <a name="server-gc"></a><span data-ttu-id="ae2fe-126">伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="ae2fe-126">Server GC</span></span>

<span data-ttu-id="ae2fe-127">以下是伺服器記憶體回收的執行緒和效能考量：</span><span class="sxs-lookup"><span data-stu-id="ae2fe-127">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="ae2fe-128">此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-128">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="ae2fe-129">執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-129">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="ae2fe-130">每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-130">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="ae2fe-131">不同堆積上的物件可以彼此參考。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-131">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="ae2fe-132">因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-132">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="ae2fe-133">伺服器記憶體回收通常具有較大的區段。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-133">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="ae2fe-134">不過，這只是一般化：區段大小是特定執行，而且可能會變更。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-134">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="ae2fe-135">請不要在調整應用程式時，假設垃圾收集行程所配置的區段大小。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-135">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="ae2fe-136">伺服器記憶體回收可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-136">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="ae2fe-137">例如，假設有12個處理常式在具有四個處理器的電腦上執行伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-137">For example, imagine that there are 12 processes that use server GC running on a computer that has four processors.</span></span> <span data-ttu-id="ae2fe-138">如果所有處理常式都是同時收集垃圾，它們會互相干擾，因為同一個處理器上有12個執行緒排程。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-138">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="ae2fe-139">如果處理常式是作用中的，最好不要讓它們全部使用伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-139">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="ae2fe-140">如果您執行的是數百個應用程式實例，請考慮使用已停用並行垃圾收集的工作站垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-140">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="ae2fe-141">這樣會產生較少的內容切換，因此可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="ae2fe-141">This will result in less context switching, which can improve performance.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae2fe-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2fe-142">See also</span></span>

- [<span data-ttu-id="ae2fe-143">背景垃圾收集</span><span class="sxs-lookup"><span data-stu-id="ae2fe-143">Background garbage collection</span></span>](background-gc.md)
- [<span data-ttu-id="ae2fe-144">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="ae2fe-144">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)
