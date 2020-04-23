---
title: .NET 垃圾回收
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
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102238"
---
# <a name="garbage-collection"></a><span data-ttu-id="25d6c-102">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="25d6c-102">Garbage collection</span></span>

<span data-ttu-id="25d6c-103">.NET 的記憶體回收行程可管理應用程式的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="25d6c-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="25d6c-104">每次當您建立新的物件時，通用語言執行平台會從 Managed 堆積配置物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="25d6c-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="25d6c-105">只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。</span><span class="sxs-lookup"><span data-stu-id="25d6c-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="25d6c-106">不過，記憶體不是無限的。</span><span class="sxs-lookup"><span data-stu-id="25d6c-106">However, memory is not infinite.</span></span> <span data-ttu-id="25d6c-107">因此記憶體回收行程最後就必須執行回收以釋放一些記憶體。</span><span class="sxs-lookup"><span data-stu-id="25d6c-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="25d6c-108">記憶體回收行程的最佳化引擎會根據所做的配置，決定執行回收的最佳時機。</span><span class="sxs-lookup"><span data-stu-id="25d6c-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="25d6c-109">當記憶體回收行程執行回收時，會檢查 Managed 堆積中是否有應用程式不再使用的物件，並執行必要的作業以回收其記憶體。</span><span class="sxs-lookup"><span data-stu-id="25d6c-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25d6c-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="25d6c-110">In this section</span></span>
  
|<span data-ttu-id="25d6c-111">Title</span><span class="sxs-lookup"><span data-stu-id="25d6c-111">Title</span></span>|<span data-ttu-id="25d6c-112">描述</span><span class="sxs-lookup"><span data-stu-id="25d6c-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="25d6c-113">垃圾回收的基礎知識</span><span class="sxs-lookup"><span data-stu-id="25d6c-113">Fundamentals of garbage collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="25d6c-114">描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。</span><span class="sxs-lookup"><span data-stu-id="25d6c-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="25d6c-115">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="25d6c-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="25d6c-116">描述用戶端應用的工作站垃圾回收與伺服器應用的伺服器垃圾回收之間的差異。</span><span class="sxs-lookup"><span data-stu-id="25d6c-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="25d6c-117">後臺垃圾回收</span><span class="sxs-lookup"><span data-stu-id="25d6c-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="25d6c-118">描述後台垃圾回收,這是在第 2 代回收進行期間收集第 0 代和 1 個物件。</span><span class="sxs-lookup"><span data-stu-id="25d6c-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="25d6c-119">大型物件堆</span><span class="sxs-lookup"><span data-stu-id="25d6c-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="25d6c-120">描述大型物件堆 (LOH) 以及垃圾回收大型物件的方式。</span><span class="sxs-lookup"><span data-stu-id="25d6c-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="25d6c-121">記憶體回收和效能</span><span class="sxs-lookup"><span data-stu-id="25d6c-121">Garbage collection and performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="25d6c-122">描述可用來診斷記憶體回收和效能問題的效能檢查。</span><span class="sxs-lookup"><span data-stu-id="25d6c-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="25d6c-123">引發的回收</span><span class="sxs-lookup"><span data-stu-id="25d6c-123">Induced collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="25d6c-124">描述如何進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="25d6c-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="25d6c-125">延遲模式</span><span class="sxs-lookup"><span data-stu-id="25d6c-125">Latency modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="25d6c-126">描述判斷記憶體回收干擾程度的模式。</span><span class="sxs-lookup"><span data-stu-id="25d6c-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="25d6c-127">共用 Web 裝載的最佳化</span><span class="sxs-lookup"><span data-stu-id="25d6c-127">Optimization for shared web hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="25d6c-128">描述如何最佳化伺服器上由數個小型網站所共用的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="25d6c-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="25d6c-129">記憶體回收通知</span><span class="sxs-lookup"><span data-stu-id="25d6c-129">Garbage collection notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="25d6c-130">描述如何判斷何時接近完整的記憶體回收，以及何時已完成。</span><span class="sxs-lookup"><span data-stu-id="25d6c-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="25d6c-131">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="25d6c-131">Application domain resource monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="25d6c-132">描述如何監視應用程式定義域的 CPU 和記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="25d6c-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="25d6c-133">弱式參考</span><span class="sxs-lookup"><span data-stu-id="25d6c-133">Weak references</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="25d6c-134">描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。</span><span class="sxs-lookup"><span data-stu-id="25d6c-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="25d6c-135">參考</span><span class="sxs-lookup"><span data-stu-id="25d6c-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="25d6c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25d6c-136">See also</span></span>

- [<span data-ttu-id="25d6c-137">清除非受控資源</span><span class="sxs-lookup"><span data-stu-id="25d6c-137">Clean up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
