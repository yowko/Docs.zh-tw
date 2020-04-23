---
title: 後臺垃圾回收
description: 瞭解 .NET 中的後台垃圾回收,以及它在工作站和伺服器垃圾回收中有何不同。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103559"
---
# <a name="background-garbage-collection"></a><span data-ttu-id="ff486-103">後臺垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ff486-103">Background garbage collection</span></span>

<span data-ttu-id="ff486-104">在後台垃圾回收 (GC) 中,臨時代 (0 和 1) 根據需要收集,而第 2 代的收集正在進行中。</span><span class="sxs-lookup"><span data-stu-id="ff486-104">In background garbage collection (GC), ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress.</span></span> <span data-ttu-id="ff486-105">後台垃圾回收在一個或多個專用線程上執行,具體取決於它是後台還是伺服器 GC,並且僅適用於第 2 代集合。</span><span class="sxs-lookup"><span data-stu-id="ff486-105">Background garbage collection is performed on one or more dedicated threads, depending on whether it's background or server GC, and applies only to generation 2 collections.</span></span>

<span data-ttu-id="ff486-106">默認情況下啟用後台垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-106">Background garbage collection is enabled by default.</span></span> <span data-ttu-id="ff486-107">可以使用 .NET Framework 應用中的[gc併發](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)配置設置或 .NET Core 應用中[的 System.GC.併發](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)設定啟用或禁用它。</span><span class="sxs-lookup"><span data-stu-id="ff486-107">It can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.</span></span>

> [!NOTE]
> <span data-ttu-id="ff486-108">後臺垃圾回收將替換[併發垃圾回收](#concurrent-garbage-collection),並在 .NET 框架 4 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="ff486-108">Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions.</span></span> <span data-ttu-id="ff486-109">在 .NET 框架 4 中,它僅支援*工作站*垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-109">In .NET Framework 4, it's supported only for *workstation* garbage collection.</span></span> <span data-ttu-id="ff486-110">從 .NET 框架 4.5 開始,後臺垃圾回收可用於*工作站*和*伺服器*垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-110">Starting with .NET Framework 4.5, background garbage collection is available for both *workstation* and *server* garbage collection.</span></span>

<span data-ttu-id="ff486-111">在後台垃圾回收期間對臨時代的收集稱為*前景*垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-111">A collection on ephemeral generations during background garbage collection is known as *foreground* garbage collection.</span></span> <span data-ttu-id="ff486-112">進行前景記憶體回收時，所有 Managed 執行緒都會暫停。</span><span class="sxs-lookup"><span data-stu-id="ff486-112">When foreground garbage collections occur, all managed threads are suspended.</span></span>

<span data-ttu-id="ff486-113">當後台垃圾回收正在進行,並且您在第 0 代中分配了足夠的物件時,CLR 將執行第 0 代或第 1 代前臺垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-113">When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection.</span></span> <span data-ttu-id="ff486-114">專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。</span><span class="sxs-lookup"><span data-stu-id="ff486-114">The dedicated background garbage collection thread checks at frequent safe points to determine whether there is a request for foreground garbage collection.</span></span> <span data-ttu-id="ff486-115">如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。</span><span class="sxs-lookup"><span data-stu-id="ff486-115">If there is, the background collection suspends itself so that foreground garbage collection can occur.</span></span> <span data-ttu-id="ff486-116">前臺垃圾回收完成後,將恢復專用後台垃圾回收線程和用戶線程。</span><span class="sxs-lookup"><span data-stu-id="ff486-116">After the foreground garbage collection is completed, the dedicated background garbage collection threads and user threads resume.</span></span>

<span data-ttu-id="ff486-117">背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。</span><span class="sxs-lookup"><span data-stu-id="ff486-117">Background garbage collection removes allocation restrictions imposed by concurrent garbage collection, because ephemeral garbage collections can occur during background garbage collection.</span></span> <span data-ttu-id="ff486-118">後台垃圾回收可以刪除臨時代中的死物件。</span><span class="sxs-lookup"><span data-stu-id="ff486-118">Background garbage collection can remove dead objects in ephemeral generations.</span></span> <span data-ttu-id="ff486-119">如果需要,它還可以在第 1 代垃圾回收期間展開堆。</span><span class="sxs-lookup"><span data-stu-id="ff486-119">It can also expand the heap if needed during a generation 1 garbage collection.</span></span>

## <a name="background-workstation-vs-server-gc"></a><span data-ttu-id="ff486-120">背景工作站與伺服器 GC</span><span class="sxs-lookup"><span data-stu-id="ff486-120">Background workstation vs. server GC</span></span>

<span data-ttu-id="ff486-121">從 .NET 框架 4.5 開始,後台垃圾回收可用於伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="ff486-121">Starting with .NET Framework 4.5, background garbage collection is available for server GC.</span></span> <span data-ttu-id="ff486-122">後台 GC 是伺服器垃圾回收的預設模式。</span><span class="sxs-lookup"><span data-stu-id="ff486-122">Background GC is the default mode for server garbage collection.</span></span>

<span data-ttu-id="ff486-123">後台伺服器垃圾回收功能與後台工作站垃圾回收類似,但有一些區別:</span><span class="sxs-lookup"><span data-stu-id="ff486-123">Background server garbage collection functions similarly to background workstation garbage collection, but there are a few differences:</span></span>

- <span data-ttu-id="ff486-124">後台工作站垃圾回收使用一個專用後台垃圾回收線程,而後台伺服器垃圾回收使用多個線程。</span><span class="sxs-lookup"><span data-stu-id="ff486-124">Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads.</span></span> <span data-ttu-id="ff486-125">通常,每個邏輯處理器都有一個專用線程。</span><span class="sxs-lookup"><span data-stu-id="ff486-125">Typically, there's a dedicated thread for each logical processor.</span></span>

- <span data-ttu-id="ff486-126">與工作站後台垃圾回收線程不同,後台伺服器 GC 線程不會超時。</span><span class="sxs-lookup"><span data-stu-id="ff486-126">Unlike the workstation background garbage collection thread, the background server GC threads do not time out.</span></span>

<span data-ttu-id="ff486-127">下圖顯示了在單獨的專用線程上執行的背景*工作站*垃圾回收:</span><span class="sxs-lookup"><span data-stu-id="ff486-127">The following illustration shows background *workstation* garbage collection performed on a separate, dedicated thread:</span></span>

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

<span data-ttu-id="ff486-129">下圖顯示了在單獨的專用線程上執行的背景*伺服器*垃圾回收:</span><span class="sxs-lookup"><span data-stu-id="ff486-129">The following illustration shows background *server* garbage collection performed on separate, dedicated threads:</span></span>

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a><span data-ttu-id="ff486-131">並行的記憶體回收</span><span class="sxs-lookup"><span data-stu-id="ff486-131">Concurrent garbage collection</span></span>

> [!TIP]
> <span data-ttu-id="ff486-132">本節適用於：</span><span class="sxs-lookup"><span data-stu-id="ff486-132">This section applies to:</span></span>
>
> - <span data-ttu-id="ff486-133">.NET 框架 3.5 及更早版本用於工作站垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ff486-133">.NET Framework 3.5 and earlier for workstation garbage collection</span></span>
> - <span data-ttu-id="ff486-134">.NET 框架 4 及更早版本用於伺服器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ff486-134">.NET Framework 4 and earlier for server garbage collection</span></span>
>
> <span data-ttu-id="ff486-135">並行垃圾在更高版本中被後台垃圾回收替換。</span><span class="sxs-lookup"><span data-stu-id="ff486-135">Concurrent garbage is replaced by background garbage collection in later versions.</span></span>

<span data-ttu-id="ff486-136">在工作站或伺服器垃圾回收中,可以[啟用併發垃圾回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md),使線程與在收集的大部分持續時間內執行垃圾回收的專用線程同時運行。</span><span class="sxs-lookup"><span data-stu-id="ff486-136">In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection.</span></span> <span data-ttu-id="ff486-137">此選項僅影響第 2 代中的垃圾回收;因此,此選項僅影響第 2 代中的垃圾回收。第 0 代和 1 始終是非併發的,因為它們完成得快。</span><span class="sxs-lookup"><span data-stu-id="ff486-137">This option affects only garbage collections in generation 2; generations 0 and 1 are always non-concurrent because they finish fast.</span></span>

<span data-ttu-id="ff486-138">並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。</span><span class="sxs-lookup"><span data-stu-id="ff486-138">Concurrent garbage collection enables interactive applications to be more responsive by minimizing pauses for a collection.</span></span> <span data-ttu-id="ff486-139">當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="ff486-139">Managed threads can continue to run most of the time while the concurrent garbage collection thread is running.</span></span> <span data-ttu-id="ff486-140">這會在記憶體回收進行時縮短暫停時間。</span><span class="sxs-lookup"><span data-stu-id="ff486-140">This results in shorter pauses while a garbage collection is occurring.</span></span>

<span data-ttu-id="ff486-141">並行記憶體回收會針對專屬執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="ff486-141">Concurrent garbage collection is performed on a dedicated thread.</span></span> <span data-ttu-id="ff486-142">默認情況下,CLR 運行工作站垃圾回收,並在單處理器和多處理器計算機上啟用併發垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-142">By default, the CLR runs workstation garbage collection with concurrent garbage collection enabled on both single-processor and multi-processor computers.</span></span>

<span data-ttu-id="ff486-143">下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="ff486-143">The following illustration shows concurrent garbage collection performed on a separate dedicated thread.</span></span>

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a><span data-ttu-id="ff486-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff486-145">See also</span></span>

- [<span data-ttu-id="ff486-146">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="ff486-146">Workstation and server garbage collection</span></span>](workstation-server-gc.md)
- [<span data-ttu-id="ff486-147">垃圾資源回收的執行時設定選項</span><span class="sxs-lookup"><span data-stu-id="ff486-147">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)
