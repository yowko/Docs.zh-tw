---
title: 延遲模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283599"
---
# <a name="latency-modes"></a><span data-ttu-id="a9b8b-102">延遲模式</span><span class="sxs-lookup"><span data-stu-id="a9b8b-102">Latency modes</span></span>

<span data-ttu-id="a9b8b-103">要回收物件，垃圾回收器 （GC） 必須停止應用程式中的所有執行執行緒。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-103">To reclaim objects, the garbage collector (GC) must stop all the executing threads in an application.</span></span> <span data-ttu-id="a9b8b-104">垃圾回收器處於活動狀態的時間段稱為其*延遲*。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-104">The period of time during which the garbage collector is active is referred to as its *latency*.</span></span>

<span data-ttu-id="a9b8b-105">在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-105">In some situations, such as when an application retrieves data or displays content, a full garbage collection can occur at a critical time and impede performance.</span></span> <span data-ttu-id="a9b8b-106">您可以藉由設定 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值的其中一個，來調整記憶體回收行程的干擾程度。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-106">You can adjust the intrusiveness of the garbage collector by setting the <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> property to one of the <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> values.</span></span>

## <a name="low-latency-settings"></a><span data-ttu-id="a9b8b-107">低延遲設置</span><span class="sxs-lookup"><span data-stu-id="a9b8b-107">Low latency settings</span></span>

<span data-ttu-id="a9b8b-108">使用"低"延遲設置意味著垃圾回收器在應用程式中侵入較少。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-108">Using a "low" latency setting means the garbage collector intrudes less in your application.</span></span> <span data-ttu-id="a9b8b-109">垃圾回收對回收記憶體更加保守。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-109">Garbage collection is more conservative about reclaiming memory.</span></span>

<span data-ttu-id="a9b8b-110"><xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列舉會提供兩個低延遲設定：</span><span class="sxs-lookup"><span data-stu-id="a9b8b-110">The <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> enumeration provides two low latency settings:</span></span>

- <span data-ttu-id="a9b8b-111">[GC延遲模式.低延遲](xref:System.Runtime.GCLatencyMode.LowLatency)禁止第 2 代集合，並且僅執行第 0 代和第 1 代集合。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-111">[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) suppresses generation 2 collections and performs only generation 0 and 1 collections.</span></span> <span data-ttu-id="a9b8b-112">它只適合短時間使用。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-112">It can be used only for short periods of time.</span></span> <span data-ttu-id="a9b8b-113">經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-113">Over longer periods, if the system is under memory pressure, the garbage collector will trigger a collection, which can briefly pause the application and disrupt a time-critical operation.</span></span> <span data-ttu-id="a9b8b-114">這項設定僅適用於工作站記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-114">This setting is available only for workstation garbage collection.</span></span>

- <span data-ttu-id="a9b8b-115">[GC延遲模式.持續低延遲](xref:System.Runtime.GCLatencyMode.SustainedLowLatency)抑制前景第 2 代集合，僅執行第 0 代、1 和後臺第 2 代集合。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-115">[GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) suppresses foreground generation 2 collections and performs only generation 0, 1, and background generation 2 collections.</span></span> <span data-ttu-id="a9b8b-116">它可以長時間使用，並且可用於工作站和伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-116">It can be used for longer periods of time, and is available for both workstation and server garbage collection.</span></span> <span data-ttu-id="a9b8b-117">如果禁用後臺垃圾回收，則無法使用此設置。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-117">This setting cannot be used if background garbage collection is disabled.</span></span>

<span data-ttu-id="a9b8b-118">在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="a9b8b-118">During low latency periods, generation 2 collections are suppressed unless the following occurs:</span></span>

- <span data-ttu-id="a9b8b-119">系統從作業系統接收到記憶體不足的通知。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-119">The system receives a low memory notification from the operating system.</span></span>

- <span data-ttu-id="a9b8b-120">應用程式代碼通過調用<xref:System.GC.Collect%2A?displayProperty=nameWithType>方法並為`generation`參數指定 2 來誘導集合。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-120">Application code induces a collection by calling the <xref:System.GC.Collect%2A?displayProperty=nameWithType> method and specifying 2 for the `generation` parameter.</span></span>

## <a name="scenarios"></a><span data-ttu-id="a9b8b-121">案例</span><span class="sxs-lookup"><span data-stu-id="a9b8b-121">Scenarios</span></span>

<span data-ttu-id="a9b8b-122">下表列出了用於使用<xref:System.Runtime.GCLatencyMode>這些值的應用程式方案：</span><span class="sxs-lookup"><span data-stu-id="a9b8b-122">The following table lists the application scenarios for using the <xref:System.Runtime.GCLatencyMode> values:</span></span>

|<span data-ttu-id="a9b8b-123">延遲模式</span><span class="sxs-lookup"><span data-stu-id="a9b8b-123">Latency mode</span></span>|<span data-ttu-id="a9b8b-124">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="a9b8b-124">Application scenarios</span></span>|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|<span data-ttu-id="a9b8b-125">對於沒有使用者介面 （UI） 或伺服器端操作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-125">For applications that have no user interface (UI) or server-side operations.</span></span><br /><br /><span data-ttu-id="a9b8b-126">禁用後臺垃圾回收後，這是工作站和伺服器垃圾回收的預設模式。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-126">When background garbage collection is disabled, this is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="a9b8b-127"><xref:System.Runtime.GCLatencyMode.Batch>模式還覆蓋[gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)設置，即它阻止後臺或併發集合。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-127"><xref:System.Runtime.GCLatencyMode.Batch> mode also overrides the [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) setting, that is, it prevents background or concurrent collections.</span></span>|
|<xref:System.Runtime.GCLatencyMode.Interactive>|<span data-ttu-id="a9b8b-128">對於大部分有使用者介面的應用程式，</span><span class="sxs-lookup"><span data-stu-id="a9b8b-128">For most applications that have a UI.</span></span><br /><br /><span data-ttu-id="a9b8b-129">這是工作站和伺服器垃圾回收的預設模式。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-129">This is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="a9b8b-130">但是，如果託管了應用，則託管進程的垃圾回收器設置將優先。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-130">However, if an app is hosted, the garbage collector settings of the hosting process take precedence.</span></span>|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|<span data-ttu-id="a9b8b-131">對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-131">For applications that have short-term, time-sensitive operations during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="a9b8b-132">例如，呈現動畫或資料獲取功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-132">For example, applications that render animations or data acquisition functions.</span></span>|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|<span data-ttu-id="a9b8b-133">適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-133">For applications that have time-sensitive operations for a contained but potentially longer duration of time during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="a9b8b-134">例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-134">For example, applications that need quick response times as market data changes during trading hours.</span></span><br /><br /><span data-ttu-id="a9b8b-135">這個模式會所產生的 Managed 堆積大小會比其他模式更大。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-135">This mode results in a larger managed heap size than other modes.</span></span> <span data-ttu-id="a9b8b-136">由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-136">Because it does not compact the managed heap, higher fragmentation is possible.</span></span> <span data-ttu-id="a9b8b-137">確定有足夠的記憶體可供使用。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-137">Ensure that sufficient memory is available.</span></span>|

## <a name="guidelines-for-using-low-latency"></a><span data-ttu-id="a9b8b-138">使用低延遲的指南</span><span class="sxs-lookup"><span data-stu-id="a9b8b-138">Guidelines for using low latency</span></span>

<span data-ttu-id="a9b8b-139">使用[GC延遲模式.低延遲](xref:System.Runtime.GCLatencyMode.LowLatency)模式時，請考慮以下準則：</span><span class="sxs-lookup"><span data-stu-id="a9b8b-139">When you use [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) mode, consider the following guidelines:</span></span>

- <span data-ttu-id="a9b8b-140">盡可能縮短這段低延遲的時間。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-140">Keep the period of time in low latency as short as possible.</span></span>

- <span data-ttu-id="a9b8b-141">請避免在低延遲期間配置大量記憶體。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-141">Avoid allocating high amounts of memory during low latency periods.</span></span> <span data-ttu-id="a9b8b-142">因為記憶體回收較少物件時，會造成記憶體不足的通知。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-142">Low memory notifications can occur because garbage collection reclaims fewer objects.</span></span>

- <span data-ttu-id="a9b8b-143">在低延遲模式下，儘量減少新分配的數量，特別是分配給大型物件堆和固定物件。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-143">While in the low latency mode, minimize the number of new allocations, in particular allocations onto the large object heap and pinned objects.</span></span>

- <span data-ttu-id="a9b8b-144">請注意無法配置的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-144">Be aware of threads that could be allocating.</span></span> <span data-ttu-id="a9b8b-145">由於<xref:System.Runtime.GCSettings.LatencyMode%2A>屬性設置是進程範圍的，<xref:System.OutOfMemoryException>因此可以在分配的任何執行緒上生成異常。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-145">Because the <xref:System.Runtime.GCSettings.LatencyMode%2A> property setting is process-wide, <xref:System.OutOfMemoryException> exceptions can be generated on any thread that is allocating.</span></span>

- <span data-ttu-id="a9b8b-146">在受限執列區域中包裝低延遲代碼。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-146">Wrap the low latency code in constrained execution regions.</span></span> <span data-ttu-id="a9b8b-147">有關詳細資訊，請參閱[約束執列區域](../../../docs/framework/performance/constrained-execution-regions.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-147">For more information, see [Constrained execution regions](../../../docs/framework/performance/constrained-execution-regions.md).</span></span>

- <span data-ttu-id="a9b8b-148">您也可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法，在低延遲期間強制層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="a9b8b-148">You can force generation 2 collections during a low latency period by calling the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9b8b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b8b-149">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="a9b8b-150">引發的收集</span><span class="sxs-lookup"><span data-stu-id="a9b8b-150">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)
- [<span data-ttu-id="a9b8b-151">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a9b8b-151">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
