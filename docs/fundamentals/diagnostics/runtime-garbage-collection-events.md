---
title: 垃圾收集運行時間事件
description: 請參閱收集 .NET 垃圾收集行程特定診斷資訊的 .NET 運行時間事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586639"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="d781c-103">.NET 執行時間垃圾收集事件</span><span class="sxs-lookup"><span data-stu-id="d781c-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="d781c-104">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d781c-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="d781c-105">它們有助於診斷和偵測，包括決定執行垃圾收集的次數、在垃圾收集期間釋放多少記憶體等等。如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="d781c-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="d781c-106">GCStart_V2 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-106">GCStart_V2 Event</span></span>

<span data-ttu-id="d781c-107">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-108">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-109">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-111">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-111">Informational (4)</span></span>|

<span data-ttu-id="d781c-112">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-112">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-113">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-113">Event</span></span>|<span data-ttu-id="d781c-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-114">Event ID</span></span>|<span data-ttu-id="d781c-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="d781c-116">1</span><span class="sxs-lookup"><span data-stu-id="d781c-116">1</span></span>|<span data-ttu-id="d781c-117">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d781c-117">A garbage collection has started.</span></span>|

<span data-ttu-id="d781c-118">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-118">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-119">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-119">Field name</span></span>|<span data-ttu-id="d781c-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-120">Data type</span></span>|<span data-ttu-id="d781c-121">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="d781c-122">第 *n* 個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d781c-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="d781c-123">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="d781c-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="d781c-124">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="d781c-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="d781c-125">`0x0` -小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="d781c-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="d781c-126">`0x1` 引入.</span><span class="sxs-lookup"><span data-stu-id="d781c-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="d781c-127">`0x2` -記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="d781c-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="d781c-128">`0x3` 空字元.</span><span class="sxs-lookup"><span data-stu-id="d781c-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="d781c-129">`0x4` -大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="d781c-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="d781c-130">`0x5` -用於小型物件堆積) 的空間 (。</span><span class="sxs-lookup"><span data-stu-id="d781c-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="d781c-131">`0x6` -) 大型物件堆積的空間 (。</span><span class="sxs-lookup"><span data-stu-id="d781c-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="d781c-132">`0x7` -已引發但未強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="d781c-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="d781c-133">`0x0` -在背景垃圾收集之外發生封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d781c-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="d781c-134">`0x1` -背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d781c-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="d781c-135">`0x2` -在背景垃圾收集期間發生封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d781c-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="d781c-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-136">win:UInt16</span></span>|<span data-ttu-id="d781c-137">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="d781c-138">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="d781c-139">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-140">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-140">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-141">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-143">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-143">Informational (4)</span></span>|

<span data-ttu-id="d781c-144">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-144">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-145">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-145">Event</span></span>|<span data-ttu-id="d781c-146">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-146">Event ID</span></span>|<span data-ttu-id="d781c-147">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="d781c-148">2</span><span class="sxs-lookup"><span data-stu-id="d781c-148">2</span></span>|<span data-ttu-id="d781c-149">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="d781c-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="d781c-150">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-150">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-151">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-151">Field name</span></span>|<span data-ttu-id="d781c-152">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-152">Data type</span></span>|<span data-ttu-id="d781c-153">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="d781c-154">第 *n* 個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d781c-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="d781c-155">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="d781c-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="d781c-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-156">win:UInt16</span></span>|<span data-ttu-id="d781c-157">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="d781c-158">GCHeapStats_V2 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="d781c-159">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-160">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-160">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-161">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-163">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-163">Informational (4)</span></span>|

<span data-ttu-id="d781c-164">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-164">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-165">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-165">Event</span></span>|<span data-ttu-id="d781c-166">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-166">Event ID</span></span>|<span data-ttu-id="d781c-167">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="d781c-168">4</span><span class="sxs-lookup"><span data-stu-id="d781c-168">4</span></span>|<span data-ttu-id="d781c-169">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="d781c-170">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-170">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-171">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-171">Field name</span></span>|<span data-ttu-id="d781c-172">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-172">Data type</span></span>|<span data-ttu-id="d781c-173">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="d781c-174">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="d781c-175">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="d781c-176">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="d781c-177">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="d781c-178">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="d781c-179">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="d781c-180">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="d781c-181">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="d781c-182">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="d781c-183">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="d781c-184">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="d781c-185">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="d781c-186">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-187">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="d781c-188">釘選的物件堆積大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d781c-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="d781c-189">在最後一個集合之後，在釘選的物件堆積中存活的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="d781c-190">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="d781c-191">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-192">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-192">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-193">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-195">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-195">Informational (4)</span></span>|

<span data-ttu-id="d781c-196">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-196">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-197">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-197">Event</span></span>|<span data-ttu-id="d781c-198">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-198">Event ID</span></span>|<span data-ttu-id="d781c-199">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="d781c-200">5</span><span class="sxs-lookup"><span data-stu-id="d781c-200">5</span></span>|<span data-ttu-id="d781c-201">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="d781c-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="d781c-202">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="d781c-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="d781c-203">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-203">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-204">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-204">Field name</span></span>|<span data-ttu-id="d781c-205">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-205">Data type</span></span>|<span data-ttu-id="d781c-206">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="d781c-207">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="d781c-208">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="d781c-209">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="d781c-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="d781c-210">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="d781c-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="d781c-211">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="d781c-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-212">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="d781c-213">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="d781c-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="d781c-214">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="d781c-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="d781c-215">GCFreeSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="d781c-216">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-217">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-217">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-218">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-220">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-220">Informational (4)</span></span>|

<span data-ttu-id="d781c-221">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-221">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-222">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-222">Event</span></span>|<span data-ttu-id="d781c-223">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-223">Event ID</span></span>|<span data-ttu-id="d781c-224">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="d781c-225">6</span><span class="sxs-lookup"><span data-stu-id="d781c-225">6</span></span>|<span data-ttu-id="d781c-226">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="d781c-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="d781c-227">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-227">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-228">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-228">Field name</span></span>|<span data-ttu-id="d781c-229">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-229">Data type</span></span>|<span data-ttu-id="d781c-230">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="d781c-231">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-232">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="d781c-233">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="d781c-234">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-235">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-235">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-236">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-238">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-238">Informational (4)</span></span>|

<span data-ttu-id="d781c-239">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-239">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-240">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-240">Event</span></span>|<span data-ttu-id="d781c-241">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-241">Event ID</span></span>|<span data-ttu-id="d781c-242">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="d781c-243">7</span><span class="sxs-lookup"><span data-stu-id="d781c-243">7</span></span>|<span data-ttu-id="d781c-244">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="d781c-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="d781c-245">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="d781c-246">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="d781c-247">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-248">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-248">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-249">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-251">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-251">Informational (4)</span></span>|

<span data-ttu-id="d781c-252">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-252">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-253">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-253">Event</span></span>|<span data-ttu-id="d781c-254">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-254">Event Id</span></span>|<span data-ttu-id="d781c-255">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="d781c-256">3</span><span class="sxs-lookup"><span data-stu-id="d781c-256">3</span></span>|<span data-ttu-id="d781c-257">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="d781c-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="d781c-258">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="d781c-259">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="d781c-260">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-261">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-261">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-262">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-264">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-264">Informational (4)</span></span>|

<span data-ttu-id="d781c-265">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-265">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-266">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-266">Event</span></span>|<span data-ttu-id="d781c-267">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-267">Event ID</span></span>|<span data-ttu-id="d781c-268">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="d781c-269">8</span><span class="sxs-lookup"><span data-stu-id="d781c-269">8</span></span>|<span data-ttu-id="d781c-270">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="d781c-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="d781c-271">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="d781c-272">GCSuspendEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="d781c-273">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-274">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-274">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-275">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-277">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-277">Informational (4)</span></span>|

<span data-ttu-id="d781c-278">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-278">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-279">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-279">Event</span></span>|<span data-ttu-id="d781c-280">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-280">Event ID</span></span>|<span data-ttu-id="d781c-281">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="d781c-282">8</span><span class="sxs-lookup"><span data-stu-id="d781c-282">8</span></span>|<span data-ttu-id="d781c-283">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="d781c-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="d781c-284">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-284">Field name</span></span>|<span data-ttu-id="d781c-285">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-285">Data type</span></span>|<span data-ttu-id="d781c-286">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="d781c-287">第 *n* 個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d781c-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="d781c-288">EE 暫停的原因。</span><span class="sxs-lookup"><span data-stu-id="d781c-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="d781c-289">`0x0`：暫停其他</span><span class="sxs-lookup"><span data-stu-id="d781c-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="d781c-290">`0x1`：暫止 GC。</span><span class="sxs-lookup"><span data-stu-id="d781c-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="d781c-291">`0x2`：暫止 AppDomain 關閉。</span><span class="sxs-lookup"><span data-stu-id="d781c-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="d781c-292">`0x3`：暫停程式碼推銷。</span><span class="sxs-lookup"><span data-stu-id="d781c-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="d781c-293">`0x4`：暫停關機。</span><span class="sxs-lookup"><span data-stu-id="d781c-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="d781c-294">`0x5`：暫停偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d781c-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="d781c-295">`0x6`：暫停 GC 準備。</span><span class="sxs-lookup"><span data-stu-id="d781c-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="d781c-296">`0x7`：暫止偵錯工具清理</span><span class="sxs-lookup"><span data-stu-id="d781c-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="d781c-297">GCAllocationTick_V3 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="d781c-298">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-299">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-299">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-300">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-302">詳細資訊 (4) </span><span class="sxs-lookup"><span data-stu-id="d781c-302">Verbose (4)</span></span>|

<span data-ttu-id="d781c-303">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-303">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-304">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-304">Event</span></span>|<span data-ttu-id="d781c-305">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-305">Event ID</span></span>|<span data-ttu-id="d781c-306">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="d781c-307">10</span><span class="sxs-lookup"><span data-stu-id="d781c-307">10</span></span>|<span data-ttu-id="d781c-308">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="d781c-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="d781c-309">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-309">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-310">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-310">Field name</span></span>|<span data-ttu-id="d781c-311">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-311">Data type</span></span>|<span data-ttu-id="d781c-312">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="d781c-313">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="d781c-313">The allocation size, in bytes.</span></span> <span data-ttu-id="d781c-314">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="d781c-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="d781c-315">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="d781c-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="d781c-316">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="d781c-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="d781c-317">`0x0` -小型物件配置 (配置是在小型物件堆積) 中。</span><span class="sxs-lookup"><span data-stu-id="d781c-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="d781c-318">`0x1` -大型物件配置 (配置位於大型物件堆積) 。</span><span class="sxs-lookup"><span data-stu-id="d781c-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="d781c-319">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="d781c-319">The allocation size, in bytes.</span></span> <span data-ttu-id="d781c-320">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="d781c-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="d781c-321">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-321">The address of the MethodTable.</span></span> <span data-ttu-id="d781c-322">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="d781c-323">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d781c-323">The name of the type that was allocated.</span></span> <span data-ttu-id="d781c-324">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="d781c-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="d781c-325">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="d781c-325">The heap where the object was allocated.</span></span> <span data-ttu-id="d781c-326">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="d781c-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="d781c-327">最後設定物件的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-328">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="d781c-329">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="d781c-330">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-331">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-331">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-332">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-334">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-334">Informational (4)</span></span>|
|<span data-ttu-id="d781c-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d781c-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d781c-336">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-336">Informational (4)</span></span>|

<span data-ttu-id="d781c-337">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-337">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-338">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-338">Event</span></span>|<span data-ttu-id="d781c-339">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-339">Event ID</span></span>|<span data-ttu-id="d781c-340">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="d781c-341">11</span><span class="sxs-lookup"><span data-stu-id="d781c-341">11</span></span>|<span data-ttu-id="d781c-342">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="d781c-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="d781c-343">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="d781c-344">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="d781c-345">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-346">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-346">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-347">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-349">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-349">Informational (4)</span></span>|
|<span data-ttu-id="d781c-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d781c-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d781c-351">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-351">Informational (4)</span></span>|

<span data-ttu-id="d781c-352">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-352">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-353">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-353">Event</span></span>|<span data-ttu-id="d781c-354">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-354">Event ID</span></span>|<span data-ttu-id="d781c-355">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="d781c-356">12</span><span class="sxs-lookup"><span data-stu-id="d781c-356">12</span></span>|<span data-ttu-id="d781c-357">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="d781c-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="d781c-358">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="d781c-359">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="d781c-360">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-361">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-361">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-362">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-364">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-364">Informational (4)</span></span>|

<span data-ttu-id="d781c-365">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-365">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-366">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-366">Event</span></span>|<span data-ttu-id="d781c-367">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-367">Event ID</span></span>|<span data-ttu-id="d781c-368">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="d781c-369">14</span><span class="sxs-lookup"><span data-stu-id="d781c-369">14</span></span>|<span data-ttu-id="d781c-370">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="d781c-370">The start of running finalizers.</span></span>|

<span data-ttu-id="d781c-371">此事件沒有任何事件資料。</span><span class="sxs-lookup"><span data-stu-id="d781c-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="d781c-372">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="d781c-373">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-374">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-374">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-375">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-377">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-377">Informational (4)</span></span>|

<span data-ttu-id="d781c-378">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-378">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-379">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-379">Event</span></span>|<span data-ttu-id="d781c-380">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-380">Event ID</span></span>|<span data-ttu-id="d781c-381">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="d781c-382">13</span><span class="sxs-lookup"><span data-stu-id="d781c-382">13</span></span>|<span data-ttu-id="d781c-383">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="d781c-383">The end of running finalizers.</span></span>|

<span data-ttu-id="d781c-384">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-384">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-385">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-385">Field name</span></span>|<span data-ttu-id="d781c-386">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-386">Data type</span></span>|<span data-ttu-id="d781c-387">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="d781c-388">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="d781c-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-389">win:UInt16</span></span>|<span data-ttu-id="d781c-390">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d781c-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="d781c-391">SetGCHandle 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-391">SetGCHandle event</span></span>

<span data-ttu-id="d781c-392">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-393">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-393">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-394">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-395">`GCHandleKeyword` (0x2) </span><span class="sxs-lookup"><span data-stu-id="d781c-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="d781c-396">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-396">Informational (4)</span></span>|

<span data-ttu-id="d781c-397">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-397">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-398">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-398">Event</span></span>|<span data-ttu-id="d781c-399">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-399">Event ID</span></span>|<span data-ttu-id="d781c-400">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="d781c-401">30</span><span class="sxs-lookup"><span data-stu-id="d781c-401">30</span></span>|<span data-ttu-id="d781c-402">已設定 GC 控制碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="d781c-403">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-403">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-404">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-404">Field name</span></span>|<span data-ttu-id="d781c-405">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-405">Data type</span></span>|<span data-ttu-id="d781c-406">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="d781c-407">配置的控制碼位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="d781c-408">建立控制碼之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="d781c-409">已設定的 GC 控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="d781c-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="d781c-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="d781c-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="d781c-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="d781c-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="d781c-412">`0x2`：強式</span><span class="sxs-lookup"><span data-stu-id="d781c-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="d781c-413">`0x3`：已釘選</span><span class="sxs-lookup"><span data-stu-id="d781c-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="d781c-414">`0x4`：變數</span><span class="sxs-lookup"><span data-stu-id="d781c-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="d781c-415">`0x5`: RefCounted</span><span class="sxs-lookup"><span data-stu-id="d781c-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="d781c-416">`0x6`：相依</span><span class="sxs-lookup"><span data-stu-id="d781c-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="d781c-417">`0x7`: AsyncPinned</span><span class="sxs-lookup"><span data-stu-id="d781c-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="d781c-418">`0x8`： SizedRef</span><span class="sxs-lookup"><span data-stu-id="d781c-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="d781c-419">建立控制碼的物件產生。</span><span class="sxs-lookup"><span data-stu-id="d781c-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="d781c-420">AppDomain 識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-421">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="d781c-422">DestroyGCHandle 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-422">DestroyGCHandle event</span></span>

<span data-ttu-id="d781c-423">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-424">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-424">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-425">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-426">`GCHandleKeyword` (0x2) </span><span class="sxs-lookup"><span data-stu-id="d781c-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="d781c-427">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="d781c-427">Informational (4)</span></span>|

<span data-ttu-id="d781c-428">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-428">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-429">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-429">Event</span></span>|<span data-ttu-id="d781c-430">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-430">Event ID</span></span>|<span data-ttu-id="d781c-431">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="d781c-432">31</span><span class="sxs-lookup"><span data-stu-id="d781c-432">31</span></span>|<span data-ttu-id="d781c-433">GC 控制碼已損毀。</span><span class="sxs-lookup"><span data-stu-id="d781c-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="d781c-434">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-434">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-435">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-435">Field name</span></span>|<span data-ttu-id="d781c-436">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-436">Data type</span></span>|<span data-ttu-id="d781c-437">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="d781c-438">終結的控制碼位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="d781c-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-439">win:UInt16</span></span>|<span data-ttu-id="d781c-440">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="d781c-441">PinObjectAtGCTime 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="d781c-442">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-443">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-443">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-444">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-446">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="d781c-446">Verbose (5)</span></span>|

<span data-ttu-id="d781c-447">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-447">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-448">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-448">Event</span></span>|<span data-ttu-id="d781c-449">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-449">Event ID</span></span>|<span data-ttu-id="d781c-450">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="d781c-451">33</span><span class="sxs-lookup"><span data-stu-id="d781c-451">33</span></span>|<span data-ttu-id="d781c-452">在 GC 期間釘選物件。</span><span class="sxs-lookup"><span data-stu-id="d781c-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="d781c-453">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-453">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-454">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-454">Field name</span></span>|<span data-ttu-id="d781c-455">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-455">Data type</span></span>|<span data-ttu-id="d781c-456">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="d781c-457">控制碼的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="d781c-458">釘選物件的位址。</span><span class="sxs-lookup"><span data-stu-id="d781c-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="d781c-459">釘選物件的大小。</span><span class="sxs-lookup"><span data-stu-id="d781c-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="d781c-460">釘選物件的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d781c-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-461">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="d781c-462">GCTriggered 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-462">GCTriggered event</span></span>

<span data-ttu-id="d781c-463">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-464">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-464">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-465">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-467">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="d781c-467">Verbose (5)</span></span>|

<span data-ttu-id="d781c-468">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-468">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-469">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-469">Event</span></span>|<span data-ttu-id="d781c-470">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-470">Event ID</span></span>|<span data-ttu-id="d781c-471">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="d781c-472">33</span><span class="sxs-lookup"><span data-stu-id="d781c-472">33</span></span>|<span data-ttu-id="d781c-473">已觸發 GC。</span><span class="sxs-lookup"><span data-stu-id="d781c-473">A GC has been triggered.</span></span>|

<span data-ttu-id="d781c-474">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-474">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-475">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-475">Field name</span></span>|<span data-ttu-id="d781c-476">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-476">Data type</span></span>|<span data-ttu-id="d781c-477">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="d781c-478">觸發 GC 的原因。</span><span class="sxs-lookup"><span data-stu-id="d781c-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="d781c-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="d781c-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="d781c-480">`0x1`：已引發</span><span class="sxs-lookup"><span data-stu-id="d781c-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="d781c-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="d781c-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="d781c-482">`0x3`：空白</span><span class="sxs-lookup"><span data-stu-id="d781c-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="d781c-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="d781c-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="d781c-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="d781c-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="d781c-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="d781c-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="d781c-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="d781c-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="d781c-487">`0x8`：壓力</span><span class="sxs-lookup"><span data-stu-id="d781c-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="d781c-488">`0x9`: InducedLowMemory</span><span class="sxs-lookup"><span data-stu-id="d781c-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-489">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="d781c-490">IncreaseMemoryPressure 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="d781c-491">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-492">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-492">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-493">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-495">資訊 (4) </span><span class="sxs-lookup"><span data-stu-id="d781c-495">Information (4)</span></span>|

<span data-ttu-id="d781c-496">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-496">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-497">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-497">Event</span></span>|<span data-ttu-id="d781c-498">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-498">Event ID</span></span>|<span data-ttu-id="d781c-499">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="d781c-500">200</span><span class="sxs-lookup"><span data-stu-id="d781c-500">200</span></span>|<span data-ttu-id="d781c-501">記憶體壓力已增加。</span><span class="sxs-lookup"><span data-stu-id="d781c-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="d781c-502">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-502">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-503">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-503">Field Name</span></span>|<span data-ttu-id="d781c-504">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-504">Data type</span></span>|<span data-ttu-id="d781c-505">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="d781c-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-506">win:UInt16</span></span>|<span data-ttu-id="d781c-507">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="d781c-508">DecreaseMemoryPressure 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="d781c-509">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-510">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-510">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-511">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-513">資訊 (4) </span><span class="sxs-lookup"><span data-stu-id="d781c-513">Information (4)</span></span>|

<span data-ttu-id="d781c-514">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-514">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-515">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-515">Event</span></span>|<span data-ttu-id="d781c-516">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-516">Event ID</span></span>|<span data-ttu-id="d781c-517">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="d781c-518">201</span><span class="sxs-lookup"><span data-stu-id="d781c-518">201</span></span>|<span data-ttu-id="d781c-519">記憶體壓力已減少。</span><span class="sxs-lookup"><span data-stu-id="d781c-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="d781c-520">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-520">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-521">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-521">Field Name</span></span>|<span data-ttu-id="d781c-522">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-522">Data type</span></span>|<span data-ttu-id="d781c-523">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="d781c-524">釋放的位元組。</span><span class="sxs-lookup"><span data-stu-id="d781c-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-525">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="d781c-526">GCMarkWithType 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-526">GCMarkWithType event</span></span>

<span data-ttu-id="d781c-527">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-528">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-528">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-529">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-531">資訊 (4) </span><span class="sxs-lookup"><span data-stu-id="d781c-531">Information (4)</span></span>|

<span data-ttu-id="d781c-532">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-532">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-533">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-533">Event</span></span>|<span data-ttu-id="d781c-534">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-534">Event ID</span></span>|<span data-ttu-id="d781c-535">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="d781c-536">202</span><span class="sxs-lookup"><span data-stu-id="d781c-536">202</span></span>|<span data-ttu-id="d781c-537">Gc 標記階段中已標示 GC 根。</span><span class="sxs-lookup"><span data-stu-id="d781c-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="d781c-538">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-538">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-539">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-539">Field Name</span></span>|<span data-ttu-id="d781c-540">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-540">Data type</span></span>|<span data-ttu-id="d781c-541">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="d781c-542">堆積數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="d781c-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d781c-543">win:UInt16</span></span>|<span data-ttu-id="d781c-544">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="d781c-545">GC 根型別。</span><span class="sxs-lookup"><span data-stu-id="d781c-545">The GC root type.</span></span><br/><br/><span data-ttu-id="d781c-546">`0x0`： Stack</span><span class="sxs-lookup"><span data-stu-id="d781c-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="d781c-547">`0x1`： Finalizer</span><span class="sxs-lookup"><span data-stu-id="d781c-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="d781c-548">`0x2`：控制碼</span><span class="sxs-lookup"><span data-stu-id="d781c-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="d781c-549">`0x3`：舊版</span><span class="sxs-lookup"><span data-stu-id="d781c-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="d781c-550">`0x4`： SizedRef</span><span class="sxs-lookup"><span data-stu-id="d781c-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="d781c-551">`0x5`：溢位</span><span class="sxs-lookup"><span data-stu-id="d781c-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="d781c-552">標示的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d781c-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="d781c-553">GCJoin_V2 事件</span><span class="sxs-lookup"><span data-stu-id="d781c-553">GCJoin_V2 event</span></span>

<span data-ttu-id="d781c-554">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="d781c-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="d781c-555">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="d781c-555">Keyword for raising the event</span></span>|<span data-ttu-id="d781c-556">層級</span><span class="sxs-lookup"><span data-stu-id="d781c-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="d781c-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d781c-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d781c-558">詳細資訊 (5)</span><span class="sxs-lookup"><span data-stu-id="d781c-558">Verbose (5)</span></span>|

<span data-ttu-id="d781c-559">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="d781c-559">The following table shows the event information:</span></span>

|<span data-ttu-id="d781c-560">事件</span><span class="sxs-lookup"><span data-stu-id="d781c-560">Event</span></span>|<span data-ttu-id="d781c-561">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d781c-561">Event ID</span></span>|<span data-ttu-id="d781c-562">引發的時機</span><span class="sxs-lookup"><span data-stu-id="d781c-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="d781c-563">203</span><span class="sxs-lookup"><span data-stu-id="d781c-563">203</span></span>|<span data-ttu-id="d781c-564">已加入 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="d781c-564">A GC thread joined.</span></span>|

<span data-ttu-id="d781c-565">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="d781c-565">The following table shows the event data:</span></span>

|<span data-ttu-id="d781c-566">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="d781c-566">Field name</span></span>|<span data-ttu-id="d781c-567">資料類型</span><span class="sxs-lookup"><span data-stu-id="d781c-567">Data type</span></span>|<span data-ttu-id="d781c-568">描述</span><span class="sxs-lookup"><span data-stu-id="d781c-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="d781c-569">堆積數目</span><span class="sxs-lookup"><span data-stu-id="d781c-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="d781c-570">指出此事件是否會在聯結開始的聯結 (開頭或結束時引發 `0x0` ， `0x1` 以進行聯結結束) </span><span class="sxs-lookup"><span data-stu-id="d781c-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="d781c-571">聯結類型。</span><span class="sxs-lookup"><span data-stu-id="d781c-571">The join type.</span></span> <br/><br/><span data-ttu-id="d781c-572">`0x0`：上次聯結</span><span class="sxs-lookup"><span data-stu-id="d781c-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="d781c-573">`0x1`：聯結</span><span class="sxs-lookup"><span data-stu-id="d781c-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="d781c-574">`0x2`：重新開機</span><span class="sxs-lookup"><span data-stu-id="d781c-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="d781c-575">`0x3`：第一個反向聯結</span><span class="sxs-lookup"><span data-stu-id="d781c-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="d781c-576">`0x4`：反向聯結</span><span class="sxs-lookup"><span data-stu-id="d781c-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="d781c-577">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d781c-577">Unique ID for the instance of CoreCLR.</span></span>|
