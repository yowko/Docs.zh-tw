---
title: "記憶體回收 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="493ca-102">記憶體回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="493ca-103">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="493ca-104">它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。</span><span class="sxs-lookup"><span data-stu-id="493ca-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="493ca-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="493ca-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="493ca-106">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="493ca-107">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="493ca-108">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="493ca-109">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="493ca-110">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="493ca-111">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="493ca-112">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="493ca-113">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="493ca-114">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="493ca-115">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="493ca-116">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="493ca-117">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="493ca-118">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="493ca-119">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="493ca-120">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="493ca-121">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="493ca-122">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="493ca-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="493ca-123">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-123">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-124">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-127">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-128">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-128">Event</span></span>|<span data-ttu-id="493ca-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-129">Event ID</span></span>|<span data-ttu-id="493ca-130">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="493ca-131">1</span><span class="sxs-lookup"><span data-stu-id="493ca-131">1</span></span>|<span data-ttu-id="493ca-132">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="493ca-133">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-134">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-134">Field name</span></span>|<span data-ttu-id="493ca-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-135">Data type</span></span>|<span data-ttu-id="493ca-136">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-137">計數</span><span class="sxs-lookup"><span data-stu-id="493ca-137">Count</span></span>|<span data-ttu-id="493ca-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-138">win:UInt32</span></span>|<span data-ttu-id="493ca-139">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="493ca-140">深度</span><span class="sxs-lookup"><span data-stu-id="493ca-140">Depth</span></span>|<span data-ttu-id="493ca-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-141">win:UInt32</span></span>|<span data-ttu-id="493ca-142">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="493ca-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="493ca-143">原因</span><span class="sxs-lookup"><span data-stu-id="493ca-143">Reason</span></span>|<span data-ttu-id="493ca-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-144">win:UInt32</span></span>|<span data-ttu-id="493ca-145">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="493ca-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="493ca-146">0x0 - 小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="493ca-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="493ca-147">0x1 - 已引起。</span><span class="sxs-lookup"><span data-stu-id="493ca-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="493ca-148">0x2 - 記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="493ca-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="493ca-149">0x3 - 空白。</span><span class="sxs-lookup"><span data-stu-id="493ca-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="493ca-150">0x4 - 大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="493ca-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="493ca-151">0x5 - 空間不足 (針對小型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="493ca-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="493ca-152">0x6 - 空間不足 (針對大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="493ca-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="493ca-153">0x7 - 已引起，但不強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="493ca-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="493ca-154">類型</span><span class="sxs-lookup"><span data-stu-id="493ca-154">Type</span></span>|<span data-ttu-id="493ca-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-155">win:UInt32</span></span>|<span data-ttu-id="493ca-156">0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="493ca-157">0x1 - 背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="493ca-158">0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="493ca-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-159">ClrInstanceID</span></span>|<span data-ttu-id="493ca-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-160">win:UInt16</span></span>|<span data-ttu-id="493ca-161">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-162">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="493ca-163">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="493ca-164">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-165">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-165">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-166">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-168">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-169">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-170">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-170">Event</span></span>|<span data-ttu-id="493ca-171">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-171">Event ID</span></span>|<span data-ttu-id="493ca-172">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="493ca-173">2</span><span class="sxs-lookup"><span data-stu-id="493ca-173">2</span></span>|<span data-ttu-id="493ca-174">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="493ca-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="493ca-175">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-176">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-176">Field name</span></span>|<span data-ttu-id="493ca-177">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-177">Data type</span></span>|<span data-ttu-id="493ca-178">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-179">計數</span><span class="sxs-lookup"><span data-stu-id="493ca-179">Count</span></span>|<span data-ttu-id="493ca-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-180">win:UInt32</span></span>|<span data-ttu-id="493ca-181">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="493ca-182">深度</span><span class="sxs-lookup"><span data-stu-id="493ca-182">Depth</span></span>|<span data-ttu-id="493ca-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-183">win:UInt32</span></span>|<span data-ttu-id="493ca-184">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="493ca-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="493ca-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-185">ClrInstanceID</span></span>|<span data-ttu-id="493ca-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-186">win:UInt16</span></span>|<span data-ttu-id="493ca-187">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="493ca-189">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="493ca-190">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-191">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-191">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-192">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-194">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-195">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-196">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-196">Event</span></span>|<span data-ttu-id="493ca-197">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-197">Event ID</span></span>|<span data-ttu-id="493ca-198">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="493ca-199">4</span><span class="sxs-lookup"><span data-stu-id="493ca-199">4</span></span>|<span data-ttu-id="493ca-200">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="493ca-201">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-202">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-202">Field name</span></span>|<span data-ttu-id="493ca-203">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-203">Data type</span></span>|<span data-ttu-id="493ca-204">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="493ca-205">GenerationSize0</span></span>|<span data-ttu-id="493ca-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-206">win:UInt64</span></span>|<span data-ttu-id="493ca-207">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="493ca-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="493ca-208">TotalPromotedSize0</span></span>|<span data-ttu-id="493ca-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-209">win:UInt64</span></span>|<span data-ttu-id="493ca-210">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="493ca-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="493ca-211">GenerationSize1</span></span>|<span data-ttu-id="493ca-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-212">win:UInt64</span></span>|<span data-ttu-id="493ca-213">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="493ca-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="493ca-214">TotalPromotedSize1</span></span>|<span data-ttu-id="493ca-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-215">win:UInt64</span></span>|<span data-ttu-id="493ca-216">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="493ca-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="493ca-217">GenerationSize2</span></span>|<span data-ttu-id="493ca-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-218">win:UInt64</span></span>|<span data-ttu-id="493ca-219">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="493ca-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="493ca-220">TotalPromotedSize2</span></span>|<span data-ttu-id="493ca-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-221">win:UInt64</span></span>|<span data-ttu-id="493ca-222">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="493ca-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="493ca-223">GenerationSize3</span></span>|<span data-ttu-id="493ca-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-224">win:UInt64</span></span>|<span data-ttu-id="493ca-225">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="493ca-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="493ca-226">TotalPromotedSize3</span></span>|<span data-ttu-id="493ca-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-227">win:UInt64</span></span>|<span data-ttu-id="493ca-228">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="493ca-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="493ca-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="493ca-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-230">win:UInt64</span></span>|<span data-ttu-id="493ca-231">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="493ca-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="493ca-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="493ca-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-233">win:UInt64</span></span>|<span data-ttu-id="493ca-234">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="493ca-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="493ca-235">PinnedObjectCount</span></span>|<span data-ttu-id="493ca-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-236">win:UInt32</span></span>|<span data-ttu-id="493ca-237">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="493ca-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="493ca-238">SinkBlockCount</span></span>|<span data-ttu-id="493ca-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-239">win:UInt32</span></span>|<span data-ttu-id="493ca-240">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="493ca-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="493ca-241">GCHandleCount</span></span>|<span data-ttu-id="493ca-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-242">win:UInt32</span></span>|<span data-ttu-id="493ca-243">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="493ca-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-244">ClrInstanceID</span></span>|<span data-ttu-id="493ca-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-245">win:UInt16</span></span>|<span data-ttu-id="493ca-246">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-247">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="493ca-248">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="493ca-249">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-250">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-250">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-251">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-253">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-254">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-255">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-255">Event</span></span>|<span data-ttu-id="493ca-256">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-256">Event ID</span></span>|<span data-ttu-id="493ca-257">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="493ca-258">5</span><span class="sxs-lookup"><span data-stu-id="493ca-258">5</span></span>|<span data-ttu-id="493ca-259">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="493ca-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="493ca-260">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="493ca-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="493ca-261">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-262">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-262">Field name</span></span>|<span data-ttu-id="493ca-263">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-263">Data type</span></span>|<span data-ttu-id="493ca-264">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-265">地址</span><span class="sxs-lookup"><span data-stu-id="493ca-265">Address</span></span>|<span data-ttu-id="493ca-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-266">win:UInt64</span></span>|<span data-ttu-id="493ca-267">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="493ca-267">The address of the segment.</span></span>|  
|<span data-ttu-id="493ca-268">大小</span><span class="sxs-lookup"><span data-stu-id="493ca-268">Size</span></span>|<span data-ttu-id="493ca-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-269">win:UInt64</span></span>|<span data-ttu-id="493ca-270">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="493ca-270">The size of the segment.</span></span>|  
|<span data-ttu-id="493ca-271">類型</span><span class="sxs-lookup"><span data-stu-id="493ca-271">Type</span></span>|<span data-ttu-id="493ca-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-272">win:UInt32</span></span>|<span data-ttu-id="493ca-273">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="493ca-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="493ca-274">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="493ca-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="493ca-275">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="493ca-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="493ca-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-276">ClrInstanceID</span></span>|<span data-ttu-id="493ca-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-277">win:UInt16</span></span>|<span data-ttu-id="493ca-278">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="493ca-279">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="493ca-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="493ca-280">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="493ca-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="493ca-281">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="493ca-282">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="493ca-283">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-284">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-284">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-285">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-287">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-288">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-289">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-289">Event</span></span>|<span data-ttu-id="493ca-290">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-290">Event ID</span></span>|<span data-ttu-id="493ca-291">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="493ca-292">6</span><span class="sxs-lookup"><span data-stu-id="493ca-292">6</span></span>|<span data-ttu-id="493ca-293">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="493ca-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="493ca-294">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-295">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-295">Field name</span></span>|<span data-ttu-id="493ca-296">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-296">Data type</span></span>|<span data-ttu-id="493ca-297">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-298">地址</span><span class="sxs-lookup"><span data-stu-id="493ca-298">Address</span></span>|<span data-ttu-id="493ca-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-299">win:UInt64</span></span>|<span data-ttu-id="493ca-300">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="493ca-300">The address of the segment.</span></span>|  
|<span data-ttu-id="493ca-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-301">ClrInstanceID</span></span>|<span data-ttu-id="493ca-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-302">win:UInt16</span></span>|<span data-ttu-id="493ca-303">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-304">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="493ca-305">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="493ca-306">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-307">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-307">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-308">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-310">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-311">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-312">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-312">Event</span></span>|<span data-ttu-id="493ca-313">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-313">Event ID</span></span>|<span data-ttu-id="493ca-314">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="493ca-315">7</span><span class="sxs-lookup"><span data-stu-id="493ca-315">7</span></span>|<span data-ttu-id="493ca-316">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="493ca-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="493ca-317">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-317">No event data.</span></span>  
  
 [<span data-ttu-id="493ca-318">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="493ca-319">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="493ca-320">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-321">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-321">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-322">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-324">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-325">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-326">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-326">Event</span></span>|<span data-ttu-id="493ca-327">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-327">Event Id</span></span>|<span data-ttu-id="493ca-328">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="493ca-329">3</span><span class="sxs-lookup"><span data-stu-id="493ca-329">3</span></span>|<span data-ttu-id="493ca-330">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="493ca-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="493ca-331">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-331">No event data.</span></span>  
  
 [<span data-ttu-id="493ca-332">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="493ca-333">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="493ca-334">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-335">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-335">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-336">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-338">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-339">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-340">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-340">Event</span></span>|<span data-ttu-id="493ca-341">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-341">Event ID</span></span>|<span data-ttu-id="493ca-342">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="493ca-343">9</span><span class="sxs-lookup"><span data-stu-id="493ca-343">9</span></span>|<span data-ttu-id="493ca-344">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="493ca-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="493ca-345">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-346">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-346">Field name</span></span>|<span data-ttu-id="493ca-347">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-347">Data type</span></span>|<span data-ttu-id="493ca-348">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-349">原因</span><span class="sxs-lookup"><span data-stu-id="493ca-349">Reason</span></span>|<span data-ttu-id="493ca-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-350">win:UInt16</span></span>|<span data-ttu-id="493ca-351">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="493ca-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="493ca-352">0x1 - 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="493ca-353">0x2 - 應用程式定義域關閉。</span><span class="sxs-lookup"><span data-stu-id="493ca-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="493ca-354">0x3 - 推銷程式碼。</span><span class="sxs-lookup"><span data-stu-id="493ca-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="493ca-355">0x4 - 關機。</span><span class="sxs-lookup"><span data-stu-id="493ca-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="493ca-356">0x5 - 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="493ca-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="493ca-357">0x6 - 準備進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="493ca-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="493ca-358">計數</span><span class="sxs-lookup"><span data-stu-id="493ca-358">Count</span></span>|<span data-ttu-id="493ca-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-359">win:UInt32</span></span>|<span data-ttu-id="493ca-360">該時間的 GC 計數。</span><span class="sxs-lookup"><span data-stu-id="493ca-360">The GC count at the time.</span></span> <span data-ttu-id="493ca-361">通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。</span><span class="sxs-lookup"><span data-stu-id="493ca-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="493ca-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-362">ClrInstanceID</span></span>|<span data-ttu-id="493ca-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-363">win:UInt16</span></span>|<span data-ttu-id="493ca-364">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-365">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="493ca-366">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="493ca-367">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="493ca-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="493ca-368">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-368">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-369">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-371">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-372">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="493ca-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="493ca-373">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-373">Event</span></span>|<span data-ttu-id="493ca-374">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-374">Event ID</span></span>|<span data-ttu-id="493ca-375">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="493ca-376">8</span><span class="sxs-lookup"><span data-stu-id="493ca-376">8</span></span>|<span data-ttu-id="493ca-377">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="493ca-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="493ca-378">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-378">No event data.</span></span>  
  
 [<span data-ttu-id="493ca-379">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="493ca-380">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="493ca-381">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-382">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-382">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-383">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-385">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-386">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-387">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-387">Event</span></span>|<span data-ttu-id="493ca-388">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-388">Event ID</span></span>|<span data-ttu-id="493ca-389">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="493ca-390">10</span><span class="sxs-lookup"><span data-stu-id="493ca-390">10</span></span>|<span data-ttu-id="493ca-391">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="493ca-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="493ca-392">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-393">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-393">Field name</span></span>|<span data-ttu-id="493ca-394">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-394">Data type</span></span>|<span data-ttu-id="493ca-395">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="493ca-396">AllocationAmount</span></span>|<span data-ttu-id="493ca-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-397">win:UInt32</span></span>|<span data-ttu-id="493ca-398">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="493ca-398">The allocation size, in bytes.</span></span> <span data-ttu-id="493ca-399">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="493ca-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="493ca-400">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="493ca-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="493ca-401">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="493ca-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="493ca-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="493ca-402">AllocationKind</span></span>|<span data-ttu-id="493ca-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-403">win:UInt32</span></span>|<span data-ttu-id="493ca-404">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="493ca-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="493ca-405">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="493ca-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="493ca-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-406">ClrInstanceID</span></span>|<span data-ttu-id="493ca-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-407">win:UInt16</span></span>|<span data-ttu-id="493ca-408">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="493ca-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="493ca-409">AllocationAmount64</span></span>|<span data-ttu-id="493ca-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="493ca-410">win:UInt64</span></span>|<span data-ttu-id="493ca-411">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="493ca-411">The allocation size, in bytes.</span></span> <span data-ttu-id="493ca-412">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="493ca-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="493ca-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="493ca-413">TypeId</span></span>|<span data-ttu-id="493ca-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="493ca-414">win:Pointer</span></span>|<span data-ttu-id="493ca-415">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="493ca-415">The address of the MethodTable.</span></span> <span data-ttu-id="493ca-416">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="493ca-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="493ca-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="493ca-417">TypeName</span></span>|<span data-ttu-id="493ca-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="493ca-418">win:UnicodeString</span></span>|<span data-ttu-id="493ca-419">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="493ca-419">The name of the type that was allocated.</span></span> <span data-ttu-id="493ca-420">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="493ca-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="493ca-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="493ca-421">HeapIndex</span></span>|<span data-ttu-id="493ca-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-422">win:UInt32</span></span>|<span data-ttu-id="493ca-423">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="493ca-423">The heap where the object was allocated.</span></span> <span data-ttu-id="493ca-424">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="493ca-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="493ca-425">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="493ca-426">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="493ca-427">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-428">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-428">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-429">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-431">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-432">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-433">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-433">Event</span></span>|<span data-ttu-id="493ca-434">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-434">Event ID</span></span>|<span data-ttu-id="493ca-435">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="493ca-436">14</span><span class="sxs-lookup"><span data-stu-id="493ca-436">14</span></span>|<span data-ttu-id="493ca-437">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="493ca-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="493ca-438">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-438">No event data.</span></span>  
  
 [<span data-ttu-id="493ca-439">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="493ca-440">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="493ca-441">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-442">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-442">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-443">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-445">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-446">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-447">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-447">Event</span></span>|<span data-ttu-id="493ca-448">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-448">Event ID</span></span>|<span data-ttu-id="493ca-449">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="493ca-450">13</span><span class="sxs-lookup"><span data-stu-id="493ca-450">13</span></span>|<span data-ttu-id="493ca-451">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="493ca-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="493ca-452">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="493ca-453">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="493ca-453">Field name</span></span>|<span data-ttu-id="493ca-454">資料類型</span><span class="sxs-lookup"><span data-stu-id="493ca-454">Data type</span></span>|<span data-ttu-id="493ca-455">描述</span><span class="sxs-lookup"><span data-stu-id="493ca-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="493ca-456">計數</span><span class="sxs-lookup"><span data-stu-id="493ca-456">Count</span></span>|<span data-ttu-id="493ca-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="493ca-457">win:UInt32</span></span>|<span data-ttu-id="493ca-458">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="493ca-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="493ca-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="493ca-459">ClrInstanceID</span></span>|<span data-ttu-id="493ca-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="493ca-460">win:UInt16</span></span>|<span data-ttu-id="493ca-461">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="493ca-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="493ca-462">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="493ca-463">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="493ca-464">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-465">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-465">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-466">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-468">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-468">Informational (4)</span></span>|  
|<span data-ttu-id="493ca-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="493ca-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="493ca-470">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-471">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-472">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-472">Event</span></span>|<span data-ttu-id="493ca-473">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-473">Event ID</span></span>|<span data-ttu-id="493ca-474">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="493ca-475">11</span><span class="sxs-lookup"><span data-stu-id="493ca-475">11</span></span>|<span data-ttu-id="493ca-476">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="493ca-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="493ca-477">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-477">No event data.</span></span>  
  
 [<span data-ttu-id="493ca-478">回到頁首</span><span class="sxs-lookup"><span data-stu-id="493ca-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="493ca-479">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="493ca-480">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="493ca-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="493ca-481">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="493ca-481">Keyword for raising the event</span></span>|<span data-ttu-id="493ca-482">層級</span><span class="sxs-lookup"><span data-stu-id="493ca-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="493ca-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="493ca-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="493ca-484">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-484">Informational (4)</span></span>|  
|<span data-ttu-id="493ca-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="493ca-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="493ca-486">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="493ca-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="493ca-487">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="493ca-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="493ca-488">事件</span><span class="sxs-lookup"><span data-stu-id="493ca-488">Event</span></span>|<span data-ttu-id="493ca-489">事件 ID</span><span class="sxs-lookup"><span data-stu-id="493ca-489">Event ID</span></span>|<span data-ttu-id="493ca-490">引發的時機</span><span class="sxs-lookup"><span data-stu-id="493ca-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="493ca-491">12</span><span class="sxs-lookup"><span data-stu-id="493ca-491">12</span></span>|<span data-ttu-id="493ca-492">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="493ca-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="493ca-493">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="493ca-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493ca-494">另請參閱</span><span class="sxs-lookup"><span data-stu-id="493ca-494">See Also</span></span>  
 [<span data-ttu-id="493ca-495">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="493ca-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
