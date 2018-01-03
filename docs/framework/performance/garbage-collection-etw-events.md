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
ms.workload: dotnet
ms.openlocfilehash: 133d48baa9613ea698b6d6a21f0dfe88a798859c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="60e0f-102">記憶體回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="60e0f-103">這些事件收集到記憶體回收的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="60e0f-104">它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。</span><span class="sxs-lookup"><span data-stu-id="60e0f-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="60e0f-105">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="60e0f-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="60e0f-106">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="60e0f-107">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="60e0f-108">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="60e0f-109">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="60e0f-110">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="60e0f-111">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="60e0f-112">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="60e0f-113">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="60e0f-114">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="60e0f-115">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="60e0f-116">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="60e0f-117">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="60e0f-118">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="60e0f-119">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="60e0f-120">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="60e0f-121">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="60e0f-122">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="60e0f-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="60e0f-123">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-123">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-124">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-127">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-128">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-128">Event</span></span>|<span data-ttu-id="60e0f-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-129">Event ID</span></span>|<span data-ttu-id="60e0f-130">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="60e0f-131">1</span><span class="sxs-lookup"><span data-stu-id="60e0f-131">1</span></span>|<span data-ttu-id="60e0f-132">已開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="60e0f-133">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-134">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-134">Field name</span></span>|<span data-ttu-id="60e0f-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-135">Data type</span></span>|<span data-ttu-id="60e0f-136">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-137">計數</span><span class="sxs-lookup"><span data-stu-id="60e0f-137">Count</span></span>|<span data-ttu-id="60e0f-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-138">win:UInt32</span></span>|<span data-ttu-id="60e0f-139">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="60e0f-140">深度</span><span class="sxs-lookup"><span data-stu-id="60e0f-140">Depth</span></span>|<span data-ttu-id="60e0f-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-141">win:UInt32</span></span>|<span data-ttu-id="60e0f-142">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="60e0f-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="60e0f-143">原因</span><span class="sxs-lookup"><span data-stu-id="60e0f-143">Reason</span></span>|<span data-ttu-id="60e0f-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-144">win:UInt32</span></span>|<span data-ttu-id="60e0f-145">觸發記憶體回收的原因：</span><span class="sxs-lookup"><span data-stu-id="60e0f-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="60e0f-146">0x0 - 小型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="60e0f-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="60e0f-147">0x1 - 已引起。</span><span class="sxs-lookup"><span data-stu-id="60e0f-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="60e0f-148">0x2 - 記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="60e0f-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="60e0f-149">0x3 - 空白。</span><span class="sxs-lookup"><span data-stu-id="60e0f-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="60e0f-150">0x4 - 大型物件堆積配置。</span><span class="sxs-lookup"><span data-stu-id="60e0f-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="60e0f-151">0x5 - 空間不足 (針對小型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="60e0f-152">0x6 - 空間不足 (針對大型物件堆積)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="60e0f-153">0x7 - 已引起，但不強制為封鎖。</span><span class="sxs-lookup"><span data-stu-id="60e0f-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="60e0f-154">類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-154">Type</span></span>|<span data-ttu-id="60e0f-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-155">win:UInt32</span></span>|<span data-ttu-id="60e0f-156">0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="60e0f-157">0x1 - 背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="60e0f-158">0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="60e0f-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-159">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-160">win:UInt16</span></span>|<span data-ttu-id="60e0f-161">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-162">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="60e0f-163">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="60e0f-164">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-165">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-165">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-166">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-168">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-169">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-170">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-170">Event</span></span>|<span data-ttu-id="60e0f-171">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-171">Event ID</span></span>|<span data-ttu-id="60e0f-172">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="60e0f-173">2</span><span class="sxs-lookup"><span data-stu-id="60e0f-173">2</span></span>|<span data-ttu-id="60e0f-174">記憶體回收已經結束。</span><span class="sxs-lookup"><span data-stu-id="60e0f-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="60e0f-175">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-176">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-176">Field name</span></span>|<span data-ttu-id="60e0f-177">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-177">Data type</span></span>|<span data-ttu-id="60e0f-178">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-179">計數</span><span class="sxs-lookup"><span data-stu-id="60e0f-179">Count</span></span>|<span data-ttu-id="60e0f-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-180">win:UInt32</span></span>|<span data-ttu-id="60e0f-181">第 *n*個記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="60e0f-182">深度</span><span class="sxs-lookup"><span data-stu-id="60e0f-182">Depth</span></span>|<span data-ttu-id="60e0f-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-183">win:UInt32</span></span>|<span data-ttu-id="60e0f-184">所收集的產生。</span><span class="sxs-lookup"><span data-stu-id="60e0f-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="60e0f-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-185">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-186">win:UInt16</span></span>|<span data-ttu-id="60e0f-187">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="60e0f-189">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="60e0f-190">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-191">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-191">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-192">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-194">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-195">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-196">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-196">Event</span></span>|<span data-ttu-id="60e0f-197">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-197">Event ID</span></span>|<span data-ttu-id="60e0f-198">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="60e0f-199">4</span><span class="sxs-lookup"><span data-stu-id="60e0f-199">4</span></span>|<span data-ttu-id="60e0f-200">每次記憶體回收結束時顯示堆積統計資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="60e0f-201">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-202">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-202">Field name</span></span>|<span data-ttu-id="60e0f-203">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-203">Data type</span></span>|<span data-ttu-id="60e0f-204">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="60e0f-205">GenerationSize0</span></span>|<span data-ttu-id="60e0f-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-206">win:UInt64</span></span>|<span data-ttu-id="60e0f-207">以位元組為單位顯示的層代 0 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="60e0f-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="60e0f-208">TotalPromotedSize0</span></span>|<span data-ttu-id="60e0f-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-209">win:UInt64</span></span>|<span data-ttu-id="60e0f-210">從層代 0 升級至層代 1 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="60e0f-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="60e0f-211">GenerationSize1</span></span>|<span data-ttu-id="60e0f-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-212">win:UInt64</span></span>|<span data-ttu-id="60e0f-213">以位元組為單位顯示的層代 1 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="60e0f-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="60e0f-214">TotalPromotedSize1</span></span>|<span data-ttu-id="60e0f-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-215">win:UInt64</span></span>|<span data-ttu-id="60e0f-216">從層代 1 升級到層代 2 的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="60e0f-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="60e0f-217">GenerationSize2</span></span>|<span data-ttu-id="60e0f-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-218">win:UInt64</span></span>|<span data-ttu-id="60e0f-219">以位元組為單位顯示的層代 2 記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="60e0f-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="60e0f-220">TotalPromotedSize2</span></span>|<span data-ttu-id="60e0f-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-221">win:UInt64</span></span>|<span data-ttu-id="60e0f-222">在回收之後存留於層代 2 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="60e0f-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="60e0f-223">GenerationSize3</span></span>|<span data-ttu-id="60e0f-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-224">win:UInt64</span></span>|<span data-ttu-id="60e0f-225">以位元組為單位顯示的目前大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="60e0f-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="60e0f-226">TotalPromotedSize3</span></span>|<span data-ttu-id="60e0f-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-227">win:UInt64</span></span>|<span data-ttu-id="60e0f-228">在回收之後存留於大型物件堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="60e0f-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="60e0f-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="60e0f-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-230">win:UInt64</span></span>|<span data-ttu-id="60e0f-231">以位元組為單位顯示的準備最終處理的物件總大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="60e0f-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="60e0f-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="60e0f-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-233">win:UInt64</span></span>|<span data-ttu-id="60e0f-234">準備好進行最終處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="60e0f-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="60e0f-235">PinnedObjectCount</span></span>|<span data-ttu-id="60e0f-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-236">win:UInt32</span></span>|<span data-ttu-id="60e0f-237">固定 (不可移動) 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="60e0f-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="60e0f-238">SinkBlockCount</span></span>|<span data-ttu-id="60e0f-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-239">win:UInt32</span></span>|<span data-ttu-id="60e0f-240">目前使用中的同步區塊數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="60e0f-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="60e0f-241">GCHandleCount</span></span>|<span data-ttu-id="60e0f-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-242">win:UInt32</span></span>|<span data-ttu-id="60e0f-243">目前使用中的記憶體回收控制代碼數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="60e0f-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-244">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-245">win:UInt16</span></span>|<span data-ttu-id="60e0f-246">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-247">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="60e0f-248">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="60e0f-249">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-250">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-250">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-251">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-253">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-254">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-255">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-255">Event</span></span>|<span data-ttu-id="60e0f-256">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-256">Event ID</span></span>|<span data-ttu-id="60e0f-257">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="60e0f-258">5</span><span class="sxs-lookup"><span data-stu-id="60e0f-258">5</span></span>|<span data-ttu-id="60e0f-259">已建立新的記憶體回收集合區段。</span><span class="sxs-lookup"><span data-stu-id="60e0f-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="60e0f-260">此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。</span><span class="sxs-lookup"><span data-stu-id="60e0f-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="60e0f-261">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-262">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-262">Field name</span></span>|<span data-ttu-id="60e0f-263">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-263">Data type</span></span>|<span data-ttu-id="60e0f-264">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-265">地址</span><span class="sxs-lookup"><span data-stu-id="60e0f-265">Address</span></span>|<span data-ttu-id="60e0f-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-266">win:UInt64</span></span>|<span data-ttu-id="60e0f-267">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="60e0f-267">The address of the segment.</span></span>|  
|<span data-ttu-id="60e0f-268">大小</span><span class="sxs-lookup"><span data-stu-id="60e0f-268">Size</span></span>|<span data-ttu-id="60e0f-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-269">win:UInt64</span></span>|<span data-ttu-id="60e0f-270">區段的大小。</span><span class="sxs-lookup"><span data-stu-id="60e0f-270">The size of the segment.</span></span>|  
|<span data-ttu-id="60e0f-271">類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-271">Type</span></span>|<span data-ttu-id="60e0f-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-272">win:UInt32</span></span>|<span data-ttu-id="60e0f-273">0x0 - 小型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="60e0f-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="60e0f-274">0x1 - 大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="60e0f-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="60e0f-275">0x2 - 唯讀堆積。</span><span class="sxs-lookup"><span data-stu-id="60e0f-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="60e0f-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-276">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-277">win:UInt16</span></span>|<span data-ttu-id="60e0f-278">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="60e0f-279">請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。</span><span class="sxs-lookup"><span data-stu-id="60e0f-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="60e0f-280">您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="60e0f-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="60e0f-281">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="60e0f-282">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="60e0f-283">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-284">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-284">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-285">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-287">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-288">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-289">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-289">Event</span></span>|<span data-ttu-id="60e0f-290">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-290">Event ID</span></span>|<span data-ttu-id="60e0f-291">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="60e0f-292">6</span><span class="sxs-lookup"><span data-stu-id="60e0f-292">6</span></span>|<span data-ttu-id="60e0f-293">已釋放記憶體回收區段。</span><span class="sxs-lookup"><span data-stu-id="60e0f-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="60e0f-294">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-295">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-295">Field name</span></span>|<span data-ttu-id="60e0f-296">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-296">Data type</span></span>|<span data-ttu-id="60e0f-297">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-298">地址</span><span class="sxs-lookup"><span data-stu-id="60e0f-298">Address</span></span>|<span data-ttu-id="60e0f-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-299">win:UInt64</span></span>|<span data-ttu-id="60e0f-300">區段的位址。</span><span class="sxs-lookup"><span data-stu-id="60e0f-300">The address of the segment.</span></span>|  
|<span data-ttu-id="60e0f-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-301">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-302">win:UInt16</span></span>|<span data-ttu-id="60e0f-303">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-304">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="60e0f-305">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="60e0f-306">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-307">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-307">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-308">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-310">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-311">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-312">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-312">Event</span></span>|<span data-ttu-id="60e0f-313">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-313">Event ID</span></span>|<span data-ttu-id="60e0f-314">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="60e0f-315">7</span><span class="sxs-lookup"><span data-stu-id="60e0f-315">7</span></span>|<span data-ttu-id="60e0f-316">已開始從通用語言執行階段的擱置中恢復。</span><span class="sxs-lookup"><span data-stu-id="60e0f-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="60e0f-317">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-317">No event data.</span></span>  
  
 [<span data-ttu-id="60e0f-318">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="60e0f-319">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="60e0f-320">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-321">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-321">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-322">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-324">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-325">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-326">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-326">Event</span></span>|<span data-ttu-id="60e0f-327">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-327">Event Id</span></span>|<span data-ttu-id="60e0f-328">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="60e0f-329">3</span><span class="sxs-lookup"><span data-stu-id="60e0f-329">3</span></span>|<span data-ttu-id="60e0f-330">從通用語言執行階段擱置恢復已結束。</span><span class="sxs-lookup"><span data-stu-id="60e0f-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="60e0f-331">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-331">No event data.</span></span>  
  
 [<span data-ttu-id="60e0f-332">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="60e0f-333">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="60e0f-334">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-335">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-335">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-336">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-338">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-339">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-340">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-340">Event</span></span>|<span data-ttu-id="60e0f-341">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-341">Event ID</span></span>|<span data-ttu-id="60e0f-342">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="60e0f-343">9</span><span class="sxs-lookup"><span data-stu-id="60e0f-343">9</span></span>|<span data-ttu-id="60e0f-344">記憶體回收執行引擎擱置的起點。</span><span class="sxs-lookup"><span data-stu-id="60e0f-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="60e0f-345">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-346">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-346">Field name</span></span>|<span data-ttu-id="60e0f-347">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-347">Data type</span></span>|<span data-ttu-id="60e0f-348">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-349">原因</span><span class="sxs-lookup"><span data-stu-id="60e0f-349">Reason</span></span>|<span data-ttu-id="60e0f-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-350">win:UInt16</span></span>|<span data-ttu-id="60e0f-351">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="60e0f-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="60e0f-352">0x1 - 記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="60e0f-353">0x2 - 應用程式定義域關閉。</span><span class="sxs-lookup"><span data-stu-id="60e0f-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="60e0f-354">0x3 - 推銷程式碼。</span><span class="sxs-lookup"><span data-stu-id="60e0f-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="60e0f-355">0x4 - 關機。</span><span class="sxs-lookup"><span data-stu-id="60e0f-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="60e0f-356">0x5 - 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="60e0f-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="60e0f-357">0x6 - 準備進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="60e0f-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="60e0f-358">計數</span><span class="sxs-lookup"><span data-stu-id="60e0f-358">Count</span></span>|<span data-ttu-id="60e0f-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-359">win:UInt32</span></span>|<span data-ttu-id="60e0f-360">該時間的 GC 計數。</span><span class="sxs-lookup"><span data-stu-id="60e0f-360">The GC count at the time.</span></span> <span data-ttu-id="60e0f-361">通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。</span><span class="sxs-lookup"><span data-stu-id="60e0f-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="60e0f-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-362">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-363">win:UInt16</span></span>|<span data-ttu-id="60e0f-364">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-365">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="60e0f-366">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="60e0f-367">下表說明關鍵字和層級：</span><span class="sxs-lookup"><span data-stu-id="60e0f-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="60e0f-368">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-368">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-369">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-371">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-372">下表說明事件資訊：</span><span class="sxs-lookup"><span data-stu-id="60e0f-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="60e0f-373">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-373">Event</span></span>|<span data-ttu-id="60e0f-374">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-374">Event ID</span></span>|<span data-ttu-id="60e0f-375">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="60e0f-376">8</span><span class="sxs-lookup"><span data-stu-id="60e0f-376">8</span></span>|<span data-ttu-id="60e0f-377">記憶體回收執行引擎擱置的終點。</span><span class="sxs-lookup"><span data-stu-id="60e0f-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="60e0f-378">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-378">No event data.</span></span>  
  
 [<span data-ttu-id="60e0f-379">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="60e0f-380">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="60e0f-381">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-382">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-382">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-383">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-385">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-386">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-387">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-387">Event</span></span>|<span data-ttu-id="60e0f-388">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-388">Event ID</span></span>|<span data-ttu-id="60e0f-389">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="60e0f-390">10</span><span class="sxs-lookup"><span data-stu-id="60e0f-390">10</span></span>|<span data-ttu-id="60e0f-391">每次配置大約 100 KB。</span><span class="sxs-lookup"><span data-stu-id="60e0f-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="60e0f-392">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-393">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-393">Field name</span></span>|<span data-ttu-id="60e0f-394">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-394">Data type</span></span>|<span data-ttu-id="60e0f-395">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="60e0f-396">AllocationAmount</span></span>|<span data-ttu-id="60e0f-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-397">win:UInt32</span></span>|<span data-ttu-id="60e0f-398">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-398">The allocation size, in bytes.</span></span> <span data-ttu-id="60e0f-399">正確的配置長度值小於 ULONG (4,294,967,295 位元組)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="60e0f-400">如果配置較大，則此欄位會包含已截斷的值。</span><span class="sxs-lookup"><span data-stu-id="60e0f-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="60e0f-401">使用 `AllocationAmount64` 以進行非常大的配置。</span><span class="sxs-lookup"><span data-stu-id="60e0f-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="60e0f-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="60e0f-402">AllocationKind</span></span>|<span data-ttu-id="60e0f-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-403">win:UInt32</span></span>|<span data-ttu-id="60e0f-404">0x0 - 小型物件配置 (配置於小型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="60e0f-405">0x1 - 大型物件配置 (配置於大型物件堆積中)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="60e0f-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-406">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-407">win:UInt16</span></span>|<span data-ttu-id="60e0f-408">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="60e0f-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="60e0f-409">AllocationAmount64</span></span>|<span data-ttu-id="60e0f-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="60e0f-410">win:UInt64</span></span>|<span data-ttu-id="60e0f-411">配置大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-411">The allocation size, in bytes.</span></span> <span data-ttu-id="60e0f-412">對於非常大的配置來說這個值是正確的。</span><span class="sxs-lookup"><span data-stu-id="60e0f-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="60e0f-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="60e0f-413">TypeId</span></span>|<span data-ttu-id="60e0f-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="60e0f-414">win:Pointer</span></span>|<span data-ttu-id="60e0f-415">MethodTable 的位址。</span><span class="sxs-lookup"><span data-stu-id="60e0f-415">The address of the MethodTable.</span></span> <span data-ttu-id="60e0f-416">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。</span><span class="sxs-lookup"><span data-stu-id="60e0f-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="60e0f-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="60e0f-417">TypeName</span></span>|<span data-ttu-id="60e0f-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="60e0f-418">win:UnicodeString</span></span>|<span data-ttu-id="60e0f-419">已配置的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="60e0f-419">The name of the type that was allocated.</span></span> <span data-ttu-id="60e0f-420">當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。</span><span class="sxs-lookup"><span data-stu-id="60e0f-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="60e0f-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="60e0f-421">HeapIndex</span></span>|<span data-ttu-id="60e0f-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-422">win:UInt32</span></span>|<span data-ttu-id="60e0f-423">物件所配置的堆積位置。</span><span class="sxs-lookup"><span data-stu-id="60e0f-423">The heap where the object was allocated.</span></span> <span data-ttu-id="60e0f-424">當與工作站記憶體回收一起執行時，這個值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="60e0f-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="60e0f-425">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="60e0f-426">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="60e0f-427">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-428">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-428">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-429">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-431">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-432">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-433">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-433">Event</span></span>|<span data-ttu-id="60e0f-434">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-434">Event ID</span></span>|<span data-ttu-id="60e0f-435">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="60e0f-436">14</span><span class="sxs-lookup"><span data-stu-id="60e0f-436">14</span></span>|<span data-ttu-id="60e0f-437">開始執行完成項。</span><span class="sxs-lookup"><span data-stu-id="60e0f-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="60e0f-438">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-438">No event data.</span></span>  
  
 [<span data-ttu-id="60e0f-439">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="60e0f-440">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="60e0f-441">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-442">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-442">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-443">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-445">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-446">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-447">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-447">Event</span></span>|<span data-ttu-id="60e0f-448">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-448">Event ID</span></span>|<span data-ttu-id="60e0f-449">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="60e0f-450">13</span><span class="sxs-lookup"><span data-stu-id="60e0f-450">13</span></span>|<span data-ttu-id="60e0f-451">結束執行完成項。</span><span class="sxs-lookup"><span data-stu-id="60e0f-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="60e0f-452">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="60e0f-453">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="60e0f-453">Field name</span></span>|<span data-ttu-id="60e0f-454">資料類型</span><span class="sxs-lookup"><span data-stu-id="60e0f-454">Data type</span></span>|<span data-ttu-id="60e0f-455">描述</span><span class="sxs-lookup"><span data-stu-id="60e0f-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="60e0f-456">計數</span><span class="sxs-lookup"><span data-stu-id="60e0f-456">Count</span></span>|<span data-ttu-id="60e0f-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="60e0f-457">win:UInt32</span></span>|<span data-ttu-id="60e0f-458">所執行的完成項數目。</span><span class="sxs-lookup"><span data-stu-id="60e0f-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="60e0f-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="60e0f-459">ClrInstanceID</span></span>|<span data-ttu-id="60e0f-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="60e0f-460">win:UInt16</span></span>|<span data-ttu-id="60e0f-461">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="60e0f-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="60e0f-462">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="60e0f-463">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="60e0f-464">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-465">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-465">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-466">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-468">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-468">Informational (4)</span></span>|  
|<span data-ttu-id="60e0f-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="60e0f-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="60e0f-470">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-471">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-472">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-472">Event</span></span>|<span data-ttu-id="60e0f-473">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-473">Event ID</span></span>|<span data-ttu-id="60e0f-474">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="60e0f-475">11</span><span class="sxs-lookup"><span data-stu-id="60e0f-475">11</span></span>|<span data-ttu-id="60e0f-476">並行記憶體回收執行緒已建立。</span><span class="sxs-lookup"><span data-stu-id="60e0f-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="60e0f-477">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-477">No event data.</span></span>  
  
 [<span data-ttu-id="60e0f-478">回到頁首</span><span class="sxs-lookup"><span data-stu-id="60e0f-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="60e0f-479">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="60e0f-480">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="60e0f-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="60e0f-481">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="60e0f-481">Keyword for raising the event</span></span>|<span data-ttu-id="60e0f-482">層級</span><span class="sxs-lookup"><span data-stu-id="60e0f-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="60e0f-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="60e0f-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="60e0f-484">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-484">Informational (4)</span></span>|  
|<span data-ttu-id="60e0f-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="60e0f-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="60e0f-486">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="60e0f-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="60e0f-487">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="60e0f-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="60e0f-488">事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-488">Event</span></span>|<span data-ttu-id="60e0f-489">事件 ID</span><span class="sxs-lookup"><span data-stu-id="60e0f-489">Event ID</span></span>|<span data-ttu-id="60e0f-490">引發的時機</span><span class="sxs-lookup"><span data-stu-id="60e0f-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="60e0f-491">12</span><span class="sxs-lookup"><span data-stu-id="60e0f-491">12</span></span>|<span data-ttu-id="60e0f-492">並行記憶體回收執行緒已終止。</span><span class="sxs-lookup"><span data-stu-id="60e0f-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="60e0f-493">沒有事件資料。</span><span class="sxs-lookup"><span data-stu-id="60e0f-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e0f-494">請參閱</span><span class="sxs-lookup"><span data-stu-id="60e0f-494">See Also</span></span>  
 [<span data-ttu-id="60e0f-495">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="60e0f-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
