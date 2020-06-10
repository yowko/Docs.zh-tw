---
title: .NET 垃圾收集
description: 瞭解 .NET 中的垃圾收集。 .NET 垃圾收集行程會管理應用程式的記憶體配置和釋放。
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662481"
---
# <a name="garbage-collection"></a><span data-ttu-id="0b45d-104">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="0b45d-104">Garbage collection</span></span>

<span data-ttu-id="0b45d-105">.NET 的記憶體回收行程可管理應用程式的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="0b45d-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="0b45d-106">每次當您建立新的物件時，通用語言執行平台會從 Managed 堆積配置物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b45d-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="0b45d-107">只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。</span><span class="sxs-lookup"><span data-stu-id="0b45d-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="0b45d-108">不過，記憶體不是無限的。</span><span class="sxs-lookup"><span data-stu-id="0b45d-108">However, memory is not infinite.</span></span> <span data-ttu-id="0b45d-109">因此記憶體回收行程最後就必須執行回收以釋放一些記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b45d-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="0b45d-110">記憶體回收行程的最佳化引擎會根據所做的配置，決定執行回收的最佳時機。</span><span class="sxs-lookup"><span data-stu-id="0b45d-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="0b45d-111">當記憶體回收行程執行回收時，會檢查 Managed 堆積中是否有應用程式不再使用的物件，並執行必要的作業以回收其記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b45d-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b45d-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="0b45d-112">In this section</span></span>
  
|<span data-ttu-id="0b45d-113">Title</span><span class="sxs-lookup"><span data-stu-id="0b45d-113">Title</span></span>|<span data-ttu-id="0b45d-114">描述</span><span class="sxs-lookup"><span data-stu-id="0b45d-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0b45d-115">垃圾收集的基本概念</span><span class="sxs-lookup"><span data-stu-id="0b45d-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="0b45d-116">描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。</span><span class="sxs-lookup"><span data-stu-id="0b45d-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="0b45d-117">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="0b45d-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="0b45d-118">說明用戶端應用程式的工作站垃圾收集與伺服器應用程式的伺服器垃圾收集之間的差異。</span><span class="sxs-lookup"><span data-stu-id="0b45d-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="0b45d-119">背景垃圾收集</span><span class="sxs-lookup"><span data-stu-id="0b45d-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="0b45d-120">描述背景垃圾收集，這是層代0和1物件的集合，而層代2回收正在進行中。</span><span class="sxs-lookup"><span data-stu-id="0b45d-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="0b45d-121">大型物件堆積</span><span class="sxs-lookup"><span data-stu-id="0b45d-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="0b45d-122">描述大型物件堆積（LOH），以及如何將大型物件進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="0b45d-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="0b45d-123">記憶體回收和效能</span><span class="sxs-lookup"><span data-stu-id="0b45d-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="0b45d-124">描述可用來診斷記憶體回收和效能問題的效能檢查。</span><span class="sxs-lookup"><span data-stu-id="0b45d-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="0b45d-125">引發的回收</span><span class="sxs-lookup"><span data-stu-id="0b45d-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="0b45d-126">描述如何進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0b45d-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="0b45d-127">延遲模式</span><span class="sxs-lookup"><span data-stu-id="0b45d-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="0b45d-128">描述判斷記憶體回收干擾程度的模式。</span><span class="sxs-lookup"><span data-stu-id="0b45d-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="0b45d-129">共用 Web 裝載的最佳化</span><span class="sxs-lookup"><span data-stu-id="0b45d-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="0b45d-130">描述如何最佳化伺服器上由數個小型網站所共用的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0b45d-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="0b45d-131">記憶體回收通知</span><span class="sxs-lookup"><span data-stu-id="0b45d-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="0b45d-132">描述如何判斷何時接近完整的記憶體回收，以及何時已完成。</span><span class="sxs-lookup"><span data-stu-id="0b45d-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="0b45d-133">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="0b45d-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="0b45d-134">描述如何監視應用程式定義域的 CPU 和記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="0b45d-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="0b45d-135">弱式參考</span><span class="sxs-lookup"><span data-stu-id="0b45d-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="0b45d-136">描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。</span><span class="sxs-lookup"><span data-stu-id="0b45d-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="0b45d-137">參考</span><span class="sxs-lookup"><span data-stu-id="0b45d-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="0b45d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b45d-138">See also</span></span>

- [<span data-ttu-id="0b45d-139">清除非受控資源</span><span class="sxs-lookup"><span data-stu-id="0b45d-139">Clean up unmanaged resources</span></span>](unmanaged.md)
