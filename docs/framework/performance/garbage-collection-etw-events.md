---
title: 記憶體回收 ETW 事件
description: 查看垃圾收集 ETW 事件的詳細資訊。 涵蓋的事件包括 GCStart_V1、GCEnd_V1、GCHeapStats_V1、GCCreateSegment_V1 等。
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 2e1e0fda5c1a80627c8dde7f49954a867b9a2b66
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720133"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="a4e80-104">記憶體回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="a4e80-105">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a4e80-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="a4e80-106">它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。</span><span class="sxs-lookup"><span data-stu-id="a4e80-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="a4e80-107">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="a4e80-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="a4e80-108">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="a4e80-109">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="a4e80-110">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="a4e80-111">GCHeapStats_V2 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-111">GCHeapStats_V2 Event</span></span>](#gcheapstats_v2-event)
- [<span data-ttu-id="a4e80-112">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-112">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="a4e80-113">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-113">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="a4e80-114">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-114">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="a4e80-115">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-115">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="a4e80-116">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-116">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="a4e80-117">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-117">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="a4e80-118">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-118">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="a4e80-119">GCAllocationTick_V3 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-119">GCAllocationTick_V3 Event</span></span>](#gcallocationtick_v3-event)
- [<span data-ttu-id="a4e80-120">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-120">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="a4e80-121">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-121">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="a4e80-122">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-122">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="a4e80-123">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-123">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="a4e80-124">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-124">GCStart_V1 Event</span></span>  

<span data-ttu-id="a4e80-125">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="a4e80-125">The following table shows the keyword and level.</span></span> <span data-ttu-id="a4e80-126">如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-126">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="a4e80-127">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-127">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-128">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-128">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-129">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-129">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-130">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-130">Informational (4)</span></span>|

<span data-ttu-id="a4e80-131">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-131">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-132">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-132">Event</span></span>|<span data-ttu-id="a4e80-133">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-133">Event ID</span></span>|<span data-ttu-id="a4e80-134">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-134">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="a4e80-135">1</span><span class="sxs-lookup"><span data-stu-id="a4e80-135">1</span></span>|<span data-ttu-id="a4e80-136">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-136">A garbage collection has started.</span></span>|

<span data-ttu-id="a4e80-137">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-137">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-138">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-138">Field name</span></span>|<span data-ttu-id="a4e80-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-139">Data type</span></span>|<span data-ttu-id="a4e80-140">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-140">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-141">Count</span><span class="sxs-lookup"><span data-stu-id="a4e80-141">Count</span></span>|<span data-ttu-id="a4e80-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-142">win:UInt32</span></span>|<span data-ttu-id="a4e80-143">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-143">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="a4e80-144">深度</span><span class="sxs-lookup"><span data-stu-id="a4e80-144">Depth</span></span>|<span data-ttu-id="a4e80-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-145">win:UInt32</span></span>|<span data-ttu-id="a4e80-146">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="a4e80-146">The generation that is being collected.</span></span>|
|<span data-ttu-id="a4e80-147">原因</span><span class="sxs-lookup"><span data-stu-id="a4e80-147">Reason</span></span>|<span data-ttu-id="a4e80-148">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-148">win:UInt32</span></span>|<span data-ttu-id="a4e80-149">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="a4e80-149">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="a4e80-150">0x0 - 小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-150">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="a4e80-151">0x1 - 已引起。</span><span class="sxs-lookup"><span data-stu-id="a4e80-151">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="a4e80-152">0x2 - 記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="a4e80-152">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="a4e80-153">0x3 - 空白。</span><span class="sxs-lookup"><span data-stu-id="a4e80-153">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="a4e80-154">0x4 - 大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-154">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="a4e80-155">0x5 - 空間不足 (針對小型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-155">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="a4e80-156">0x6 - 空間不足 (針對大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-156">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="a4e80-157">0x7 - 已引起，但不強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="a4e80-157">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="a4e80-158">類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-158">Type</span></span>|<span data-ttu-id="a4e80-159">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-159">win:UInt32</span></span>|<span data-ttu-id="a4e80-160">0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-160">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="a4e80-161">0x1 - 背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-161">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="a4e80-162">0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-162">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="a4e80-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-163">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-164">win:UInt16</span></span>|<span data-ttu-id="a4e80-165">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="a4e80-166">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-166">GCEnd_V1 Event</span></span>

<span data-ttu-id="a4e80-167">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-167">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-168">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-168">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-169">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-169">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-170">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-170">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-171">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-171">Informational (4)</span></span>|

<span data-ttu-id="a4e80-172">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-172">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-173">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-173">Event</span></span>|<span data-ttu-id="a4e80-174">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-174">Event ID</span></span>|<span data-ttu-id="a4e80-175">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-175">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="a4e80-176">2</span><span class="sxs-lookup"><span data-stu-id="a4e80-176">2</span></span>|<span data-ttu-id="a4e80-177">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="a4e80-177">The garbage collection has ended.</span></span>|

<span data-ttu-id="a4e80-178">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-178">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-179">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-179">Field name</span></span>|<span data-ttu-id="a4e80-180">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-180">Data type</span></span>|<span data-ttu-id="a4e80-181">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-181">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-182">Count</span><span class="sxs-lookup"><span data-stu-id="a4e80-182">Count</span></span>|<span data-ttu-id="a4e80-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-183">win:UInt32</span></span>|<span data-ttu-id="a4e80-184">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-184">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="a4e80-185">深度</span><span class="sxs-lookup"><span data-stu-id="a4e80-185">Depth</span></span>|<span data-ttu-id="a4e80-186">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-186">win:UInt32</span></span>|<span data-ttu-id="a4e80-187">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="a4e80-187">The generation that was collected.</span></span>|
|<span data-ttu-id="a4e80-188">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-188">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-189">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-189">win:UInt16</span></span>|<span data-ttu-id="a4e80-190">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-190">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="a4e80-191">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-191">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="a4e80-192">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-192">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-193">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-193">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-194">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-194">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-195">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-195">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-196">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-196">Informational (4)</span></span>|

<span data-ttu-id="a4e80-197">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-197">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-198">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-198">Event</span></span>|<span data-ttu-id="a4e80-199">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-199">Event ID</span></span>|<span data-ttu-id="a4e80-200">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-200">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="a4e80-201">4</span><span class="sxs-lookup"><span data-stu-id="a4e80-201">4</span></span>|<span data-ttu-id="a4e80-202">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-202">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="a4e80-203">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-203">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-204">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-204">Field name</span></span>|<span data-ttu-id="a4e80-205">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-205">Data type</span></span>|<span data-ttu-id="a4e80-206">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-206">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-207">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="a4e80-207">GenerationSize0</span></span>|<span data-ttu-id="a4e80-208">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-208">win:UInt64</span></span>|<span data-ttu-id="a4e80-209">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-209">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="a4e80-210">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="a4e80-210">TotalPromotedSize0</span></span>|<span data-ttu-id="a4e80-211">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-211">win:UInt64</span></span>|<span data-ttu-id="a4e80-212">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-212">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="a4e80-213">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="a4e80-213">GenerationSize1</span></span>|<span data-ttu-id="a4e80-214">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-214">win:UInt64</span></span>|<span data-ttu-id="a4e80-215">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-215">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="a4e80-216">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="a4e80-216">TotalPromotedSize1</span></span>|<span data-ttu-id="a4e80-217">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-217">win:UInt64</span></span>|<span data-ttu-id="a4e80-218">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-218">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="a4e80-219">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="a4e80-219">GenerationSize2</span></span>|<span data-ttu-id="a4e80-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-220">win:UInt64</span></span>|<span data-ttu-id="a4e80-221">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-221">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="a4e80-222">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="a4e80-222">TotalPromotedSize2</span></span>|<span data-ttu-id="a4e80-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-223">win:UInt64</span></span>|<span data-ttu-id="a4e80-224">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-224">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="a4e80-225">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="a4e80-225">GenerationSize3</span></span>|<span data-ttu-id="a4e80-226">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-226">win:UInt64</span></span>|<span data-ttu-id="a4e80-227">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-227">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="a4e80-228">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="a4e80-228">TotalPromotedSize3</span></span>|<span data-ttu-id="a4e80-229">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-229">win:UInt64</span></span>|<span data-ttu-id="a4e80-230">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-230">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="a4e80-231">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="a4e80-231">FinalizationPromotedSize</span></span>|<span data-ttu-id="a4e80-232">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-232">win:UInt64</span></span>|<span data-ttu-id="a4e80-233">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-233">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a4e80-234">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-234">FinalizationPromotedCount</span></span>|<span data-ttu-id="a4e80-235">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-235">win:UInt64</span></span>|<span data-ttu-id="a4e80-236">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-236">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a4e80-237">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-237">PinnedObjectCount</span></span>|<span data-ttu-id="a4e80-238">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-238">win:UInt32</span></span>|<span data-ttu-id="a4e80-239">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-239">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="a4e80-240">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-240">SinkBlockCount</span></span>|<span data-ttu-id="a4e80-241">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-241">win:UInt32</span></span>|<span data-ttu-id="a4e80-242">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-242">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="a4e80-243">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-243">GCHandleCount</span></span>|<span data-ttu-id="a4e80-244">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-244">win:UInt32</span></span>|<span data-ttu-id="a4e80-245">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-245">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="a4e80-246">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-246">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-247">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-247">win:UInt16</span></span>|<span data-ttu-id="a4e80-248">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-248">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gcheapstats_v2-event"></a><span data-ttu-id="a4e80-249">GCHeapStats_V2 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-249">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="a4e80-250">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-250">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-251">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-251">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-252">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-252">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-253">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-253">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-254">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-254">Informational (4)</span></span>|

<span data-ttu-id="a4e80-255">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-255">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-256">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-256">Event</span></span>|<span data-ttu-id="a4e80-257">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-257">Event ID</span></span>|<span data-ttu-id="a4e80-258">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-258">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="a4e80-259">4</span><span class="sxs-lookup"><span data-stu-id="a4e80-259">4</span></span>|<span data-ttu-id="a4e80-260">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-260">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="a4e80-261">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-261">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-262">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-262">Field name</span></span>|<span data-ttu-id="a4e80-263">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-263">Data type</span></span>|<span data-ttu-id="a4e80-264">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-264">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-265">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="a4e80-265">GenerationSize0</span></span>|<span data-ttu-id="a4e80-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-266">win:UInt64</span></span>|<span data-ttu-id="a4e80-267">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-267">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="a4e80-268">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="a4e80-268">TotalPromotedSize0</span></span>|<span data-ttu-id="a4e80-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-269">win:UInt64</span></span>|<span data-ttu-id="a4e80-270">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-270">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="a4e80-271">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="a4e80-271">GenerationSize1</span></span>|<span data-ttu-id="a4e80-272">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-272">win:UInt64</span></span>|<span data-ttu-id="a4e80-273">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-273">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="a4e80-274">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="a4e80-274">TotalPromotedSize1</span></span>|<span data-ttu-id="a4e80-275">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-275">win:UInt64</span></span>|<span data-ttu-id="a4e80-276">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-276">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="a4e80-277">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="a4e80-277">GenerationSize2</span></span>|<span data-ttu-id="a4e80-278">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-278">win:UInt64</span></span>|<span data-ttu-id="a4e80-279">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-279">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="a4e80-280">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="a4e80-280">TotalPromotedSize2</span></span>|<span data-ttu-id="a4e80-281">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-281">win:UInt64</span></span>|<span data-ttu-id="a4e80-282">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-282">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="a4e80-283">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="a4e80-283">GenerationSize3</span></span>|<span data-ttu-id="a4e80-284">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-284">win:UInt64</span></span>|<span data-ttu-id="a4e80-285">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-285">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="a4e80-286">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="a4e80-286">TotalPromotedSize3</span></span>|<span data-ttu-id="a4e80-287">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-287">win:UInt64</span></span>|<span data-ttu-id="a4e80-288">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-288">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="a4e80-289">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="a4e80-289">FinalizationPromotedSize</span></span>|<span data-ttu-id="a4e80-290">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-290">win:UInt64</span></span>|<span data-ttu-id="a4e80-291">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-291">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a4e80-292">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-292">FinalizationPromotedCount</span></span>|<span data-ttu-id="a4e80-293">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-293">win:UInt64</span></span>|<span data-ttu-id="a4e80-294">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-294">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="a4e80-295">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-295">PinnedObjectCount</span></span>|<span data-ttu-id="a4e80-296">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-296">win:UInt32</span></span>|<span data-ttu-id="a4e80-297">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-297">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="a4e80-298">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-298">SinkBlockCount</span></span>|<span data-ttu-id="a4e80-299">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-299">win:UInt32</span></span>|<span data-ttu-id="a4e80-300">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-300">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="a4e80-301">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="a4e80-301">GCHandleCount</span></span>|<span data-ttu-id="a4e80-302">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-302">win:UInt32</span></span>|<span data-ttu-id="a4e80-303">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-303">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="a4e80-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-304">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-305">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-305">win:UInt16</span></span>|<span data-ttu-id="a4e80-306">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="a4e80-307">GenerationSize4</span><span class="sxs-lookup"><span data-stu-id="a4e80-307">GenerationSize4</span></span>|<span data-ttu-id="a4e80-308">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-308">win:UInt64</span></span>|<span data-ttu-id="a4e80-309">釘選的物件堆積大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a4e80-309">The size, in bytes, of the pinned object heap.</span></span>|
|<span data-ttu-id="a4e80-310">TotalPromotedSize4</span><span class="sxs-lookup"><span data-stu-id="a4e80-310">TotalPromotedSize4</span></span>|<span data-ttu-id="a4e80-311">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-311">win:UInt64</span></span>|<span data-ttu-id="a4e80-312">在最後一個集合之後，在釘選的物件堆積中存活的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-312">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="a4e80-313">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-313">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="a4e80-314">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-315">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-315">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-316">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-318">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-318">Informational (4)</span></span>|

<span data-ttu-id="a4e80-319">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-319">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-320">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-320">Event</span></span>|<span data-ttu-id="a4e80-321">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-321">Event ID</span></span>|<span data-ttu-id="a4e80-322">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="a4e80-323">5</span><span class="sxs-lookup"><span data-stu-id="a4e80-323">5</span></span>|<span data-ttu-id="a4e80-324">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="a4e80-324">A new garbage collection segment has been created.</span></span> <span data-ttu-id="a4e80-325">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="a4e80-325">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="a4e80-326">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-326">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-327">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-327">Field name</span></span>|<span data-ttu-id="a4e80-328">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-328">Data type</span></span>|<span data-ttu-id="a4e80-329">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-329">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-330">位址</span><span class="sxs-lookup"><span data-stu-id="a4e80-330">Address</span></span>|<span data-ttu-id="a4e80-331">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-331">win:UInt64</span></span>|<span data-ttu-id="a4e80-332">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-332">The address of the segment.</span></span>|
|<span data-ttu-id="a4e80-333">大小</span><span class="sxs-lookup"><span data-stu-id="a4e80-333">Size</span></span>|<span data-ttu-id="a4e80-334">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-334">win:UInt64</span></span>|<span data-ttu-id="a4e80-335">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="a4e80-335">The size of the segment.</span></span>|
|<span data-ttu-id="a4e80-336">類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-336">Type</span></span>|<span data-ttu-id="a4e80-337">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-337">win:UInt32</span></span>|<span data-ttu-id="a4e80-338">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="a4e80-338">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="a4e80-339">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="a4e80-339">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="a4e80-340">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="a4e80-340">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="a4e80-341">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-341">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-342">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-342">win:UInt16</span></span>|<span data-ttu-id="a4e80-343">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-343">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="a4e80-344">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="a4e80-344">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="a4e80-345">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="a4e80-345">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="a4e80-346">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-346">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="a4e80-347">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-347">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-348">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-348">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-349">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-349">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-350">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-350">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-351">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-351">Informational (4)</span></span>|

<span data-ttu-id="a4e80-352">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-352">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-353">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-353">Event</span></span>|<span data-ttu-id="a4e80-354">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-354">Event ID</span></span>|<span data-ttu-id="a4e80-355">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="a4e80-356">6</span><span class="sxs-lookup"><span data-stu-id="a4e80-356">6</span></span>|<span data-ttu-id="a4e80-357">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="a4e80-357">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="a4e80-358">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-358">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-359">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-359">Field name</span></span>|<span data-ttu-id="a4e80-360">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-360">Data type</span></span>|<span data-ttu-id="a4e80-361">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-361">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-362">位址</span><span class="sxs-lookup"><span data-stu-id="a4e80-362">Address</span></span>|<span data-ttu-id="a4e80-363">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-363">win:UInt64</span></span>|<span data-ttu-id="a4e80-364">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-364">The address of the segment.</span></span>|
|<span data-ttu-id="a4e80-365">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-365">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-366">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-366">win:UInt16</span></span>|<span data-ttu-id="a4e80-367">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-367">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="a4e80-368">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-368">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="a4e80-369">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-369">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-370">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-370">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-371">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-371">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-372">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-372">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-373">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-373">Informational (4)</span></span>|

<span data-ttu-id="a4e80-374">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-374">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-375">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-375">Event</span></span>|<span data-ttu-id="a4e80-376">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-376">Event ID</span></span>|<span data-ttu-id="a4e80-377">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-377">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="a4e80-378">7</span><span class="sxs-lookup"><span data-stu-id="a4e80-378">7</span></span>|<span data-ttu-id="a4e80-379">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="a4e80-379">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="a4e80-380">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-380">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="a4e80-381">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-381">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="a4e80-382">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-382">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-383">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-383">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-384">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-384">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-385">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-385">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-386">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-386">Informational (4)</span></span>|

<span data-ttu-id="a4e80-387">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-387">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-388">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-388">Event</span></span>|<span data-ttu-id="a4e80-389">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-389">Event Id</span></span>|<span data-ttu-id="a4e80-390">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-390">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="a4e80-391">3</span><span class="sxs-lookup"><span data-stu-id="a4e80-391">3</span></span>|<span data-ttu-id="a4e80-392">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="a4e80-392">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="a4e80-393">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-393">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="a4e80-394">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-394">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="a4e80-395">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-395">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-396">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-396">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-397">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-397">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-398">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-398">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-399">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-399">Informational (4)</span></span>|

<span data-ttu-id="a4e80-400">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-400">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-401">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-401">Event</span></span>|<span data-ttu-id="a4e80-402">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-402">Event ID</span></span>|<span data-ttu-id="a4e80-403">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-403">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="a4e80-404">9</span><span class="sxs-lookup"><span data-stu-id="a4e80-404">9</span></span>|<span data-ttu-id="a4e80-405">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="a4e80-405">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="a4e80-406">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-406">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-407">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-407">Field name</span></span>|<span data-ttu-id="a4e80-408">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-408">Data type</span></span>|<span data-ttu-id="a4e80-409">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-409">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-410">原因</span><span class="sxs-lookup"><span data-stu-id="a4e80-410">Reason</span></span>|<span data-ttu-id="a4e80-411">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-411">win:UInt16</span></span>|<span data-ttu-id="a4e80-412">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="a4e80-412">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="a4e80-413">0x1 - 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-413">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="a4e80-414">0x2 - 應用程式定義域關閉。</span><span class="sxs-lookup"><span data-stu-id="a4e80-414">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="a4e80-415">0x3 - 推銷程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4e80-415">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="a4e80-416">0x4 - 關機。</span><span class="sxs-lookup"><span data-stu-id="a4e80-416">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="a4e80-417">0x5 - 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a4e80-417">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="a4e80-418">0x6 - 準備進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a4e80-418">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="a4e80-419">Count</span><span class="sxs-lookup"><span data-stu-id="a4e80-419">Count</span></span>|<span data-ttu-id="a4e80-420">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-420">win:UInt32</span></span>|<span data-ttu-id="a4e80-421">該時間的 GC 計數。</span><span class="sxs-lookup"><span data-stu-id="a4e80-421">The GC count at the time.</span></span> <span data-ttu-id="a4e80-422">通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。</span><span class="sxs-lookup"><span data-stu-id="a4e80-422">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="a4e80-423">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-423">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-424">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-424">win:UInt16</span></span>|<span data-ttu-id="a4e80-425">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-425">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="a4e80-426">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-426">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="a4e80-427">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-427">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-428">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-428">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-429">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-429">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-431">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-431">Informational (4)</span></span>|

<span data-ttu-id="a4e80-432">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-432">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-433">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-433">Event</span></span>|<span data-ttu-id="a4e80-434">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-434">Event ID</span></span>|<span data-ttu-id="a4e80-435">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-435">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="a4e80-436">8</span><span class="sxs-lookup"><span data-stu-id="a4e80-436">8</span></span>|<span data-ttu-id="a4e80-437">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="a4e80-437">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="a4e80-438">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-438">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="a4e80-439">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-439">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="a4e80-440">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-440">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-441">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-441">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-442">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-442">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-443">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-443">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-444">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-444">Informational (4)</span></span>|

<span data-ttu-id="a4e80-445">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-445">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-446">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-446">Event</span></span>|<span data-ttu-id="a4e80-447">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-447">Event ID</span></span>|<span data-ttu-id="a4e80-448">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-448">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="a4e80-449">10</span><span class="sxs-lookup"><span data-stu-id="a4e80-449">10</span></span>|<span data-ttu-id="a4e80-450">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="a4e80-450">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="a4e80-451">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-451">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-452">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-452">Field name</span></span>|<span data-ttu-id="a4e80-453">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-453">Data type</span></span>|<span data-ttu-id="a4e80-454">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-454">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-455">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="a4e80-455">AllocationAmount</span></span>|<span data-ttu-id="a4e80-456">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-456">win:UInt32</span></span>|<span data-ttu-id="a4e80-457">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-457">The allocation size, in bytes.</span></span> <span data-ttu-id="a4e80-458">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-458">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="a4e80-459">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="a4e80-459">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="a4e80-460">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-460">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="a4e80-461">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="a4e80-461">AllocationKind</span></span>|<span data-ttu-id="a4e80-462">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-462">win:UInt32</span></span>|<span data-ttu-id="a4e80-463">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-463">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="a4e80-464">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-464">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="a4e80-465">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-465">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-466">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-466">win:UInt16</span></span>|<span data-ttu-id="a4e80-467">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-467">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="a4e80-468">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="a4e80-468">AllocationAmount64</span></span>|<span data-ttu-id="a4e80-469">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-469">win:UInt64</span></span>|<span data-ttu-id="a4e80-470">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-470">The allocation size, in bytes.</span></span> <span data-ttu-id="a4e80-471">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="a4e80-471">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="a4e80-472">TypeId</span><span class="sxs-lookup"><span data-stu-id="a4e80-472">TypeId</span></span>|<span data-ttu-id="a4e80-473">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="a4e80-473">win:Pointer</span></span>|<span data-ttu-id="a4e80-474">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-474">The address of the MethodTable.</span></span> <span data-ttu-id="a4e80-475">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-475">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a4e80-476">TypeName</span><span class="sxs-lookup"><span data-stu-id="a4e80-476">TypeName</span></span>|<span data-ttu-id="a4e80-477">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a4e80-477">win:UnicodeString</span></span>|<span data-ttu-id="a4e80-478">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e80-478">The name of the type that was allocated.</span></span> <span data-ttu-id="a4e80-479">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="a4e80-479">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a4e80-480">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="a4e80-480">HeapIndex</span></span>|<span data-ttu-id="a4e80-481">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-481">win:UInt32</span></span>|<span data-ttu-id="a4e80-482">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-482">The heap where the object was allocated.</span></span> <span data-ttu-id="a4e80-483">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-483">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="a4e80-484">GCAllocationTick_V3 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-484">GCAllocationTick_V3 Event</span></span>

<span data-ttu-id="a4e80-485">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-485">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-486">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-486">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-487">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-487">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-488">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-488">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-489">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-489">Informational (4)</span></span>|

<span data-ttu-id="a4e80-490">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-490">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-491">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-491">Event</span></span>|<span data-ttu-id="a4e80-492">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-492">Event ID</span></span>|<span data-ttu-id="a4e80-493">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-493">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="a4e80-494">10</span><span class="sxs-lookup"><span data-stu-id="a4e80-494">10</span></span>|<span data-ttu-id="a4e80-495">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="a4e80-495">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="a4e80-496">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-496">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-497">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-497">Field name</span></span>|<span data-ttu-id="a4e80-498">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-498">Data type</span></span>|<span data-ttu-id="a4e80-499">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-499">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-500">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="a4e80-500">AllocationAmount</span></span>|<span data-ttu-id="a4e80-501">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-501">win:UInt32</span></span>|<span data-ttu-id="a4e80-502">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-502">The allocation size, in bytes.</span></span> <span data-ttu-id="a4e80-503">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-503">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="a4e80-504">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="a4e80-504">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="a4e80-505">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-505">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="a4e80-506">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="a4e80-506">AllocationKind</span></span>|<span data-ttu-id="a4e80-507">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-507">win:UInt32</span></span>|<span data-ttu-id="a4e80-508">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-508">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="a4e80-509">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-509">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="a4e80-510">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-510">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-511">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-511">win:UInt16</span></span>|<span data-ttu-id="a4e80-512">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-512">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="a4e80-513">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="a4e80-513">AllocationAmount64</span></span>|<span data-ttu-id="a4e80-514">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a4e80-514">win:UInt64</span></span>|<span data-ttu-id="a4e80-515">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-515">The allocation size, in bytes.</span></span> <span data-ttu-id="a4e80-516">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="a4e80-516">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="a4e80-517">TypeId</span><span class="sxs-lookup"><span data-stu-id="a4e80-517">TypeId</span></span>|<span data-ttu-id="a4e80-518">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="a4e80-518">win:Pointer</span></span>|<span data-ttu-id="a4e80-519">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-519">The address of the MethodTable.</span></span> <span data-ttu-id="a4e80-520">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-520">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a4e80-521">TypeName</span><span class="sxs-lookup"><span data-stu-id="a4e80-521">TypeName</span></span>|<span data-ttu-id="a4e80-522">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a4e80-522">win:UnicodeString</span></span>|<span data-ttu-id="a4e80-523">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e80-523">The name of the type that was allocated.</span></span> <span data-ttu-id="a4e80-524">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="a4e80-524">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="a4e80-525">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="a4e80-525">HeapIndex</span></span>|<span data-ttu-id="a4e80-526">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-526">win:UInt32</span></span>|<span data-ttu-id="a4e80-527">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="a4e80-527">The heap where the object was allocated.</span></span> <span data-ttu-id="a4e80-528">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="a4e80-528">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|<span data-ttu-id="a4e80-529">位址</span><span class="sxs-lookup"><span data-stu-id="a4e80-529">Address</span></span>|<span data-ttu-id="a4e80-530">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="a4e80-530">win:Pointer</span></span>|<span data-ttu-id="a4e80-531">最後設定物件的位址。</span><span class="sxs-lookup"><span data-stu-id="a4e80-531">The address of the last allocated object.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="a4e80-532">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-532">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="a4e80-533">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-533">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-534">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-534">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-535">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-535">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-536">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-536">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-537">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-537">Informational (4)</span></span>|

<span data-ttu-id="a4e80-538">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-538">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-539">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-539">Event</span></span>|<span data-ttu-id="a4e80-540">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-540">Event ID</span></span>|<span data-ttu-id="a4e80-541">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-541">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="a4e80-542">14</span><span class="sxs-lookup"><span data-stu-id="a4e80-542">14</span></span>|<span data-ttu-id="a4e80-543">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="a4e80-543">The start of running finalizers.</span></span>|

<span data-ttu-id="a4e80-544">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-544">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="a4e80-545">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-545">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="a4e80-546">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-546">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-547">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-547">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-548">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-548">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-549">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-549">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-550">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-550">Informational (4)</span></span>|

<span data-ttu-id="a4e80-551">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-551">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-552">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-552">Event</span></span>|<span data-ttu-id="a4e80-553">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-553">Event ID</span></span>|<span data-ttu-id="a4e80-554">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-554">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="a4e80-555">13</span><span class="sxs-lookup"><span data-stu-id="a4e80-555">13</span></span>|<span data-ttu-id="a4e80-556">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="a4e80-556">The end of running finalizers.</span></span>|

<span data-ttu-id="a4e80-557">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="a4e80-557">The following table shows the event data:</span></span>

|<span data-ttu-id="a4e80-558">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a4e80-558">Field name</span></span>|<span data-ttu-id="a4e80-559">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4e80-559">Data type</span></span>|<span data-ttu-id="a4e80-560">描述</span><span class="sxs-lookup"><span data-stu-id="a4e80-560">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a4e80-561">Count</span><span class="sxs-lookup"><span data-stu-id="a4e80-561">Count</span></span>|<span data-ttu-id="a4e80-562">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a4e80-562">win:UInt32</span></span>|<span data-ttu-id="a4e80-563">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="a4e80-563">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="a4e80-564">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a4e80-564">ClrInstanceID</span></span>|<span data-ttu-id="a4e80-565">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a4e80-565">win:UInt16</span></span>|<span data-ttu-id="a4e80-566">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a4e80-566">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="a4e80-567">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-567">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="a4e80-568">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-568">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-569">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-569">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-570">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-570">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-571">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-571">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-572">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-572">Informational (4)</span></span>|
|<span data-ttu-id="a4e80-573">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a4e80-573">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a4e80-574">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-574">Informational (4)</span></span>|

<span data-ttu-id="a4e80-575">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-575">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-576">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-576">Event</span></span>|<span data-ttu-id="a4e80-577">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-577">Event ID</span></span>|<span data-ttu-id="a4e80-578">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-578">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="a4e80-579">11</span><span class="sxs-lookup"><span data-stu-id="a4e80-579">11</span></span>|<span data-ttu-id="a4e80-580">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="a4e80-580">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="a4e80-581">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-581">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="a4e80-582">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-582">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="a4e80-583">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="a4e80-583">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a4e80-584">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4e80-584">Keyword for raising the event</span></span>|<span data-ttu-id="a4e80-585">層級</span><span class="sxs-lookup"><span data-stu-id="a4e80-585">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a4e80-586">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="a4e80-586">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="a4e80-587">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-587">Informational (4)</span></span>|
|<span data-ttu-id="a4e80-588">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a4e80-588">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a4e80-589">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="a4e80-589">Informational (4)</span></span>|

<span data-ttu-id="a4e80-590">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="a4e80-590">The following table shows the event information:</span></span>

|<span data-ttu-id="a4e80-591">事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-591">Event</span></span>|<span data-ttu-id="a4e80-592">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4e80-592">Event ID</span></span>|<span data-ttu-id="a4e80-593">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a4e80-593">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="a4e80-594">12</span><span class="sxs-lookup"><span data-stu-id="a4e80-594">12</span></span>|<span data-ttu-id="a4e80-595">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="a4e80-595">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="a4e80-596">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="a4e80-596">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4e80-597">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4e80-597">See also</span></span>

- [<span data-ttu-id="a4e80-598">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="a4e80-598">CLR ETW Events</span></span>](clr-etw-events.md)
