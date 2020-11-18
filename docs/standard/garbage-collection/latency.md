---
title: 延遲模式
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 2e7b30a50e2513c567abf2116ab5495e717a8e22
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831191"
---
# <a name="latency-modes"></a><span data-ttu-id="cda4d-102">延遲模式</span><span class="sxs-lookup"><span data-stu-id="cda4d-102">Latency modes</span></span>

<span data-ttu-id="cda4d-103">若要回收物件，垃圾收集行程 (GC) 必須停止應用程式中所有執行中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="cda4d-103">To reclaim objects, the garbage collector (GC) must stop all the executing threads in an application.</span></span> <span data-ttu-id="cda4d-104">在這段期間內，垃圾收集行程是使用中的時間，稱為 *延遲*。</span><span class="sxs-lookup"><span data-stu-id="cda4d-104">The period of time during which the garbage collector is active is referred to as its *latency*.</span></span>

<span data-ttu-id="cda4d-105">在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。</span><span class="sxs-lookup"><span data-stu-id="cda4d-105">In some situations, such as when an application retrieves data or displays content, a full garbage collection can occur at a critical time and impede performance.</span></span> <span data-ttu-id="cda4d-106">您可以藉由設定 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值的其中一個，來調整記憶體回收行程的干擾程度。</span><span class="sxs-lookup"><span data-stu-id="cda4d-106">You can adjust the intrusiveness of the garbage collector by setting the <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> property to one of the <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> values.</span></span>

## <a name="low-latency-settings"></a><span data-ttu-id="cda4d-107">低延遲設定</span><span class="sxs-lookup"><span data-stu-id="cda4d-107">Low latency settings</span></span>

<span data-ttu-id="cda4d-108">使用「低」延遲設定表示您的應用程式中的垃圾收集行程行程干擾較少。</span><span class="sxs-lookup"><span data-stu-id="cda4d-108">Using a "low" latency setting means the garbage collector intrudes less in your application.</span></span> <span data-ttu-id="cda4d-109">回收記憶體的垃圾收集更保守。</span><span class="sxs-lookup"><span data-stu-id="cda4d-109">Garbage collection is more conservative about reclaiming memory.</span></span>

<span data-ttu-id="cda4d-110"><xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列舉會提供兩個低延遲設定：</span><span class="sxs-lookup"><span data-stu-id="cda4d-110">The <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> enumeration provides two low latency settings:</span></span>

- <span data-ttu-id="cda4d-111">[GCLatencyMode](xref:System.Runtime.GCLatencyMode.LowLatency) 會隱藏層代2回收，並且只執行層代0和1回收。</span><span class="sxs-lookup"><span data-stu-id="cda4d-111">[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) suppresses generation 2 collections and performs only generation 0 and 1 collections.</span></span> <span data-ttu-id="cda4d-112">它只適合短時間使用。</span><span class="sxs-lookup"><span data-stu-id="cda4d-112">It can be used only for short periods of time.</span></span> <span data-ttu-id="cda4d-113">經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。</span><span class="sxs-lookup"><span data-stu-id="cda4d-113">Over longer periods, if the system is under memory pressure, the garbage collector will trigger a collection, which can briefly pause the application and disrupt a time-critical operation.</span></span> <span data-ttu-id="cda4d-114">這項設定僅適用於工作站記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cda4d-114">This setting is available only for workstation garbage collection.</span></span>

- <span data-ttu-id="cda4d-115">[GCLatencyMode](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) 會隱藏前景層代2回收，並且只執行層代0、1和背景層代2回收。</span><span class="sxs-lookup"><span data-stu-id="cda4d-115">[GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) suppresses foreground generation 2 collections and performs only generation 0, 1, and background generation 2 collections.</span></span> <span data-ttu-id="cda4d-116">它可以長時間使用，並且可用於工作站和伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cda4d-116">It can be used for longer periods of time, and is available for both workstation and server garbage collection.</span></span> <span data-ttu-id="cda4d-117">如果停用背景垃圾收集，則無法使用此設定。</span><span class="sxs-lookup"><span data-stu-id="cda4d-117">This setting cannot be used if background garbage collection is disabled.</span></span>

<span data-ttu-id="cda4d-118">在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="cda4d-118">During low latency periods, generation 2 collections are suppressed unless the following occurs:</span></span>

- <span data-ttu-id="cda4d-119">系統從作業系統接收到記憶體不足的通知。</span><span class="sxs-lookup"><span data-stu-id="cda4d-119">The system receives a low memory notification from the operating system.</span></span>

- <span data-ttu-id="cda4d-120">應用程式程式碼會藉由呼叫方法來引發集合 <xref:System.GC.Collect%2A?displayProperty=nameWithType> ，並為參數指定 2 `generation` 。</span><span class="sxs-lookup"><span data-stu-id="cda4d-120">Application code induces a collection by calling the <xref:System.GC.Collect%2A?displayProperty=nameWithType> method and specifying 2 for the `generation` parameter.</span></span>

## <a name="scenarios"></a><span data-ttu-id="cda4d-121">案例</span><span class="sxs-lookup"><span data-stu-id="cda4d-121">Scenarios</span></span>

<span data-ttu-id="cda4d-122">下表列出使用這些值的應用程式案例 <xref:System.Runtime.GCLatencyMode> ：</span><span class="sxs-lookup"><span data-stu-id="cda4d-122">The following table lists the application scenarios for using the <xref:System.Runtime.GCLatencyMode> values:</span></span>

|<span data-ttu-id="cda4d-123">延遲模式</span><span class="sxs-lookup"><span data-stu-id="cda4d-123">Latency mode</span></span>|<span data-ttu-id="cda4d-124">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="cda4d-124">Application scenarios</span></span>|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|<span data-ttu-id="cda4d-125">針對沒有使用者介面 (UI) 或伺服器端作業的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cda4d-125">For applications that have no user interface (UI) or server-side operations.</span></span><br /><br /><span data-ttu-id="cda4d-126">停用背景垃圾收集時，這是工作站和伺服器垃圾收集的預設模式。</span><span class="sxs-lookup"><span data-stu-id="cda4d-126">When background garbage collection is disabled, this is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="cda4d-127"><xref:System.Runtime.GCLatencyMode.Batch> 模式也會覆寫 [>gcconcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 設定，也就是說，它會防止背景或並行集合。</span><span class="sxs-lookup"><span data-stu-id="cda4d-127"><xref:System.Runtime.GCLatencyMode.Batch> mode also overrides the [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) setting, that is, it prevents background or concurrent collections.</span></span>|
|<xref:System.Runtime.GCLatencyMode.Interactive>|<span data-ttu-id="cda4d-128">對於大部分有使用者介面的應用程式，</span><span class="sxs-lookup"><span data-stu-id="cda4d-128">For most applications that have a UI.</span></span><br /><br /><span data-ttu-id="cda4d-129">這是工作站和伺服器垃圾收集的預設模式。</span><span class="sxs-lookup"><span data-stu-id="cda4d-129">This is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="cda4d-130">但是，如果裝載應用程式，則裝載進程的垃圾收集行程設定會優先執行。</span><span class="sxs-lookup"><span data-stu-id="cda4d-130">However, if an app is hosted, the garbage collector settings of the hosting process take precedence.</span></span>|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|<span data-ttu-id="cda4d-131">對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。</span><span class="sxs-lookup"><span data-stu-id="cda4d-131">For applications that have short-term, time-sensitive operations during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="cda4d-132">例如，呈現動畫或資料取得函數的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cda4d-132">For example, applications that render animations or data acquisition functions.</span></span>|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|<span data-ttu-id="cda4d-133">適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。</span><span class="sxs-lookup"><span data-stu-id="cda4d-133">For applications that have time-sensitive operations for a contained but potentially longer duration of time during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="cda4d-134">例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cda4d-134">For example, applications that need quick response times as market data changes during trading hours.</span></span><br /><br /><span data-ttu-id="cda4d-135">這個模式會所產生的 Managed 堆積大小會比其他模式更大。</span><span class="sxs-lookup"><span data-stu-id="cda4d-135">This mode results in a larger managed heap size than other modes.</span></span> <span data-ttu-id="cda4d-136">由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。</span><span class="sxs-lookup"><span data-stu-id="cda4d-136">Because it does not compact the managed heap, higher fragmentation is possible.</span></span> <span data-ttu-id="cda4d-137">確定有足夠的記憶體可供使用。</span><span class="sxs-lookup"><span data-stu-id="cda4d-137">Ensure that sufficient memory is available.</span></span>|

## <a name="guidelines-for-using-low-latency"></a><span data-ttu-id="cda4d-138">使用低延遲的指導方針</span><span class="sxs-lookup"><span data-stu-id="cda4d-138">Guidelines for using low latency</span></span>

<span data-ttu-id="cda4d-139">當您使用 [GCLatencyMode LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 模式時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="cda4d-139">When you use [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) mode, consider the following guidelines:</span></span>

- <span data-ttu-id="cda4d-140">盡可能縮短這段低延遲的時間。</span><span class="sxs-lookup"><span data-stu-id="cda4d-140">Keep the period of time in low latency as short as possible.</span></span>

- <span data-ttu-id="cda4d-141">請避免在低延遲期間配置大量記憶體。</span><span class="sxs-lookup"><span data-stu-id="cda4d-141">Avoid allocating high amounts of memory during low latency periods.</span></span> <span data-ttu-id="cda4d-142">因為記憶體回收較少物件時，會造成記憶體不足的通知。</span><span class="sxs-lookup"><span data-stu-id="cda4d-142">Low memory notifications can occur because garbage collection reclaims fewer objects.</span></span>

- <span data-ttu-id="cda4d-143">在低延遲模式中，將新配置的數目降至最低，特別是在大型物件堆積和釘選的物件上。</span><span class="sxs-lookup"><span data-stu-id="cda4d-143">While in the low latency mode, minimize the number of new allocations, in particular allocations onto the large object heap and pinned objects.</span></span>

- <span data-ttu-id="cda4d-144">請注意無法配置的執行緒。</span><span class="sxs-lookup"><span data-stu-id="cda4d-144">Be aware of threads that could be allocating.</span></span> <span data-ttu-id="cda4d-145">由於 <xref:System.Runtime.GCSettings.LatencyMode%2A> 屬性設定是整個進程，因此 <xref:System.OutOfMemoryException> 可以在任何配置的執行緒上產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cda4d-145">Because the <xref:System.Runtime.GCSettings.LatencyMode%2A> property setting is process-wide, <xref:System.OutOfMemoryException> exceptions can be generated on any thread that is allocating.</span></span>

- <span data-ttu-id="cda4d-146">將低延遲程式碼包裝在限制執列區域中。</span><span class="sxs-lookup"><span data-stu-id="cda4d-146">Wrap the low latency code in constrained execution regions.</span></span> <span data-ttu-id="cda4d-147">如需詳細資訊，請參閱 [限制執列區域](../../framework/performance/constrained-execution-regions.md)。</span><span class="sxs-lookup"><span data-stu-id="cda4d-147">For more information, see [Constrained execution regions](../../framework/performance/constrained-execution-regions.md).</span></span>

- <span data-ttu-id="cda4d-148">您也可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法，在低延遲期間強制層代 2 回收。</span><span class="sxs-lookup"><span data-stu-id="cda4d-148">You can force generation 2 collections during a low latency period by calling the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="cda4d-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="cda4d-149">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="cda4d-150">引發的集合</span><span class="sxs-lookup"><span data-stu-id="cda4d-150">Induced Collections</span></span>](induced.md)
- [<span data-ttu-id="cda4d-151">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="cda4d-151">Garbage Collection</span></span>](index.md)
