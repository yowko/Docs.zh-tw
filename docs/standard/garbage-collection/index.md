---
title: "記憶體回收"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "36"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c8288473b25b3f3cd75666e1da0611dec37c3127
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="garbage-collection"></a><span data-ttu-id="5c944-102">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="5c944-102">Garbage Collection</span></span>
<span data-ttu-id="5c944-103">.NET 的記憶體回收行程可管理應用程式的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="5c944-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="5c944-104">每次當您建立新的物件時，通用語言執行平台會從 Managed 堆積配置物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c944-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="5c944-105">只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。</span><span class="sxs-lookup"><span data-stu-id="5c944-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="5c944-106">不過，記憶體不是無限的。</span><span class="sxs-lookup"><span data-stu-id="5c944-106">However, memory is not infinite.</span></span> <span data-ttu-id="5c944-107">因此記憶體回收行程最後就必須執行回收以釋放一些記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c944-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="5c944-108">記憶體回收行程的最佳化引擎會根據所做的配置，決定執行回收的最佳時機。</span><span class="sxs-lookup"><span data-stu-id="5c944-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="5c944-109">當記憶體回收行程執行回收時，會檢查 Managed 堆積中是否有應用程式不再使用的物件，並執行必要的作業以回收其記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c944-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="5c944-110">相關主題</span><span class="sxs-lookup"><span data-stu-id="5c944-110">Related Topics</span></span>  
  
|<span data-ttu-id="5c944-111">標題</span><span class="sxs-lookup"><span data-stu-id="5c944-111">Title</span></span>|<span data-ttu-id="5c944-112">描述</span><span class="sxs-lookup"><span data-stu-id="5c944-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c944-113">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="5c944-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="5c944-114">描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。</span><span class="sxs-lookup"><span data-stu-id="5c944-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="5c944-115">記憶體回收和效能</span><span class="sxs-lookup"><span data-stu-id="5c944-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="5c944-116">描述可用來診斷記憶體回收和效能問題的效能檢查。</span><span class="sxs-lookup"><span data-stu-id="5c944-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="5c944-117">引發的收集</span><span class="sxs-lookup"><span data-stu-id="5c944-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="5c944-118">描述如何進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="5c944-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="5c944-119">延遲模式</span><span class="sxs-lookup"><span data-stu-id="5c944-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="5c944-120">描述判斷記憶體回收干擾程度的模式。</span><span class="sxs-lookup"><span data-stu-id="5c944-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="5c944-121">共用 Web 裝載的最佳化</span><span class="sxs-lookup"><span data-stu-id="5c944-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="5c944-122">描述如何最佳化伺服器上由數個小型網站所共用的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="5c944-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="5c944-123">記憶體回收通知</span><span class="sxs-lookup"><span data-stu-id="5c944-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="5c944-124">描述如何判斷何時接近完整的記憶體回收，以及何時已完成。</span><span class="sxs-lookup"><span data-stu-id="5c944-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="5c944-125">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="5c944-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="5c944-126">描述如何監視應用程式定義域的 CPU 和記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="5c944-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="5c944-127">弱式參考</span><span class="sxs-lookup"><span data-stu-id="5c944-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="5c944-128">描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。</span><span class="sxs-lookup"><span data-stu-id="5c944-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="5c944-129">參考資料</span><span class="sxs-lookup"><span data-stu-id="5c944-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="5c944-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c944-130">See Also</span></span>  
 [<span data-ttu-id="5c944-131">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="5c944-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
