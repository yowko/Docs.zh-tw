---
title: 背景垃圾收集
description: 瞭解 .NET 中的背景垃圾收集，以及它在工作站和伺服器垃圾收集中的差異。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: 780503288d3474cd99a595bdbd52c3a5abba5308
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990228"
---
# <a name="background-garbage-collection"></a><span data-ttu-id="8e984-103">背景垃圾收集</span><span class="sxs-lookup"><span data-stu-id="8e984-103">Background garbage collection</span></span>

<span data-ttu-id="8e984-104">在背景垃圾收集（GC）中，當層代2的集合正在進行時，會視需要收集暫時層代（0和1）。</span><span class="sxs-lookup"><span data-stu-id="8e984-104">In background garbage collection (GC), ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress.</span></span> <span data-ttu-id="8e984-105">背景垃圾收集會在一或多個專用線程上執行，視其為背景或伺服器 GC 而定，而且只適用于層代2回收。</span><span class="sxs-lookup"><span data-stu-id="8e984-105">Background garbage collection is performed on one or more dedicated threads, depending on whether it's background or server GC, and applies only to generation 2 collections.</span></span>

<span data-ttu-id="8e984-106">預設會啟用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-106">Background garbage collection is enabled by default.</span></span> <span data-ttu-id="8e984-107">您可以使用 .NET Framework apps 中的[gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)設定，或 .net Core 應用程式中的[system.object](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)設定來啟用或停用它。</span><span class="sxs-lookup"><span data-stu-id="8e984-107">It can be enabled or disabled with the [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.</span></span>

> [!NOTE]
> <span data-ttu-id="8e984-108">背景垃圾收集會取代[並行垃圾收集](#concurrent-garbage-collection)，並在 .NET Framework 4 和更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="8e984-108">Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions.</span></span> <span data-ttu-id="8e984-109">在 .NET Framework 4 中，只有*工作站*垃圾收集才支援此功能。</span><span class="sxs-lookup"><span data-stu-id="8e984-109">In .NET Framework 4, it's supported only for *workstation* garbage collection.</span></span> <span data-ttu-id="8e984-110">從 .NET Framework 4.5 開始，背景垃圾收集適用于*工作站*和*伺服器*垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-110">Starting with .NET Framework 4.5, background garbage collection is available for both *workstation* and *server* garbage collection.</span></span>

<span data-ttu-id="8e984-111">背景垃圾收集期間暫時層代的集合，稱為「*前景*垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="8e984-111">A collection on ephemeral generations during background garbage collection is known as *foreground* garbage collection.</span></span> <span data-ttu-id="8e984-112">進行前景記憶體回收時，所有 Managed 執行緒都會暫停。</span><span class="sxs-lookup"><span data-stu-id="8e984-112">When foreground garbage collections occur, all managed threads are suspended.</span></span>

<span data-ttu-id="8e984-113">當背景垃圾收集正在進行中，而且您已在層代0中配置足夠的物件時，CLR 會執行層代0或第1代的前景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-113">When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection.</span></span> <span data-ttu-id="8e984-114">專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。</span><span class="sxs-lookup"><span data-stu-id="8e984-114">The dedicated background garbage collection thread checks at frequent safe points to determine whether there is a request for foreground garbage collection.</span></span> <span data-ttu-id="8e984-115">如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。</span><span class="sxs-lookup"><span data-stu-id="8e984-115">If there is, the background collection suspends itself so that foreground garbage collection can occur.</span></span> <span data-ttu-id="8e984-116">前景垃圾收集完成之後，專用的背景垃圾收集執行緒和使用者執行緒就會繼續。</span><span class="sxs-lookup"><span data-stu-id="8e984-116">After the foreground garbage collection is completed, the dedicated background garbage collection threads and user threads resume.</span></span>

<span data-ttu-id="8e984-117">背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。</span><span class="sxs-lookup"><span data-stu-id="8e984-117">Background garbage collection removes allocation restrictions imposed by concurrent garbage collection, because ephemeral garbage collections can occur during background garbage collection.</span></span> <span data-ttu-id="8e984-118">背景垃圾收集可以移除暫時層代中的無作用物件。</span><span class="sxs-lookup"><span data-stu-id="8e984-118">Background garbage collection can remove dead objects in ephemeral generations.</span></span> <span data-ttu-id="8e984-119">它也可以在層代1垃圾收集期間視需要擴充堆積。</span><span class="sxs-lookup"><span data-stu-id="8e984-119">It can also expand the heap if needed during a generation 1 garbage collection.</span></span>

## <a name="background-workstation-vs-server-gc"></a><span data-ttu-id="8e984-120">背景工作站與伺服器 GC 的比較</span><span class="sxs-lookup"><span data-stu-id="8e984-120">Background workstation vs. server GC</span></span>

<span data-ttu-id="8e984-121">從 .NET Framework 4.5 開始，會提供伺服器 GC 的背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-121">Starting with .NET Framework 4.5, background garbage collection is available for server GC.</span></span> <span data-ttu-id="8e984-122">背景 GC 是伺服器垃圾收集的預設模式。</span><span class="sxs-lookup"><span data-stu-id="8e984-122">Background GC is the default mode for server garbage collection.</span></span>

<span data-ttu-id="8e984-123">背景伺服器垃圾收集的功能類似于背景工作站垃圾收集，但有一些差異：</span><span class="sxs-lookup"><span data-stu-id="8e984-123">Background server garbage collection functions similarly to background workstation garbage collection, but there are a few differences:</span></span>

- <span data-ttu-id="8e984-124">背景工作站垃圾收集使用一個專用的背景垃圾收集執行緒，而背景伺服器垃圾收集則使用多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e984-124">Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads.</span></span> <span data-ttu-id="8e984-125">一般來說，每個邏輯處理器都有專用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e984-125">Typically, there's a dedicated thread for each logical processor.</span></span>

- <span data-ttu-id="8e984-126">不同于工作站背景垃圾收集執行緒，背景伺服器 GC 執行緒不會超時。</span><span class="sxs-lookup"><span data-stu-id="8e984-126">Unlike the workstation background garbage collection thread, the background server GC threads do not time out.</span></span>

<span data-ttu-id="8e984-127">下圖顯示在另一個專用線程上執行的背景*工作站*垃圾收集：</span><span class="sxs-lookup"><span data-stu-id="8e984-127">The following illustration shows background *workstation* garbage collection performed on a separate, dedicated thread:</span></span>

![背景工作站記憶體回收](media/fundamentals/background-workstation-garbage-collection.png)

<span data-ttu-id="8e984-129">下圖顯示在不同的專用線程上執行的背景*伺服器*垃圾收集：</span><span class="sxs-lookup"><span data-stu-id="8e984-129">The following illustration shows background *server* garbage collection performed on separate, dedicated threads:</span></span>

![背景伺服器記憶體回收](media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a><span data-ttu-id="8e984-131">並行的記憶體回收</span><span class="sxs-lookup"><span data-stu-id="8e984-131">Concurrent garbage collection</span></span>

> [!TIP]
> <span data-ttu-id="8e984-132">本節適用於：</span><span class="sxs-lookup"><span data-stu-id="8e984-132">This section applies to:</span></span>
>
> - <span data-ttu-id="8e984-133">適用于工作站垃圾收集的 .NET Framework 3.5 和更早版本</span><span class="sxs-lookup"><span data-stu-id="8e984-133">.NET Framework 3.5 and earlier for workstation garbage collection</span></span>
> - <span data-ttu-id="8e984-134">.NET Framework 4 和更早版本進行伺服器垃圾收集</span><span class="sxs-lookup"><span data-stu-id="8e984-134">.NET Framework 4 and earlier for server garbage collection</span></span>
>
> <span data-ttu-id="8e984-135">在較新版本中，會以背景垃圾收集取代並行的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-135">Concurrent garbage is replaced by background garbage collection in later versions.</span></span>

<span data-ttu-id="8e984-136">在 [工作站] 或 [伺服器垃圾收集] 中，您可以[啟用並行垃圾收集](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)，讓執行緒可以與在集合大部分持續時間內執行垃圾收集的專用線程並存執行。</span><span class="sxs-lookup"><span data-stu-id="8e984-136">In workstation or server garbage collection, you can [enable concurrent garbage collection](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection.</span></span> <span data-ttu-id="8e984-137">此選項只會影響層代2中的垃圾收集;層代0和1一律為非並行，因為它們會快速完成。</span><span class="sxs-lookup"><span data-stu-id="8e984-137">This option affects only garbage collections in generation 2; generations 0 and 1 are always non-concurrent because they finish fast.</span></span>

<span data-ttu-id="8e984-138">並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。</span><span class="sxs-lookup"><span data-stu-id="8e984-138">Concurrent garbage collection enables interactive applications to be more responsive by minimizing pauses for a collection.</span></span> <span data-ttu-id="8e984-139">當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="8e984-139">Managed threads can continue to run most of the time while the concurrent garbage collection thread is running.</span></span> <span data-ttu-id="8e984-140">這項設計會導致在發生垃圾收集時暫停的時間較短。</span><span class="sxs-lookup"><span data-stu-id="8e984-140">This design results in shorter pauses while a garbage collection is occurring.</span></span>

<span data-ttu-id="8e984-141">並行記憶體回收會針對專屬執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="8e984-141">Concurrent garbage collection is performed on a dedicated thread.</span></span> <span data-ttu-id="8e984-142">根據預設，CLR 會執行工作站垃圾收集，同時在單處理器和多處理器電腦上啟用並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="8e984-142">By default, the CLR runs workstation garbage collection with concurrent garbage collection enabled on both single-processor and multi-processor computers.</span></span>

<span data-ttu-id="8e984-143">下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="8e984-143">The following illustration shows concurrent garbage collection performed on a separate dedicated thread.</span></span>

![並行記憶體回收執行緒](media/gc-concurrent.png)

## <a name="see-also"></a><span data-ttu-id="8e984-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e984-145">See also</span></span>

- [<span data-ttu-id="8e984-146">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="8e984-146">Workstation and server garbage collection</span></span>](workstation-server-gc.md)
- [<span data-ttu-id="8e984-147">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="8e984-147">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)
