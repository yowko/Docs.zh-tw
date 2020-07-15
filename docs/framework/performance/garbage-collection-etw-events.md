---
title: 記憶體回收 ETW 事件
description: 查看垃圾收集 ETW 事件的詳細資訊。 涵蓋的事件包括 GCStart_V1、GCEnd_V1、GCHeapStats_V1、GCCreateSegment_V1 等等。
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309738"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0addc-104">記憶體回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="0addc-105">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0addc-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0addc-106">它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。</span><span class="sxs-lookup"><span data-stu-id="0addc-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="0addc-107">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="0addc-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="0addc-108">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="0addc-109">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="0addc-110">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="0addc-111">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="0addc-112">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="0addc-113">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="0addc-114">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="0addc-115">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="0addc-116">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="0addc-117">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="0addc-118">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="0addc-119">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="0addc-120">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="0addc-121">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="0addc-122">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="0addc-123">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="0addc-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="0addc-124">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0addc-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="0addc-125">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-125">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-126">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-127">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-128">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-128">Informational (4)</span></span>|

<span data-ttu-id="0addc-129">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-129">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-130">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-130">Event</span></span>|<span data-ttu-id="0addc-131">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-131">Event ID</span></span>|<span data-ttu-id="0addc-132">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="0addc-133">1</span><span class="sxs-lookup"><span data-stu-id="0addc-133">1</span></span>|<span data-ttu-id="0addc-134">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-134">A garbage collection has started.</span></span>|

<span data-ttu-id="0addc-135">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-135">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-136">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-136">Field name</span></span>|<span data-ttu-id="0addc-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-137">Data type</span></span>|<span data-ttu-id="0addc-138">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-139">計數</span><span class="sxs-lookup"><span data-stu-id="0addc-139">Count</span></span>|<span data-ttu-id="0addc-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-140">win:UInt32</span></span>|<span data-ttu-id="0addc-141">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0addc-142">深度</span><span class="sxs-lookup"><span data-stu-id="0addc-142">Depth</span></span>|<span data-ttu-id="0addc-143">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-143">win:UInt32</span></span>|<span data-ttu-id="0addc-144">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="0addc-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="0addc-145">原因</span><span class="sxs-lookup"><span data-stu-id="0addc-145">Reason</span></span>|<span data-ttu-id="0addc-146">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-146">win:UInt32</span></span>|<span data-ttu-id="0addc-147">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="0addc-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0addc-148">0x0 - 小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="0addc-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0addc-149">0x1 - 已引起。</span><span class="sxs-lookup"><span data-stu-id="0addc-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0addc-150">0x2 - 記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="0addc-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0addc-151">0x3 - 空白。</span><span class="sxs-lookup"><span data-stu-id="0addc-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0addc-152">0x4 - 大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="0addc-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0addc-153">0x5 - 空間不足 (針對小型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="0addc-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0addc-154">0x6 - 空間不足 (針對大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="0addc-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0addc-155">0x7 - 已引起，但不強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="0addc-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="0addc-156">類型</span><span class="sxs-lookup"><span data-stu-id="0addc-156">Type</span></span>|<span data-ttu-id="0addc-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-157">win:UInt32</span></span>|<span data-ttu-id="0addc-158">0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0addc-159">0x1 - 背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0addc-160">0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="0addc-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-161">ClrInstanceID</span></span>|<span data-ttu-id="0addc-162">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-162">win:UInt16</span></span>|<span data-ttu-id="0addc-163">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="0addc-164">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="0addc-165">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-166">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-167">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-168">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-169">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-169">Informational (4)</span></span>|

<span data-ttu-id="0addc-170">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-170">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-171">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-171">Event</span></span>|<span data-ttu-id="0addc-172">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-172">Event ID</span></span>|<span data-ttu-id="0addc-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="0addc-174">2</span><span class="sxs-lookup"><span data-stu-id="0addc-174">2</span></span>|<span data-ttu-id="0addc-175">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="0addc-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="0addc-176">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-176">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-177">Field name</span></span>|<span data-ttu-id="0addc-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-178">Data type</span></span>|<span data-ttu-id="0addc-179">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-180">計數</span><span class="sxs-lookup"><span data-stu-id="0addc-180">Count</span></span>|<span data-ttu-id="0addc-181">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-181">win:UInt32</span></span>|<span data-ttu-id="0addc-182">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0addc-183">深度</span><span class="sxs-lookup"><span data-stu-id="0addc-183">Depth</span></span>|<span data-ttu-id="0addc-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-184">win:UInt32</span></span>|<span data-ttu-id="0addc-185">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="0addc-185">The generation that was collected.</span></span>|
|<span data-ttu-id="0addc-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-186">ClrInstanceID</span></span>|<span data-ttu-id="0addc-187">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-187">win:UInt16</span></span>|<span data-ttu-id="0addc-188">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="0addc-189">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="0addc-190">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-191">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-191">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-192">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-194">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-194">Informational (4)</span></span>|

<span data-ttu-id="0addc-195">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-195">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-196">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-196">Event</span></span>|<span data-ttu-id="0addc-197">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-197">Event ID</span></span>|<span data-ttu-id="0addc-198">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="0addc-199">4</span><span class="sxs-lookup"><span data-stu-id="0addc-199">4</span></span>|<span data-ttu-id="0addc-200">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="0addc-201">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-201">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-202">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-202">Field name</span></span>|<span data-ttu-id="0addc-203">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-203">Data type</span></span>|<span data-ttu-id="0addc-204">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0addc-205">GenerationSize0</span></span>|<span data-ttu-id="0addc-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-206">win:UInt64</span></span>|<span data-ttu-id="0addc-207">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="0addc-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0addc-208">TotalPromotedSize0</span></span>|<span data-ttu-id="0addc-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-209">win:UInt64</span></span>|<span data-ttu-id="0addc-210">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="0addc-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0addc-211">GenerationSize1</span></span>|<span data-ttu-id="0addc-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-212">win:UInt64</span></span>|<span data-ttu-id="0addc-213">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="0addc-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0addc-214">TotalPromotedSize1</span></span>|<span data-ttu-id="0addc-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-215">win:UInt64</span></span>|<span data-ttu-id="0addc-216">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="0addc-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0addc-217">GenerationSize2</span></span>|<span data-ttu-id="0addc-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-218">win:UInt64</span></span>|<span data-ttu-id="0addc-219">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="0addc-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0addc-220">TotalPromotedSize2</span></span>|<span data-ttu-id="0addc-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-221">win:UInt64</span></span>|<span data-ttu-id="0addc-222">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="0addc-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0addc-223">GenerationSize3</span></span>|<span data-ttu-id="0addc-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-224">win:UInt64</span></span>|<span data-ttu-id="0addc-225">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="0addc-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0addc-226">TotalPromotedSize3</span></span>|<span data-ttu-id="0addc-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-227">win:UInt64</span></span>|<span data-ttu-id="0addc-228">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="0addc-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0addc-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="0addc-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-230">win:UInt64</span></span>|<span data-ttu-id="0addc-231">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0addc-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="0addc-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="0addc-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-233">win:UInt64</span></span>|<span data-ttu-id="0addc-234">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0addc-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0addc-235">PinnedObjectCount</span></span>|<span data-ttu-id="0addc-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-236">win:UInt32</span></span>|<span data-ttu-id="0addc-237">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="0addc-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0addc-238">SinkBlockCount</span></span>|<span data-ttu-id="0addc-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-239">win:UInt32</span></span>|<span data-ttu-id="0addc-240">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="0addc-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0addc-241">GCHandleCount</span></span>|<span data-ttu-id="0addc-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-242">win:UInt32</span></span>|<span data-ttu-id="0addc-243">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="0addc-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-244">ClrInstanceID</span></span>|<span data-ttu-id="0addc-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-245">win:UInt16</span></span>|<span data-ttu-id="0addc-246">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="0addc-247">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="0addc-248">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-249">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-249">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-250">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-251">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-252">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-252">Informational (4)</span></span>|

<span data-ttu-id="0addc-253">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-253">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-254">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-254">Event</span></span>|<span data-ttu-id="0addc-255">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-255">Event ID</span></span>|<span data-ttu-id="0addc-256">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="0addc-257">5</span><span class="sxs-lookup"><span data-stu-id="0addc-257">5</span></span>|<span data-ttu-id="0addc-258">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="0addc-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0addc-259">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="0addc-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="0addc-260">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-260">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-261">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-261">Field name</span></span>|<span data-ttu-id="0addc-262">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-262">Data type</span></span>|<span data-ttu-id="0addc-263">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-264">位址</span><span class="sxs-lookup"><span data-stu-id="0addc-264">Address</span></span>|<span data-ttu-id="0addc-265">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-265">win:UInt64</span></span>|<span data-ttu-id="0addc-266">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="0addc-266">The address of the segment.</span></span>|
|<span data-ttu-id="0addc-267">大小</span><span class="sxs-lookup"><span data-stu-id="0addc-267">Size</span></span>|<span data-ttu-id="0addc-268">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-268">win:UInt64</span></span>|<span data-ttu-id="0addc-269">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="0addc-269">The size of the segment.</span></span>|
|<span data-ttu-id="0addc-270">類型</span><span class="sxs-lookup"><span data-stu-id="0addc-270">Type</span></span>|<span data-ttu-id="0addc-271">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-271">win:UInt32</span></span>|<span data-ttu-id="0addc-272">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="0addc-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0addc-273">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="0addc-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0addc-274">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="0addc-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="0addc-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-275">ClrInstanceID</span></span>|<span data-ttu-id="0addc-276">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-276">win:UInt16</span></span>|<span data-ttu-id="0addc-277">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="0addc-278">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="0addc-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0addc-279">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="0addc-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="0addc-280">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="0addc-281">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-282">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-282">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-283">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-284">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-285">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-285">Informational (4)</span></span>|

<span data-ttu-id="0addc-286">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-286">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-287">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-287">Event</span></span>|<span data-ttu-id="0addc-288">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-288">Event ID</span></span>|<span data-ttu-id="0addc-289">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="0addc-290">6</span><span class="sxs-lookup"><span data-stu-id="0addc-290">6</span></span>|<span data-ttu-id="0addc-291">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="0addc-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="0addc-292">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-292">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-293">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-293">Field name</span></span>|<span data-ttu-id="0addc-294">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-294">Data type</span></span>|<span data-ttu-id="0addc-295">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-296">位址</span><span class="sxs-lookup"><span data-stu-id="0addc-296">Address</span></span>|<span data-ttu-id="0addc-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-297">win:UInt64</span></span>|<span data-ttu-id="0addc-298">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="0addc-298">The address of the segment.</span></span>|
|<span data-ttu-id="0addc-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-299">ClrInstanceID</span></span>|<span data-ttu-id="0addc-300">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-300">win:UInt16</span></span>|<span data-ttu-id="0addc-301">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="0addc-302">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="0addc-303">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-304">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-304">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-305">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-306">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-307">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-307">Informational (4)</span></span>|

<span data-ttu-id="0addc-308">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-308">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-309">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-309">Event</span></span>|<span data-ttu-id="0addc-310">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-310">Event ID</span></span>|<span data-ttu-id="0addc-311">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="0addc-312">7</span><span class="sxs-lookup"><span data-stu-id="0addc-312">7</span></span>|<span data-ttu-id="0addc-313">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="0addc-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="0addc-314">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="0addc-315">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="0addc-316">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-317">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-317">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-318">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-319">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-320">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-320">Informational (4)</span></span>|

<span data-ttu-id="0addc-321">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-321">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-322">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-322">Event</span></span>|<span data-ttu-id="0addc-323">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-323">Event Id</span></span>|<span data-ttu-id="0addc-324">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="0addc-325">3</span><span class="sxs-lookup"><span data-stu-id="0addc-325">3</span></span>|<span data-ttu-id="0addc-326">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="0addc-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="0addc-327">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="0addc-328">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="0addc-329">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-330">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-330">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-331">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-332">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-333">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-333">Informational (4)</span></span>|

<span data-ttu-id="0addc-334">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-334">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-335">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-335">Event</span></span>|<span data-ttu-id="0addc-336">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-336">Event ID</span></span>|<span data-ttu-id="0addc-337">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="0addc-338">9</span><span class="sxs-lookup"><span data-stu-id="0addc-338">9</span></span>|<span data-ttu-id="0addc-339">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="0addc-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0addc-340">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-340">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-341">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-341">Field name</span></span>|<span data-ttu-id="0addc-342">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-342">Data type</span></span>|<span data-ttu-id="0addc-343">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-344">原因</span><span class="sxs-lookup"><span data-stu-id="0addc-344">Reason</span></span>|<span data-ttu-id="0addc-345">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-345">win:UInt16</span></span>|<span data-ttu-id="0addc-346">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="0addc-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0addc-347">0x1 - 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0addc-348">0x2 - 應用程式定義域關閉。</span><span class="sxs-lookup"><span data-stu-id="0addc-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0addc-349">0x3 - 推銷程式碼。</span><span class="sxs-lookup"><span data-stu-id="0addc-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0addc-350">0x4 - 關機。</span><span class="sxs-lookup"><span data-stu-id="0addc-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0addc-351">0x5 - 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0addc-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0addc-352">0x6 - 準備進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0addc-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="0addc-353">計數</span><span class="sxs-lookup"><span data-stu-id="0addc-353">Count</span></span>|<span data-ttu-id="0addc-354">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-354">win:UInt32</span></span>|<span data-ttu-id="0addc-355">該時間的 GC 計數。</span><span class="sxs-lookup"><span data-stu-id="0addc-355">The GC count at the time.</span></span> <span data-ttu-id="0addc-356">通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。</span><span class="sxs-lookup"><span data-stu-id="0addc-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="0addc-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-357">ClrInstanceID</span></span>|<span data-ttu-id="0addc-358">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-358">win:UInt16</span></span>|<span data-ttu-id="0addc-359">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="0addc-360">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="0addc-361">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-362">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-362">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-363">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-364">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-365">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-365">Informational (4)</span></span>|

<span data-ttu-id="0addc-366">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-366">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-367">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-367">Event</span></span>|<span data-ttu-id="0addc-368">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-368">Event ID</span></span>|<span data-ttu-id="0addc-369">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0addc-370">8</span><span class="sxs-lookup"><span data-stu-id="0addc-370">8</span></span>|<span data-ttu-id="0addc-371">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="0addc-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0addc-372">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="0addc-373">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="0addc-374">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-375">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-375">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-376">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-377">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-378">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-378">Informational (4)</span></span>|

<span data-ttu-id="0addc-379">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-379">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-380">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-380">Event</span></span>|<span data-ttu-id="0addc-381">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-381">Event ID</span></span>|<span data-ttu-id="0addc-382">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="0addc-383">10</span><span class="sxs-lookup"><span data-stu-id="0addc-383">10</span></span>|<span data-ttu-id="0addc-384">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="0addc-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="0addc-385">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-385">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-386">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-386">Field name</span></span>|<span data-ttu-id="0addc-387">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-387">Data type</span></span>|<span data-ttu-id="0addc-388">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0addc-389">AllocationAmount</span></span>|<span data-ttu-id="0addc-390">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-390">win:UInt32</span></span>|<span data-ttu-id="0addc-391">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="0addc-391">The allocation size, in bytes.</span></span> <span data-ttu-id="0addc-392">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="0addc-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0addc-393">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="0addc-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0addc-394">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="0addc-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="0addc-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0addc-395">AllocationKind</span></span>|<span data-ttu-id="0addc-396">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-396">win:UInt32</span></span>|<span data-ttu-id="0addc-397">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="0addc-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0addc-398">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="0addc-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="0addc-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-399">ClrInstanceID</span></span>|<span data-ttu-id="0addc-400">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-400">win:UInt16</span></span>|<span data-ttu-id="0addc-401">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="0addc-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0addc-402">AllocationAmount64</span></span>|<span data-ttu-id="0addc-403">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0addc-403">win:UInt64</span></span>|<span data-ttu-id="0addc-404">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="0addc-404">The allocation size, in bytes.</span></span> <span data-ttu-id="0addc-405">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="0addc-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="0addc-406">TypeId</span><span class="sxs-lookup"><span data-stu-id="0addc-406">TypeId</span></span>|<span data-ttu-id="0addc-407">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="0addc-407">win:Pointer</span></span>|<span data-ttu-id="0addc-408">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="0addc-408">The address of the MethodTable.</span></span> <span data-ttu-id="0addc-409">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="0addc-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0addc-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="0addc-410">TypeName</span></span>|<span data-ttu-id="0addc-411">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0addc-411">win:UnicodeString</span></span>|<span data-ttu-id="0addc-412">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="0addc-412">The name of the type that was allocated.</span></span> <span data-ttu-id="0addc-413">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="0addc-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0addc-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0addc-414">HeapIndex</span></span>|<span data-ttu-id="0addc-415">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-415">win:UInt32</span></span>|<span data-ttu-id="0addc-416">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="0addc-416">The heap where the object was allocated.</span></span> <span data-ttu-id="0addc-417">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="0addc-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="0addc-418">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="0addc-419">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-420">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-420">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-421">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-422">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-423">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-423">Informational (4)</span></span>|

<span data-ttu-id="0addc-424">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-424">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-425">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-425">Event</span></span>|<span data-ttu-id="0addc-426">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-426">Event ID</span></span>|<span data-ttu-id="0addc-427">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="0addc-428">14</span><span class="sxs-lookup"><span data-stu-id="0addc-428">14</span></span>|<span data-ttu-id="0addc-429">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="0addc-429">The start of running finalizers.</span></span>|

<span data-ttu-id="0addc-430">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="0addc-431">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="0addc-432">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-433">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-433">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-434">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-435">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-436">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-436">Informational (4)</span></span>|

<span data-ttu-id="0addc-437">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-437">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-438">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-438">Event</span></span>|<span data-ttu-id="0addc-439">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-439">Event ID</span></span>|<span data-ttu-id="0addc-440">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="0addc-441">13</span><span class="sxs-lookup"><span data-stu-id="0addc-441">13</span></span>|<span data-ttu-id="0addc-442">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="0addc-442">The end of running finalizers.</span></span>|

<span data-ttu-id="0addc-443">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="0addc-443">The following table shows the event data:</span></span>

|<span data-ttu-id="0addc-444">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0addc-444">Field name</span></span>|<span data-ttu-id="0addc-445">資料類型</span><span class="sxs-lookup"><span data-stu-id="0addc-445">Data type</span></span>|<span data-ttu-id="0addc-446">描述</span><span class="sxs-lookup"><span data-stu-id="0addc-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0addc-447">計數</span><span class="sxs-lookup"><span data-stu-id="0addc-447">Count</span></span>|<span data-ttu-id="0addc-448">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0addc-448">win:UInt32</span></span>|<span data-ttu-id="0addc-449">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="0addc-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="0addc-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0addc-450">ClrInstanceID</span></span>|<span data-ttu-id="0addc-451">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0addc-451">win:UInt16</span></span>|<span data-ttu-id="0addc-452">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="0addc-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="0addc-453">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0addc-454">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-455">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-455">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-456">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-457">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-458">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-458">Informational (4)</span></span>|
|<span data-ttu-id="0addc-459">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0addc-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0addc-460">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-460">Informational (4)</span></span>|

<span data-ttu-id="0addc-461">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-461">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-462">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-462">Event</span></span>|<span data-ttu-id="0addc-463">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-463">Event ID</span></span>|<span data-ttu-id="0addc-464">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0addc-465">11</span><span class="sxs-lookup"><span data-stu-id="0addc-465">11</span></span>|<span data-ttu-id="0addc-466">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="0addc-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="0addc-467">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="0addc-468">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0addc-469">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="0addc-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0addc-470">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0addc-470">Keyword for raising the event</span></span>|<span data-ttu-id="0addc-471">層級</span><span class="sxs-lookup"><span data-stu-id="0addc-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0addc-472">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0addc-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0addc-473">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-473">Informational (4)</span></span>|
|<span data-ttu-id="0addc-474">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0addc-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0addc-475">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="0addc-475">Informational (4)</span></span>|

<span data-ttu-id="0addc-476">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="0addc-476">The following table shows the event information:</span></span>

|<span data-ttu-id="0addc-477">事件</span><span class="sxs-lookup"><span data-stu-id="0addc-477">Event</span></span>|<span data-ttu-id="0addc-478">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0addc-478">Event ID</span></span>|<span data-ttu-id="0addc-479">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0addc-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0addc-480">12</span><span class="sxs-lookup"><span data-stu-id="0addc-480">12</span></span>|<span data-ttu-id="0addc-481">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="0addc-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="0addc-482">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="0addc-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="0addc-483">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0addc-483">See also</span></span>

- [<span data-ttu-id="0addc-484">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0addc-484">CLR ETW Events</span></span>](clr-etw-events.md)
