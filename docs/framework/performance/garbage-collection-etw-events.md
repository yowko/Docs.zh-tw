---
title: 記憶體回收 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040575"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="b77b7-102">記憶體回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="b77b7-103">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b77b7-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="b77b7-104">它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。</span><span class="sxs-lookup"><span data-stu-id="b77b7-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="b77b7-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="b77b7-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="b77b7-106">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="b77b7-107">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="b77b7-108">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="b77b7-109">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="b77b7-110">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="b77b7-111">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="b77b7-112">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="b77b7-113">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="b77b7-114">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="b77b7-115">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="b77b7-116">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="b77b7-117">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="b77b7-118">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="b77b7-119">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="b77b7-120">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="b77b7-121">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="b77b7-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="b77b7-122">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="b77b7-123">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-123">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-124">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-126">Informational (4)</span></span>|

<span data-ttu-id="b77b7-127">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-127">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-128">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-128">Event</span></span>|<span data-ttu-id="b77b7-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-129">Event ID</span></span>|<span data-ttu-id="b77b7-130">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="b77b7-131">1</span><span class="sxs-lookup"><span data-stu-id="b77b7-131">1</span></span>|<span data-ttu-id="b77b7-132">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-132">A garbage collection has started.</span></span>|

<span data-ttu-id="b77b7-133">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-133">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-134">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-134">Field name</span></span>|<span data-ttu-id="b77b7-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-135">Data type</span></span>|<span data-ttu-id="b77b7-136">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-137">計數</span><span class="sxs-lookup"><span data-stu-id="b77b7-137">Count</span></span>|<span data-ttu-id="b77b7-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-138">win:UInt32</span></span>|<span data-ttu-id="b77b7-139">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="b77b7-140">深度</span><span class="sxs-lookup"><span data-stu-id="b77b7-140">Depth</span></span>|<span data-ttu-id="b77b7-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-141">win:UInt32</span></span>|<span data-ttu-id="b77b7-142">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="b77b7-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="b77b7-143">原因</span><span class="sxs-lookup"><span data-stu-id="b77b7-143">Reason</span></span>|<span data-ttu-id="b77b7-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-144">win:UInt32</span></span>|<span data-ttu-id="b77b7-145">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="b77b7-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="b77b7-146">0x0 - 小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="b77b7-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="b77b7-147">0x1 - 已引起。</span><span class="sxs-lookup"><span data-stu-id="b77b7-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="b77b7-148">0x2 - 記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="b77b7-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="b77b7-149">0x3 - 空白。</span><span class="sxs-lookup"><span data-stu-id="b77b7-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="b77b7-150">0x4 - 大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="b77b7-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="b77b7-151">0x5 - 空間不足 (針對小型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="b77b7-152">0x6 - 空間不足 (針對大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="b77b7-153">0x7 - 已引起，但不強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="b77b7-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="b77b7-154">輸入</span><span class="sxs-lookup"><span data-stu-id="b77b7-154">Type</span></span>|<span data-ttu-id="b77b7-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-155">win:UInt32</span></span>|<span data-ttu-id="b77b7-156">0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="b77b7-157">0x1 - 背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="b77b7-158">0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="b77b7-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-159">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-160">win:UInt16</span></span>|<span data-ttu-id="b77b7-161">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="b77b7-162">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="b77b7-163">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-164">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-164">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-165">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-167">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-167">Informational (4)</span></span>|

<span data-ttu-id="b77b7-168">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-168">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-169">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-169">Event</span></span>|<span data-ttu-id="b77b7-170">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-170">Event ID</span></span>|<span data-ttu-id="b77b7-171">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="b77b7-172">2</span><span class="sxs-lookup"><span data-stu-id="b77b7-172">2</span></span>|<span data-ttu-id="b77b7-173">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="b77b7-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="b77b7-174">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-174">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-175">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-175">Field name</span></span>|<span data-ttu-id="b77b7-176">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-176">Data type</span></span>|<span data-ttu-id="b77b7-177">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-178">計數</span><span class="sxs-lookup"><span data-stu-id="b77b7-178">Count</span></span>|<span data-ttu-id="b77b7-179">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-179">win:UInt32</span></span>|<span data-ttu-id="b77b7-180">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="b77b7-181">深度</span><span class="sxs-lookup"><span data-stu-id="b77b7-181">Depth</span></span>|<span data-ttu-id="b77b7-182">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-182">win:UInt32</span></span>|<span data-ttu-id="b77b7-183">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="b77b7-183">The generation that was collected.</span></span>|
|<span data-ttu-id="b77b7-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-184">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-185">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-185">win:UInt16</span></span>|<span data-ttu-id="b77b7-186">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="b77b7-187">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="b77b7-188">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-189">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-189">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-190">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-192">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-192">Informational (4)</span></span>|

<span data-ttu-id="b77b7-193">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-193">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-194">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-194">Event</span></span>|<span data-ttu-id="b77b7-195">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-195">Event ID</span></span>|<span data-ttu-id="b77b7-196">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="b77b7-197">4</span><span class="sxs-lookup"><span data-stu-id="b77b7-197">4</span></span>|<span data-ttu-id="b77b7-198">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="b77b7-199">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-199">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-200">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-200">Field name</span></span>|<span data-ttu-id="b77b7-201">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-201">Data type</span></span>|<span data-ttu-id="b77b7-202">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="b77b7-203">GenerationSize0</span></span>|<span data-ttu-id="b77b7-204">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-204">win:UInt64</span></span>|<span data-ttu-id="b77b7-205">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="b77b7-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="b77b7-206">TotalPromotedSize0</span></span>|<span data-ttu-id="b77b7-207">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-207">win:UInt64</span></span>|<span data-ttu-id="b77b7-208">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="b77b7-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="b77b7-209">GenerationSize1</span></span>|<span data-ttu-id="b77b7-210">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-210">win:UInt64</span></span>|<span data-ttu-id="b77b7-211">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="b77b7-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="b77b7-212">TotalPromotedSize1</span></span>|<span data-ttu-id="b77b7-213">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-213">win:UInt64</span></span>|<span data-ttu-id="b77b7-214">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="b77b7-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="b77b7-215">GenerationSize2</span></span>|<span data-ttu-id="b77b7-216">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-216">win:UInt64</span></span>|<span data-ttu-id="b77b7-217">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="b77b7-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="b77b7-218">TotalPromotedSize2</span></span>|<span data-ttu-id="b77b7-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-219">win:UInt64</span></span>|<span data-ttu-id="b77b7-220">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="b77b7-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="b77b7-221">GenerationSize3</span></span>|<span data-ttu-id="b77b7-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-222">win:UInt64</span></span>|<span data-ttu-id="b77b7-223">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="b77b7-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="b77b7-224">TotalPromotedSize3</span></span>|<span data-ttu-id="b77b7-225">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-225">win:UInt64</span></span>|<span data-ttu-id="b77b7-226">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="b77b7-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="b77b7-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="b77b7-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-228">win:UInt64</span></span>|<span data-ttu-id="b77b7-229">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="b77b7-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="b77b7-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="b77b7-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-231">win:UInt64</span></span>|<span data-ttu-id="b77b7-232">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="b77b7-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="b77b7-233">PinnedObjectCount</span></span>|<span data-ttu-id="b77b7-234">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-234">win:UInt32</span></span>|<span data-ttu-id="b77b7-235">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="b77b7-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="b77b7-236">SinkBlockCount</span></span>|<span data-ttu-id="b77b7-237">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-237">win:UInt32</span></span>|<span data-ttu-id="b77b7-238">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="b77b7-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="b77b7-239">GCHandleCount</span></span>|<span data-ttu-id="b77b7-240">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-240">win:UInt32</span></span>|<span data-ttu-id="b77b7-241">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="b77b7-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-242">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-243">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-243">win:UInt16</span></span>|<span data-ttu-id="b77b7-244">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="b77b7-245">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="b77b7-246">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-247">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-247">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-248">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-250">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-250">Informational (4)</span></span>|

<span data-ttu-id="b77b7-251">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-251">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-252">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-252">Event</span></span>|<span data-ttu-id="b77b7-253">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-253">Event ID</span></span>|<span data-ttu-id="b77b7-254">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="b77b7-255">5</span><span class="sxs-lookup"><span data-stu-id="b77b7-255">5</span></span>|<span data-ttu-id="b77b7-256">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="b77b7-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="b77b7-257">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="b77b7-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="b77b7-258">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-258">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-259">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-259">Field name</span></span>|<span data-ttu-id="b77b7-260">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-260">Data type</span></span>|<span data-ttu-id="b77b7-261">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-262">地址</span><span class="sxs-lookup"><span data-stu-id="b77b7-262">Address</span></span>|<span data-ttu-id="b77b7-263">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-263">win:UInt64</span></span>|<span data-ttu-id="b77b7-264">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="b77b7-264">The address of the segment.</span></span>|
|<span data-ttu-id="b77b7-265">大小</span><span class="sxs-lookup"><span data-stu-id="b77b7-265">Size</span></span>|<span data-ttu-id="b77b7-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-266">win:UInt64</span></span>|<span data-ttu-id="b77b7-267">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="b77b7-267">The size of the segment.</span></span>|
|<span data-ttu-id="b77b7-268">輸入</span><span class="sxs-lookup"><span data-stu-id="b77b7-268">Type</span></span>|<span data-ttu-id="b77b7-269">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-269">win:UInt32</span></span>|<span data-ttu-id="b77b7-270">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="b77b7-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="b77b7-271">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="b77b7-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="b77b7-272">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="b77b7-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="b77b7-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-273">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-274">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-274">win:UInt16</span></span>|<span data-ttu-id="b77b7-275">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="b77b7-276">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="b77b7-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="b77b7-277">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="b77b7-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="b77b7-278">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="b77b7-279">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-280">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-280">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-281">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-283">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-283">Informational (4)</span></span>|

<span data-ttu-id="b77b7-284">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-284">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-285">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-285">Event</span></span>|<span data-ttu-id="b77b7-286">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-286">Event ID</span></span>|<span data-ttu-id="b77b7-287">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="b77b7-288">6</span><span class="sxs-lookup"><span data-stu-id="b77b7-288">6</span></span>|<span data-ttu-id="b77b7-289">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="b77b7-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="b77b7-290">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-290">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-291">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-291">Field name</span></span>|<span data-ttu-id="b77b7-292">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-292">Data type</span></span>|<span data-ttu-id="b77b7-293">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-294">地址</span><span class="sxs-lookup"><span data-stu-id="b77b7-294">Address</span></span>|<span data-ttu-id="b77b7-295">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-295">win:UInt64</span></span>|<span data-ttu-id="b77b7-296">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="b77b7-296">The address of the segment.</span></span>|
|<span data-ttu-id="b77b7-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-297">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-298">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-298">win:UInt16</span></span>|<span data-ttu-id="b77b7-299">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="b77b7-300">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="b77b7-301">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-302">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-302">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-303">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-305">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-305">Informational (4)</span></span>|

<span data-ttu-id="b77b7-306">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-306">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-307">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-307">Event</span></span>|<span data-ttu-id="b77b7-308">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-308">Event ID</span></span>|<span data-ttu-id="b77b7-309">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="b77b7-310">7</span><span class="sxs-lookup"><span data-stu-id="b77b7-310">7</span></span>|<span data-ttu-id="b77b7-311">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="b77b7-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="b77b7-312">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="b77b7-313">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="b77b7-314">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-315">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-315">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-316">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-318">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-318">Informational (4)</span></span>|

<span data-ttu-id="b77b7-319">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-319">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-320">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-320">Event</span></span>|<span data-ttu-id="b77b7-321">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-321">Event Id</span></span>|<span data-ttu-id="b77b7-322">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="b77b7-323">3</span><span class="sxs-lookup"><span data-stu-id="b77b7-323">3</span></span>|<span data-ttu-id="b77b7-324">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="b77b7-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="b77b7-325">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="b77b7-326">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="b77b7-327">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-328">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-328">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-329">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-331">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-331">Informational (4)</span></span>|

<span data-ttu-id="b77b7-332">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-332">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-333">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-333">Event</span></span>|<span data-ttu-id="b77b7-334">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-334">Event ID</span></span>|<span data-ttu-id="b77b7-335">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="b77b7-336">9</span><span class="sxs-lookup"><span data-stu-id="b77b7-336">9</span></span>|<span data-ttu-id="b77b7-337">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="b77b7-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="b77b7-338">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-338">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-339">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-339">Field name</span></span>|<span data-ttu-id="b77b7-340">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-340">Data type</span></span>|<span data-ttu-id="b77b7-341">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-342">原因</span><span class="sxs-lookup"><span data-stu-id="b77b7-342">Reason</span></span>|<span data-ttu-id="b77b7-343">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-343">win:UInt16</span></span>|<span data-ttu-id="b77b7-344">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="b77b7-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="b77b7-345">0x1 - 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="b77b7-346">0x2 - 應用程式定義域關閉。</span><span class="sxs-lookup"><span data-stu-id="b77b7-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="b77b7-347">0x3 - 推銷程式碼。</span><span class="sxs-lookup"><span data-stu-id="b77b7-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="b77b7-348">0x4 - 關機。</span><span class="sxs-lookup"><span data-stu-id="b77b7-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="b77b7-349">0x5 - 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b77b7-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="b77b7-350">0x6 - 準備進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77b7-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="b77b7-351">計數</span><span class="sxs-lookup"><span data-stu-id="b77b7-351">Count</span></span>|<span data-ttu-id="b77b7-352">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-352">win:UInt32</span></span>|<span data-ttu-id="b77b7-353">該時間的 GC 計數。</span><span class="sxs-lookup"><span data-stu-id="b77b7-353">The GC count at the time.</span></span> <span data-ttu-id="b77b7-354">通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。</span><span class="sxs-lookup"><span data-stu-id="b77b7-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="b77b7-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-355">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-356">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-356">win:UInt16</span></span>|<span data-ttu-id="b77b7-357">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="b77b7-358">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="b77b7-359">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-360">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-360">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-361">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-363">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-363">Informational (4)</span></span>|

<span data-ttu-id="b77b7-364">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-364">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-365">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-365">Event</span></span>|<span data-ttu-id="b77b7-366">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-366">Event ID</span></span>|<span data-ttu-id="b77b7-367">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="b77b7-368">8</span><span class="sxs-lookup"><span data-stu-id="b77b7-368">8</span></span>|<span data-ttu-id="b77b7-369">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="b77b7-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="b77b7-370">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="b77b7-371">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="b77b7-372">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-373">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-373">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-374">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-376">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-376">Informational (4)</span></span>|

<span data-ttu-id="b77b7-377">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-377">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-378">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-378">Event</span></span>|<span data-ttu-id="b77b7-379">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-379">Event ID</span></span>|<span data-ttu-id="b77b7-380">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="b77b7-381">10</span><span class="sxs-lookup"><span data-stu-id="b77b7-381">10</span></span>|<span data-ttu-id="b77b7-382">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="b77b7-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="b77b7-383">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-383">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-384">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-384">Field name</span></span>|<span data-ttu-id="b77b7-385">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-385">Data type</span></span>|<span data-ttu-id="b77b7-386">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="b77b7-387">AllocationAmount</span></span>|<span data-ttu-id="b77b7-388">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-388">win:UInt32</span></span>|<span data-ttu-id="b77b7-389">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-389">The allocation size, in bytes.</span></span> <span data-ttu-id="b77b7-390">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="b77b7-391">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="b77b7-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="b77b7-392">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="b77b7-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="b77b7-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="b77b7-393">AllocationKind</span></span>|<span data-ttu-id="b77b7-394">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-394">win:UInt32</span></span>|<span data-ttu-id="b77b7-395">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="b77b7-396">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="b77b7-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-397">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-398">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-398">win:UInt16</span></span>|<span data-ttu-id="b77b7-399">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="b77b7-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="b77b7-400">AllocationAmount64</span></span>|<span data-ttu-id="b77b7-401">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b77b7-401">win:UInt64</span></span>|<span data-ttu-id="b77b7-402">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-402">The allocation size, in bytes.</span></span> <span data-ttu-id="b77b7-403">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="b77b7-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="b77b7-404">TypeId</span><span class="sxs-lookup"><span data-stu-id="b77b7-404">TypeId</span></span>|<span data-ttu-id="b77b7-405">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="b77b7-405">win:Pointer</span></span>|<span data-ttu-id="b77b7-406">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="b77b7-406">The address of the MethodTable.</span></span> <span data-ttu-id="b77b7-407">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="b77b7-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="b77b7-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="b77b7-408">TypeName</span></span>|<span data-ttu-id="b77b7-409">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b77b7-409">win:UnicodeString</span></span>|<span data-ttu-id="b77b7-410">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="b77b7-410">The name of the type that was allocated.</span></span> <span data-ttu-id="b77b7-411">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="b77b7-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="b77b7-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="b77b7-412">HeapIndex</span></span>|<span data-ttu-id="b77b7-413">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-413">win:UInt32</span></span>|<span data-ttu-id="b77b7-414">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="b77b7-414">The heap where the object was allocated.</span></span> <span data-ttu-id="b77b7-415">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="b77b7-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="b77b7-416">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="b77b7-417">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-418">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-418">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-419">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-421">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-421">Informational (4)</span></span>|

<span data-ttu-id="b77b7-422">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-422">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-423">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-423">Event</span></span>|<span data-ttu-id="b77b7-424">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-424">Event ID</span></span>|<span data-ttu-id="b77b7-425">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="b77b7-426">14</span><span class="sxs-lookup"><span data-stu-id="b77b7-426">14</span></span>|<span data-ttu-id="b77b7-427">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="b77b7-427">The start of running finalizers.</span></span>|

<span data-ttu-id="b77b7-428">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="b77b7-429">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="b77b7-430">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-431">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-431">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-432">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-434">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-434">Informational (4)</span></span>|

<span data-ttu-id="b77b7-435">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-435">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-436">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-436">Event</span></span>|<span data-ttu-id="b77b7-437">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-437">Event ID</span></span>|<span data-ttu-id="b77b7-438">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="b77b7-439">13</span><span class="sxs-lookup"><span data-stu-id="b77b7-439">13</span></span>|<span data-ttu-id="b77b7-440">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="b77b7-440">The end of running finalizers.</span></span>|

<span data-ttu-id="b77b7-441">下表說明事件資料：</span><span class="sxs-lookup"><span data-stu-id="b77b7-441">The following table shows the event data:</span></span>

|<span data-ttu-id="b77b7-442">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b77b7-442">Field name</span></span>|<span data-ttu-id="b77b7-443">資料類型</span><span class="sxs-lookup"><span data-stu-id="b77b7-443">Data type</span></span>|<span data-ttu-id="b77b7-444">描述</span><span class="sxs-lookup"><span data-stu-id="b77b7-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b77b7-445">計數</span><span class="sxs-lookup"><span data-stu-id="b77b7-445">Count</span></span>|<span data-ttu-id="b77b7-446">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b77b7-446">win:UInt32</span></span>|<span data-ttu-id="b77b7-447">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="b77b7-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="b77b7-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b77b7-448">ClrInstanceID</span></span>|<span data-ttu-id="b77b7-449">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b77b7-449">win:UInt16</span></span>|<span data-ttu-id="b77b7-450">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b77b7-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="b77b7-451">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="b77b7-452">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-453">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-453">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-454">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-456">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-456">Informational (4)</span></span>|
|<span data-ttu-id="b77b7-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="b77b7-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b77b7-458">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-458">Informational (4)</span></span>|

<span data-ttu-id="b77b7-459">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-459">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-460">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-460">Event</span></span>|<span data-ttu-id="b77b7-461">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-461">Event ID</span></span>|<span data-ttu-id="b77b7-462">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="b77b7-463">11</span><span class="sxs-lookup"><span data-stu-id="b77b7-463">11</span></span>|<span data-ttu-id="b77b7-464">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="b77b7-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="b77b7-465">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="b77b7-466">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="b77b7-467">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="b77b7-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b77b7-468">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b77b7-468">Keyword for raising the event</span></span>|<span data-ttu-id="b77b7-469">層級</span><span class="sxs-lookup"><span data-stu-id="b77b7-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b77b7-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b77b7-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b77b7-471">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-471">Informational (4)</span></span>|
|<span data-ttu-id="b77b7-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="b77b7-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b77b7-473">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="b77b7-473">Informational (4)</span></span>|

<span data-ttu-id="b77b7-474">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="b77b7-474">The following table shows the event information:</span></span>

|<span data-ttu-id="b77b7-475">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-475">Event</span></span>|<span data-ttu-id="b77b7-476">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b77b7-476">Event ID</span></span>|<span data-ttu-id="b77b7-477">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b77b7-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="b77b7-478">12</span><span class="sxs-lookup"><span data-stu-id="b77b7-478">12</span></span>|<span data-ttu-id="b77b7-479">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="b77b7-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="b77b7-480">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="b77b7-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="b77b7-481">請參閱</span><span class="sxs-lookup"><span data-stu-id="b77b7-481">See also</span></span>

- [<span data-ttu-id="b77b7-482">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="b77b7-482">CLR ETW Events</span></span>](clr-etw-events.md)
